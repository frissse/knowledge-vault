---
alias: supernode
definition:  a supernode is any node that also serves as one of that network's relayers and proxy servers, handling data flow and connections for other users
type: term
port: N/A
OSI-layer: application
more-info: "https://en.wikipedia.org/wiki/Skype_protocol"
---
[[NT Networking MOC]]

Skype oplossing voor NAT ▶ gebruik van een superNode
- superNodes zijn hosts met een globaal IP (en hoge ping)
- dienen bij opstart als relay (doorgeefluik)
- clients die achter een NAT werken maken een verbinding met andere clients via de supernodes
	- 1st via UDP, dan via TCP
- UDP hole punching, mogelijk 'hole' in firewall voor UDP