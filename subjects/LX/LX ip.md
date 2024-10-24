---
alias: ip link
usage: ip [OPTIONS] OBJECT {COMMAND | help}
example: ip addr show
definition: a powerful utility for network configuration and management
type: bash-command
subject: networking
more-info: "https://www.howtogeek.com/657911/how-to-use-the-ip-command-on-linux/"
---
 
[[LX command]]

`ip link`
`ip link add type dummy`
`ip link set eth0 up`
`ip link set dummy0 up`

`ip addr`
`ip addr add 192.168.1.100/24 dev eth0`
`ip address add dev dummy0 10.10.10.1/24`
`ip route delete 10.0.0.0/24 via 192.168.1.1 dev eth0`

toont pakketstatistieken per interface
`ip -s link`
`ip -s address`

toont tabel van gekende ip mac addressen
`ip n`


