---
alias: networking documentation
type: documentation-writeup
---
[[NT Networking MOC]]
#school 

### sources

![[net3-p1w1-theorie-tcpip-herhaling 4.pptx]]

![[net3-p1w1-theorie-LAN-WAN-verbinding-slides 4.pptx]]

![[net3-p1w1-theorie-tcpip-osimodel 4.doc]]

[[net3-p1w2-theorie-vyos 1.odp]]

[[net3-p1w3-config-vyos-firewall.pdf]]

[[net3-p1w4-theorie-DSL-Kabel-Fiber.odt]]

[[net3-p1w4-theorie-kabel-fiber.pptx]]

[[net3-p1w4-theorie-wireless-WLAN.pptx]]

![[net3-p1w5-theorie-ATM_BGP_FR_MPLS 1.pptx]]

![[net3-p1w5-theorie-bluetooth 1.pptx]]

![[net3-p1w5-theorie-ir 1.pptx]]

![[net3-p1w5-theorie-rfid 1.pptx]]

![[net3-p1w5-oef-ipv6.odt]]

![[net3-p1w5-theorie-cursus-ipv6.odt]]

![[net3-p1w5-theorie-ipv6.pptx]]

![[net3-p1w6-theorie-voip.pptx]]

[[net3-p1w6-theorie-gsm.pdf]]
### example networks

[[Pasted image 20240924122943.png]]

![[Pasted image 20240925084720.png]]

[[Pasted image 20240925093651.png]]


### mogelijke examen vragen



PROXY
Begrippen: 
- Disk cache, 
- non-cacheble, 
- neighbour proxy, 
- parent proxy, 
- transparante proxy, 
- ICP

- Wanneer kan een proxy server een HIT/MISS hebben?
- Geef 3 voorbeelden van TTL waarden bij een proxy server.
- Waarvoor wordt SOCKS gebruikt?
- Waarvoor dient ICP?
- Aan de hand van Firewalls, proxy en LAN-WAN verbindingen moet je in staat zijn om een basis netwerk ontwerp te maken en verbeteren.

SNMP
Begrippen: 
- SNMP agent, 
- SNMP trap, 
- MIB, 
- ASN, 
- OID

- Geef een voorbeeld van een OID.
- Waarom zou je SNMPv3 gebruiken en niet SNMPv2?
- Waarom zou je SNMPv2 gebruiken en niet SNMPv3?
- Wat doet volgend commando: createUser authOnlyUser MD5 "secret007"
- Wat doet volgend commando: createUser authPrivUser SHA "geheim007" AES

HTTP3
Begrippen: 
- ossification, 
- 0-RTT, 
- TCP line blocking, 
- Connection Migration, 
- spin bit

- Op welke manieren kan HTTP3 HTTP2 versnellen?
- Wat is het probleem met het invoeren van een nieuw transportprotocol?
- Hoe wordt HTTP3 beschikbaar gesteld zodat een browser kan overschakelen naar QUIC?

### OSI MODEL lagen

#### (en|de)capsulatie doorheen het model

van [[NT OSI transport]] > [[NT OSI physical]]

het proces kan vergeleken worden met het doorgeven van een boodschp doorheen een bedrijf en bij elke stap wordt de boodschap in een nieuwe envelop gestopt, samen de envelop van de vorige stap

1. [[NT OSI application]]
2. [[NT OSI presentation]]
3. [[NT OSI session]]
4. [[NT OSI transport]]
5. [[NT OSI network]]
6. [[NT OSI data]]
7. [[NT OSI physical]]


![[Pasted image 20240917123407.png]]

### LAN-WAN verbindingen

welke elementen heb je sowieso nodig om een netwerk te kunnen opstellen

- [[NT router]]
- [[NT firewall]] 
- (traditionele) [[NT proxy server ]]
- transparante [[NT proxy server]]
- [[NT NAT]]

### [[NT NAT]]

### [[NT vyOS]]

### [[NT firewall]]

### [[NT DSL]], kabel & [[NT Fiber]]

[[NT asynchrone communicatie]]
[[NT synchrone communicatie]]
[[NT FDM multiplexing]]
[[NT Multiplexing TDM]]
[[NT Multiplexing statistical TDM]]
[[NT wavelength division multiplexing]]

