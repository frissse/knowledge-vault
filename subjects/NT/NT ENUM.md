---
alias: ENUM
definition: A DNS like architecture to map E.164 telephone numbers
type: standaard
port: N/A
OSI-layer: application
more-info: "https://en.wikipedia.org/wiki/Telephone_number_mapping"
---
[[NT Networking MOC]]

- oplossing voor het zoeken naar een nummer
- encodeert een [[NT E.164]] nummer in een DNS request
	- volledig nummer nemen, cijfers omkeren, punt tussen cijfers en .e164.arpa toevoegen
	- +32 (0)3/613.13.13 wordt 3.1.3.1.3.1.6.3.2.3