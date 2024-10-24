---
alias: SIP
definition: Session Initiation Protocol 
type: protocol
port: UDP 5060
OSI-layer: application
more-info: "https://en.wikipedia.org/wiki/Session_Initiation_Protocol"
---
[[NT Networking MOC]]

 - syntax gebaseerd op [[NT HTTP|HTTP]] & [[NT SMTP|SMTP]]
 - SIP adres lijkt op een mail adres: sip:alexander.waumans@student.kdg.be
 - headers zijn voor call routering
 - de body van het packet beschrijf media stroom
	 - codex, [[NT RTP|RTP]] poorten


- SIP netwerken bestaan uit volgende elementen
	- User agent: phone
	- SIP proxy server
		- routeren van SIP gesprekken
		- regestrar: mappen van IP adres naar SIP adres
		- zowel het registreren als de invite gebeurt door het gebruik van de location database
		- het vinden van de eerste proxy
			- outbound proxy
			- handmatig geconfigureerd ([[NT DHCP|DHCP]])
			- [[NT DNS|DNS]] lookup
		  
 ![[screenshot6.png]]
 
 om te kunnen verbinden met het huidige netwerk ▶ een signaling & media gateway nodig
 zowel RTP als SIP gebruikt
 
 ![[screenshot7.png]]
 
 header:
 ![[Pasted image 20241023080307.png]]

commandos:
![[screenshot5.png]]