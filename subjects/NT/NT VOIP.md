---
alias: VOIP
definition: voice over IP
type: technology
port: N/A
OSI-layer: application
more-info: ""
---
[[NT Networking MOC]]

### info

klassieke telefoonnetwerk gebruikte door de jaren 3 technologieen
- PSTN = Public Switched Telephone Network
- [[NT E.164|E.164]] = standardized nummer plan for PSTN
- DTMF = Dual Tone Multi Frequency "touch tones"

wat is VoIP = traditionele telefoongesprekken over het Internet protocol
- bestaat uit 2 kanalen
	- controlekanaal
		- om verbinding op te zetten
	- mediakanaal
		- doorsturen geencodeerde voice data

VoIP protocollen
- [[NT RTP]]
- [[NT SIP]]
- [[NT SCCP]] - [[NT Cisco|Cisco]] protocol
- Skype - eigen protocol gebaseerd op Kazaa
- [[NT XMPP]] - XML gebaseerd

voice codecs
- zelfde codec gebruikt bij H.323 & SIP
- kleine [[NT packet|packet]]en : 50 tot 250 bytes
- standaard voor voice codecs = G.7xx
	- G.711: 64 kbps (Pulse Code modulation) ▶ how to voice is modulated from analog to binary
	- G.726: 16-40 kbps (adaptive differential PCM)
- codecs worden niet door iedereen ondersteunt

probleem VoIP met [[NT firewall|firewall]]
- controle en media stream volgen verschillende weg ▶ geen status dus firewall blokt 

problemen [[NT NAT|NAT]]
NAT breekt SIP controlekanaal
media kanalen van VoIP gaan uit van end to end internet, niet NAT ▶ kan leiden tot enkelrichting audio
[[NT ENUM|ENUM]] 

oplossingin NAT
protocol aware firewall gebruiken
media proxy op application niveau gebruiken

[[NT STUN|STUN]] = Simple Traversal of UDP through NAT



beveiliging
- fysiek scheiden van data & voice geeft beste veiligheid, maar vraagt grotere investering
- gebruik van zelfde fysieke infra, maar logisch gescheiden via VLANs

- SIP protocol
	- geen authenticatie
	- geen integriteit
	- geen confidentialiteit
- wel een secure SIP protocol
	- authenticatie met X.509 certs
	- met integriteit en confidentialiteit
- signaal beveiliging kan gegarandeerd worden via [[NT TLS|TLS]] 
	- bi directionele PKI voorziet authenticatie
		- gedeelde secret uitgewisseld met RSA
		- berekent Hashed Message Authentication Code (HMAC) ▶ MD5 of SHA1
	- HMAC voorziet integreteit
	- encryptie geen confidentialiteit

### commandos

DHCP adressen laten uitdelen door router

```
Router(config)#ip dhcp pool voiptest
Router(dhcp-config)#network 192.168.10.0 255.255.255.0
Router(dhcp-config)#default-router 192.168.10.1
Router(dhcp-config)#option 150 ip 192.168.10.1
Router(dhcp-config)#exit
```

Configuratie VoIP router

```
Router(config)#telephony-service
Router(config-telephony)#max-dn 24           
Router(config-telephony)#max-ephones 24    
Router(config-telephony)#ip source-address 192.168.10.1 port 2000
 Router(config-telephony)# auto assign 1 to 24
Router(config)#ephone-dn 1                                                        
Router(config-ephone-dn)#number 501 
                          
Router(config)#ephone-dn 2 
Router(config-ephone-dn)#number 502

Router(config)#ephone-dn 3
Router(config-ephone-dn)#number 333
```

Configuratie switch

```
Switch(config)#interface range fa0/1 – 24
Switch(config-if-range)#switchport mode access
Switch(config-if-range)#switchport voice vlan 1
```

