---
alias: ATM
definition: Asynchronous Transfer Mode
type: protocol
port: N/A
OSI-layer: N/A
more-info: "https://en.wikipedia.org/wiki/Asynchronous_Transfer_Mode"
---
[[NT Networking MOC]]

![[Pasted image 20241020104234.png]]

[[NT LAN|LAN]] & [[NT WAN|WAN]] technologie

ATM past niet in het OSI model
ATM = overlay network
- eigen hierarische adressering met autoconfiguratie
- ATM routeert

nadelen van ATM
- firewalls kunnen connectie niet meer interpreteren zodra een ATM connectie is opgezet
- zeer duur
- gebruik van ATM binnen LAN = verlies van bandbreedte -> transitie van TCP naar ATM zorgt voor meer overhead

[[NT QoS|QoS]] gebruikt soort contract waarin verschillende eigenschappen van de connectie worden vastgelegd
- vertraging van het zenden van de cellen
- cell loss rate
- ...

Negotiated Service Connection
moet afgesproken worden voor het opzetten van een ATM connectie
- Peak Cell Rate = max snelheid voor piekverkeer
- Average Cell Rate =m gemiddelde snelheid
- QOS = vertraging en verlies van cellen

ATM werkt op het principe van schakelen
- elke verbinding heeft zijn eigen toegangssnelheden, bandbreedt en capaciteit

elke ATM switch met CAC (Connection Admission Control) functie of er aan de QoS kan voldaan worden

connection oriented - end to end virtual circuits
	ATM-cel is basis van connection
steeds zoeken naar ideale lengte van een pakket(cel)
- lange cal meer informatie maar duurt langer om te vullen
- korte cel sneller gevuld maar heeft veel overheid ten opzicht van de informatie die het bevat

cel = 48 bytes (consensus tss wat EU 32 bytes en VS wilden 64 bytes) 
-> ATM cel = 53 bytes ( 5bytes header & 48 bytes data)

virtuele circuits (connecties binnen ATM): verschillende soorten
- PVC = Permanent Virtual Circuit
	- vast gealloceerde verbinding tss 2 eindgebruikers
		- voorafgesproken PCR & SCR
- SVC = Switched virtual Circuit
	- slechts opgezet wanneer en zolang het nodig is

soorten verbindingen
- point to point
	- 1 of 2 richtingsverkeer
- point to multipoint
	- enkel 1 richtingsverkeer

ATM heeft 3 layers
- adaptatie laag
	- conversie van ATM datatypes -> 48 bytes
	- verschillende soort van adaptie
		- AAL 1 - circuit emulation
			- voor tijdgevoelige/ real time verkeer
		- AAL 2 - audio/video
			- variabele bitrates
		- AAL 3/4 - data transfer
			- best effort data overdracht
		- AAL 5
			- LAN verkeer 
			- vereenvoudigde versie van AAL 4 -> minder overhead bij data
			- SEAL = Simple and efficient adaptation layer
			- (in praktijk ATM nt gebruikt voor LAN)
- ATM laag
	- toevoegen of verwijderen van 5 bytes header
![[Pasted image 20241020103514.png]]
	- header bevat volgende informatie
		- algemene flow control
		- VC identifier/VP identifier
		- payload type identifier
		- aangeven of het data of controle verkeer is
		- byte voor fileprobleem
	- cell loss priority
		- cellen die vloeken tegen de QoS krijgen CLP=1, mogen eerst gedropt worden
			- leaky bucket algoritme - constante data flow garantie
	- header error check
		- beheer van virtuele circuits & paden
		- routeren van ATM switches
	- totale bandbreedte opgesplitst in virtuele paden, virtuele paden opgesplitst in virtuele circuits
	![[screenshot_1.png]]
	- ATM werkt op basis van virtuele paden
		-> per pad een VPI (virtual path identifier)
		langs een virtueel pad -> verschillende virtuele kanalen -> per toepassingen een virtual channel identifier
	- interfaces bij ATM:
		- UNI: User-Network interface
			- rand netwer: meer bits voor toepassingen
			- 8 bits voor VPI
		- NNI: Network-Network Interface
			- 12 bits voor VPI
	- network provisioning 
	  -> op voorhand vastleggen van een virtueel pad: VPI -> poort > VPI
		-> gebeurt door controlle cellen
- fysieke laag
	- conversie naar elektrisch of optisch signaal
	- medium : verschillende opties
		- STP, UTP, COAX, nulti & single mode fiber, wireless
		- [[NT xDSL|xDSL]]
	- cell rate decoupling
		- lege cellen worden opgevuld met bepaald patroon om aan te geven dat ze leeg zijn


