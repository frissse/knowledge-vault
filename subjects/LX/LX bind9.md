---
alias: bind9
usage:  
example: 
definition: open source DNS server for linux
type: service 
subject: networking
more-info: "https://www.isc.org/bind/"
---
[[LX command]]
[[NT DNS|DNS]]
install via apt
`sudo apt install bind9`

om na te kijken of de configs juist opgesteld zijn
`sudo named-checkconf`

om na te kijken of de zones juist geconfigureerd zijn
`sudo named-checkzones waumans.local /etc/bind/waumans.local`
`sudo named-checkzones ip-reversed.in-addr.arpa /etc/bind/revwaumans.local`

maak een conf file aan in de /etc folder
`vim /etc/bind/named.conf.local`

voeg de DNS & de reverse configuratie toe vd lokale network zone

```
zone "waumans.local" {
		type master;
		file "/etc/bind/waumans.local";
}

zone "1.168.192.in-addr.arpa" {
		type master;
		file "/etc/bind/revwaumans.local"

}
```

maak dan een file aan met de waumans.local configuratie in /etc/bind/waumans.local
"forward lookup zone"

```
$TTL 2d; 2 days
@ IN SOA waumans.local rooot.waumans.local. (
		3
		604800
		86400
		2419200
		604800 )
		IN NS ns.waumans.local
		IN MX 10 mail.waumans.local
ns      IN A 192.168.1.222
mail    IN A 192.168.1.222
		
```

vervolgens de reversed DNS configuratie in /etc/bind/revwaumans.local

`cp /etc/bind/waumans.local /etc/bind/revwaumans.local`

```
$TTL 2d; 2 days
@ IN SOA waumans.local root.waumans.local. (
                3
                604800
                86400
                2419200
                604800 )
                IN NS ns.waumans.local.
131      IN PTR ns.waumans.local
131      IN PTR mail.waumans.local

```

zorg dat deze records het omgekeerde zijn van wat in waumans.local file is gedefinieert

vervolgens testen of de records resolven met nslookup

`nslookup mail.waumans.local`