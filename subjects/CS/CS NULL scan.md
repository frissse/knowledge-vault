---
alias: Null scan
definition: 
type: term
subject: cybersecurity
more-info: ""
---

[[CS CyberSecurity MOC]]
[[LX linux MOC]]
[[,nmap]]
[[,wireshark]]

- identiek aan [[CS XMAS scan|xmas-scan]] & [[CS FIN scan|fin-scan]] 
	- TCP pakket met geen enkele enkele FLAG aan
- poort is OPEN als de server niets stuurt
- poort is CLOSED als de server een RST stuurt
- poort is FILTERED als een ICMP fout bericht komt
 