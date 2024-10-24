---
alias: WPA
definition: Wifi Protected Access
type: protocol
port: N/A
OSI-layer: data-link
more-info: "https://en.wikipedia.org/wiki/Wi-Fi_Protected_Access"
---
[[NT Networking MOC]]

#### info

- Tijdelijke oplossing voor WEP zwakheden
- Werkt op bestaande hardware (enkel firmware update nodig)
- Onderdeel van 802.11i en dus forward compatible
- Doel
	- Verbeterde versleuteling
	- User authenticatie met 2 modi
		- WPA Personal : TKIP/MIC   en  Pre Shared Key (PSK)
		- WPA Enterprise : TKIP/MIC en 802.1X/EAP

<u>4 way handshake</u>
▶ gedeelde sleutel uitwisselen
▶ sessie sleutel aanmaken 

- **Stap 1 - Verzoek (AP → Apparaat)**: De router (Access Point, AP) stuurt een bericht naar het apparaat om te beginnen met de beveiligde verbinding. Dit bericht bevat een willekeurige waarde, de "nonce", die later wordt gebruikt in de encryptie.
    
- **Stap 2 - Antwoord (Apparaat → AP)**: Het apparaat krijgt dat bericht en combineert het met zijn eigen gegevens (zoals de wachtwoordzin) om een nieuwe waarde te berekenen. Het stuurt deze berekende waarde terug naar de router.
    
- **Stap 3 - Bevestiging (AP → Apparaat)**: De router gebruikt de informatie uit stap 2 om te bevestigen dat beide partijen dezelfde geheime sleutel kunnen gebruiken zonder deze te delen. Daarna stuurt de router nog een extra sleutel om de verbinding verder te beveiligen.
    
- **Stap 4 - Voltooiing (Apparaat → AP)**: Het apparaat bevestigt dat het alles goed heeft ontvangen en de beveiligde verbinding is nu opgezet.

▶ 4-way handshake attack (Key ReInstallation Attack)

1. Observatie van de 4-way handshake

De aanvaller bevindt zich in de buurt van zowel de router (access point) als het slachtoffer (bijvoorbeeld een smartphone of laptop). Tijdens de 4-way handshake stuurt de router een willekeurige "nonce" naar het apparaat. Deze nonce wordt gebruikt om de versleuteling voor die sessie op te zetten. Normaal gesproken wordt deze nonce maar één keer gebruikt.

2. Herhaalde verzending van het derde handshake-bericht

De aanval vindt plaats door het **derde bericht** van de 4-way handshake opnieuw te verzenden naar het apparaat. Dit bericht bevat de nonce en wordt normaal slechts eenmaal door de router verzonden. Maar de aanvaller vangt het derde bericht op en stuurt het opnieuw naar het apparaat.

3. Herinstallatie van de versleutelde sleutel

Wanneer het apparaat het derde bericht opnieuw ontvangt, denkt het dat de verbinding mislukt is en **herinstalleert het dezelfde encryptiesleutel opnieuw** in plaats van een nieuwe te gebruiken. Hierdoor wordt de teller die ervoor zorgt dat de versleuteling uniek blijft, teruggezet naar nul. Dit zorgt ervoor dat de aanvaller dezelfde encryptiesleutel opnieuw kan gebruiken.

4. Gevolg: Verzwakte encryptie

Door dit proces kan de aanvaller bepaalde delen van de versleuteling voorspellen of breken, waardoor ze het netwerkverkeer kunnen afluisteren of zelfs manipuleren. Het kan de aanvaller ook in staat stellen om gegevens in te voegen of sommige vormen van verkeer te vervalsen.
#### soorten

<u>WPA Personal</u>

- encryptie op basis van [[NT TKIP|TKIP]]
- authenticatie op basis van PSP (pre shared key)
	- zonder authenticatie servers
	- gebaseerd op 4-way key handshake

<u>WPA Enterprise</u>

- Authenticatie IEEE 802.1X/EAP
- Centraal beheer van gebruikersaccounts
	- AAA server is nodig (Authenticatie, Authorizatie, Accounting)
		- RADIUS protocollen voor AAA en sleuteldistributie
- Meerdere authenticatiemethodes: met paswoorden, digitale certificaten
	- [[NT TLS|TLS]] met certificaten
	- PEAP, LEAP met paswoorden

Nadelen van WPA
- bij een zwakke paswoordzin kan het paswoord brute force gekraakt worden (best Random PSK key)
- Voor de top 1000 SSID / meest gebruikte paswoorden bestaan vooraf gegenereerde rainbowtables
	- Zwakheid in TKIP waardoor je valse ARP pakketten kan sturen Nov 2008 Beck Tews attack  (De inhoud van ARP pakketten is bijna helemaal bekend dus deze zijn een gemakkelijk doelwit om er de MIC en de sleutel uit te halen) 
	- Verkeer naar de client kan gedecrypteerd worden
- Verbetering is overschakelen naar AES (WPA2)

<u>WPA2</u>

- AES gebruikt als encryptie  (Dit is het grootste verschil met WPA)
	- Meestal in hardware (software is te traag)
- Personal Mode
	- Authenticatie PSK (Pre Shared Key)
	- Encryptie AES-CCMP
- Enterprise Mode
	- Authenticatie  802.1X/EAP
	- Encryptie AES-CCMP

WPA3

- standaard sinds 2018
- stereke encryptie: AES-128
	- offline brute force verhinderen
	- betere security ook bij zwakkere passwoorden
- downgrade attack mogelijk