---
alias: xmas-scan
definition: 
type: term
subject: cybersecurity
more-info: ""
---
[[CS CyberSecurity MOC]]
[[LX linux MOC]]
[[,nmap]]
[[,wireshark]]

versturen van "onmogelijk" TCP packet met PSH URG FIN flags aan
	- poort is OPEN als server niets stuurt
	- poort is CLOSED als de server een RST stuurt
		![[Pasted image 20241007081715.png]]
	- poort is FILTERED als de server een ICMP foutbericht stuurt
		- er is een firewall die de scan blokkeert, maar de firewall doet geen DROP van de packets
		  -> je weet niet of poort OPEN of CLOSED is