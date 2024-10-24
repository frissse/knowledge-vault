---
alias: iptables
usage: sudo iptables --verbose --numeric --list --line-numbers 
example: sudo iptables --policy chain rule 
definition: administration tool for IPv4/IPv6 packet filtering and NAT
type: bash-command
subject: security
more-info: "https://www.man7.org/linux/man-pages/man8/iptables.8.html"
---
 
[[LX command]]
[[NT Networking MOC]]

### sources

![[net3-p13-theorie-iptables.pptx]]

### theorie

	standaard geinstalleerd op linux systemen
"tabellen" die gemaakt zijn om pakketen te verwerken op verschillende niveaus
- filter: meest gebruikt
- raw: low level pakket aanpassingen -> 
  The raw table is primarily used to mark packets that should not be tracked by the connection tracking system
- [[NT NAT|NAT]]: ip tables kan ook NAT vertaling doen 
- mangle: aanpassen van de [[NT TTL]] & markeren van een pakket voor routering

de filtering gebeurt op basis van chains(ketens), je kan ook CUSTOM chains aan maken
- INPUT: binnenkomend verkeer
- OUTPUT: uitgaan verkeer
- FORWARD: doorgaand verkeerd

je formuleert regels op basis van de ketens, deze worden in volgorde overlopen
-> wanneer pakket voldoet aan bepaalde regel wordt de bijhorende actie ondernomen: --jump
- -j LOG pakket loggen
- -j ACCEPT pakket toelaten
- -j DROP pakket weggooien
- -j REJECT pakket weigeren met een foutmelding
-> wanneer geen enkele regels matched valt het terug op de default regel

op [[LX linux MOC|linux]] systemen staat de `iptables -P INPUT ACCEPT` = "kom allemaal gezellig binnen"


de 127.0.0.1 in de "ogen" van de firewall is ook verkeer

<u>custom chains</u>

