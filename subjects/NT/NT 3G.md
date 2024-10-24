---
alias: 3G
definition: 
type: technology
port: N/A
OSI-layer: N/A
more-info: ""
---
[[NT Networking MOC]]

- gebruikt IMT 2000 (=International Mobile Telecommunications-2000), een global standaard voor wireless communication
- wereldwijd 'seamless' toegang
- downwards compatibel met [[NT 2G|2G]]
- hoge data snelheden
	- 'high speed data' eisen vereisen het volgende
		- 144 kbs voor hoge snelheid mobiliteit
		- 384 kbs voor voetgangs of lage snelheid
		- 2 Mbps voor stilstaand
- multi media applicaties
- data transport toegelaten

<u>UMTS</u> (=Universal Mobile Telecommunications System)
(de eigenlijke 3G)

a 3G (third-generation) mobile communication technology designed to provide high-speed data transmission and enhanced mobile services

al het verkeerd komt te samen binnen 1 systeem

UTRA = de radio access technologie used by UMTS

werkt in paren

gebruikt zowel [[NT FDM multiplexing|multiplexing FDM]](most common used)als [[NT Multiplexing TDM|Multiplexing TDM]] (used in urban dense areas)

FDD: 
- “Frequency Divison Duplex” 
- Twee frequenties gescheiden voor UL en DL
TDD: 
- “Time Division Duplex” 
- Eén “ongepaarde” frequentie waarin UL en DL “flexibel” in de tijd worden gealloceerd

ander alternatief = CDMA 
- geeft het gehele radio frequentie spectrum aan de gebruiker
- iedereen gebruikt zijn eigen unieke code als onderscheiding van het gebruik
- een GSM is een soort hark (met verschillende stelen waarop signalen kunnen opgevangen worden)
	- op die manier meerdere signalen tegelijk op te vangen
- belangrijk voordeel van CDMA = power control
	- het signaal uitgezonden wordt aangepast op basis van de afstande tov het station
	- 2 manieren van power control
		- open loop power control
			- GSM bepaalt initiele zend vermogen UL/DL
			- GSM weet door downlink kwaliteit van signaal
			- GSM past hierdoor zijn UL power aan
			- zendmast (BSC) legt de DL power op aan de GSM
		- closed loop power control
			- zendmast (BSC) meet power van elke GSM
			- zendmast (BSC) bepaalt algemene QoS netwerk
			- zendmast (BSC) legt UL & DL power op aan GSM
			- doel: zo weinig mogelijk energie gebruiken

All users transmit simultaneously over the same frequency band, but because each user has a unique code, the signals can be separated at the receiver by correlating the received signal with the corresponding code.


![[Pasted image 20241023173859.png]]

![[Pasted image 20241023174258.png]]

 