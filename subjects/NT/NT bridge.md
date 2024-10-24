---
alias: bridge
definition: a computer networking device that creates a single, aggregate network from multiple communication networks or network segments
type: infrastructure
port: N/A
OSI-layer: physical
more-info: "https://en.wikipedia.org/wiki/Network_bridge"
---
[[NT Networking MOC]]

Een netwerk bridge verbindt meerdere netwerksegmenten op laag 2 (data link laag) van het OSI model

Bridges zijn vergelijkbaar met repeaters omdat ze ook segmenten met elkaar verbinden 
	▶ MAAR bridges doen niet gewoon een broadcast op het andere segment

soorten bridges

transparant (learning) bridges
- gebruikt een forward tabel om [[NT frame|frame]]s door te sturen naar andere netwerk segmenten
- begint steeds met een lege forward tabel
- wanneer het destination adres niet in forward tabel wordt deze gebroadcast tot dat de destination gevonden is

source route bridging
- 2 soorten frames om het jusite doelnetwerk te vinden
	- ALl-Route frames: nieuwe routes leren
	- Single Route frames: gebruikt wanneer route gekend is
		▶ 1ste AR frame die doel raakt wordt de beste SR route 
- elk frame heeft een max hop count