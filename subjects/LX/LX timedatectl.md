---
alias: timedatectl
usage: timedatectl [OPTIONS...] {COMMAND}
example: timedatectl status
definition: see values about time and date 
type: bash-command
subject: monitoring
more-info: "https://www.howtogeek.com/782032/how-to-use-the-timedatectl-command-on-linux/"
---
 
[[LX command]]

Uitlezen tijd
`timedatectl`
Instellen tijd
`timedatectl set-time "2019-02-29 18:17:16"`
Instellen tijdszone
`timedatectl set-timezone "Europe/Brussels"`
Instellen ntp (tijdssynchronisatie over het netwerk)
`timedatectl set-ntp 0`   #Uitschakelen
`timedatectl set-ntp 1`   #Inschakelen