---
alias: application layer
definition: an abstraction layer that specifies the shared communication protocols and interface methods used by hosts in a communications network
type: term
port: N/A
OSI-layer: application
more-info: "https://en.wikipedia.org/wiki/Application_layer"
---
[[NT OSI model]]
 

(netwerk)applicaties worden hier gedraaid)

bij het idee van de browser, is de applicatielaag, de laag die op zoek gaat met wie je gaat communiceren.
-> ze levert hiervoor diensten, bv. bestandsoverdracht en virtuele terminals ([[NT telnet]] of [[NT ssh]])

typische TCP/IP applicaties:

- [[NT telnet]] 23 of [[NT ssh]] 22
- [[NT FTP]] gebruikt 2 poorten: 
  21 = send & controle signalen, 
  20 = om de data terug te krijgen
- ftp werkt met [[NT TCP]] dus steeds bevestiging dat elke packetje worden geleverd
  -> vraagt veel resources van je systeem 
- [[NT TFTP]] werkt met [[NT UDP]] " als  da aan komt komt da aan, als da ni aankomt is da maar zo"
  Microsoft stuurt een packet 4 maal om zeker te zijn dat het aan komt
- [[NT SMTP]]
- [[NT SNMP]]
- [[NT HTTP]]
- [[NT DHCP]]