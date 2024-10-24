---
alias: NAT
definition: Network Address Translation
type: technology
port: N/A
OSI-layer: Transport
more-info: "https://en.wikipedia.org/wiki/Network_address_translation"
---
[[NT Networking MOC]]
### sources

![[net3-p1w1-theorie-NAT.pptx]]

[[NAT explained]]

### info

- network address translation
- externe IPs mappen nr interne IPs
- "pure" NAT ga je de interne IPs mappen op de # externe IPs die je hebt, maar dit is niet meer mogelijk de dag vandaag
- NAPT = NAT met ports, dus elk intern IP wordt op een port gemapt om externe verbinding te verkrijgen
- wel nog nodig om een access-list te definen zodat je vast zet welk ip adressen NAT mogen gebruiken
- HTTP accelerator

you never see the actual address of a device, just the internal global address the router of that network uses for NAT 

#### general
- primary use: preserving [[NT IPv4|IPv4]] addresses
- NAT usually happens at the border of a [[NT stub network]]

![[Pasted image 20240923195149.png]]
- 4 types of addresses used in NAT
	- inside address: address of the device that is translated by NAT
	- outside address: the address of the destination device
	- local address: any address that appears on the inside portion of the network
	- global address: any address that appears on the outside portion of the network
- this translates into -> 
	- [[NT inside local address]]:
	  address of source as seen from inside the network
	- [[NT inside global address]]:
	  adress of source as seen from outside the network
	- [[NT outside global address]]:
	  address of destination as seen from outside the network
	- [[NT outside local address]]:
	  address of destination as seen from inside the network
- the [[NT router]] that translates the internal to an outside adress usually changes the inside local address to an insider global address
- the response comes back to this addess and the router knows who this address belongs to and routes in back to the sender of the request


| advantages                                                                                                 | disadvantages                                |
| ---------------------------------------------------------------------------------------------------------- | -------------------------------------------- |
| conserves the legally registered addressing scheme by allowing the privatization of intranets              | increases forwarding delays                  |
| conserves addresses through application port-level multiplexing.                                           | end-to-end adressing is lost                 |
| increases flexibility of connections to the public network                                                 | end-to-end traceability is lost              |
| provides consistency for internal networking addressing schemes                                            | complicates the use of tunneling protocols   |
| keeps the existing private address scheme in check while allowing change to a new public addressing scheme | TCP & UDP connections can be disrupted by it |
| hides address from the outside world                                                                       |                                              |


#### types of NAT

1. static NAT

	- 1 to 1 mapping of local and global addresses -> this remains constant
	- useful for devices who need a consistent address

2. dynamic NAT

	- uses a pool of public addresses and assigns FIFS (first come, first serve)
	- inside device request outside network access > if an address available gets adress out of the public [[NT IPv4|IPv4]] address pool 
	- buying enough public addresses for everyone to use, can be very expensive as 

3. PAT (=Port Address Translation)
	- AKA NAT overload
	- maps multiple private [[NT IPv4|IPv4]] addresses to a single public address or a few addresses
	- source port number is used to uniquely identify the specific NAT translation
	- ensures that devices use different [[NT TCP|TCP]] port for each session
	- 
	- PAT works with Next Available Port
	  if the previous port is not in use, that one is used when requested again from same source
	  if in use PAT selects the next available port starting from the beginning of the appropriate port group 
	  0-511, 
	  512-1,023, 
	  or 1,024-65,535
4. NAT64
	- used to transparently provide access between [[NT IPv6|IPv6]] and [[NT IPv4|IPv4]] only networks
	- temporary mechanism during transition to IPv6

#### configuration

1. verifying & monitoring

`clear ip nat translation *`
`show ip nat translations [verbose]`
`show ip nat statistics`
`show run conf | include NAT`

2. static NAT

```bash
R2(config)# ip nat inside source static 192.168.10.254 209.165.201.5
R2(config)#
R2(config)# interface serial 0/1/0
R2(config-if)# ip address 192.168.1.2 255.255.255.252
R2(config-if)# ip nat inside
R2(config-if)# exit
R2(config)# interface serial 0/1/1
R2(config-if)# ip address 209.165.200.1 255.255.255.252
R2(config-if)# ip nat outside
```

3. dynamic NAT

```bash
R2(config)# ip nat pool NAT-POOL1 209.165.200.226 209.165.200.240 netmask 255.255.255.224
R2(config)# access-list 1 permit 192.168.0.0 0.0.255.255
R2(config)# ip nat inside source list 1 pool NAT-POOL1
R2(config)# interface serial 0/1/0
R2(config-if)# ip nat inside
R2(config-if)# interface serial 0/1/1
R2(config-if)# ip nat outside
```

4. PAT

<u>single IP</u>

```
R2(config)# ip nat inside source list 1 interface serial 0/1/0 overload
R2(config)# access-list 1 permit 192.168.0.0 0.0.255.255
R2(config)# interface serial0/1/0
R2(config-if)# ip nat inside
R2(config-if)# exit
R2(config)# interface Serial0/1/1
R2(config-if)# ip nat outside
```

<u>pool of addresses</u>

```
R2(config)# ip nat pool NAT-POOL2 209.165.200.226 209.165.200.240 netmask 255.255.255.224
R2(config)# access-list 1 permit 192.168.0.0 0.0.255.255
R2(config)# ip nat inside source list 1 pool NAT-POOL2 overload
R2(config)# interface serial0/1/0
R2(config-if)# ip nat inside
R2(config-if)# interface serial0/1/0
R2(config-if)# ip nat outside
```,