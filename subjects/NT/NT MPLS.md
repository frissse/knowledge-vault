---
alias: MPLS
definition: multi protocol layer switching
type: protocol
port: N/A
OSI-layer: data-link
more-info: ""
---
[[NT Networking MOC]]

[[NT WAN|WAN]] protocol

MPLS is een framework dat schaalbaarheid en routering van traffic flow voorziet in bestaand ATM & Frame Relay netwerken

specifieert de manier waarop verkeersstromen tussen verschillende niveaus kunnen vloeien
-> onafhankelijk van laag 2 & laag 3 protcollen
-> gebeurt tussen laag 2 en laag 3

traditionele routering op laag 3 -> te veel op basis van kortste pad, te weinig rekening met congestie en vertraging

nood aan meer bandbreedte voor data, spraak en multimedia alsook voor kwaliteitsverzekering ([[NT QoS|QoS]])

mapped [[NT IPv4|IPv4]] adressen naar eenvoudige labels
wanneer een packet eerst op het MPLS netwerk komt krijgt deze een label toegewezen door de Label Edge Router
vervolgens worden de packete geforward door de Label Switch Router in het netwerk
voorziet een interface naar bestaande routing protocollen zoals [[NT OSPF|OSPF]]
label bevat:
- exp bits - geven verkeersklasse aan
- BS - soort stop bit
- TTL - time to live

label worden "meegepatk" via piggybacking van [[NT BGP|BGP]], alsook nieuw protocol gedefinieerd Label Distribution Protocol
