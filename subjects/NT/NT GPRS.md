---
alias: GPRS
definition: General Packet Radio Service
type: technologie
port: N/A
OSI-layer: N/A
more-info: "https://en.wikipedia.org/wiki/General_Packet_Radio_Service"
---
[[NT Networking MOC]]

- gebruikt het huidig [[NT GSM|GSM]] netwerk om meer en snellere informatie te verzenden
	- om dit te kunnen doen moest de base stations ("zendmasten") upgegrade worden
	- alsook de control moest voor versie 2,3 aangepast worden
- GPRS gebruikt [[NT packet switching|packet switching]]
- GPRS gebruikt lege time slots op een kanaal
	- theoretisch max 8 time slots
	- praktisch max 4 timeslots

<u>nadelen GPRS</u>
- beperkte cel capaciteit voor alle gebruikers
- in de praktijk ▶ snelheid beperkt tot 40kbps
- modulatie techniek wijkt af van die gebruikt bij [[NT 3G|3G]]
	- GSMK vs 8 PSK

<u>GPRS vs GSM</u>

![[Pasted image 20241023171052.png]]

<u>coderingschema bij GPRS</u>

- bepaalt hoeveel informatie er tegelijk verzonden kan worden
- hoe dichter de GSM bij een basis station is ▶ hoe beter coderingsschema kan zijn
- CS-4 = vlakbij basis station

![[Pasted image 20241023165714.png]]

<u>techniek met tijdslots</u>

GSM runt op [[NT Multiplexing TDM|Multiplexing TDM]], GPRS hergebruikt deze transitiemethode die gebouwd is rond tijd toe kennen aan de gebruiker 

In GPRS, instead of dedicating a time slot to a single voice call, multiple time slots can be used to transmit data packets. 

This means GPRS can utilize up to 8 time slots per radio frequency channel for data transmission

![[Pasted image 20241023170042.png]]