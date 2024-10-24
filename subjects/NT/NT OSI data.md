---
alias: data link layer
definition: the protocol layer that transfers data between nodes on a network segment across the physical layer
type: term
port: N/A
OSI-layer: datalink
more-info: "https://en.wikipedia.org/wiki/Data_link_layer"
---
[[NT OSI model]]

frame ipv packet

voortziet de betrouwbare dataoverdracht over een fysische verbinding
-> gebruikt fysische adressering zoals [[NT MAC address]] (een 48bit uniek adres)

controlesum wordt toegevoegd aan einde vn frame ,[[NT IPv6]] geen checksum meer, data wordt geen meerdere malen meer per laag gecheckt, maar enkel 1malig

pakketten worden in een frame verwerkt, MAC adress 48-bit
   - voegt een [[NT Ethernet header]] toe 
   - de adressering op deze laag gebeurt op basis van een [[NT MAC address]]
   - ethernet is een broadcasting medium -> elk packet op het netwerk wordt gezien door elke machine op dat netwerk