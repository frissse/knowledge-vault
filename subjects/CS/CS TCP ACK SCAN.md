---
alias: TCP ACK scan 
definition: 
type: term
subject: cybersecurity
more-info: "https://www.geeksforgeeks.org/what-is-tcp-ack-scanning/?ref=oin_asr4"
---

[[CS CyberSecurity MOC]]
[[LX linux MOC]]
[[,nmap]]
[[,wireshark]]

- er wordt een TCP packet met ACK flag verstuurd
- poort is FILTERED als de server een ICMP foutbericht stuurt
	- er is een firewall die XMAS pakketen blokkeert
	- die firewall doet geen DROP
- poort is UNFILTERED als de servre een RST stuurt
	- je weet niet of de poort OPEN / CLOSED is
- 