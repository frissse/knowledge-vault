---
alias: ICMPv6
definition: network layer protocol in IPv6 for error handling
type: protocol
port:
OSI-layer: network
more-info: "https://en.wikipedia.org/wiki/ICMPv6"
---
[[NT Networking MOC]]
[[NT IPv6|IPv6]]

functionaliteiten van ICMPv6
- error handling
- diagnositcs
- neighbor discovery
- router discovery
- multicast listener discovery

types of ICMPv6 message types
- error messages
	- type 1: destination unreachable
	- type 2: packet too big
	- type 3: time exceeeded
- information messages
	- type 128/129: echo request/reply
- neighbor discovery messages
	- type 135/136: neighbor sollicitation/advertisement
	- type 133/134: router sollicitation/advertisement

 