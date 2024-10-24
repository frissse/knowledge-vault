---
alias: systemctl
usage: systemctl [command] [service]
example: systemctl start helloworld
definition: Control the systemd system and service manager
type: bash-command
subject: services
more-info: "https://www.geeksforgeeks.org/systemctl-in-unix/?ref=header_outind"
---
 
[[LX command]]

reload the system daemon
`systemctl daemon-reload`

starts the service

`systemctl start helloworld`

stops the service
`systemctl status helloworld`

start up with boot
`systemctl enable helloworld`

do not start up with boot
`systemctl disable helloworld`

Uitschakelen systeem cpu's uit
`systemctl halt`

Uitschakelen systeem stroom uit
`systemctl poweroff`

Herstarten systeem 
`systemctl reboot`

Suspend systeem (alles low power)
`systemctl suspend`

Hibernate
`systemctl hibernate`

`systemd-analyze`
Toont opstarttijd firmware, bootloader, kernel en processen

`systemd-cgtop`
Toont welke slices meeste resources gebruiken






