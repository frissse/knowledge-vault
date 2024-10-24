---
alias: FTP
definition: File Transfer Protocol
type: protocol
port: 21
OSI-model: Application
more-info: "https://en.wikipedia.org/wiki/File_Transfer_Protocol"
---

[[NT protocol]]
[[NT TCP]]

[RFC959](https://www.rfc-editor.org/rfc/rfc959)
[wikipedia](https://en.wikipedia.org/wiki/File_Transfer_Protocol)

### theorie

er bestaan 2 soorten van FTP
1. actieve FTP
	1. aanvraag FTP op poort 21
	2. data FTP op poort 20

	![[Pasted image 20240925081901.png]]

2. passieve FTP
	1. aanvraag FTP op poort 21
	2. server stuur data terug op random poort waarop client moet connecteren
	![[Pasted image 20240925081924.png]]

vergelijking tussen beiden

![[Pasted image 20241006113800.png]]
### configuratie & gebruik

| `ftp<br>> get`               | downloads a file from the server onto the host | all | [more commands](https://en.wikipedia.org/wiki/List_of_FTP_commands) | [[NT FTP]]                         |
| ---------------------------- | ---------------------------------------------- | --- | ------------------------------------------------------------------- | ---------------------------------- |
| `smbclient -L  <ip address>` | login to SMB server                            | all |                                                                     | [[NT SMB]]<br>[[MT Microsoft MOC]] |


wanneer 1ste request wordt gemaakt bij server wordt er een modus afgesproken (actief of passief)
code 227 betekend dat passief modus zal gebruikt worden

![[Pasted image 20240924114440.png]]