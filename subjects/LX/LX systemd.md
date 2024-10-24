---
alias: systemd
usage: multiple
example: systemd-analyze
definition: collection of commands to manage system services 
type: bash-command
subject: services
more-info: "https://www.linuxtrainingacademy.com/systemd-cheat-sheet/"
---
 
[[LX command]]

`systemd-cgls /user.slice`
toont de services/processen die als gewone user draaien

`systemd-cgtop`
toont welke slices meeste resources gebruiken

`systemd-analyze`
Toont opstarttijd firmware, bootloader, kernel en processen

`Systemd-analyze blame`
toont top van opstarttijden


