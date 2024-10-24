---
alias: PEAP
definition: Protect EAP
type: protocol
port: N/A
OSI-layer: data-link
more-info: ""
---
[[NT Networking MOC]]

- Minstens een server-side PKI certificaat
	- Hiermee wordt een beveiligde [[NT TLS|TLS]] tunnel gemaakt waarbinnen de authenticatie van de gebruiker loopt
- Sleutels voor de encryptie worden getransporteerd met de public key van de authenticatie server 
- De uitwisseling van authenticatieinformatie met de client gebeurt nu in een geencrypteerde tunnel

- Alle PEAPs gebruiken een beveiligde TLS tunnel, waarin ze een authenticatieproces uitvoeren
- PEAPv0 /EAP MSCHAPv2
	- Microsoft EAP (Microsoft ondersteunt enkel PEAPv0)
- PEAPv1/ EAP-GTC (Generic Token Card)
	- Gebruiker heeft een Token voor tijdelijk paswoord