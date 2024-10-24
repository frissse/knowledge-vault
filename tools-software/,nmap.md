---
type: MT tool
alias: 
---
 
[[MT tool]]
[[CS CyberSecurity MOC]]

Network exploration tool and security / port scanner

| command                        | explanation                                                                                                                                                                                                                                   | distro | more info                                   |
| ------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------ | ------------------------------------------- |
| `nmap -sC -sV -v <ip address>` | -sC: Performs a script scan using the default set of scripts. It is equivalent to --<br>script=default.<br>-sV: Version detection<br>-v: Increases the verbosity level, causing Nmap to print more information about the<br>scan in progress. | all    | [man-pages](https://nmap.org/book/man.html) |
| `nmap -p- -sV <ip address>`    | scan all ports + version info on target                                                                                                                                                                                                       |        |                                             |
| `nmap -O`                      | scan for OS information                                                                                                                                                                                                                       |        |                                             |
