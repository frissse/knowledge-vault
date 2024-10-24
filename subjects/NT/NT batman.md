---
alias: batman
definition: Better Approach To Mobile Adhoc Network
type: topologie
port: N/A
OSI-layer: physical
more-info: "https://en.wikipedia.org/wiki/B.A.T.M.A.N."
---
[[NT topologie|topologie]]

- Kennis over het netwerk is gedecentraliseerd
- Elk pakket krijgt een dynamisch geleerde route
	- Batman-adv kernel module
	- Virtuele netwerkinterface die voor transport zorgt
	- Regelmatige broadcast van een batman node naar zijn buren
	- Luistert en onthoudt broadcasts van andere buren 
	- Onthoudt langs welke node pakketten moeten gestuurd worden (niet de hele route), kan ook melden dat hij dezelfde kan bereiken
- Werkt ook samen met wired!

B.A.T.M.A.N.'s crucial point is the decentralization of knowledge about the best route through the network — no single node has all the data. 

This technique eliminates the need to spread information about network changes to every node in the network