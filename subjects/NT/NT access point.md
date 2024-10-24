---
alias: access point
definition: networking hardware device that allows other Wi-Fi devices to connect to a wired network or wireless network. 
type: infrastructure
port: N/A
OSI-layer: physical
more-info: "https://en.wikipedia.org/wiki/Wireless_access_point"
---
[[NT Networking MOC]]

multi radio access point: 
een draadloos netwerkapparaat dat meerdere radiosignalen (meestal op verschillende frequentiebanden) kan uitzenden en ontvangen, waardoor het meerdere draadloze netwerken of apparaten tegelijkertijd kan ondersteunen

meerdere access points samen vormen een 'extended service set'
- AP’s zenden regelmatig beacons uit
- Draadloze apparaten scannen en ontdekken
- Authenticatie en associatie met een AP
- Aanliggende AP’s gebruiken verschillende ‘radio kanalen’

<u>thin & fat access point</u>

fat access point:
▶ Voorziet alle functies voor WLAN functionaliteit:
- RF-naar-RF verbindingen
- RF-naar-draad conversie
- Authenticatie
- Encryptie
- Beheer

thin access
- radio frequenties naar radio frequenties omzetten
- radio frequenties naar wired trafiek omzetten

stealth AP: [[NT SSID|SSID]] van network is verborgen ▶ verhindert automatisch detectie van netwerk (maar niet veilig want netwerk nog steeds getoond wanneer sniffing)
