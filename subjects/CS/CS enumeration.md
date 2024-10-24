---
alias: enumeration
type: documentation-writeup
subject: cybersecurity
---
[[CS cybersecurity course|cybersecurity course]]
### sources

[[cybersec-p1w4-enumeration-oef41.pdf]]

[[cybersec-p1w4-enumeration-oef42.pdf]]

[[cybersec-p1w4-enumeration-oef43.pdf]]

[[cybersec-p1w4-enumeration-oef44.pdf]]

[[cybersec-p1w4-enumeration.pdf]]

### info

enumeration is part of scanning
-> gathering more information about the target system
- Machine names
- User or Group names
- Shares (Network resources)
- Applications or services (daemons)
- Network info:
	- Routing tables
	- SNMP information
	- More DNS details

-> usually after exploit -> "digging deeper"

GET PERMISSION to do this

#### [[IT Windows]]

on [[IT Windows]]: multiple accounts
- User accounts -> define access to a machine/domain
	- default user accounts
		- guest 
		- administrator
			- disabled by default -> as in: you cannot log in with this user
			- cannot be deleted, cannot be locked out
			- no restriction in permissions
	- default built-in systems accounts (used by processes)
		- Local Service:
			- used by service control manager
			- extensive permissions
			- act as a computer on the netwokr
		- Network Service
			- runs system services with network access
			- The main benefit of the Network Service is its restricted permissions. 
			  If malware or a hacker compromises a service running under this account, they have limited access to the local machine
		- SCM = service control manager
		- System: used by OS and Windows Systems
- Groups (Machine & Domain)
	- (Domain) Local groups: gives permissions and contain global groups
	- Global groups: organize users
	- Universal groups: organize users or global groups and can be placed in domain local groups/ domain universal groups across domain boundaries
- Users, groups & computers have a SID = Security Identifier
	- = Unique for User Account, not Unique for built-in accounts
	- Assigned by a Domain Controller
	- Variable length
	- S-1-5 is default start
	- Used in
		- Security descriptors(owner/primary group of object)
		- ACLs
		- Access Tokens

![[Pasted image 20241008091653.png]]

well known SIDs

Guest: ends in 501
Admin: ends in 500
S-1-5-18: LocalSystem account
S-1-0-0 (Null SID): This is assigned when the SID value is unknown or for a group without any members.
S-1-1-0 (World): This is a group consisting of every user.
S-1-2-0 (Local): This SID is assigned to users who log on to a local terminal.

Windows Security Database

- Local
	- SAM (Security Accounts Manager)
		- Database
		- Contains SIDs
		- Part of Windows Registry
- Domain (on Domain Controller)
	- Active Directory
		- Database
		- Contains objects
		- [[IT LDAP]] compatible
	- On domain located in ntds.dit


Windows Null sessions

A null session is an unauthenticated connection to a Windows computer or server. It allows a user to connect without providing a username or password, essentially giving them anonymous access to certain resources

null sessions were created to enable trusted relationships between domains
it allowed to:
- for SYSTEM account to be authenticated to list system resources
- for trusted domains to enumerate resources
- for non domain computers to authenticate and enumerate users

Since Vista & Windows 2008 ▶ null sessions are hardened
they were hardened through:
- default blocking of null sessions
- security enhancements in access control
- anonymous SID filtering
- local & group policies

with NETbios possible to create null sessions without usern/passw
▶ on ports 137, 138, 139, 445

can be prevented through:
- configuration settings in registry keys
	- restrict anonymous enumeration of SAM (=Security Accounts Manager Account) Accounts and shares
	- setting the HKLM to 0 | 1 | 2 
		- 0 = None (based on default permissions)
		- 1 = Anonymous users restriction (enumeration of SAM database is not permitted33)
		- 2 = No access without explicit credentials
- configuration through group policies

#### [[LX linux MOC]]

info about users on a Linux system is stored in /etc/passwd & /etc/shadow
info stored in `/etc/passwd`:
- username & user ID
- password
- GID
- location of home directory
- preferred shell

info stored in `/etc/shadow`

Username:hashtype$passwordhash:last:min:max:warn:inactive:expire

UID and what the numbers mean

- UID 0 (zero) is reserved for the root.
- UIDs 1–99 are reserved for other predefined accounts.
- UID 100–999 are reserved by system for administrative and system accounts/groups.
- UID 1000–10000 are occupied by applications account.
- UID 10000+ are used for user accounts.

GUID and what they mean

- GID 0 (zero) is reserved for the root group.
- GID 1–99 are reserved for the system and application use.
- GID 100+ allocated for the user’s group.

#### Network enumeration

through:

[[NT DNS|DNS]]
[[NT router|router]]/routing information
[[NT SNMP|SNMP]]

### oefeningen

<u>4.1</u>

to install the PSTools

[link](https://blog.johnsonpremier.net/pstools_configuration/)
`set-executionpolicy remotesigned`

retrieving the SID information from a Windows system in [[MT Powershell]] can be done like this:

```powershell
# 1. Get the SID of the current user
whoami /user  # Retrieves the SID of the currently logged-in user

# 2. Get the SID of a specific user account using WMI
Get-WmiObject Win32_UserAccount | Where-Object { $_.Name -eq "Username" }  # Replace "Username" with the actual username

# 3. Get the SID of a specific user using Get-LocalUser (for PowerShell 5.1+)
(Get-LocalUser -Name "Username").Sid  # Replace "Username" with the actual username

# 4. Get the SID of the local machine (computer SID)

(Get-WmiObject Win32_ComputerSystem).SID  # Retrieves the SID of the computer system

# 5. Get the SID of a local group (e.g., Administrators)
(Get-LocalGroup -Name "Administrators").Sid  # Retrieves the SID of the "Administrators" group

# 6. Get the SIDs of all local users
Get-WmiObject Win32_UserAccount | Select-Object Name, SID  # Retrieves and displays the names and SIDs of all local users

# Alternative method (PowerShell 5.1+):
Get-LocalUser | Select-Object Name, SID  # Retrieves and displays the names and SIDs of all local users

# 7. Get the SID of a domain user
$objUser = New-Object System.Security.Principal.NTAccount("DomainName", "Username")  # Replace "DomainName" and "Username"
$objUser.Translate([System.Security.Principal.SecurityIdentifier]).Value  # Retrieves and displays the SID of the domain user>)

```

with the `net` command
```
net users
net localgroup
net user “username””
net view
net share
```

the `$` behind a share means that it is hidden

to see open ports use

`netstat -a`

4.2

download link for DontStop target: [link](https://www.vulnhub.com/entry/d0not5top-12,191/) (mirror)

use [[,netdiscover]] in Kali to scan the networjk

`netdiscover -i eth1 (hostonly)-r 192.168.56.0`

![[Pasted image 20241014183112.png]]

as the DHCP as only just been turnt on, the 101 address is probably the target (range starts at 100)

next we will use nmap on the ip address

`nmap -sV -A 192.167.56.100`

the open ports on the target are 22,25,80,111 so [[NT ssh|SSH]], [[NT HTTP|HTTP]], [[NT SMTP|SMTP]] 

first enumeration we will do with '[[,nikto]]', a webserver scanner
we find that it runs a website that uses [[,wordpress]], it als has interesting url paths open like myPHPAdmin

next we scan wit [[,dirb]], by using its wordlist it scans the URL for know paths

