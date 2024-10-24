---
alias: IPv4
definition: Internet Protocol v4
type: protocol
port: N/A
OSI-layer: Network
more-info: "https://en.wikipedia.org/wiki/IPv4"
---
[[NT protocol]]

32-bit adres in 4 octets

0000 0000 . 0000 0000 . 0000 0000 . 0000 0000 

bestaat uit 
netwerk (NETW) --> aangegeven door [[NT subnetmask]]
& 
host (HOST) adres
naargelang # bits voor netwerk adres -> verschillende klasse van IP adres

Klasse A: 
- 0-126
- 8 bits voor NETW 
- NETW.HOST.HOST.HOST
- private adres: 10.X.X.X
Klasse B: 
- 128-191
- 16 bits voor NETW 
- NETW.NETW.HOST.HOST
- private adres: 172.16.X.X
Klasse C: 
- 192-224
- 24 bits voor NETW 
- NETW.NETW.NETW.HOST
- private adres: 192.168.1.X

Klasse D: multicast

Klasse E: loopback (127.0.0.1)