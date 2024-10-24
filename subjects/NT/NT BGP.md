---
alias: BGP
definition: border gateway protocol
type: protocol
port: 179 TCP
OSI-layer: application
more-info: "https://en.wikipedia.org/wiki/Border_Gateway_Protocol"
---
[[NT Networking MOC]]

routing protocol 
- waarmee ISP met elkaar verbinden
- tussen autonome systemen
	- een verzameling van IP netwerken & routers beheert door dezelfde administrator
	- elk AS heeft uniek nummer
		- privaat of publiek (16 of 32 bit)
	- via de Autonome Systemen worden announcements doorgestuurd naar elkaar, op die manier krijgen ze elk kennis van elkaar
	- routering gebeurt intern en extern
		- intern = IBGP
		- extern EBGP
	- CIDR = class less inter domain routing
		- IP adressen worden niet via klasse doorgegeven maar op bassi van een prefix
- werkt met een distance vector

BGP sessie:
- alle actieve routes worden uitgewisseld
- alle incrementele updates worden uitgevoerd
	- een update = IP prefix + attributen
		- attributen zijn
			- AS_PATH (gelijkaardig aan # hops)
			- MULTI_EXIT_DISC: zelf in te stellen tussen jou en je buren, hoe lager hoe sneller deze verbinding wordt gebruikt
	- een update met langste prefix = meeste informatie & krijgen voorrang 

kiezen van het beste pad (naar de bestemming)
- externe routes krijgen voorrang op interne
	- kortste AS_PATH
	- kortste MULTI_EXIT_DISC
	- de route met laagste IP krijgt voorrang