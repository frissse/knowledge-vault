---
alias: Frame relay
definition: framed relay
type: protocol
port: N/A
OSI-layer: data-link
more-info: ""
---
[[NT Networking MOC]]

DTE = Data Terminal Equipment
CIR = commited information rate
-> afspraak over snelheid die gebruikt zal worden in de connectie
- afgesproken burst
- afgesproken tijd
- afgesproken max rate

een gestandariseerde verbindings service voor [[NT WAN|WAN]]s 
-> vaak gebruikt om verschillende [[LAN]]s met elkaar te verbinden
-> het eigenlijk netwerk zijn verschillende switches die doorverbinden
-> verschillende LANs connecteren met hun DTE

een [[NT X.25|X.25]] lit versie -> zonder extensieve error correctie
verschillen tss X.25 & Frame Relay
- frame relay niet zo robuust
- gaat uit van een betrouwbaar verbindingsmedium
- geen hertransmissie van verloren data
- geen sliding windows
- geen eigen foutafhandeling, moet gebeuren door hogere lagen
- hogere performantie

gebruikt [[NT packet switching]] (transferring variable length packets/frames)

frame relay gebruikt VC (=virtual circuits) to establish logical paths between 2 end points
-> wanneer 2 DTEs via het Frame Relay network met elkaar verbinden (zie [[NT ATM|ATM]])
-> verschillende virtuil circuits onderschieden door DLCI = data link connection identifier

door het LAPF (=Link Access Procedure for Frame Relay) worden laag 3 pakketten omgevormd naar Frame Relay frames
-> daarna doorgegeven naar laag 1 en via kabel doorgestuurd
LAPF bevat het volgende
- bit voor Cell Loss Priority
- bit voor aangeven file probleem

Frame Relay vs ATM

| frame relay                     | ATM                             |
| ------------------------------- | ------------------------------- |
| variabele packetgrootte         | vaste kleine pakketten (cellen) |
| geen [[NT QoS\|QoS]] standaaard | QoS en prioriteiten vastgelegd  |
| meer ondersteund door providers | zeer goed schaalbaar            |
| goedkoper                       | duur, complex                   |
| 64 KBps -> 40 MBps              | 1.5 MBps -> 622 MBps            |
|                                 | cor van netwerken               |
