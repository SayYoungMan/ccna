# CCNA CheatSheet

## Standards

### IEEE

- 802.3i: 10Base-T (Ethernet)
- 802.3u: 100Base-TX (Fast Ethernet)
- 802.3z: 1000Base-LX
- 802.3ab: 1000Base-T (Gigabit Ethernet)
- 802.3ae: 10GBase-SR/LR/ER
- 802.3an: 10GBase-T (10 Gig Ethernet)
- 802.1q: dot1q VLAN tagging
- 802.1d: STP
- 802.1w: RSTP
- 802.1s: MSTP
- 802.11, 802.11b, 802.11g: 2.4GHz Wireless network
- 802.11a: 5GHz Wireless network
- 802.11i: WPA2
- 802.1x: Authentication for wireless network
- 802.3af: PoE
- 802.3at: PoE+
- 802.3ad: LACP

### RFC

- RFC 1918: Private IPv4 Range
- RFC 4954: QoS DSCP marking recommendation

## Addresses

### MAC Address

- CDP Multicast: 0100.0CCC.CCCC
- LLDP Multicast: 0180.C200.000E
- HSRPv1 virtual MAC: 0000.0c07.acXX
- HSRPv2 virtual MAC: 0000.0c9f.fXXX
- VRRP virtual MAC: 0000.5e00.01XX
- GLBP virtual MAC: 0007.b400.XXYY

### IPv4

- RIPv2 multicast: 224.0.0.9
- EIGRP multicast: 224.0.0.10
- OSPF Hello multicast: 224.0.0.5
- OSPF DR/BDR multicast: 224.0.0.6
- HSRPv1 multicast: 224.0.0.2
- HSRPv2 multicast: 224.0.0.102
- VRRP multicast: 224.0.0.18
- GLBP multicast: 224.0.0.102

## Times

- STP Forward delay (How long will the switch will stay in listening/learning state): 15 seconds
- STP Hello BPDUs: every 2 seconds
- STP Max age: 20 seconds (6 seconds for RSTP)
- STP convergence: 50 seconds
- RIP advertisement: every 30 seconds
- OSPF hello message: every 10 seconds (30 seconds for nonbroadcast, point-to-multipoint)
- OSPF dead timer: 40 seconds (120 seconds for nonbroadcast, point-to-multipoint)
- OSPF LSA aging: 30 minutes
- CDP message: every 60 seconds
- CDP holdtime: 180 seconds
- LLDP message: every 30 seconds
- LLDP holdtime: 120 seconds
- LLDP reinitialization delay: 2 seconds
- Err-disable recovery: 5 minutes
- Mac address table aging: 5 minutes
- PAgP notification: every 30 seconds
- ARP table aging: 240 seconds
- HSRP Hello Messages: every 3 seconds

## Protocol Numbers

### UDP

- 53: DNS
- 67: DHCP Server
- 68: DHCP Client
- 69: TFTP
- 123: NTP
- 161: SNMP Agent
- 162: SNMP Manager
- 514: Syslog
- 1812: RADIUS
- 1813: RADIUS
- 1985: HSRP
- 3222: GLBP
- 5246: CAPWAP Control tunnel
- 5247: CAPWAP Data tunnel

### TCP

- 20: FTP data
- 21: FTP control
- 22: SSH
- 23: Telnet
- 25: SMTP
- 49: TACACS+
- 53: DNS
- 80: HTTP
- 110: POP3
- 443: HTTPS
- 8140: Puppet
- 10002: Chef
