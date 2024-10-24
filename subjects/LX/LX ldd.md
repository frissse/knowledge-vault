---
alias: ldd
usage: ldd [application]
example: ldd /bin/sh
definition: tool used for examining the shared libraries required by an executable or shared object file
type: bash-command
subject: monitoring
more-info: "https://www.howtoforge.com/linux-ldd-command/ "
---
 
[[LX command]]

Stel dat een applicatie de verkeerde bibliotheek gebruikt, dan kan je dit aanpassen in /etc/ld.conf.d/*.conf . 

Daarna voer je ldconfig uit,  om de wijzigingen door te voeren.

pmap PID: toont ook dynamisch ingeladen libraries