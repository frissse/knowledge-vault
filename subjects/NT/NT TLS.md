---
alias: TLS
definition: Transport Layer Security
type: term
port: N/A
OSI-layer: application
more-info: "https://en.wikipedia.org/wiki/Transport_Layer_Security"
---
[[NT Networking MOC]]
[[CS cryptography]]

#### info

doel van TLS:
- betrouwbaar vertrouwelijk communicatiekanaal verkrijgen
- authenticiteit communicerende applicaties vaststellen

op elke applicatielaag kan TLS gebruikt worden: 
op [[NT TCP|TCP]]: [[NT HTTP|HTTP]], [[NT SMTP|SMTP]], [[NT POP]], [[NT FTP|FTP]]
op [[NT UDP|UDP]]: [[NT SOCKS]]

<u>begrippen</u>

- message digest
	- doel: integriteit van een boodschap verzekeren
	- werking: hash functie zet bericht om naar een vat aantal karakters
	  "the output of a cryptographic function that takes an input (or "message") and returns a fixed-size string of bytes"
	  MD5 & SHA-1 zijn voorbeelden van message digest functies

- symmetrische versleuteling
	- afgesproken sleutel tussen beiden kanten van een communicatie

- assymetrische versleuteling
	- werking: publieke en private sleutel
		- publieke sleutel: ontcijferen maar niet versleutelen
		- private sleutel: kan versleutelen maar niet ontcijferen

- digitale handtekening
	- door middel van message digest aangeven dat het bericht enkel van de desbetreffende afzender kan komen

- certificaat
	- een 3de partije die verzekert dat afzender en ontvanger is wie hij zegt dat ie is
	- kan dienen ter authenticatie van
		- server
		- persoon
		- software


#### usage

<u>aanmaken certificaat voor webserver</u>

webserver maakt eigen private key:

`openssl genrsa -out webserver.key 4092`

webserver maakt certificate signing request voor CA

`openssl req -new -key webserver.key -out webserver.csr`

webserver tekent het certificate signing request

`openssl ca -in webserver.csr -config /etc/ssl/openssl.cnf`





