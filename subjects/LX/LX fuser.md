---
alias: fuser
usage: fuser [options] -SIGNAL [file|socket]
example: fuser -m /mnt/sda1
definition: who is using which disk
type: bash-command
subject: monitoring
more-info: "https://www.geeksforgeeks.org/fuser-command-in-linux/"
---
 
[[LX command]]

you can use this command to kill the process that uses a certain disk to later unmount it 

`fuser -km /mnt/device`