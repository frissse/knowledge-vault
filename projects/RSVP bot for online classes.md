---
type: MT Project

---
[[IT integratieProject2]]

## sources

https://chromewebstore.google.com/detail/google-meet-attendance-pa/ojekneoedmekheoagiblbpdanchcoaoo?pli=1
https://developers.google.com/sheets/api/reference/rest
https://learn.microsoft.com/en-us/graph/api/resources/teams-api-overview?view=graph-rest-1.0


## stack

[[MT Powershell]] modules installed:
- MicrosoftTeams
- Microsoft.Graph

Power Automate

[[MT Powershell]]

[[IT Google]] API voor Google Spreadsheet

Graph API Client ID: 3de7bdf7-6b58-4ffa-8a03-8ca9c4b866e0

de source van de server service is een excel sheet waarin de naam en klasgroep van deze persoon staat

server heeft een service runnen die in de background al de calls die de docent doet, logged
wanneer er iemand is die aanwezig is in de call wordt dit gelogd op de server
wanneer deze persoon 5 min voor einde call nog steeds aanwezig wordt deze persoon automatisch op aanwezig gezet

### stappen voor uitvoering

1. er start een meeting
2. meeting vindt plaats
3. meeting stopt
4. een attendence report wordt aangemaakt (handmatig)
5. notification wordt uitgestuurd via email & teams
6. gebruiker download attendee report in .csv
7. powershel script wordt getriggered wnr file in `\Downloads` folder terecht komt
8. powershell script interpreteert csv file met aanwezigheden
9. vervolgens wordt deze aanwezigheden vd meeting gemapt op het VDAB excel sheet
   wnr persoon aanwezig in meeting -> wordt persoon op aanwezig gezet


### structuur sripts: welk doet wat?

<u>barat install</u> 

eerste script dat zal gerund worden na dpkg install
-> enige script dat met sudo rechten gerund moeten worden

dit script moet het volgende doen
1. user 'barat aanmaken'
2. de python venv aanmaken + importeren nodige packages 
3. service aanmaken, naar juiste file moven, de ownership van de service naar de barat user zetten en de service enablen MAAR nt starten

<u>barat start</u>

start de service op, maar moet mogelijk zijn zonder sudo rechten




