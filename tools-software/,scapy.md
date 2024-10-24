---
type: MT tool
alias: scapy
type: networking
short description: a powerful and flexible tool that allows you to send, sniff, dissect and forge network packets of various protocols
link: "https://scapy.readthedocs.io/en/latest/introduction.html"
---
[[MT tool]]
[[NT Networking MOC]]
[[PR python]]

#### installation

to install on [[LX linux MOC|linux]] distros, do:

`sudo apt-get install tcpdump python3-crypto ipython3 python3-scapy`

to install with pip

`pip3 install scapy-python3`

#### info

python library to manipulate network [[NT packet|packet]]s and [[NT frame|frame]]s
- aanmaken & decoderen van pakketen
- sniffen op het netwerk
- antwoorden onderscheppen

kan bv gebruikt worden om:
- poortscans te doen
- traceroute
- firewall testing
- netwerk aanvallen discovery

in scapy is elk pakket een object
▶ packet kan laag per laag samengesteld worden

```python
pakket = IP()/TCP()
pakket = Ether() / IP () / TCP()
```

een voorbeeld met de waarden per laag ingevuld

op [[NT OSI data|data link layer]]  (Ether) het [[NT MAC address]]
op [[NT OSI network|network layer]]: het [[NT IPv4|IPv4]] adres
op [[NT OSI transport|transport layer]]: de poort (hier [[NT HTTP|HTTP]] trafiek op poort 80)

```python
from scapy.all import *
ether=Ether(src="AB:AC:DD:9F:3C:AB")
ip=IP(dst="8.8.8.8")
tcp=TCP(dport=80)

pakket=ether/ip/tcp

```

pakket tonen kan met het `show()` command

pakket zenden

```python
# !/usr/bin/env python3
from scapy.all import *
send(IP(dst="127.0.0.1")/ICMP())
```

pakket sturen en antwoord ontvangen

```python
sr() # meerdere pakketen sturen & ontvangen
sr1() # 1 pakket sturen en ontvangen
srp() # zelf maar voor frame op laag 2

#!/usr/bin/env python3
dstip   ="8.8.8.8"
dports =[20,21,80]
ip=IP(dst="127.0.0.1")
tcp=TCP(dport=dports)
pakketten=sr(ip/tcp,timeout=1)
ans,unans=pakketten
ans.summary()  
```

mogelijke TCP flags die je kan gebruiken

```
F	FIN 	= 0x01 
S	SYN 	= 0x02 
R	RST 	= 0x04 
P	PSH 	= 0x08 
A	ACK 	= 0x10 
U	URG 	= 0x20 
E	ECE 	= 0x40 Explicit Congestion notification Echo 
C	CWR 	= 0x80 Congestion Window Reduced
```

