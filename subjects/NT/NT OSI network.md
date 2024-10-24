---
alias: network layer
definition:  provides the means of transferring variable-length network packets from a source to a destination host via one or more networks
type: term
port: N/A
OSI-layer: network
more-info: "https://en.wikipedia.org/wiki/Network_layer"
---

[[NT OSI model]]

hier zijn het packeten
hier krijgen segmenten een IP header met 32-bit [[NT IPv4|IPv4]] of [[NT IPv6|IPv6]] adres

segmenten krijgeen een IP header & 2 32-bit [[NT IPv4]] adres
   taak van deze laag is het vinden van de bestemmeling van het transport segment
   voegt zijn eigen [[NT IP header]] toe, om extra informatie mee te geven zodat het segment kan doorgestuurd worden per hop