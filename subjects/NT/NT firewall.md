---
alias: firewall
definition: monitors in/outcoming traffic based on predetermined rules
type: term
port: N/A
OSI-layer: multiple
more-info: "https://en.wikipedia.org/wiki/Firewall_(computing)"
---
[[NT Networking MOC]]
[[NT Cisco]]
[[LX iptables]]

### sources

[[net3-p1w2-theorie-firewalls.pdf]
![[net3-p1w3-theorie-iptables.pptx]]
![[net3-p1w2-theorie-firewalls.pptx]]
### theorie

een soort hindernis, die ervoor zorgt dat er geen ongewenst verkeer naar het interne netwerk kan komen

Het woord ‘firewall’ is afkomstig van de autoindustrie. 
Een firewall bevindt zich tussen de passagiersruimte en de motorkap. Wanneer de motor vuur zou vatten, beschermt de firewall de chauffeur en de passagiers tegen de vlammen.

firewall gebruikt volgende technieken om zijn doel te bereiken

- controle van internet trafiek
- [[NT ACL|ACL]] (toegangslijsten)
- [[NT proxy server|proxy server]]

firewalls zijn gebaseerd op een identify and trust principe
-> we identificeren herkomst v verkeer en op basis daarvan laten we het verkeer wel of niet doorgaan

eerst valkuil in dit principe is het moeilijk identificeren van de "identiteit" van de herkomst van het verkeer]
hoe kan ik zeker weten dat deze werkelijk van het ip adres afkomstig dat meegegeven is in de header

firewalls kunnen ook vanbinnen uit werken
bv om het gebruik van bepaalde applicaties en diensten te beperken en/of te loggen binnen een netwerk

minimale firewall is opgebouwd uit volgende componenten

- [[NT ACL|ACL]] 
- application wrappers
- self policing (beveiliging van de server zelf)

- een [[NT TCP]] pakket bestaat uit volgende informatie
	- bron IP adres -> [[NT DHCP|DHCP]] of fixed
	- bron poort -> random toegewezen, > 1023
	- bron [[NT MAC address]]
	- doel IP adres -> [[NT DNS]]
	- doel poort -> well known ports
	- doel [[NT MAC address]]
		- binnen [[NT LAN]]: via [[NT ARP]] 
		- buiten [[NT LAN]]: via 
- wanneer het packet is opgemaakt wordt er via de client & server, of via 2 hosts een verbinding opgezet met de [[NT 3-way handshake|3-way handshake]]
- de verbinding wordt stop gezet door een FIN of RST [[NT packet|packet]] te sturen
	- dit soort pakketen kan gestuurd worden "in naam van jou" met een vals (door [[NT spoofing|spoofing]]) server adres
	- verhinderd door [[NT stateful|stateful]] te werken en dus extra data en statussen bij te houden van het verkeer op het netwerk 


### configuratie & gebruik

een simpele firewall rule zou er (als opbouw) als volgt kunnen uitzien

TCP SYN, IN gt 1024 80 any ip address

- TCP: het protocol van de verbinding, kan ook [[NT UDP|UDP]] zijn
- SYN: het type packet, hier dus het opzetten van de verbinding
- IN: IN of OUT trafiek van het netwerk
- gt 1023: de destination poort van het verkeerd is groter dan 1023, refereert dus naar een simpele host
- 80: source port van het verkeer, [[NT HTTP|HTTP]] trafiek dus

!any IN elke poort elke poort 200.2.2.0/24 200.2.2.0/24

- anti spoofing firewall rule
- voorkomen dat iemand van buiten het netwerk een adres gebruikt dat binnen het netwerk hoort te zijn

[[NT ICMP|ICMP]] redirect

- aangeven dat er een betere route is om packet naar die destination te sturen
- maar wordt misbruikt, door alle ICMP verkeer via een bepaalde host te laten passeren waardoor dit verkeerd dus gemanipuleerd kan worden -> zelf ICMP redirects sturen en verkeer misleiden

!ip IN,OUT sourcerout - any any

-> firewall regel die [[NT source routing|source routing]] aangeeft

[[NT DNS|DNS]] firewalls

UDP OUT gt 1023 53 any 8.8.8.8 (adres [[IT Google|Google]] [[NT DNS|DNS]])

- externe DNS 
	- beperken welke externe DNS servers toegelaten zijn

TCP SYN, IN any 53 8.8.8.8 adres-interne-dns

- beperken welke externe DNS servers parents zijn van jouw DNS server

gebruik van [[NT stateful|stateful]] firewalls bij [[NT Cisco|Cisco]] door het gebruik van de reflect en evaluate commando's

```
interface FastEthernet 0/0
ip access-group INKOMEND in
ip access-group UITGAAND out
 
ip access-list extended UITGAAND
permit tcp any any reflect TCPVERKEER
 
ip access-list extended INKOMEND
permit icmp any any
deny udp any any
evaluate TCPVERKEER
```

 
### mogelijke examenvragen

- [[NT IP spoofing]], 
- [[NT source routing]], 
- [[NT ICMP redirect]], 
- actieve [[NT FTP|FTP]], 
- passieve [[NT FTP|FTP]],
  
- statefull filtering, statefull inspection,
- Je krijgt een firewall regel (of enkele regels) en je moet de functie ervan kunnen verklaren (zeggen wat ze doen en hoe ze werken).
- Leg het verschil uit tussen de werking met een interne en een externe [[NT DNS|DNS]]
- Hoe werkt een [[NT redlan]] en een [[NT bluelan]].
- Wat betekent de optie RELATED bij het gebruik van FTP bij [[LX iptables]] ? Geef een voorbeeld.
- Wat betekent de optie ESTABLISHED bij gebruik van TCP bij [[LX iptables]]? Geef een voorbeeld
- Wat betekent de optie ESTABLISHED bij gebruik van UDP bij [[LX iptables]]?
- Wat betekent de optie RELATED bij gebruik van ICMP bij [[LX iptables]]? Geef een voorbeeld.
- Ik stuur met nemesis spoofed FIN en RST pakketten naar mijn firewall. Al mijn connecties in het interne netwerk worden afgesloten. Wat kan ik doen om dat te verhinderen?