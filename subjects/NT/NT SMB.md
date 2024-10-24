---
alias: SMB
definition: Server Message Block
type: protocol
port: 445 TCP
OSI-model: application
more-info: "https://nl.wikipedia.org/wiki/Server_Message_Block"
---

[[NT Networking MOC]]
[[MT Microsoft MOC]]



mostly used on Microsoft devices

runs at the Application or Presentation layers

mostly used with [[IT NETBios]] 

gebruik het package smbclient om op [[LX linux MOC|linux]]  te gebruiken

port: 445 TCP

| `smbclient -L  <ip address>`      | login to SMB server                                                                                                                                             | all |     | [[NT SMB]]<br>[[MT Microsoft MOC]] |
| --------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- | --- | --- | ------------------------------ |
| `smbclient \\\\ip address\\share` | inloggen op specifieke share op SMB server<br><br>rond navigeren doe je met de gebruikelijke ls cd en pwd commandos<br><br>![[Pasted image 20240912203337.png]] | all |     | [[NT SMB]]<br>[[MT Microsoft MOC]] |
