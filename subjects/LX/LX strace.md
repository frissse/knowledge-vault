---
alias: strace
usage: strace [command to be traced]
example: strace ls
definition: In the simplest case **strace** runs the specified _command_ until it exits
type: bash-command 
subject: monitoring
more-info: "https://www.geeksforgeeks.org/strace-command-in-linux-with-examples/"
---
 
[[LX command]]

Toont alle bestanden/bibliotheken die door een proces gebruikt worden

Voor een nieuw proces, bv uptime
	`strace -eopen uptime`
Vasthechten aan een bestaand proces
	`strace -i PID`