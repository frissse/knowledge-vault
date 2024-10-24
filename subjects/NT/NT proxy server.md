---
alias: proxy server
definition: an intermediary between client and server
type: technology
port: TBD
OSI-layer: application 
more-info: "https://en.wikipedia.org/wiki/Proxy_server"
---
[[NT Networking MOC]]

### sources

[[proxy server what is it and what does it do]]
[[Google is forcing you to use their proxy]]

### info

proxy servers kunnen op verschillende niveaus gebruikt worden
- netwerk niveau
	- werken op een lager niveau
	- loggen en geven [[NT packet|packet]]en door zonder te weten wat de info ervan is
- applicatie niveau
	- ontrafelen hier wel de packeten en geven aanvragen door
	- betere verstaanbare logging door interpretatie van de inforamtie die ze verwerken

- (traditionele) [[NT proxy server ]]
	- "acts as intermediary between a client & server"
	- proxy voorziet een bepaalde anonimiteit omdat het verkeerd door de proxy gerout wordt en op die manier het [[NT IPv4]] adres kan gemaskeerd worden
	- proxy voorziet ook caching functionaliteit
	- daarnaast is het ook makkelijker om aan access control te doen
	- voert diensten uit voor intern netwerk
	- kan je herkennen aan de poort nummers, "foefelen" een beetje met onthouden port nummers
	- [[NT firewall]] functies door gescheiden LAN & WAN verkeer
	- geen default gateway in te stellen
- transparante [[NT proxy server]]
	- zelfde als een traditionele proxy server maar gebruikers denken dat het verkeer gwn via [[NT router]] gebeurt
	- op dat moment is de router zowel een proxy als een router
	- [[NT DNS]] server draait op de proxy
	- default gateway moet ingesteld worden
	- veel gebruikt voor monitoring van data op een netwerk

can also be anonymous, 
hiding the identity of the actual client visiting a website

worden soms ook gebruikt voor data scraping om te voorkomen dat je IP geband wordt door het sturen van vele requests

kan ook de snelheid verhogen door het cachen van websites en andere data + save of bandwidth

kan data niet encrypeteren daarvoor wordt een VPN 

[[IT Google]] is baking in proxy server inside [[,chrome]] . 
it is a bit like a man in the middle attack
probably using 2 hops

runs in the background on [[NT ssh]], je opent een tunnel op een poort en direct traffic through it

[[,shadowsocks]]
### configuration

`ssh -D port`

set the proxy to localhost and that port





\
