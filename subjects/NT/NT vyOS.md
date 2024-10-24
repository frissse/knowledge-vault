---
alias: vyOS
definition: open source routing software running on Debian
type: technology
port: N/A
OSI-layer: N/A
more-info: "https://vyos.io/"
---
[[NT Networking MOC]]

## sources

https://akyriako.medium.com/configure-vyos-as-a-software-based-router-for-your-home-labs-private-networks-a0f4529f0b99

[[net3-p1w2-oef-vyos-manual.pdf]]

![[net3-p1w2-theorie-vyos.odp]]

## info

CLI = gebaseed op [[NT Juniper]]

Ondersteunt onder andere:
- Routing: RIPv2, [[NT OSPF]], [[NT BGP]]
- [[NT Frame Relay]], [[NT PPP encapsulatie]]
- [[NT NAT]], [[NT DHCP]] en DHCP relay
- Redundancy ([[NT VRRP]])
- Statefull [[NT firewall]], [[LX tcpdump]]

CLI runt in 3 modes

1. operational mode 
   status opvragen
2. configuration mode

## configuraton

configuratie save location:
/opt/vyos/etc/config/config.boot

<u>default login:</u>
username: vyos
password: vyos

| command                                                                                                                                                                                                                                                                              | usage                                                                        |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------- |
| install image                                                                                                                                                                                                                                                                        | wnr boot van live CD, permanent install de software                          |
| configure                                                                                                                                                                                                                                                                            | switch to configuration mode                                                 |
| discard                                                                                                                                                                                                                                                                              | to exit zonder wijzigingen door te voeren                                    |
| commit                                                                                                                                                                                                                                                                               | wel wijzigingen doorvoeren                                                   |
| exit discard                                                                                                                                                                                                                                                                         | niet bewaren van wijzigingen                                                 |
| configure<br>set system login user vyos authentication plaintext-password supersecret007<br>commit                                                                                                                                                                                   | set new password voor vyos user                                              |
| how configuration commands > /tmp/configcmds.txt                                                                                                                                                                                                                                     | bewaar alle conf commando's in een bestand                                   |
| show configuration<br>show interfaces<br>show ip route<br>show nat<br>show firewall                                                                                                                                                                                                  |                                                                              |
| run show configuration                                                                                                                                                                                                                                                               | to run operator commando's in configure modus                                |
| configure<br>set interfaces ethernet eth0 address dhcp<br>commit<br>save                                                                                                                                                                                                             | configure to get ip addr from [[NT DHCP]] on an interface                    |
| configure<br>set interfaces ethernet eth1 address 192.168.56.192/24<br>commit<br>save                                                                                                                                                                                                | configure a static ip on the interface                                       |
| configure<br>set interfaces ethernet eth1 address 192.168.56.192/24<br>set service ssh<br>commit                                                                                                                                                                                     | configure ssh on the interface eth1                                          |
| delete interface ethernet eth0 address dhcp                                                                                                                                                                                                                                          | verwijder de setting om adres te krijgen op interface via DHPC               |
| mount /dev/sdb1 /mnt -t vfat	<br>cp /config/config.boot /mnt	<br>umount /mnt                                                                                                                                                                                                         | config file saven naar USB                                                   |
| set protocols static route 0.0.0.0/0 next-hop 192.168.56.1 distance '1'                                                                                                                                                                                                              | static routering                                                             |
| set interfaces loopback lo address 1.1.1.1/32<br>set protocols rip network 192.168.0.0/24<br>set protocols rip redistribute connected                                                                                                                                                | routering met [[NT RIP]]                                                     |
| set firewall name INSIDE-OUT default-action drop<br>set firewall name INSIDE-OUT rule 10 action accept<br>set firewall name INSIDE-OUT rule 10 protocol tcp<br>set firewall name INSIDE-OUT rule 10 destination port 80<br>set interfaces ethernet eth1 firewall out name INSIDE-OUT | firewall out config<br>configure [[NT firewall]] om http server toe te laten |
| set firewall name OUTSIDE-IN default-action drop<br>set firewall name OUTSIDE-IN rule 100 action accept<br>set firewall name OUTSIDE-IN rule 100 state established <br>set interfaces ethernet eth1 firewall in name OUTSIDE-IN                                                      | firewall in config                                                           |
|                                                                                                                                                                                                                                                                                      |                                                                              |
