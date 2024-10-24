---
alias: RADIUS
definition: Remote Authentication Dial-In User Service
type: technology
port: N/A
OSI-layer: data-link
more-info: "https://en.wikipedia.org/wiki/RADIUS"
---
[[NT Networking MOC]]

- Met een RADIUS server kunnen clients geen data verzenden over de AP's zonder een geldige authenticatiesleutel
	- Client binnen range => AP stuurt challenge
	- Client authenticeert bij AP -> stuurt door naar RADIUS
	- Client stuurt credentials naar RADIUS
	- RADIUS server stuurt een geëncrypteerde authenticatiesleutel naar AP
	- De AP gebruikt deze authenticatiesleutel om beveiligde verbindingen op te zetten met de clients
		- Microsoft RADIUS server heet IAS