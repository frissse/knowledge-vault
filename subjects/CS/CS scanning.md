---
alias: scanning
definition: how the target application will respond to various intrusion attempts
type: term
subject: pentesting
more-info: "https://www.eccouncil.org/cybersecurity-exchange/penetration-testing/penetration-testing-phases/"
---

### sources

[[cybersec-p1w3-scanning-oef30 1.pdf]]

[[cybersec-p1w3-scanning-oef31 1.pdf]]

[[cybersec-p1w3-scanning-oef32 1.pdf]]

[[cybersec-p1w3-scanning-oef33 1.pdf]]

### info

- identify hosts within ranges
- enumeration: ports & services
- scan types
	- network scan/sweep
		- identify active hosts on the target's network
		- via ping [[NT ICMP|ICMP]] -> ping is disabled by default
		- via port scanner [[,nmap]] -> uses [[NT TCP|TCP]] & [[NT UDP|UDP]]
			sends back the status TCP or UDP ports on the target
			- Open-Accepted
			- Closed-Denied-Not Listening
			- Filtered-Dropped-Blocked -> no reply from host
![[Pasted image 20241001102915.png]]			  

- 