---
alias: TCP windows scan
definition: 
type: term
subject: cybersecurity
more-info: ""
---

[[CS CyberSecurity MOC]]
[[LX linux MOC]]
[[,nmap]]
[[,wireshark]]

- idem als TCP windows scan
- poort is FILTERED als de server een ICMP foutbericht stuurt
- de window size van het RST pakket van de server wordt nagekeken
	- als > 0 -> poort = OPEN
	- anders poort = CLOSED
 