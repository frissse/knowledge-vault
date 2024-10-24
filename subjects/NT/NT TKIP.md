---
alias: TKIP
definition: Temporal Key Integrity Protocol
type: protocol
port: N/A
OSI-layer:
more-info: ""
---
[[NT Networking MOC]]
[[CS CyberSecurity MOC]]

an interim solution to replace WEP without requiring the replacement of legacy hardware

- Encryptiemethode 
	- Wrapper rond WEP
		- Gebruikt dezelfde RC4-Engine van WEP
- Gebruikt een [[NT MIC]] (Michael genoemd) op het einde van elk plaintext bericht (uitgebreide CRC)
		▶ Verzekert dat berichten niet gespooft worden

 