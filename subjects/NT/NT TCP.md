---
alias: TCP
definition: Transmission Control Protocol 
type: protocol
OSI-layer: Transport
more-info: "https://en.wikipedia.org/wiki/"
---
[[NT protocol]]

![[Pasted image 20240925095350.png]]

TCP provides [reliable](https://en.wikipedia.org/wiki/Reliability_(computer_networking) "Reliability (computer networking)"), ordered, and [error-checked](https://en.wikipedia.org/wiki/Error_detection_and_correction "Error detection and correction") delivery 
of a [stream](https://en.wikipedia.org/wiki/Reliable_byte_stream "Reliable byte stream") of [octets](https://en.wikipedia.org/wiki/Octet_(computing) "Octet (computing)") (bytes) between applications running on hosts communicating via an IP network

[[NT TCP]] verdeelt de data stroom in segmenten
   - onderling tss 2 computers wordt afgesproken hoe groot zo'n segment mag zijn, de kleinste optie wordt gekozen
   - [[NT TCP]] zet een header voor elk datagram -> 20 octets groot
   - belangrijkste info in de [[NT TCP header]]
	   -  port numbers bron & bestemming -> port number van de bestemming kom je te weten wnr de connectie tot stand komt
	   - volgnummer van segment: 
		   - "wanneer elk segment 500 octets heeft -> 1st segment krijgt nummer 0, 2de krijgt 500, 3de 1500, enz"
		   - volgnummer wordt vastgelegd bij het initieren van een TCP verbinding (SYN) -> [[NT ISN]]
		   - De sequence number in de header geeft altijd het volgnummer van de eerste byte van het segment aan
		   - bij ontvangst van de byte vh segment stuurt de ontvanger een ACK nummer, dat de volgend verwachte segmence nummber aangeeft
		   - een "window" bepaalt hoeveel data er per keer kan verzonden worden
	   - checksum: sum van alle octets
o