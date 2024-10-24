---
alias: transport layer
definition: provides services such as connection-oriented communication, reliability, flow control, and multiplexing
type: term
port: N/A
OSI-layer: transport
more-info: "https://en.wikipedia.org/wiki/Transport_layer"
---
[[NT OSI model]]

data wordt in segmenten gegoten en krijgen een HEADER met extra informatie

2 mogelijkheden voor protocol: betrouwbaar of onbetrouwbaar
- [[NT TCP]] = betrouwbaar
	- handshake, ACK, SYN
	- kijkt het volgende na:
		- het opzetten & beëindigen van verbindingen
		- het correct doorsturen van data
		- bevestigen dat data is doorgestuurd of niet
		- verzekert dat de pakketen waarin de data wordt verzonden terug in de juiste volgorde worden gezet
		- flow control: regelen hoeveel data en wanneer deze kan doorgestuurd worden
	- voorbeelden van technolgie die TCP gebruiken
		[[NT FTP]], [[NT telnet]], [[NT HTTP]]
- [[NT UDP]] = onbetrouwbaar
	- voorbeelden van UDP technologieen
	  [[NT TFTP|TFTP]], [[NT SNMP|SNMP]], [[IT NFS]], [[NT DNS|DNS]], [[NT RIP]]

de reden waarom er met packetjes wordt gewerkt en de data dus wordt opgesplitst is zo dat door de transfer van data van 1 gebruiker het netwerk niet gehijacked wordt en er dan meerdere data verstuurd kan worden. achteraf worden de packetjes weer samengevoegd

client side port nummers steeds groter 1024, boven de well known ports