---
alias: footprinting
definition: the process of collecting data over time in order to make a targeted cyberattack
type: term 
subject: pentesting
more-info: ""
---

= "reconnaissance"
information discovery on client/organization

2 types
1. active - direct interact with the target door
	- ping sweep: doorlopen van actieve IP adressen
	- door het gebruik van [[,nmap]] tool om te kijken welke poorten welke service gebruiken
	- opstellen van een network diagram
	- [[CS social engineering|social engineering]]
	
1. passive - without direct interaction with target
	- via adverts
	- domain contact info via [[LX whois|whois]]
	- social network | [[CS OSINT|OSINT]]
	- disgruntled employees

tools used for footprinting
- Google Dorks
operators

![[Pasted image 20240930145805.png]]

collectie van exploits via google dorks [link](https://www.exploit-db.com/google-hacking-database)

- [[LX nslookup]]
- [[LX whois|whois]]

who to protect against fingerprinting?

cleaun up old logs,...
use robots.txt so webiste does not get scrapped
disallow directory listing [[,apache|apache httpd]]

footprinting kan ook gebeuren via "de human manier"