aanmaken van eigen chainsm
bv voor TCP verkeer filter (zie [[#examples]])

[[NT stateful|stateful]] configuratie -> beslissingen maken op basis van de current state van de connectie -> NEW | ESTABLISHED

iptables -A OUTPUT -p tcp -m state --state NEW,ESTABLISHED -j ACCEPT

RELATED kan ook gebruikt worden als optie
-> laat ook gerelateerde [[NT ICMP|ICMP]] berichten door

[[NT UDP|UDP]] kan in principe nooit stateful zijn

maar kan met ip tables "pseudo" stateful gemaakt worden
bv. bij DNS weet je dat er als er een aanvraag verstuurd wordt een antwoord wordt verwacht, ip tables stelt hier een timer in (zie [[#examples]])

<u>module limit</u>
- vaak gebruikt voor [[CS DoS]] attacks / SYN floods
- "krediet": door de limit-burst parameter wordt er een maximale aantal "connectie" gedefinieerd
- wanneer de limiet krediet is opgebruikt, wordt per limit tijd extra krediet toegelaten

### configuratie & gebruik

<u>opbouw van een IPTABLES rule:</u>

`iptables [-I | -A] [INPUT | OUTPUT] [[ -s | -d ] [-p | --tcpflags] | -m [ state | limit [ --limit /s /m /h /d ]] |[--dport | --sport]] -j [LOG [ --log-prefix ]| ACCEPT | DROP | REJECT ] ` 

-I of -A: insert of append de regels (zet bovenaan of onderaan de lijst)
INPUT of OUTPUT: regels gaat over inkomend of uitgaan verkeer

-s of -d, -p, --dport of --sport
= parameters voor filtering verkeer
- -s of -d: source of bron adres
- -p: protocol 
	- --tcp-flags: ALL FIN PSH URG
- --dport of --sport: source of destination port

-j: actie te ondernemen


<u>best practices</u>
- schrijf een script die de regels in 1 keer toevoegd
- flush eerst alle regels (default blijft staan)
  ```
	iptables -F INPUT
	iptables -F OUTPUT
	```
- regels met zwaar verkeer komen zo vroeg mogelijk in tabel
- standaard [[NT TCP|TCP]] regels in 1 regel gieten (80 + 443 poort)
- state & conncetion modules gebruiken voor established verkeer
- wanneer er gelogd worden: 1st loggen, dan droppen (zie [[#examples]])


<u>overige commands</u>

| command               | explanation                             |
| --------------------- | --------------------------------------- |
| iptables -L           | show the iptables running on the system |
| iptables -F           | verwijder regeles (flush)               |
| iptables -N chainname | aanmaken van een nieuwe chain           |

### examples

`iptables -A INPUT -p tcp --dport 80 -j ACCEPT`

-> append regel aan de list die inkomend TCP verkeer op poort 80 toelaat

`iptables -A INPUT -p tcp --dport 80  -s 10.1.1.2 -j ACCEPT`

-> specifiekere filtering dan hierboven, want filter op basis van source IP adres

`iptables -N TCPFILTER`
`iptables -A INPUT -p tcp -j TCPFILTER`

-> aanmaken van een eigen chains en deze gebruiken voor inkomend tcp trafiek

`iptables -A TCPFILTER -p tcp --tcp-flags ALL FIN,PSH,URG -j DROP`

-> blokken van XMAS portscan

`iptables -A OUTPUT -p udp -d 8.8.8.8 --dport 53  -m state --state NEW,ESTABLISHED -j ACCEPT`
`iptables -A INPUT-p udp -s 8.8.8.8 --sport 53 -m state --state ESTABLISHED -j ACCEPT`

-> een pseudo stateful [[NT UDP|UDP]] packet filtering voor [[NT DNS|DNS]] trafiek 

`iptables -A INPUT -p tcp --dport 80 -j ACCEPT`
`iptables -A OUTPUT -p tcp -m state --state ESTABLISHED -j ACCEPT

-> basic webserver traffic filtering met een filtering op outgoing traffic met de state als ESTABLISHED
zorgt er eigenlijk hiervoor dat de webserver enkel op bestaande verbindingen packetten kan terug sturen maar zelf geen nieuwe verbindingen kan starten

```
iptables -A INPUT --source 10.1.1.0/24 --destination 	10.1.1.0/24 -j DROP  
```

-> anti spoofing: blocken van trafiek die het source als destination network bevat "niemand van extern netwerk kan hetzelfde hebben als een inter netwerk"

`iptables -A INPUT -p tcp --sport 1024:65535 --dport 1024:65535  -m state --state ESTABLISHED -j ACCEPT`
`iptables -A OUTPUT -p tcp --sport 1024:65535 --dport 1024:65535   -m state --state ESTABLISHED,RELATED -j ACCEPT`

-> passieve FTP met ICMP foutmeldingen allowed 

`iptables -A INPUT --source 200.2.2.0/24 --destination 200.2.2.0/24 -j LOG --log-prefix "Spoofing-DROP: "`
`iptables -A INPUT --source 200.2.2.0/24 --destination 200.2.2.0/24 -j DROP`

-> voorbeeld van hoe een logging regel voor anti spoofing opbouwen en erna wordt het pakket gedropt

`iptables -A INPUT  -p tcp -j LOG --log-prefix "IPTABLES TCP-INPUT: "`
`iptables -A OUTPUT -p tcp -j DROP`

-> TCP verkeer dat niet voldoet aan eerder regels worden gelogd en dan gedropt

### oefening

FINALE script

```
#!/bin/bash

if [ $(id -u) -ne 0 ]; then
	echo "script must be run as root"
	exit 1

fi

iptables -F INPUT
iptables -F OUTPUT
iptables -Z
iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -A OUTPUT -p tcp --destination-port 80 -j ACCEPT
iptables -A INPUT -p tcp --source-port 80 --dport 1025:65535 -j ACCEPT
iptables -A OUTPUT -p udp --dport 53 -d 8.8.8.8 -j ACCEPT
iptables -A OUTPUT -p tcp --dport 53 -d 8.8.8.8 -j ACCEPT
iptables -A INPUT -p udp --sport 53 -s 8.8.8.8 -j ACCEPT
iptables -A INPUT -p tcp --sport 53 -s 8.8.8.8 -j ACCEPT
iptables -A OUTPUT -p udp -d 8.8.8.8 --dport 53  -m state --state NEW,ESTABLISHED -j LOG --log-prefix "UDP iptables"
ip6tables -A INPUT -p icmpv6 --icmpv6-type echo-request -j DROP
iptables -A INPUT -p icmp --icmp-type echo-request -j ACCEPT
iptables -L -n -v
```

NODIG: 

2 Linuxen (mag live),
Je kan via het Clone commando eenvoudig een virtuele machine clonen
sudo apt install apache2 openssh-server vsftpd filezilla putty lynx
Voor de oefening is het handig om binnen de virtuele machines 8.8.8.8 als DNS server in te stellen.

OPGAVE

1. Zorg bij beide virtuele machines minstens voor een netwerkkaart van het type "Host Only" en vboxnet0 (daarbuiten mag je ook nog een "NAT" netwerkkaart hebben, zodat je bijvoorbeeld nog op internet kan. Stel bij de Advanced settings de netwerkkaart in met Promiscuous op Allow All, zodat je kan sniffen. 

2. Netwerkverbinding testen:
a) Ping van de machine A naar machine B.
Om te kijken of het sniffen werkt start je op machine B het programma tcpdump.
Stel nu je ping in zodat je 100 pings per seconde doet. Met welk commando kan dit?

op machine 1:`ping -i 0.01 ip-mach-2`
op machine 2: `sudo tcpdump -i <host only interface>`

b) Doe een [[LX nslookup]] van bv www.kdg.be
Je moet een antwoord van een DNS server krijgen met het IP adres van www.kdg.be

 Iptables zit in de kernel gecompileerd. Standaard komt de iptables log dus terecht in de systeemlog /var/log/syslog en/of in de kernel log /var/log/kern.log

3. Maak het script iptables.sh aan. Hiermee kan je alle firewallregels met één script instellen.

Start met dit script (dat moet je als root uitvoeren):

iptables -F INPUT
iptables -F OUTPUT
iptables -Z
iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -A OUTPUT -p tcp --destination-port 80 -j ACCEPT
iptables -A INPUT -p tcp --source-port 80 --dport 1025:65535 -j ACCEPT
iptables -L -n -v

4. Welke iptables commando's aan het begin van het script maken alle chains leeg?

iptables -F INPUT
iptables -F OUTPUT

6. Welke iptables commando's aan het begin van je script stellen alle default policies in op DROP?

iptables -P INPUT DROP
iptables -P OUTPUT DROP

7. We gaan nu de UDP aanvraag voor de nslookup loggen met iptables. Zoek zelf op met welke iptables regel je dit kan doen. gebruik een eigen log-prefix 'UDP IPTABLES' . Kijk na of je nslookup gelogd wordt.

 sudo iptables -A OUTPUT -p udp --dport 53 -j LOG --log-prefix "DNS Request: "

9. Test op de Host Only interface een ip v6 ping uit tussen de machines (bv ping -6 -I enp0s8 fe80......)
Schrijf regels die wel een v6 ping blokkeren maar niet een v4 ping



8. Installeer het tooltje nemesis. Opgelet deze gebruikt ook het pakket libnet1 (zie referentie) Zoek op met welk commando je een DNS aanvraag kan doen. Doe opnieuw een DNS aanvraag. (man nemesis-dns geeft een manual page)


9. Maak een iptables regel waarmee je een limiet legt op het aantal icmp pakketten per seconde. Stel maximum 1 per seconde in met een burst van 5. Log dit met prefix 'ICMP IPTABLES'. Test nu uit of je ping van 100 per seconde gedetecteerd wordt.

10. Schrijf een loopscriptje in shell dat met nemesis-icmp pings doet (deze pings wachten niet op een reply en zullen dus zo snel mogelijk uitgevoerd worden). 

11. Maak met nemesis nu een DNS request met als SRC en DST adres je eigen adres. Komt er iets speciaal in de log?


12. Schrijf iptables regels voor udp die enkel udp verkeer toelaat naar binnen, dat je zelf hebt aangevraagd. Bij uitbreiding zorg je er ook voor dat deze regel niet geldt voor een lokale interface.

13. Voer het commando iptables -n -L INPUT uit. Wat krijg je te zien?

14. Stel een zo strikt mogelijke ACL in op je Linux waarmee je zorgt dat je Linux kan pingen naar een andere computer, maar niemand naar je Linux.

15. Installeer en start de apache webserversudo apt-get install apache2/etc/init.d/apache2 start(Kijk even na in een browser of er op jou IP adres een website draait)Zorg er nu, via iptables voor dat mensen die op poort 8080 verbinden ook de website te zien krijgen van poort 80.

16. Installeer een ftp server (bv vsftpd) Installeer en start wireshark.
a) Test uit of je een passieve ftp sessie kan starten naar je server (als gui kan je filezilla installeren).Bekijk in wireshark de initiele handshake tussen de client en de FTP server.Noteer volgende informatie van alle pakketten en de richting:SRC IP/SRC PORT/DST IP/DST PORT
b) Test uit of je actieve ftp kan starten naar de serverBekijk in wireshark de initiele handshake tussen de client en de FTP server. Noteer volgende informatie van alle pakketten en de richting:SRC IP/SRC PORT/DST IP/DST PORT. Schrijf zo strikt mogelijke regels 

17. Installeer en start de ssh server openssh-server

Start de apache webserver op poort 8080 in plaats van de standaard poort 80.
Test uit of je vanaf de client kan surfen naar 8080
Start de openssh server. Test uit of je met je client kan verbinden naar poort 22 (ssh)
