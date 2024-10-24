---
alias: vmstat
usage: vmstat** [ option ] [delay [count]]
example: vmstat 5
definition: a command with no parameters, it will show you a set of values. These values are the averages for each of the statistics since your computer was last rebooted.
type: bash-command
subject: monitoring
more-info: "https://www.howtogeek.com/424334/how-to-use-the-vmstat-command-on-linux/"
---
 
[[LX command]]

![[Pasted image 20240922105601.png]]

cpu: user, system, idle en waiting (I/O)
procs: runnable (gereed) of blocked (wachten op I/O)
memory: vrij, buffer (naar HDD), cache (van HDD)
swap: si (KB ingeswapt), so (KB uitgeswapt)
si > so: mogelijk dezelfde pagina's ingeswapt
io: bi blocks van de schijf, bo blocks naar de schijf 

De procs kolom r (runnable) geeft het aantal wachtenden voor de processor(en) weer. 
>  4 keer het aantal processoren
=> processen te lang wachten om te kunnen draaien. 
=> snellere processoren nodig (niet méér CPU's).

De procs kolom b (blocked) geeft het aantal geblokkeerde processen aan. Deze wachten dus op I/O. Wanneer dit aantal hoog is, is het aan te raden om je schijfactiviteit te bekijken met iostat. 