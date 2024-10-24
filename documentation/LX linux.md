---
alias: linux documentation
type: documentation-writeup
---
[[IT computer stuff MOC]] 
[[LX linux MOC]]

commands -> [[bash-zsh]]
### sources

<u>linux tuning</u>

![[cs3-p1w1-systemd.odp]]
![[cs3-p1w1-linux-tuning 2.odp]]

<u>LVM</u>

![[cs2-p1w1-lvm 1.odp]]

[https://tuxfixer.com/centos-7-installation-with-lvm-raid-1-mirroring/
https://tldp.org/HOWTO/Partition/fdisk_partitioning.html
https://www.thegeekdiary.com/centos-rhel-how-to-add-physical-volume-pv-to-a-volume-group-vg-in-lvm/](https://github.com/Julian-Heng/yabai-config
https://www.youtube.com/watch?v=uXvWuLn-ZYk
https://canvas.kdg.be/courses/47688/assignments/210309
https://www.thegeekdiary.com/centos-rhel-how-to-add-physical-volume-pv-to-a-volume-group-vg-in-lvm/
https://www.techotopia.com/index.php/Adding_a_New_Disk_to_a_Fedora_Volume_Group_and_Logical_Volume
https://www.howtoforge.com/replacing_hard_disks_in_a_raid1_array
https://www.youtube.com/watch?v=4p2TH7Fwvqs
https://tldp.org/HOWTO/Partition/fdisk_partitioning.html
https://www.golinuxcloud.com/logical-volume-manager-how-to/)

<u>packages</u>

https://www.youtube.com/watch?v=ep88vVfzDAo&t=240s

https://www.baeldung.com/linux/create-debian-package

https://askubuntu.com/questions/1345319/missing-final-newline

https://eart![[cs3-p1w3-theorie-portscan.pptx]]hly.dev/blog/creating-and-hosting-your-own-deb-packages-and-apt-repo/
https://www.internalpointers.com/post/build-binary-deb-package-practical-guide

<u>portscan</u> 

![[cs3-p1w3-theorie-portscan 1.pptx]]

<u>python & scapy</u>

![[cs3-p1w4-theorie-scapy.pptx]]
![[cs3-p1w3-oef-scapy 1.odt]]
<u>tls</u>

![[cs3-p1w3-theorie-tls 1.odt]]

![[cs3-p1w4-theorie-tls-penguins.pptx]]

<u>deb packages</u>

[[cs3-p1w4-theorie-debpackages-ubuntucustompackage.pdf]]

[[cs3-p1w4-theorie-debpackages.pdf]]

apparmor & Selinux

![[cs3-p1w5-theorie-apparmor.odp]]

![[cs3-p1w5-theorie-SElinux.odp]]

<u>ansible</u>

![[cs3-p1w5-theorie-ansible.odp]]

[[cs3-p1w5-oef-ansible.pdf]]
### installation
- when booting from a flash drive make sure the 'Secure Boot' setting is set to 'disabled'

- the partitions needs to start a Linux operating system are
	- /boot/efi: FAT32 format, at least 512mb in size
	- /home: ext4, size of your choice
	- / : ext4, around 10gb

<u>installing [[LX ubuntu]] in VM</u>

guest addittions install:
```
sudo apt update
sudo apt install build-essential dkms linux-headers-$(uname -r)

```

insert the Guest Additions CD

open the CD ROM and run the autorun.sh 

### networking

setting static [[NT IPv4|IPv4]] in [[LX debian]] 
do this by configuring the `/etc/interfaces` file

[[NT DNS|DNS]]

in [[LX Fedora|Fedora]] the network manager uses the /etc/resolve.conf file to set the DNS servers
by creating a `/etc/sysmted/resolved.conf` file you can set the DNS server yourself
to add [[,NextDNS]] as a DNS server add the following to the file

```
[Resolve]  
DNS=45.90.28.0#**484714**.dns.nextdns.io  
DNS=2a07:a8c0::#**484714**.dns.nextdns.io  
DNS=45.90.30.0#**484714**.dns.nextdns.io  
DNS=2a07:a8c1::#**484714**.dns.nextdns.io  
DNSOverTLS=yes
```

### basic commands

#### p1w2

<u>oefeningen</u>

2.1 Paden
Hieronder zie je een lijst van paden. Welke paden zijn relatief, absoluut of fout in Linux?
1. /home - absoluut
2. log/apt - relatief
3. ../.. - relatief
4. ~/Documents - absoluut
5. c:\users - absoluut
6. ./Desktop - relatief
7. ../../etc - relatief
8. /etc/cron.d - absoluut
9. `\usr\bin` - absoluut
10. Downloads - relatief

2.2 Eenvoudige commando's
1. Wat is de eenvoudigste wijze om een lijst van alle commando's te krijgen die beginnen met "pdf" ?
   [[LX ls]]
   `ls /usr/bin/pdf*` of `compgen -c | grep '^pdf'`
2. Wat doet het volgende commando: "date +%T"
   [[LX date]]
   `toon de tijd`

	![[Pasted image 20240924195553.png]]
   
3. Wat doet het commando "id"?
	*toont de uid, guid en de groups waar de current user deel van is*

4. Kopieer het bestand /etc/passwd naar je bureaublad. Verplaats het bestand daarna naar de directory /tmp/tijdelijk. (Je zal die directory eerst moeten aanmaken.) Welke commando's gebruik je hiervoor

	[[LX mkdir]]
	[[LX cp]]

	```
	mkdir /tmp/tijdelijk/
	cp /etc/passwd /tmp/tijdelijk/
	cp /tmp/tijdelijk/passwd /home/parallels/Desktop
	```

5. Toon alle files in “/etc” waarvan de filenaam begint met een “n” en eindigt op “conf”. Gebruik een absoluut pad.

	`ls /etc/n*.conf`

	![[Pasted image 20240924200108.png]]
	

6. Geef een lijst van alle files die in de directory /var/log/ staan en op “.log” eindigen. Gebruik een absoluut pad.
   
	`ls /var/log/*.log`

7. Met welk commando kan je zien hoeveel regels er staan in het bestand /var/log/syslog?

	[[LX cat]]

	`cat /var/log/syslog | wc -l`

8. Zoek op hoe je een user kan locken met passwd (niet doen!)

	[[LX sudo]]

	`sudo passwd -l username`

9. wat doet ls -ls?

	toont output in lijst vorm met disk blocks (1ste nummer)

10. wat doen de commando's "hostname" en "uname -a" 

	`hostname`:
	toont de [[NT DNS]] name of the system

	`uname -a`
	toont systeem informatie, zoals de kernel version, architecture etc
    
11. hoe kan je ls omgekeerd laten sorteren?
    
	`ls | sort -r`

12. toon de inhoud van /proc/cpuinfo
    
	`cat /proc/cpuinfo`

13. Maak 3 bestanden aan in je home-folder met namen "eenBestand", "nogeenBestand" en "laatsteBestand". Wis nu alle bestanden die eindigen in "eenBestand". Verfieer dat enkel het laatste bestand over blijft.

	[[LX touch]]

	```
	touch {touch {eenbestand,nogeenbestand,laatstebestand}
	rm *eenbestand
	```

14. Voer het commando "bash" uit. Wat gebeurt er dan? Wat gebeurt er als je "exit" ingeeft?

	je start een bash shell, `exit` stopt deze

<u>peer tuturing</u>

Part 1: Navigating Directories

1. **Check current directory:**
   ```bash
   pwd
   ```
   - Output: Prints the current working directory path.

2. **List contents:**
   ```bash
   ls
   ls- l    # Lists files with detailed information (permissions, size, etc.).
   ls - a   # Lists files with detailed information (permissions, size, etc.).
   ```

3. **Create directories:**
   ```bash
   mkdir Linux_Practice
   cd Linux_Practice
   mkdir Sub1 Sub2
   ```

4. **Move between directories:**
   ```bash
   cd Sub1
   cd ..
   ```

5. **Remove directories:**
   ```bash
   rmdir Sub2
   ```

Part 2: File Management

1. **Create files:**
   ```bash
   touch file1.txt file2.txt
   ```

2. **Copy file1.txt to Sub1:**
   ```bash
   cp file1.txt Sub1/
   ```

3. **Move and rename file2.txt to renamed_file2.txt in Sub1:**
   ```bash
   mv file2.txt Sub1/renamed_file2.txt
   ```

4. **View file contents:**
   ```bash
   cat file1.txt
   less file1.txt
   ```

5. **Delete renamed_file2.txt:**
   ```bash
   rm Sub1/renamed_file2.txt
   ```

Part 3: Solve with Commands

1. **Concatenate .txt files:**
   ```bash
   cat Sub1/*.txt > combined.txt
   ```

2. **Create a file with random numbers:**
   ```bash
   for i in {1..100}; do echo $((RANDOM % 1000 + 1)); done > random_numbers.txt
   ```

3. **Recovering a file from Trash:**
   ```bash
   mv ~/.local/share/Trash/files/important.txt ./Linux_Practice/
   ```


Part 4: Exploring Commands with man

1. `ls` Command
   - **Useful Options:**
     - `ls -l`: Provides detailed information about files and directories.
     - `ls -a`: Shows all files, including hidden files.

   - **Description:**
     The `ls` command is used to list the contents of a directory.

2. `cp` Command
   - **Useful Options:**
     - `cp -r`: Recursively copies directories.
     - `cp -i`: Prompts for confirmation before overwriting files.

   - **Description:**
     The `cp` command is used to copy files and directories.

Bonus Challenge

1. **Creating a symbolic link:**

[[LX ln]]
   ```bash
   ln -s file1.txt symlink_to_file1.txt
   ```


Challenges and Findings
- Learning to use `man` effectively provided insights into various command options.
- Creating a random number file using built-in tools
- Navigating the Trash directory

### linux headers
Linux headers are declarations of a programming interface needed to interface with Linux kernel.

In short, if you have a program that talks with the kernel, to build that program, you need those files.
[link](https://stackoverflow.com/questions/76495059/what-are-linux-headers-and-why-do-we-need-them)

### linux tuning
#### /etc/issue

toont de melding die getoond bij opstarten van het systeem

![[Pasted image 20240919100309.png]]

kan ook gebruikt worden op netwerkverbinding bij [[NT telnet]] of [[NT ssh]]

#### /etc/motd

Message of the day

![[Pasted image 20240919100441.png]]

#### /etc/profile & /etc/bashrc

opstartbestanden voor iedereen op systeem 
/etc/profile gebruikt voor het definiëren van env vars
bv $PATH $USER $LOGNAME $HOSTNAME

/etc/.bashrc is een config file voor de shell
alternatief is /etc/.zshrc wanneer shell = /bin/[[,zsh]]

per gebruiker is er ook een ~/.bash_profile die de gebruiker zelf kan aanpassen bv env vars
#### umask

Met het commando umask kan je default permissies  
instellen voor gebruikers die niet echt op hun rechten  
letten

omgekeerd van chmod, aangeven wat NIET mag

standaard staan deze op 022 

#### shutdown

uittesten van linux systeem met command

kan ook gedaan worden met: 
CTRL + ALT + DEL x2
CTRL + ALT + BACKSPACE = afsluiten xwindows

#### user management

/etc/login.defs 
-> uitgebreide opties (home dir, nummer, groep)

/etc/pam.d 
-> security instellingen

/etc/skel
-> default directories & bestanden/instellingen van een nieuwe gebruiker

om een user toe te voegen aan sudoers in [[subjects/LX/LX debian|LX debian]]
`usermod -aG sudo username`

als dat niet werkt op de sudoers file als root
`visudo`
en voeg volgende lijn toe bij # User privilege specification
`username ALL=(ALL:ALL) ALL`

#### process monitoring

see commands in [[bash-zsh]]

#### /etc/inittab - runlevels

overzicht runlevels

![[Pasted image 20240922181117.png]]

In /etc/inittab
	0 - halt (Do NOT set initdefault to this)
	1 - Single user mode
	2 - Multiuser, zonder netwerk
	3 - Multiuser met netwerk
	4 - unused
	5 - Multiuser met netwerk en grafisch
	6 - reboot (Do NOT set initdefault to this)
Starten van de n- de runlevel kan met: init n
Opgelet UBUNTU: Runlevel 2-5 is multiuser!!

Default opstarten
	id:3:initdefault:
	si::sysinit:/etc/rc.d/rc.sysinit 
	rc.sysinit laadt alle: 
modules zoals sound, netwerk,...
devices zoals floppy, cdrom, partities...

opstartvolgorde van de modules
manueel kan dit als volgt:

```
root@linux# cd /etc/rc3.d
root@linux# ln -s ../init.d/apache2 S85apache
root@linux# cd /etc/rc5.d
root@linux# ln -s ../init.d/apache2 S85apache
root@linux# chkconfig --list apache2
apache2         0:off   1:off   2:off   3:on    4:off   5:on    6:off
```

Door de S "nummer"  voor de naam, wordt bepaald welke service eerst start. 
Namen die met een K "nummer"  worden in die runlevel gestopt.
De "nummer" van 00 tot 99 geeft de volgorde aan
De kleinste nummer komt eerst
	```
```
ls /etc/rc2.d/K*
/etc/rc2.d/K05preload              
/etc/rc2.d/K08vmware  …
ls /etc/rc2.d/S*     
	 
/etc/rc2.d/S10acpid                     
/etc/rc2.d/S10sysklogd
```

#### sysv-rc-conf

 an easy to use interface for managing `/etc/rc{runlevel}.d/` symlinks. The interface comes in two different flavors, one that simply allows turning services on or off and another that allows for more fine tuned management of the symlinks

sysv-rc-conf = sysv runlevel config

![[Pasted image 20240922153759.png]]
#### systemd 

#### theorie

systemd laat toe om het systeem parallel op te starten -> werkt asynchroon/concurrent
ervoor met sysv en upstart kon dit enkel serieel en semi parallel 

modulariseren vn de daemon/services
kan nu met configuratie bestanden ipv init.d script
gebruik van declaratie van eigenschappen in plaats van scripts

aanpassing van code gebeurt via unit files
bestaat uit meerdere programma'

`/lib/systemd/system/` 

default folder om systemd file in op te slaan

`/etc/systemd/system/`

lokale aanpassingen en override of extension


unit files bestaan uit:
- Acties & parameters
	- ExecStart=
	- mag naar elke executable wijzen
- bevatten vaak ook een [Unit] en [Service] sectie
- De [Install] sectie bepaalt target waarmee unit verbonden is
- Dependencies
- default dependencies
	- Requires= en After= on basic.target; 
	- Conflicts= en Before= on shutdown.target.
- Want & Require starten andere services op
	- Andere service stopt en Require => service stopt ook
	- Andere service stopt en Want => service stopt niet
- After geeft aan dat de service moet opstarten na de aangegeven services zijn opgestart

soorten unit files
- service
- socket
- device
- mount
- scope
- slice
- automount
- swap
- target
- path
- timer
- snapshot

systemd target = synchronisatie punt -> voeren iets uit 
target refereeert naar het runlevel (single user, multiuser,...)

voorbeeld systemd unit file

[Unit]
Description=The Apache HTTP Server
After=network.target remote-fs.target nss-lookup.target

[Service]
Type=forking
Environment=APACHE_STARTED_BY_SYSTEMD=true
ExecStart=/usr/sbin/apachectl start
ExecStop=/usr/sbin/apachectl stop
ExecReload=/usr/sbin/apachectl graceful
PrivateTmp=true
Restart=on-abort

[Install]
WantedBy=multi-user.target

stappen om voorbeeld systemd unit/service aan te maken: helloworld.service

1. maak het shell script aan dat de service zal runnen: /usr/bin/helloworld.sh

```
#!/bin/bash
echo Helloworld op $(date)
```

script uitvoerbaar maken!

`sudo chmod +x /usr/local/bin/hello-world.sh`


2. maak de .service file aan 

```
[Unit]
Description = Mijn eerste helloworld
[Service]
ExecStart = /usr/bin/helloworld.sh
```

3. opstarten & bekijken met [[LX systemctl]]

andere optie is om chkservice te gebruiken

![[Pasted image 20240922175612.png]]

status:
=    stopped   of   >  running
[x]   enabled     [ ] disabled    Link naar service aan/uit
[s]    statisch    Afhankelijk van andere service/ geen [Install]
-m-   masked   niet beheerbaar (ook niet manueel)

#### oefeningen

1. chkservice
Installeer chkservice
Het commando dat je daarvoor gebruikt is:

`sudo apt install chkservice`

Met welk commando zie je de bestanden die chkservice installeert:

[[LX ldd]]
`ldd /bin/chkservice`

Zorg dat de nginx server opgestart is, maar niet automatisch opstart bij het opstarten van de machine.
Welke tekens worden er gebruikt om aan te geven dat dit juist is ingesteld?

[[LX systemctl]]
`systemctl status nginx`
`systemctl disable nginx`

2. Gebruik systemd om de services weer te geven die de langste opstarttijd hebben.
Welk commando gebruik je hiervoor?

[[LX systemd]]
`systemd-analyze blame`

Welke 4 services nemen het meeste tijd in beslag?

![[Pasted image 20240922192128.png]]

3. Stop en start de nginx service met systemctl. Dit doe je met commando:

`systemctl restart nginx`

4. Bekijk de log van nginx Dit doe je met commando:

[[LX journalctl]]
`journalctl -u nginx`


6. Schrijf "helloworldd" een script (service) die om de tien seconden Hello World en de datum en tijd toont.
Het script moet luisteren naar het eerste argument "start" om op te starten en het eerste argument "stop" om de opgestarte service te stoppen.
Test dit script eerst commandline uit!
Zet helloworldd in /usr/local/sbin
Schrijf in /etc/systemd/system/ een heloworldd.service die zorgt dat jouw script wordt opgestart. Je kan als inspiratie /lib/systemd/system/nginx.service gebruiken.
Zet wel het Type op simple (forking start een kind op, maar dat doen wij niet)
Geef het commando systemctl daemon-reload om de veranderingen in te laten.

Test nu uit of je de helloworldd service kan opstarten/stoppen/status bekijken via systemctl.



6. Op Centos/Redhat systemen bestaat een systemd service en die heet firewalld. Op Debian systemen bestaat die nog niet. Straks wel, want jij gaat die maken!

Deze bash functie veegt alle regels van de firewall en laat alles toe:
firewalld_stop() {
[[LX iptables]] -F
iptables -X
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT
}

Deze bash functie veegt alle regels van de firewall, verbiedt alle icmp versie 4 pakketten en laat de rest toe
firewalld_start() {
iptables -F
iptables -X
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT
iptables -A INPUT -p icmp -j DROP
iptables -A OUTPUT -p icmp -j DROP
}
Schrijf het script /usr/local/sbin/firewalld dat deze functies gebruikt.
Voorzie ook dat je script een restart en een reload kan doen (doe voor beide een stop en start)
Test uit met een ping versie 4.

Schrijf nu een firewalld service

Test nu uit of je de firewalld service kan opstarten/stoppen/status bekijken via systemctl.

1. schrijf het firewalld script

```
#/bin/bash  
  
firewalld_stop() {  
       iptables -F  
       iptables -X  
       iptables -P INPUT ACCEPT  
       iptables -P FORWARD ACCEPT  
       iptables -P OUTPUT ACCEPT  
}  
  
firewalld_start() {  
       iptables -F  
       iptables -X  
       iptables -P INPUT ACCEPT  
       iptables -P FORWARD ACCEPT  
       iptables -P OUTPUT ACCEPT  
       iptables -A INPUT -p icmp -j DROP  
       iptables -A OUTPUT -p icmp -j DROP  
}  
  
case "$1" in  
   start)  
       firewalld_stop  
       ;;  
   stop)  
       firewalld_start  
       ;;  
   *)  
       echo "Usage: $0 {start|stop}"  
       exit 1  
       ;;  