[[NT simplex]]
[[NT half duplex]] 
[[NT full duplex]] 

[[NT baudrate]]
[[NT bitrate]]
[[NT scrambling]]

[[NT bandwidth]]
[[NT run length encoding]]
[[NT Huffmann encoding]]
[[NT Lempel-ziv compression]]

[[NT modulation]]
[[NT modem]] 

[[NT AM]] \
[[NT FM]]
[[NT PM]]
[[NT QAM]] 
[[NT amplitude]]
[[NT fase]]

[[NT ADSL]]
[[NT upstream]]
[[NT downstream]]
[[NT echo cancellation]]
[[NT DMT]]

[[NT DSLAM]] 
[[NT last mile]]
[[NT xDSL]]
[[NT CMTS]]
[[NT DOCSIS]] 
[[NT Hybrid Fibre Coax]]
[[NT Solitonen]]
[[NT PCS]]
[[NT powerline]]

- Wat is het verschil tussen het gebruik van TDM en STDM
- Leg uit hoe QAM modulatie werkt.
- Waarom is er bij de meeste internetverbindingen een verschil in upstream en downstream verkeer?
- Wat is er verbeterd bij ISP's in verband met ruis?
- Hoe werkt echo cancellation en wat kan je er mee doen?
- Waarvoor staat de A bij ADSL en wat betekent deze?
- Hoe werken subkanalen bij DMT modulatie?
- Wat zijn de belangrijkste verbeteringen bij ADSL2+
- Wat is een realtime Signaal/Ruis monitor?
- Welke aanpassingen moesten er aan de kabel gebeuren voor het gebruik van de nieuwe kabeldiensten ten opzichte van vroeger?
- Wat is HFC?
- Wat is dispersie en wat zijn silitonen?
- Wat is the last mile in verband met Powerline technology?
- Geef enkele voorbeelden van het gebruik van powerline technologie.
- Geef de belangrijkste verschillen tussen een circuit en een packet switched netwerk
### Wireless & Wireless security

1997 Originele 802.11 standaard 
	enkel SSID, MAC filter,  WEP (Wired Equivalent Privacy)
2001 Fluhrer, Mantin en Shamir ontdekken zwakheden WEP	 
	IEEE richt "Task Group i" op
2003 Wi-Fi (industriegroep) 
	Introductie Wi-Fi Protected Access (WPA)
		Tussenoplossing voor WEP
2004 WPA2
	Gebaseerd op IEEE 802.11i standaard 

[[NT ad-hoc topologie]]
[[NT infrastructure topologie]]
[[NT MANET]]
[[NT batman]] 

[[NT WLAN roaming]]
[[NT gain]] 
[[NT beamwidth]]

[[NT WiFi]]
[[NT NIC]]
[[NT access point|access point]]
[[NT switch]]
[[NT bridge]]

[[NT IEEE 802.11]]
[[NT WEP]]
[[NT WPA]]
[[NT SSID]]
[[NT TKIP]], 
[[NT MSCHAPv2]] 
[[NT MIC]]
[[NT LEAP]]
[[NT PEAP]] 
[[NT RADIUS]]
[[NT TLS|TLS]]

- Hoe werkt wireless roaming?
- Wat zijn de voornaamste wijzigingen bij 802.11ac ten opzichte van het huidige 802.11n protocol? 
- Wat zijn de nadelen van WEP
- Wat of wie ;-) is Michael?
- Hoe werkt het wireless KdG netwerk?
- Wat is de functie van een RADIUS server?

### [[NT bluetooth]], [[NT IR]] & [[NT RFID]]

- RFID tag, 
- Actief, Passief, Semi-Actief
- frequency hopping, 
- piconet
- scatternet

- Wat zijn de nadelen van RFID
- Geef 3 voorbeelden RFID een van Actief, Passief en Semi-Actief
### [[NT ATM]] [[NT BGP]] [[NT FR]] [[NT MPLS]]

- PVC, 
- SVC, 
- UNI, 
- NNI, 
- Cell Loss Priority,
- VCI, 
- VPI, 
- AS, 
- CIDR, 
- prefix
- network provisioning, overlay network
- DCE, 
- DTE, 
- SVC, 
- PVC, 
- DLCI
- LSP, 
- LSR, 
- LER, 
- label substitution

