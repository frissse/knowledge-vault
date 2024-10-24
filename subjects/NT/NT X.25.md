---
alias: X.25
definition: a protocol for packet switched data communication 
type: protocol
port: 
OSI-layer: physical, network, data-link
more-info: "https://en.wikipedia.org/wiki/X.25"
---
[[NT Networking MOC]]

DTE = data terminal equipment
DCE = data circuit terminating equipment - kloksnelheid
PAD = packet assembler/disassembler

![[screenshot_2.png]]

X.25 past niet helemaal in het [[NT OSI model|OSI Model]] -> werd ervoor ontworpen
maar mapt op laag 1 tot 3 in het model
- LAAG 3
	- PLP packet protocol
	- adressering
- LAAG 2
	- LAP-B (Link Access Procedure, Balanced)
	- voorziet uitgebreide error correctie
- LAAG 1
	- X.21 bitstroom