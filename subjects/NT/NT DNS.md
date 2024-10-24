---
alias: DNS
definition: Domain Name System
type: protocol
port: 53 UDP
OSI-layer: application
more-info: "https://en.wikipedia.org/wiki/Domain_Name_System"
---
[[NT protocol]]
[[NT UDP]]
### sources

[[cs2-p1w2-dns.pdf]]
https://www.dnsknowledge.com/whatis/authoritative-name-server/
https://www.youtube.com/watch?v=mpQZVYPuDGU
https://www.youtube.com/watch?v=7MT1F0O3_Yw

### info

een technologie die domain names op IP addresses mapt

<u>hierarchie van DNS servers</u>

1. Root Server

root servers zitten helemaal boven aan de tree van de domain resolve
ze stellen het "." voor in een domain name

2. Top Level Domain server

deze stellen de ".be" & ".com" voor, per domain extensie heb je TLD servers

3. Authoritive Name Server

"the final authority about the domain name"
it provides the actual answer to a DNS query
deze server gebruikt cache voor faster responding
deze zoekt naar de juiste name server om het domain op een IP adress te mappen

een DNS databaase hebben zone files
deze zone files bevatten DNS records

<u>DNS records</u>

een DNS record bevat:

TTL nummer (time to live, refresh rate)
Name
IP Adress 
Type

types of DNS records

A: IPv4 records
AAAA: IPv6 records
CNAME: 
- canonical/alias records, forwarding for example a sub domain to another domain
- vaakg gebruikt om wwww.example.com naar example.com
MX: mail server record
SOA: start of authority
- stored administrative information about a DNS zone
- DNS zone is een onderdeel van een bepaald domain (bv subdomain etc)
- worden opgesplitst voor managebility

![[Pasted image 20240927140014.png]]

SERIAL # represents a version of the zone (configuration)
when it is update it tells the secondary servers to update as well

NS
- is the final authority for DNS queries
- steeds 2 records, main & backup name server

DNS Cache poisoning is wanneer de stap tussen die finale resolve en de respons onderschept wordt en een malious response ingevoegd wordt die verwijst naar een andere website

het moeilijke in deze attack is om de query ID te achterhalen.
vroeger was het een counter die cumuleerde. nu is het een randomized nummer.

als het lukt om een name server over te nemen is het mogelijk om eender welk IP te linken aan een domain name query

opeens verwijst facebook.com naar een het IP van een russische malifide webserver 

DNS gebruikt ook de poort 53 op [[NT TCP|TCP]] maar dit is enkel voor routers onderling om naam-ip tabellen uit te wissel

<u>internve vs externe DNS</u> ([[NT firewall|firewall]])

interne DNS is voor resolutie op eigen private network
externe DNS is voor broader domain name resolution

bij externe DNS ga je beperken welke externe DNS servers er toegelaten zijn
-> anders alle [[NT UDP|UDP]] vanuit poort 53 toegelaten

bij interne DNS servers ga je beperken welke externe DNS server 'parent' zijn van jouw DNS server
-> hier ga je de onderlinge communicatie over TCP aan banden leggen (met wie mag mij interne DNS communiceren)


### configuration

used: [[LX bind9]]



