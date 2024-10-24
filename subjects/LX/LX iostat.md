---
alias: iostat
usage: iostat
example: iostat
definition: used for monitoring system input/output statistics for devices and partitions
type: bash-command
subject: monitoring
more-info: "https://www.geeksforgeeks.org/iostat-command-in-linux-with-examples/"
---
 
[[LX command]]

- ****%user :**** It shows the percentage of CPU being utilization that while executing at the user level.
- ****%nice :**** It shows the percentage of CPU utilization that occurred while executing at the user level with a nice priority.
- ****%system :**** It shows the percentage of CPU utilization that occurred while executing at the system (kernel) level.
- ****%iowait :**** It shows the percentage of the time that the CPU or CPUs were idle during which the system had an outstanding disk I/O request.
- ****%steal :**** It shows the percentage of time being spent in involuntary wait by the virtual CPU or CPUs while the hypervisor was servicing by another virtual processor.
- ****%idle :**** It shows the percentage of time that the CPU or CPUs were idle and the system did not have an outstanding disk I/O request.