- Vergelijk een circuit switched met een packet switched netwerk
- Wat is het verschil tussen X.25 en Frame Relay?
- Wat is het verschil tussen LAP-B en LAP-F?
- Waarvoor wordt LMI gebruikt?
- Vergelijk Frame Relay met ATM
- Wat is label substitution?
- Hoe kent MPLS een label toe bij ATM, Frame Relay of andere protocollen?
- Hoe worden de MPLS labels doorgestuurd?
- Op welke 2 manieren kan een LSP worden opgezet bij MPLS?
- Wat is het verschil tussen een LER en een LSR bij MPLS?
- Bespreek bondig de header van een ATM cel.
- Wat is het verschil tussen UNI en NNI? Waarom is er een verschil?
- Geef de soorten ATM Adaption Lagen en geef een voorbeeld van het gebruik bij elk type.
- Waarom is ATM niet meer zo populair?
- Mag je de nummer van een AS kiezen? Verklaar.
- Wat is het voordeel van het gebruik van CIDR?
- Hoe bepaalt BGP welke netwerken hij in zijn tabel opneemt?
- Hoe kan BGP misbruikt worden om internet verkeer te onderscheppen?

### [[NT IPv6|IPv6]]

IPv6
Begrippen:
- link local adres, 
- unique local adres, 
- fragmentatie, 
- MTU, 
- QoS, 
- label

- Welke 3 soorten adressen kent IPv6? Geef een voorbeeld van hun gebruik.
- Waarvoor dienen zones?
- Mijn Windows IPv6 adres ziet er als volgt uit: fe80::250:56ff:fec0:8%1 Wat betekent fe80? Wat betekent %1? Wat betekent :: ?
- Mijn IPv4 adres in windows is 169.254.12.134. Wat betekent dit? Hoe werkt dit systeem in IPv6?
- Waarom is het uitbreiden van de header een voordeel bij IPv6 tov IPv4?
- Waarom bestaat 'Time To Live' niet meer bij IPv6?
- Wat doe je als IPv4 de té grote pakketten niet kan slikken?
- Hoe werkt stateless autoconfiguration?
- Hoe werkt statefull autoconfiguration?
- Hoe werkt autoconfiguratie bij mobiele toestellen?
- Geef kort de 5 belangrijkste wijzigingen bij IPv4 tov IPv6.

#### oefening

1. Start als root tcpdump (sudo apt-get install tcpdump) op je loopback interface
	Installeer een openssh server op Linux (apt-get install openssh-server)
	a) Test de verbinding uit naar je ssh server op 127.0.0.1 (IPv4)
	`tcpdump -i lo`
	b) Maak een verbinding naar je ssh server op ::1 (zoek op met man ssh).
	`ssh -6 aw@::1`
	c) Verifieer met tcpdump of wireshark dat de communicatie over IPv6 loopt.
2. Pas je apache configuratie aan zodat deze ENKEL werkt met ipv6. Werkt dit?
	Hoe geraak je in je browser aan een ipv6 website?

	voeg toe aan de ports.conf voor apache2: `/etc/apache2/ports.conf` 

	`Listen [ : : ]:80` (zonder spaties)
	en verwijder de Listen op de [[NT IPv4|IPv4]] poort 80

	vervolgens voeg je dit toe aan de .conf file 

	```bash
	<VirtualHost [::]:80>
	ServerName mijnserver.local
	ServerAlias www.mijnserver.local
		DocumentRoot /var/www/html
	</VirtualHost>
	```
	

3. Firewall regels
	a) Bekijk je IPv6 adres in Linux met het commando ip
	Zorg dat je enkel de v6 adressen krijgt 

	`ip -6 a`

	b) Geef linux met het commando ip, het adres 2001::1
	Geef je host op de juiste interface het adres 2001::2

	enable ipv6 on the interface first
	`sysctl -w net.ipv6.conf.vboxnet0.disable_ipv6=0`

	vervolgens
	`ip -6 addr add 2001::1/64 dev vboxnet0`

	c) Ping vanuit linux naar je host IPv6 2001::2. `ping6 -I enp0s8 2001::2`
	d) Bekijk de default IPv6 firewall regels in Ubuntu.
	e) Voeg een regel toe met ip6tables om deze ping (en énkel deze ping) te verbieden.
