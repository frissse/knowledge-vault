---
alias: IPv6
definition: Internet Protocol v6
type: protocol
port: N/A
OSI-layer: Network
more-info: "https://en.wikipedia.org/wiki/IPv6"
---
[[NT Networking MOC]]
[[NT protocol]]
[[NT OSI network]]

### info

huidige situatie [[NT IPv4|IPv4]]:
- 32 bit adressen zijn op
- routing tabellen zijn te groot (400k rijen)
- heeft geen packet beveiliging as default
- realtime ondersteuning beperkt ([[NT QoS|QoS]])

verschil IPv4 en IPv6

| IPv4                                            | IPv6                                                                                      |
| ----------------------------------------------- | ----------------------------------------------------------------------------------------- |
| 32 bit                                          | 128 bit                                                                                   |
|                                                 | addressen zijn meer hierarichisch opgebouwd<br>multicast & anycast adressen zijn mogelijk |
| header is leeg wanneeer geen informatie gegeven | header met optionele velden                                                               |
|                                                 | uitbreidbare header, werkt met pointers                                                   |
|                                                 | mogelijkheid tot het labelen van de traffic,<br>voor QoS purposes                         |
|                                                 | authenticatie en privacy ingebouwd                                                        |

addressering bij IPv6

3 opties:
- Unicast
	- 1 adres per interface
- Anycast
	- groep interfaces
- Multicat
	- afleveren bij alle interfaces
	- soort van broadcast

soorten adressen
- link-local
	- FE80::/10 huidige private addressen
	- geldt enkel binnen een link/organisatie (gebaseerd op het [[NT MAC address|MAC address]])
- unqiue local
	- FC00::/7
	- bevat pseudo random 40 bit nummer
- multicast
	- FFxx (begint steeds met FF)
- loopback
	- ::1 

Ipv6 werkt met zones, extra informatie om routering te vergemakkelijken 
- windows: FE80::3%1
- linux: FE80::3eth0

IPv6 header

![[screenshot_3.png]]

verdwenen (tov IPv4):
- header length
- identification flags
- fragment offset
- header checksum
veranderd (tov IPv4)
- TTL > Hop Limit
- options > extension headers
- type of service > traffic class
- no header checksum: IPv6 gaat ervan uit de de integriteit check gebeurd door higher layer protocols

nieuw bij IPv6 is de uitbreidingsheader (Next Header)
a flexible, modular approach to packet processing
-> extra informatie wordt meegegeven in een extra deel van het IP packet ipv lege informatie bij IPv4
de Next Header kan volgende informatie bevatten
- Hop-by-Hop Options header
	opties voor tussenliggende nodes
- routing header
	- source routing
- fragment header
	- pakket met grotere MTU (max transfer unit) fragmenteren
	- gebeurt enkle bij de source en niet onderweg zoals bij IPv4
- destination options header
	- veiligheid opties
- authenticatie/encryptie headers
- When there are no additional IPv6 extension headers, the Next Header field specifies the protocol used by the upper-layer (e.g., TCP, UDP, ICMPv6).
- Each extension header also has its own Next Header field to continue the chain, eventually leading to the upper-layer protocol.

pakketgrootte:
- minimum 1280 octets
- aangeraden = 1500 octets
- wnr packet too big ▶ ICMPv6 stuurt Packet Too Big message
- de pakketgrootte wordt bij bron afgesproken en niet bij elke hop zoals bij IPv4

stateless autoconfiguratie (SLAAC)
- SLAAC allows a device (such as a computer, phone, or IoT device) to generate its own IPv6 address based on information received from the local network.
- een manier voor devices om hun eigen IP address te configuren zonder het gebruik van DHCP
- designed om de configuratie van IPv6 addressen te vergemakkelijken
- het "stateless" deel betekent dat de router de individuele addressen niet moet bijhouden
- het proces van SLAAC
	- link local address configuration
		- wanneer verbonden met IPv6 netwerk, device creert eerst een link local adres
		- samengesteld door de netwerks prefix en het MAC adres
	- neighbor discovery protocol
		- the device uses the Neighbor Discovery Protocol (NDP) to ensure that the address is unique on the local network
	- router advertisement messages
		- message contains
			- networks's global prefix
			- default gateway
			- flags showing if stateful or stateless is being used
	- global address configuration
		- devices generates its own global address if SLAAC is being used on the network
	- duplicate address detection
		- check for duplicate address on the network
	- using the address

mobiele autoconfiguratie
- GSM device krijgt steeds een Home Agent adres in "thuis basis"
- wanneer op verplaatsing, krijgt een tijdelijk adres
- device stuurt dan naar home agent het tijdelijk adres om een connectie aan te leggen
- elke connectie moet nu via de Home Agent baseren (als een soort router)

[[NT ICMPv6|ICMPv6]] 
- network layer protocol

flow labels & verkeersklasse
- flow labels doel:
	- QoS
	- realtime diensen
- verkeersklasse doel:
	- prioriteiten inrichtingen onderling tusse de verschillende soort packetten
	- enkel aanpassingen mogelijk door nodes van dezelfde klasse

authenticatie header
- verzekering van herkomst van het verkeer 
- gebruikt een security parameter index
	- afgesproken 32 bit nummers zender <-> ontvanger
- volgnummer
	- verzekeren integriteit
	- 32 bit nummer
- integrity check value
	- hash berekend met gedeeld geheim zender <-> ontvanger

encryptie header
- sleutels voor encryptie uitgewisseld over [[NT UDP|UDP]] poort 500
- encapsulation security payload header
	- encryptie protocol
	- volgnummer
	- checksum
- gebeurt enkel op data die verstuurd wordt (payload)