---
alias: RFID
definition: Radio Frequency Identification 
type: technology
port: N/A
OSI-layer: physical
more-info: "https://en.wikipedia.org/wiki/Radio-frequency_identification"
---
[[NT Networking MOC]]

een systeem gebaseerd op radio frequenties
heeft de mogelijkheid om informatie op te slaan in apparaten ▶ RFID tags
RFID tags zijn intelligente barcodes die kunnen verbinden met een netwerk
netwerk bestaat uit:
- een transponder
- een lees/schrijf unit
RFID tags hebben 3 categorieen
- actief
	- met batterij
	- kunnen signaal uitzenden (met interval)
	- reikwijdte tot 100m
- semi actief
	- met batterij
	- antwoorden enkel wanneer iets gevraagd wordt
- passief
	- ID kan enkel gescand worden
	- meeste winkel tags zijn in principe geen RFID want geen unieke ID
	  wel bij Decathlon
	- vb: 
		- id tags bij handen (max afstand 5 cm)
		- vervoersbewijzen De Lijn

vergelijking barcode vs RFID tag


| barcode                            | rfid                             |
| ---------------------------------- | -------------------------------- |
| identificatie artikel type         | identificatie artikel exemplaar  |
| een voor een te scannen            | tegelijk in bulk lezen           |
| leesafstand is enkele centimeters  | leesafstand is enkele meters     |
| directe zichtbaarheid noodzakelijk | directe zichtbaarheid niet nodig |
| eenmalig aanmaken                  | herprogrammeerbaar (sommige)     |
| lage productie kosten              | duur in vergelijking met barcode |
| eenvoudig aan te brengen           | aanbrengen vergt aandacht        |

RFID werkt op verschillende frequenties

- identificatie mens/dier
	- 125 kHz - 134 kHz - low frequency
- bibliotheek
	- 13.56 MHz - high frequency
- supply chain / luchtvaart
	- 868 tot 955 MHz - ultra high frequency
	- decathlon heefft 200.000 UHF tags voor zijn producten
		- frequency = 865 - 868
		- uitleeshoek is belangrijk
- tolpoorten / fleet management
	- actieve tags
	- 2.45 Ghz
	- 5.8Ghz

nadelen van RFID

- passieve tags werken niet met vloeistof/metaal in de nabijheid
	- 125 Khz tags worden niet gestoord
- tags die te dicht bij elkaar liggen storen elkaar
	- 13.45 moeten op 60 cm liggen
- geen beveiliging ▶ enkel binaire datastroom met nummer

 