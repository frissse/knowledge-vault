---
alias: WLAN roaming
definition: switching between different access point in a network
type: term
port: N/A
OSI-layer: data-link
more-info: "https://en.wikipedia.org/wiki/Roaming"
---
[[NT Networking MOC]]

In een multi-cel WLAN netwerk met een aantal APs kunnen gebruikers zich vrij verplaatsen eens ze geauthenticeerd en geassocieerd zijn.

Gebruikers kunnen dan overschakelen op de AP met het sterkste signaal

soorten WLAN roaming:
- Seamless roaming
	- Gebruikt bij GSM
- Nomadic roaming
	- Gebruikt bij WLAN apparaten

 roaming gebruikt een 'break before make' principe 
 ▶ een bestaande connectie wordt 1st afgesloten alvorens met een andere te verbinden
 ▶ gebeurt in 4 stappen
 1. disassociatie
 2. zoeken
 3. her-associatie
 4. authenticatie

gebeurt op [[NT OSI data|data link layer]] ▶ gebruikers behouden hun [[NT IPv4|IPv4]] adres 