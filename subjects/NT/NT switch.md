---
alias: switch
definition:  networking hardware that connects devices on a computer network by using packet switching to receive and forward data to the destination device
type: infrastructure
port: N/A
OSI-layer: data-link
more-info: "https://en.wikipedia.org/wiki/Network_switch"
---
[[NT Networking MOC]]

<u>verschillende manieren van switching</u>

- cut-through
	- doorsturen vanaf dat het eerste deel van [[NT frame|frame]] herkend zijn (source & destination adres)
- fast-forward: 
	- doorsturen wanneer destination [[NT MAC address|MAC address]] gekend is 
- store-and-forward switching 
	- inlezen [[NT frame|frame]] in buffer en dan doorsturen
	- verhindert onvolledige berichten en giants (te grote data pakketten)