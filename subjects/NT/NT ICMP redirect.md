---
alias: ICMP redirect
definition: used by routers to inform hosts about more efficient routes for sending packets to a destination
type: term
port: N/A
OSI-layer: network
more-info: "https://www.twingate.com/blog/glossary/icmp%20redirect"
---
[[NT ICMP|ICMP]]
[[NT router|router]]


When a router receives a packet and determines that another router on the same network provides a shorter path, 
it sends an ICMP Redirect message to the host, advising it to send future packets to the optimal router
-> This message includes the new gateway address and the original packet's header information, enabling the host to update its routing table accordingly.


The primary purpose is to optimize routing, reduce network resource utilization, and improve network performance by ensuring packets take the shortest path.
 