esac  

```

2. schrijf de unit file in /etc/systemd/system/firewalld.service

```
[Unit]  
Description=Firewall Service  
After=network.target  
  
[Service]  
Type=simple  
ExecStart= sudo /usr/local/sbin/firewalld.sh start  
ExecStop=sudo /usr/local/sbin/firewalld.sh  stop  
Restart=always  
  
[Install]  
WantedBy=multi-user.target
```

3. reload the daemon

`sudo systemctl daemon-reload`

4. start de service

`sudo systemctl start fireballd.service`
#### ext3/4 journaling

journaling is a key feature that helps prevent data corruption by keeping track of changes that will be made to the file system in a journal before committing them to the main file system structure

data=writeback: 
- Journal schrijft eerst metadata, dan de data. 
- Dit geeft GEEN garantie voor de data integriteit. 
- Na een crash kan bv de oude data in de files staan. 
- Dit is de **performantste** methode.

data=ordered (default mode): 
- Journal schrijft de data en de metadata als één transactie. 
- Dit garandeert dat de data consistent is met het file system. 
- Recente bestanden herstellen altijd na een crash.

data=journal:  
- Journal bevat zowel data als metadata, 
- Performantiedaling. 
- Data en metadata worden 2 keer geschreven.

ext4 = ext2 + journal

met [[LX tune2fs]] kan je [[LX ext2]] omvormen naar [[LX ext3]]

ext3 heeft minste geheugen en CPU nodig om te werken

#### swapspace

standaard [[IT swap]] = partitie, maar mag ook een bestand zijn

aanmaken leeg bestand voor [[IT swap]]

eerst file aanmaken met [[LX dd]] command
`dd if=/dev/zero of=/pagefile bs=1024 count=100000`

mark the file as swap
`mkswap /pagefile`

activeren als swapfile
`swapon /pagefile`

file vs partitie
- bijna geen performanite verschil
- hibernation gebruikt swap partitie en niet file bij [[LX ubuntu]]

#### ramdisk

plaats in [[IT RAM]] reserveren voor een bepaalde applicatie
```
root@linux:~# mkdir -p /mnt/myramdisk
root@linux:~# mount -t ramfs ramfs /mnt/myramdisk -o maxsize=100000
root@linux:~# chown jancelis:jancelis /mnt/myramdisk
```

#### /etc/fstab

![[Pasted image 20240922161848.png]]

- Het device (apparaat)
- De directory waarnaar het apparaat gemount is
- Het type bestandssysteem (ext3, vfat, ntfs, tmpfs,...)
- Extra mount opties (rechten, gebruikte karakters,...)

**Dump (5th Field)**: Used by the `dump` command to decide if a filesystem needs to be backed up.
**Values**:
    - `0`: The filesystem will not be dumped (backed up).
    - `1`: The filesystem will be backed up. This is typically used for important filesystems like `/`.
Usage**: This is mostly obsolete and rarely used in modern Linux systems, as `dump` is not commonly used for backups anymore. Most entries are set to `0`.

**Pass (6th Field)**: Controls the order in which filesystems are checked at boot.
**Values**:
- `0`: Do not check this filesystem at boot. Used for non-essential filesystems like network shares.
- `1`: Check this filesystem first, usually reserved for the root (`/`) filesystem.
- `2`: Check this filesystem after all `1` filesystems. Typically used for other local filesystems like `/home`, `/var`, etc.
**Usage**: The `fsck` utility checks filesystems with pass number `1` first and then proceeds to `2`. All filesystems with the same pass number are checked in parallel if possible.

#### kernel modules

[[LX modinfo]] 
[[LX lsmod]]

inladen vn module via [[LX modprobe]]

When loading a module, `modprobe` automatically handles dependencies by loading other required modules as specified in the module's configuration files

uitladen vn een module via [[LX rmmod]]

Directly removes a specified module from the kernel without considering dependencies. If a module is in use by other modules or processes, `rmmod` will fail unless forced.

#### /proc

- virtueel bestandssysteem
- bestaat nt op schijf, aangemaakt door [[LX kernel]] in [[IT RAM]]
- wordt gebruikt om informatie bij te houden
- oorspronkelijk was dit enkel voor processen, vandaar de naam

voorbeeld:

file met file path /proc/sys/vm/swappiness
- waarde van 0 tot 100
- toont ongebruikt ram percentage weer
	- 0 is zo weinig mogelijk swappen naar schijf pas als geheugen vol
	- 100 is zo veel mogelijk swappen dus direct
	- 10 pas wanneer RAM rond de 90 procent gebruikt is, beginnen swappen

waarde kan aan gepast worden TIJDELIJK in deze file

om dit blijvend aan te passen kan je dit in de /etc/sysctl.conf file doen

je kan de parameter in dit script ook op een andere manier aanpassne
bv wnr je ping wilt deactiveren 

- bv Uitlezen van een parameter en deze in een variabele brengen:
`geenping=$(cat /proc/sys/net/ipv4/icmp_echo_ignore_all)`
- Desactiveren van een ping zolang de machine draait:
`echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_all`
- Desactiveren van een ping ook na een reboot:
`echo "net.ipv4.icmp_echo_ignore_all=1" >> /etc/sysctl.conf`

`sysctl -a ` kan je al deze parameters zien

#### control groups

cgroups zijn [[LX kernel]] voorzieningen om resources vast te leggen op een slice(een aantal services die samen horen)

bv. storage, geheugen, CPU & netwerk


#### oefeningen linux tuning

exercises on linux tuning

1. Copieer met "time" een groot bestand vanaf je cdrom of usb naar je schijf. Doe dit 2 keer. Vergelijk de 2 metingen

[[LX time]]
`time cp <source file path> <destination file path>`

2. Schakel process accounting aan. Kijk welk proces het meest gebruikt wordt.

installeer de acct 

`sudo apt install acct`
[[LX accton]]
`accton /var/log/account/pacct`
![[Pasted image 20240919103019.png]]

`sa --percentages --seperate-times`

![[Pasted image 20240919103240.png]]

3. Draai het tooltje vmstat (om de 2 seconden, 10 metingen)
[[LX vmstat]]
`vmstat 2 10`

![[Pasted image 20240919103808.png]]

4. kernel cache opzoeken
[[LX slabtop]]
`sudo slabtop -s c` sort list op cache size

![[Pasted image 20240919111848.png]]

5. Draaien er applicaties die ipc gebruiken op je systeem?
[[LX ipcs]]
`ipcs -a` toont de shared memory used on the device

![[Pasted image 20240919112341.png]]

6. 
	1. Gebruik ldd om te kijken welke libraries vi gebruik
	2. Gebruik pmap om te kijken hoeveel geheugen vi gebruikt
	3. Wat is het verschil tussen de bibliotheken die pmap toont en de bibliotheken die ldd toont?
	   
	   ldd toont de shared libraries
	   terwijl pmap een memory toont van het running process 
	   toont ook stack, heap en memory

	   ldd is used om te kijken welke libraries er gebruikt zullen worden moest een programma uitgevoerd worden
	   pmap kijkt naar een already running applicatie en de memory usage daarvan

[[LX ldd]]
`ldd $(which vi)`

	![[Pasted image 20240919113149.png]]

start eerst vi op
vervolgens zoek je de process id op
[[LX ps]]
`ps aux | grep [v]i`
en dan doe je `pmap -x <process id>`

![[Pasted image 20240919113511.png]]

7.  Test met hdparm de prestaties uit van je schijf
[[LX hdparm]]
`sudo hdparm -t /dev/<disk number>`

![[Pasted image 20240919114234.png]]

8.  Gebruik lsof om te kijken welke processen (al-dan-niet gewenst) het netwerk gebruiken.
[[LX lsof]]
`sudo lsof -i -P -n`

-i toont network files
-P toont port numbers
-n avoids converting ip to hostnames

![[Pasted image 20240919114527.png]]

alternatief is `sudo lsof -i4`

![[Pasted image 20240919114810.png]]

9. Gebruik het tooltje ip om een extra netwerkkaart aan te maken met de naam dummy1. Deze krijgt het adres 1.2.3.4/24.  
   Test uit of je deze kan pingen. Verwijder dan deze interface.

[[LX ip]]

`sudo ip link add type dummy`
`ip link set dummy0 up`
`ip address add dev dummy0 1.2.3.4/24`
`ping 1.2.3.4`

10. Schrijf een korte oneindige loop in shell script.  
Zorg met cpulimit dat de oneindige loop zo weinig mogelijk cputijd gebruikt. Lukt dit?

cpulimit package moet geinstalleerd worden

`sudo apt install cpulimit`

[[LX cpulimit]]

`cpulimit -p <pid van proces> --limt <perc limit of CPU>`

11. Maak een extra swapfile met de naam pagefile.sys. Zorg dat het systeem deze swapfile ook gebruikt. Waarom gebruikt linux een swapartitie en meestal geen swapfile?

maak een file aan met `dd`
`sudo dd if=/dev/zero of=/pagefile.sys bs=1024 count=100000`

verander die file in een swap
`mkswap /pagefile.sys`

enable swapping op de file
`sudo swapon /pagefile.sys`

12. Verander een kernelparameter zodat deze zo veel mogelijk swapt. Start enkele programma's en zorg ervoor dat je swapfile gebruikt wordt (zoek zelf uit hoe je dat kan zien).

	https://askubuntu.com/questions/642817/how-do-i-edit-a-file-in-proc-that-can-be-viewed-with-cat-but-is-not-editable-b

	https://superuser.com/questions/173353/how-permanently-change-linux-swap-disk-priority

13. Compileer de voorziene c en cpp source bestanden en start de gecompileerde programma's op. Zoek zelf uit wat er fout loopt wanneer je het programma opstart.

	https://www.digitalocean.com/community/tutorials/how-to-install-the-apache-web-server-on-ubuntu-20-04

explanation of the C code

korte uitleg code a.c

er wordt een vier dimensie pointer aangemaakt waar voor elke pointer een gigantisch aantal memory wordt gealloceerd
voortgaand hieraan wordt er een leave functie aangemaakt die checkt op een segmentatie fout en de functie 'leavet' wanneer dit gebeurt

korte uitleg code b.c

een programma die een [[CS DoS]] attack uitvoert op een lokale apache server

korte uitleg code d.c

moven van een file naar een varierende tmp folder die niet bestaat

### logic volume management

#### theorie

= software die ervoor zorgt dat je opslag kan configureren, zonder aanpassingen aan partities en harde schijven

stappen voor opzetten LVM

1. definieer physical volumes
   schijven en partities die je gaat gebruiken met LVM
2. definieer volume groups
   in een volume group combineer je een of meerdere schijven en partities
3. definieer logische volumes binnen een volume group
   binnen een volume group kan je 1 of meerdere logische volumes maken

![[Pasted image 20240922185216.png]]

eigenschappen van LVM

- Verplaatsen Logische Volumes over verschillende fysische schijven/partities
- Groeien en krimpen van Logische Volumes on the fly
- Maken copy-on-write “snapshots” van Logische Volumes
- Vervangen van on-line schijven zonder onderbreking
- Mirroring of striping binnen Logische Volumes

`cat /proc/mdstat` to check RAID setup

[[LX pvcreate]]
[[LX lvcreate]]
[[LX pvdisplay]]
[[LX vgdisplay]]

#### oefening

<u>installatie van CentOS met LVM</u>

virtualisatie gebeurt met [[,UTM]] of [[,virtualbox]]

1. maak de volgende schijven aan 

![[Pasted image 20240923090909.png]]

![[Pasted image 20240923091004.png]]

raid0 = 20 GB
raid1 = 20 GB
home1 = 100 MB
home2 = 200 MB

zorg ook dat de .ISO "dvd" gemount is in de CD/ROM slot van de controller

start de VM op

2. start de VM op

![[Pasted image 20240923092102.png]]

in de installation destination selecter je de 2 20GB drives en selecteer je de custom partitioning option

3. partition settings
   
   je krijgt nu het volgend scherm te zien
   
   ![[Pasted image 20240923092649.png]]

	1. voeg een /boot mount toe, 1000 MB groot
	   
	   ![[Pasted image 20240923092428.png]]

		maak op dezelfde manier ook een /boot/efi partitie aan van 500 MB groot

	2. setup de raid

		![[Pasted image 20240923092608.png]]

	3. nu een swap partitie

		ook die zet je in een RAID configuratie met [[LX ext4]] als format

	 4. finaal de '/' partitie

		de size is wat overschiet
		
		![[Pasted image 20240923093133.png]]

		creer het Logical Volume met de 2 HDD
		zorg dat deze ook in [[IT RAID]] zijn opgezet


	als alles goed ging krijg je volgend scherm te zien

	![[Pasted image 20240923093811.png]]

en begint de installatie



### portscan

#### tools

[[,wireshark]]
[[,tcpdump]]
[[,snort]]
[[,nmap]]
[[,p0f]]

#### theorie

<u>type van portscans</u>

gebaseerd op de  [[NT TCP|TCP]] [[NT 3-way handshake|3-way handshake]]

| scan                                     | OPEN            | CLOSED          | FILTERED         | UNFILTERED | wireshark filter                                                 | nmap             |                                                                               |
| ---------------------------------------- | --------------- | --------------- | ---------------- | ---------- | ---------------------------------------------------------------- | ---------------- | ----------------------------------------------------------------------------- |
| [[CS TCP connect scan\|connect-scan]]    | SYN ACK         | RST             |                  |            | `tcp.flags.syn==1 and tcp.flags.ack==0 and tcp.window_size>1024` | nmap -sS         |                                                                               |
| [[CS TCP stealth scan\|stealth-scan]]    | SYN ACK         | RST             |                  |            | `tcp.flags.syn==1 and tcp.flags.ack==0 and tcp.window_size>1024` |                  | geen RST-ACK respons bij OPEN, maar RST                                       |
| [[CS XMAS scan\|xmas-scan]]              | niets           | RST             | ICMP foutbericht |            | `tcp.flags.fin==1 && tcp.flags.push==1 && tcp.flags.urg==1`      | nmap -sX         |                                                                               |
| [[CS FIN scan\|fin-scan]]                | niets           | RST             | ICMP foutbericht |            | `tcp.flags==0x001`                                               | nmap -sF         | fin packet gestuurd                                                           |
| [[CS NULL scan\|Null scan]]              | niets           | RST             | ICMP foutbericht |            | `tcp.flags==0`                                                   | nmap -sN         | TCP pakket met geen enkel flag                                                |
| [[CS TCP ACK SCAN\|TCP ACK scan]]        |                 |                 | ICMP foutbericht | RST        | `tcp.flags.ack==1tcp.flags.ack == 1 && tcp.window_size == 0`     | nmap -sA         |                                                                               |
| [[CS TCP window scan\|TCP windows scan]] | window size > 0 | window size < 0 | ICMP foutbericht |            | `tcp.window_size>0`                                              | nmap -sW         |                                                                               |
| [[CS decay scan\|TCP decay scan]]        |                 |                 |                  |            | `tcp.flags.syn == 1 && tcp.flags.ack == 0`                       | `nmap -D RND:10` | bekijk de verschillende ip addressen used in<br>Wireshark’s Conversation List |

- [[CS TCP connect scan]]
- [[CS TCP stealth scan]]
- [[CS XMAS scan]]
- [[CS FIN scan]]
- [[CS NULL scan]]
- [[CS TCP ACK SCAN]]
- [[CS TCP window scan]]
- [[CS decay scan]]
#### oefening
1. Hoe werd het binaire logbestand portscan2021.pcap aangemaakt?


2. Wat is het IP adres van de aanvaller?

	192.168.56.1

3. Wat is het IP adres van de target?

	192.168.56.100-103

4. Welke poorten staan open op de target?

	port 22,53,80


6. De target werd op minstens 4 manieren gescand. Geef de 4 methodes en leg uit hoe ze werken.

	- stealth scan
	- tcp connect scan


7. Welke scantool werd gebruikt om de target te scannen? Hoe weet je dit?

[[,nmap]]

8. Welke commando's heeft de aanvaller gebruikt? (geef deze zo volledig mogelijk met alle parameters)

nmap -sV -p 

9. Welk besturingssysteem draait de aanvaller?

linux

10. Stel snort in (zorg dat portscans gedetecteerd worden) en laat snort de portscan analyseren.
Welke aanval(len) zie je in de logs?

### [[PR python|python]] & [[,scapy]]

#### oefening scapy

packages to install 

`sudo apt-get install nmap wireshark tcpdump python3-scapy ipython3 python3-graphviz python3-pip imagemagick`

en

`pip3 install pycrypto`

8. DHCP REQUEST
Gebruik de referenties om een script te schrijven dat op zoek gaat naar alle DHCP servers in het netwerk door een DHCP request te sturen en te kijken wie daar op antwoordt.
Je kan dit ook testen door een DHCP request te sturen op je Host Only interface. Hierop moet dan wel een actieve DHCP server staan. 

9. SCANS
a) XMAS SCAN
Schrijf in python v3 een XMAS scan. Bekijk de scan met wireshark.
Zorg ervoor dat je juist dezelfde output krijgt als bij een nmap XMAS scan.
-Datum/tijd
-Elapsed time
-MAC Address

b) SYN SCAN
Schrijf in python v3 een SYN scan. Bekijk de scan met wireshark.
Zorg ervoor dat je juist dezelfde output krijgt als bij een nmap SYN  scan.

10. SCHRIJVEN VAN PCAP
Schrijf een scapy script dat in python3:
- het eerste argument gebruikt als filename voor de log
- 10 pakketten snift
- deze wegschrijft naar een pcap log
- deze log opent in wireshark

### [[NT TLS]]

1. Activeer je SSL module  
De module mod_ssl zit standaard in het pakket apache-common  
sudo a2enmod ssl  
  
2. Maak een nieuwe site  
sudo touch /etc/apache2/sites-available/sslsite.conf  
  
3. Activeer je nieuwe site (ook al is deze nu nog leeg)  
sudo a2ensite sslsite  
  
4. Pas het bestand /etc/apache2/sites-available/sslsite.conf aan met volgende gegevens:  

```
NameVirtualHost *:443  
<VirtualHost *:443>  
DocumentRoot /var/www/  
SSLEngine on  
SSLCertificateFile /etc/pki/tls/certs/mijnsslserver.crt   
SSLCertificateKeyFile /etc/pki/tls/private/mijnsslserver.key  
</VirtualHost>  
```

  
5. Kijk na in /etc/apache2/ports.conf of de server ook op poort 443 zal luisteren  
  
6. Maak je eigen certificaat en sleutel aan (met jouw naam en emailadres van KdG) en zet deze klaar op de plaats die je aangaf in /etc/apache2/sites-available/sslsite  

	[link](https://www.digitalocean.com/community/tutorials/how-to-set-up-and-configure-a-certificate-authority-on-ubuntu-22-04)

pki = public key infrastructure

```bash
sudo apt install easy-rsa
mkdir ~/easy-rsa # creating a folder for all certs 
ln -s /usr/share/easy-rsa/* ~/easy-rsa/ # link the easy-rsa to your own create dir
chmod 700 /home/sammy/easy-rsa # change the permissions of the file
cd ~/easy-rsa 
./easy-rsa init-pki
./easyrsa build-ca # maake een certificate authority aan
```

<u>maak een cert aan voor je server</u>

```bash
openssl genrsa -out mijnserver.key
openssl req -new -key mijnserver.key -out mijnserver.req
cp mijnserver.req ./pki/reqs
./easyrsa sign-req mijnserver
```

stel de `/etc/hosts` in zodat het localhost adres naar de website verwijst

vergeet ook niet om het certificaat te kopieren naar de plaats waar `update-ca-certificates` ze zoekt

`sudo cp ./issued/mijnserver.crt /usr/local/share/ca-certificates/`

en dan de ca-certificates op het systeem te refreshen

`sudo update-ca-certificates`

Opgelet!  
- Gebruik de zwaarst mogelijke encryptie en sleutels  
- Configureer je eigen interne CA  
Wat is het verschil tussen een key met een passphrase en een key zonder passphrase?  
- Stel openssl.cnf in zodat default BE, Antwerpen,Antwerpen,KdG en uw email adres worden gebruikt  
  
7. Start Apache2 opnieuw op  
  `systemctl restart apache2`
  
8. Je kan het certificaat uittesten via de browser op hetzelfde adres.  
  
9. Zorg ervoor dat apache enkel minstens TLS versie 1.2 gebruikt  

pas in `/etc/apache2/mods-available/ssl.conf` de setting SSLProtocol aan

10. Installeer en configureer proftpd zodat FTP over TLS mogelijk is.  
    Test eerst uit zonder TLS.  
    Test uit met Filezilla met de optie "Require explicit FTP over TLS"

/home/aw/easy-rsa/pki/issued/ftp.mijnserver.crt
/home/aw/easy-rsa/pki/ftp.mijnserver.key

```bash
sudo apt install proftpd
sudo apt install proftpd-mod-crypto # bevat de tls module
```

zet in de `/etc/proftopd/modules.conf`
LoadModule mod_tls.c aan (uncomment)

voeg het volgende toe aan de /etc/proftpd/proftpd.conf file

```
<IfModule mod_tls.c>
  TLSEngine                   on
  TLSLog                      /var/log/proftpd/tls.log

  TLSProtocol                  TLSv1.2 TLSv1.3  # You can also include TLSv1.1 if needed

  TLSRSACertificateFile        <locatie van .crt file>
  TLSRSACertificateKeyFile     <locatie van .key file>
  TLSCipherSuite               HIGH:MEDIUM:+TLSv1:!SSLv2:!SSLv3
  TLSCertificateFile           <locaite van het root crt file voor de CA>
  
  TLSOptions                   NoCertRequest
  TLSVerifyClient              off

  # Enable or disable anonymous access based on your setup
  TLSRequired                  on   # This forces TLS for both control and data connections

  # Allow FTPS explicit connections (AUTH TLS)
  TLSRenegotiate               required off
  TLSOptions                   NoSessionReuseRequired

  # Protect FTP login credentials
  TLSVerifyClient              off
</IfModule>
```


### deb packages


first make sure the right env vars are set to have the correct meta data for the package



to make a package structure with the native architecture (this case debian) use

```
dh_make --native
```

in order to do that the folder structure need to be like `package-name/package-name-version`

easy script to do this:

```bash
#!/bin/bash  
package="barat-server"  
version="1"  
mkdir -p "${package}/${package}-${version}"
```

then make a `package-name.install` where you show which files should become part of the package. example (here /usr/bin and /usr/share)

```
../etc/barat/testExcel.xlsx etc/barat
usr/bin/barat
usr/lib/barat
```

when you run the `debuild -d` command then these files will be put in the debian folder with the package-name as name of the folder

![[Pasted image 20241015195234.png]]

from then on you should work in the original file and run a `debuil -d` whenever you want to change a new .deb file with the changes

these original folders should be in the package-name/package-name-version folder

when you want to tat pushing tho a PPA repo on Launchpad you need to generate a key and add it to the repo + get verified

1. create a gpg key

`gpg --full-gen-key`


2. add the key to the keyserver.ubuntu.com

list the key: `gpg --list-keys`

`gpg --keyserver keyserver.ubuntu.com --send-keys <generated key>`

3. next add the key to your PPA repo, the link for my repo: `https://launchpad.net/~frisse1/+editpgpkeys`

![[Pasted image 20241016213517.png]]

### AppArmor & SELINUX

NODIG: Ubuntu /Debian (mag zonder grafische interface)
`sudo apt-get install apparmor-utils auditd mono-complete`

sources: [link](http://www.mono-project.com/docs/getting-started/application-deployment/)

1. Download het mono programma getstuff.exe  
	Dit programma downloadt het python programma httpserver.py  
Volg de Layout Recommendation vanuit REF1 om dit als een regulier programma op je systeem te voorzien:  
	- maak de directory /usr/lib/getstuff aan  
	- copieer getstuff.exe naar /usr/lib/getstuff/getstuff.exe  
	- schrijf in /usr/bin/getstuff dat je /usr/lib/gestuff/getstuff.exe met mono opstart  
	- maak /usr/bin/getstuff executable  

```bash
sudo mkdir /usr/lib/getstuff
sudo vim /usr/bin/getstuff
sudo chmod +x /usr/bin/getstuff
```

inhoud van `/usr/bin/getstuff`

```bash
#!/bin/sh 
exec /usr/bin/mono /usr/lib/getstuff/getstuff.exe "$@"
```


1. Maak als root een apparmor profiel aan voor getstuff  
	a) `sudo aa-genprof /usr/bin/getstuff`  
	b) Start nu de applicatie  
	- IN EEN ANDERE TERMINAL  
	- ALS GEWONE GEBRUIKER.  
	Doe dit vanuit de homedirectory van de gebruiker.  
	Het profiel werkt nu in complain mode  
	c) Kies Scan en duid alles aan wat je nodig hebt!  
	Let er op dat getstuff moet werken voor alle gebruikers!  
	Let op temp files en procesnummers  
	d) Finish (profiel werkt in enforce mode)  
je vind het aangemaakte profiel in `/etc/apparmord.d/usr.bin.<applicatienaam>`
inhoud van de `/etc/apparmord.d/usr.bin.getstuff

```bash
# Last Modified: Thu Oct 17 10:44:07 2024
abi <abi/3.0>,

include <tunables/global>

/usr/bin/getstuff {
  include <abstractions/audio>
  include <abstractions/base>
  include <abstractions/bash>
  include <abstractions/evince>

  /etc/gai.conf r,
  /etc/host.conf r,
  /etc/hosts r,
  /etc/ld.so.cache r,
  /etc/locale.alias r,
  /etc/mono/4.5/ r,
  /etc/mono/4.5/machine.config r,
  /etc/mono/config r,
  /etc/nsswitch.conf r,
  /etc/protocols r,
  /etc/terminfo/ r,
  /run/systemd/resolve/stub-resolv.conf r,
  /usr/bin/dash ix,
  /usr/bin/getstuff r,
  /usr/bin/mono-sgen mrix,
  /usr/lib/ r,
  owner /dev/shm/mono.* rw,
  owner /home/**/ r,
  owner /home/**/httpserver.py rw,
  owner /proc/*/maps r,

}

```
1. Doe sudo su en tik cd /root  
	Start nu het programma getstuff op als root.  
	De download mag niet meer lukken (kijk na of het bestand httpserver.py geschreven wordt)  
	Kijk na in /var/log/audit/audit.log  
4. Zorg ervoor dat root nu ook kan downloaden naar de directory /root  
5. Maak, gelijkaardig aan getstuff.exe, volgens REF1 een executable /usr/bin/httpserver voor httpserver.py aan. (deze draait niet met mono maar met python3)  
volg de stappen in stap 1

inhoud van httpserver.py

```python
#!/usr/bin/env python3

import http.server
import socketserver

# Define the port
PORT = 1234
DIRECTORY = "/usr/lib/httpserver"
# Handler for HTTP requests
class MyHttpRequestHandler(http.server.SimpleHTTPRequestHandler):
    def __init__(self, *args, **kwargs):
        # Override the directory parameter in SimpleHTTPRequestHandler
        super().__init__(*args, directory=DIRECTORY, **kwargs)

# Create a TCP server that listens on the specified port
with socketserver.TCPServer(("", PORT), MyHttpRequestHandler) as httpd:
    print(f"Serving on port {PORT}")
    httpd.serve_forever()


```

maak ook een `index.html` aan om te tonen wanneer je naar het adres van de webserver surft

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Simple Web Server</title>
</head>
<body>
    <h1>Welcome to My Simple Web Server!</h1>
    <p>This is a basic page served by a Python web server.</p>
</body>
</html>

```

er moet veel meer toegelaten worden dan bij de getstuff, vandaar is de file `/etc/apparmord.d/usr.bin.httpserver` iets uitgebreider

```bash
# Last Modified: Thu Oct 17 11:25:38 2024
abi <abi/3.0>,

include <tunables/global>

/usr/bin/httpserver {
  include <abstractions/base>
  include <abstractions/bash>
  include <abstractions/consoles>
  include <abstractions/openssl>
  include <abstractions/python>

  /etc/ld.so.cache r,
  /usr/bin/dash ix,
  /usr/bin/httpserver r,
  /usr/bin/python3.10 mrix,
  /usr/lib/ r,
  /usr/lib/python3.10/* rw,
  /usr/share/dpkg/cputable r,
  /etc/default/apport r,
  network inet stream,
  network inet dgram,
  network inet6 stream,
  network inet6 dgram,
  network unix stream,
  network unix dgram,
  /etc/mime.types r,
  /etc/apt/apt.conf.d/ r,
  /usr/share/dpkg/tupletable r,
  capability dac_read_search,
  capability dac_override,

}
```


1. Maak nu ook een apparmor profiel voor /usr/bin/httpserver. Let erop dat je ook uittest of je de httpserver kan bereiken vanuit je browser vanop http://localhost:1234

Opmerking: Je profiel opnieuw maken kan je door /etc/apparmor.d/usr.bin.getstuff te verwijderen en  
de machine terug op te starten

### ansible