4. Vyos
	Stel Vyos in zodat deze via Router Advertisements IPv6 adressen uitdeelt.
	Opgelet NIET als DHCPv6 server! Laat deze adressen uitdelen in het IPv6 subnet van
	student.kdg.be (`2001:06A8:0540:0101:: / 64`) 

	```
	set service router-advert interface eth1
	set service router-advert interface eth1 name-server 2001:06A8:0540:0101::8888
	set service router-advert interface eth1 prefix ::/64
	set service router-advert interface eth1 prefix ::/64 valid-lifetime '86400'
	set service router-advert interface eth1 prefix ::/64 preferred-lifetime '14400'
	```

	Geef de Host-Only netwerkkaart ook een adres in die range.
	Zorg dat je alle parameters instelt bij de router-advert.
	Stel de valid-lifetime in op 2592000 en de preferred-lifetime op 2073600
	
5. Voorzie een Linux client (NAT, Host-Only)
	Zorg er via de commandline voor dat de Linux client een IPv6 adres krijgt van de VyOS Router.
	Noteer de commando's die je nodig hebt:
	`accept-ra: true ` toevoegen aan de netplan config fuile
	Om een een ip versie 6 te bekijken: `ip -6 a`
	Om via dhcpv6 (of Router Advertisements) een adres te bekomen:
	Om de ip versie 6 route te bekijken: `ip -6 route `
	Om een ip versie 6 ping uit te voeren: `ping6 <ipv6 adres>`
6. Configureer VLC als streaming server
	a) Laat vlc (sudo apt-get install vlc) een film over http streamen (IPv6)
	a) Gebruik nmap om na te kijken of de IPv6 poort open staat
	(zoek op met man nmap)
	b) Gebruik op dezelfde machine als client smplayer.
	(sudo apt-get install smplayer)
	Deze moet de IPv6 stream kunnen bekijken.
	c) Gebruik tcpdump of wireshark om te verifiëren dat smplayer IPv6 gebruikt.
7. Multicast?
	Kijk na of je ook vlc in IPv6 kan laten multicasten (bv via FF15::1).

### [[NT VOIP]]

[[NT SIP]] 
[[NT STUN]] 
[[NT PBX]]
[[NT RTP]] 
[[NT SuperNode]]

- Wat is de functie van SIP?
- Hoe werkt ENUM
- Hoe kan je het NAT/PAT probleem oplossen voor VoIP?
- Hoe geraakt Skype door een firewall?
- Hoe wordt een gesprek gestart tussen 2 VoiP toestellen?
#### oefening

DOEL: Configuratie VoIP met Cisco  
NODIG: Packettracer  
REF: http://www.packettracernetwork.com/advanced-network-features/voip/  
voipconfiguration.html  

Voer de configuratie van de referentie uit. Kijk na of je kan bellen!  
http://www.packettracernetwork.com/advanced-network-features/voip/  
voipconfiguration.html

### [[NT GSM]]

[[NT 2G|2G]]
[[NT GPRS|GPRS]](2.5G)
[[NT EDGE]](2.5G)
[[NT 3G|3G]]
[[NT 4G|4G]]

- TDMA, 
- CDMA, 
- HLR, 
- VLR, 
- soft-, softer- hard-handover
- HARQ, 
- Beamforming

- Je hebt in het buitenland een GSM gesprek. Hoe weet diegene die belt, waar je je bevind?
- Wat is tromboning? Kan er iets tegen gedaan worden?
- Wat zijn de zwakheden bij de veiligheid van het huidige GSM netwerk?
- Welke aanpassing was er nodig aan het GSM netwerk voor het gebruik van WAP?
- Waarom is GPRS verkeer sneller dan GSM verkeer?
- Wat zijn de nadelen van GPRS?
- Waar gebruikt UMTS FDD?
- Waar gebruikt UMTS TDD?
- Waarom is UMTS sneller dan GPRS?
- Wat is CDMA spreading en despreading?
- Hoe werkt OFDM?
- Waarom is Power Control belangrijk bij UMTS?
- Wat is het verschil tussen een soft en een softer handover?
- Wat is cell breathing?
- Hoe werkt een Rake receiver?

Wat zijn Dual Mode GSM's?