---
type: MT tool
alias: wireshark 
type: networking
short description: a free and open source tool for network analysis and troubleshooting
link: https://www.wireshark.org/
--- 
[[MT tool]]

#### filters

detect network scans in [[,wireshark]]

| scan name          | wireshark filter                                                    | nmap command      |
| ------------------ | ------------------------------------------------------------------- | ----------------- |
| TCP SYN scan       | ``tcp.flags.syn==1 and tcp.flags.ack==0 and tcp.window_size<=1024`` | nmap -sT <target> |
| TCP Connect() scan | `tcp.flags.syn==1 and tcp.flags.ack==0 and tcp.window_size>1024`    | nmap -sS <target> |
| TCP Null           | `tcp.flags==0`                                                      | nmap -sN <target> |
| TCP FIN            | `tcp.flags==0x001`                                                  | nmap -sF <target> |
| TCP Xmass scan     | `tcp.flags.fin==1 && tcp.flags.push==1 && tcp.flags.urg==1`         | nmap -sX <target> |
| UDP port scan      | `icmp.type==3 and icmp.code==3`                                     | nmap -sU <target> |

