---
alias: WEP 
definition: obsolete, severely flawed security protocol for wireless networks
type: protocol 
port: N/A
OSI-layer: data-link
more-info: "https://en.wikipedia.org/wiki/Wired_Equivalent_Privacy"
---
[[NT Networking MOC]]

2 authenticatie diensten

- Open System authenticatie
	- Eender wie zich aanmeldt, wordt geauthenticeerd
- Shared-Key authenticatie
	- Client moet de gedeelde sleutel kennen om te verbinden
	- Zwakheid: sniffen van gedeelde sleutel processen

WEP uses the stream cipher RC4 for confidentiality, and the CRC-32 checksum for integrity

CRC te zwak voor garanderen data integriteit
 