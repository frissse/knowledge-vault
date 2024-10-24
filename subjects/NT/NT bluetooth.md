---
alias: bluetooth
definition: een open standaard voor draadloze verbindingen tussen apparaten op korte afstand
type: standard
port: N/A
OSI-layer: physical
more-info: "https://nl.wikipedia.org/wiki/Bluetooth"
---
[[NT Networking MOC]]

[[NT PAN]]

netwerken in beperkt gebied voor persoonlijk gebruik

uitgevonden in 1994 door Ericsson
naam komt van Harald Blauwtand -> logo van bluetooth zijn rune tekens van zijn naam

technologie werkt op basis van radio frequencies
maakt gebruikt van [[NT frequency hopping|frequency hopping]] 

bluetooth bevat verschillende profielen op basis van de verschillende use cases

- different profiles
	- HSP (Headset Profile)
		- Use: Basic voice and audio communication between devices like mobile phones and headsets.
		- Function: Allows you to make and receive calls via a Bluetooth headset.
	- HFP (Hands-Free Profile)
		- Use: Hands-free communication, typically in cars.
		- Function: Lets you use your car’s audio system to make and receive calls, control volume, and handle other call-related functions.
	- A2DP (Advanced Audio Distribution Profile)
		- Use: High-quality audio streaming.
		- Function: Enables the transmission of stereo sound from one device (like a phone) to another (like Bluetooth speakers or headphones).
	- AVRCP (Audio/Video Remote Control Profile)
		- Use: Remote control of media playback.
		- Function: Lets you control playback, volume, and other media functions from a Bluetooth device, such as using a phone to control a Bluetooth speaker.
	- PBAP (Phone Book Access Profile)
		- Use: Accessing contact information.
		- Function: Allows devices, such as a car’s infotainment system, to access and display your phone’s contact list.
	- MAP (Message Access Profile)
		- Use: Message notifications and access.
		- Function: Lets a car or other device read, send, or manage text messages from a connected phone.
	- PAN (Personal Area Network Profile)
		- Use: Networking over Bluetooth.
		- Function: Enables internet and local network connectivity between devices using Bluetooth, such as creating a wireless network between your phone and computer.
	- HID (Human Interface Device Profile)
		- Use: Wireless connection of input devices.
		- Function: Allows devices like Bluetooth keyboards, mice, and game controllers to connect and communicate with computers or smartphones.
	- SPP (Serial Port Profile)
		- Use: Wireless data transmission.
		- Function: Emulates a serial port connection, often used for devices like GPS receivers or older devices needing wireless communication
	- FTP (File Transfer Profile)
		- Use: File sharing.
		- Function: Allows one Bluetooth device to browse and transfer files to another Bluetooth device, such as between a phone and a computer.
	- OBEX (Object Exchange)
		- Use: Basic file and object exchange.
		- Function: Supports protocols like FTP and OPP (Object Push Profile) for sending files like images or contacts between devices.

bluetooth bestaat uit verschillende lagen
- Object Exchange RF communicatie
	- uitwisselen van binaire objecten
	- gelijkaardig design als [[NT HTTP|HTTP]] 
- Link Manager Protocol: verbindingsbeheer
	- zet verbindingskanalen op tussen apparaten
	- zorgt voor de authenticatie en encryptie
		- een connectie via bluetooth wordt vaak 1st gedaan via de discovery van het apparaat
		- vervolgens authenticatie via een pincode
	- [[NT synchrone communicatie|synchrone communicatie]] & [[NT asynchrone communicatie|asynchrone communicatie]]
		- VOICE = synrhoon
			- werkt met gereserveerde time slots
			- werkt zoals [[UDP]], geen hertransmissie van verloren frames
		- DATA = asynchroon
			- afspraak over lengte en modulatie
			- wel hertransmissie
			- Low Power Mode: schakelt zelf uit na bepaalde stilte periode
- Service Discovery Protocol
	- protocol dat uitzoekt welke services er mogelijk zijn en op welke manier er mee verbonden kan worden
		- elke service heeft een Universally Unique Identifier

een piconet (een ad hoc bluetooth netwerk) wordt aangemaakt door de link manager (discovery van alle diensten)
▶ bevat max 8 apparaten

verschillende piconets samen = scatternet
- toestellen sturen elkaars communicatie door
- bij elke verbinding: 1 apparaat de slave, 1 apparaat de master
	- master kan verbinden met max 7 actieve slaves
	- tot 255 (3 bit [[NT MAC address|MAC address]]) slaves kunnen passief klaarstaan om connectie te maken met master

![[Pasted image 20241016092020.png]]

 