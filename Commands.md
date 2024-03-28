# Cisco IOS Commands for CCNA

## General

### Switching between modes

- `>enable`: Enter privileged EXEC mode
- `#configure terminal`: Enter global configuration mode
- `exit`: Move back one level in hierarchical command structure
- `(config)#interface <interface-id>`: Enter configuration interface mode
- `(config)#interface range <range>`: Enter config-if-range mode where changes apply to all interfaces

### Configuration files

- `write`: Write running-config to startup-config
- `write memory`: Write running-config to startup-config
- `copy running-config startup-config`: Write running-config to startup-config

## Switching

### MAC Address

- `#show arp`: Show IP to MAC address mapping
- `#show mac address-table`: Show MAC address to port mapping
- `#clear mac address-table dynamic`: Remove all dynamically learned MAC addresses
  - `#clear mac address-table dynamic address <mac-address>`: Remove specific MAC address entry
  - `#clear mac address-table dynamic interface <interface-id>`: Remove specific interface entry

### Switch Interfaces

- `#show interfaces <interface-id>`: Show extensive information about the interface
- `#show interfaces status`: Show summary of switch interfaces
- `(config-if)#speed <speed>`: Set the speed of communication
- `(config-if)#duplex <mode>`: Set the duplex mode of communication
- `(config-if)#description <name>`: Set the name field of the interface

## IPv4

- `#show ip route`: Show routing table
- `#show ip interface brief`: Show status of each interface as well as IP addresses
- `(config)#ip route <ip-address> <subnet-mask> <next-hop>`: Configure static route
- `(config)#ip route 0.0.0.0 0.0.0.0 <next-hop>`: Configure default route
- `(config-if)#ip address <address> <subnet-mask>`: Assign IPv4 address to the interface
- `(config-if)#no shutdown`: Enable the interface

## IPv6

- `#show ipv6 interface brief`: Show summary of addresses assigned
- `#show ipv6 neighbor`: Show IPv6 neighbor table
- `(config)#ipv6 unicast-routing`: Allow the router to perform IPv6 routing
- `(config-if)#ipv6 address <ipv6-address/prefix>`: Assign IPv6 address to the interface
- `(config-if)#ipv6 address <network/prefix> eui-64`: Use EUI-64 interface identifier to generate IPv6 address
- `(config-if)#ipv6 enable`: Enable IPv6 on an interface and assign link-local address
- `(config-if)#ipv6 address <ipv6-address> anycast`: Configure anycast address
- `(config-if)#ipv6 address autoconfig`: Use SLAAC to assign IPv6 address automatically
- `(config)#ipv6 route <destination/prefix> {<next-hop>|<exit-interface> <next-hop>} <ad>`: Configure IPv6 static route

## VLAN

- `#show vlan brief`: Show summary of VLAN information
- `(config)#vlan <vlan-number>`: Create VLAN and enter config-vlan mode
- `(config-vlan)#name <name>`: Assign a name to the VLAN
- `(config-if)#switchport mode {access|trunk}`: Configure the port to be access/trunk port
- `(config-if)#switchport access vlan <vlan-number>`: Assign port to the VLAN
- `(config-if)#switchport voice vlan <vlan-id>`: Tag phone's traffic with VLAN ID

### Trunk Port

- `#show interfaces trunk`: Show information about trunk ports
- `(config-if)#switchport trunk encapsulation {dot1q|isl}`: Set the encapsulation mode of the trunk port
- `(config-if)#switchport trunk native vlan <vlan-number>`: Configure native VLAN of the trunk port
- `(config-if)#switchport trunk allowed vlan <vlans>`: Configure the list of allowed VLANs
  - `switchport trunk allowed vlan add <vlan-number>`: Add VLAN to allowed list.
  - `switchport trunk allowed vlan remove <vlan-number>`: Remove VLAN from allowed list.
  - `switchport trunk allowed vlan all`: Allow all VLANs (default state).
  - `switchport trunk allowed vlan except <range>`: Allow all VLANs except the ones specified.
  - `switchport trunk allowed vlan none`: Not allow any VLAN.

### Router on a Stick (ROAS)

- `(config)#interface <interface-id>.<subinterface-number>`: Enter config-subif mode
- `(config-subif)#encapsulation dot1q <vlan-number> {native}`: Subinterface will behave as if it arrived on the interface if frame is tagged with the VLAN number

### SVI (Switch Virtual Interface)

- `(config)#ip routing`: Enable layer 3 routing on the switch
- `(config-if)#no switchport`: Configure the interface as routed (layer 3) port

### DTP

- `show dtp interface <interface-id>`: Show DTP information about the interface
- `(config-if)#switchport nonegotiate`: Disable DTP
- `(config-if)#switchport mode dynamic {auto|desirable}`: Set DTP dynamic modes

### VTP

- `#show vtp status`: Reveal useful information about VTP
- `(config)#vtp mode {server|client|transparent}`: Set VTP mode of operation
- `(config)#vtp domain <name>`: Change the VTP domain name

## Spanning Tree Protocol (STP)

- `(config)#spanning-tree mode <mode>`: Set the mode of STP
- `(config)#spanning-tree vlan <vlan-number> root {primary|secondary}`: Set the switch as primary of secondary root bridge for particular VLAN
- `(config)#spanning-tree vlan <vlan-number> priority <priority>`: Manually set the STP priority.
- `(config-if)#spanning-tree portfast`: Enable portfast for the interface
- `(config)#spanning-tree portfast default`: Enable portfast to all access ports
- `(config-if)#spanning-tree bpduguard enable`: Enable BPDU guard on the interface
- `(config)#spanning-tree portfast bpduguard default`: Enable BPDU guard on all portfast ports

## Etherchannel

- `#show etherchannel load-balance`: Show current load balancing method
- `#show etherchannel port-channel`: Show virtual port-channel interface information
- `#show etherchannel summary`: Show summary of etherchannel information
- `(config)#port-channel load-balance <method>`: Set the load balancing method
- `(config-if-range)#channel-group <number> mode <mode>`: Set etherchannel for range of interfaces
- `(config-if-range)#channel-protocol {pagp|lacp}`: Set channel protocol (not really used)

## Dynamic Routing

### RIP

- `(config)#router rip`: Use RIP on the router and enter config-router mode
- `(config-router)#version <version>`: Set RIP version
- `(config-router)#no auto-summary`: Disable auto conversion to classful networks
- `(config-router)#passive-interface <interface-id>`: Stop RIP advertisements out of the interface
- `(config-router)#default-information originate`: Advertise default route information to neighbours
- `(config-router)#network <ip-address>`: Activate RIP on the interfaces that fall in the classful IP address range

### EIGRP

- `(config)#router eigrp <as-number>`: Set EIGRP on the router

### OSPF

- `#show ip ospf interface brief`: Show summary of OSPF interfaces
- `(config)#router ospf <process-id>`: Use OSPF and enter OSPF configuration mode
- `(config-router)#network <ip-address> <wildcard-mask> area <number>`: Enable OSPF on the interfaces under specified IP range in the specified area
- `(config-router)#passive-interface <interface-id>`: Stop sending OSPF hello messages out of the interface
- `(config-router)#router-id <id>`: Manually configure router ID
- `(config-router)#maximum-paths <number>`: Set maximum number of paths to use for ECMP load-balancing
- `(config-router)#auto-cost reference-bandwidth <bandwidth>`: Set reference bandwidth in Mbps
- `(config-if)#ip ospf cost <cost>`: Manually configure the OSPF cost on the interface
- `(config-if)#ip ospf <process-id> area <area>`: Active OSPF directly on an interface
- `(config-router)#passive-interface default`: Configure all interfaces as passive interfaces
- `(config-if)#ip ospf network <type>`: Configure the network type on an interface
- `(config-if)#ip ospf priority <number>`: Change the OSPF interface priority
- `(config-if)#ip ospf hello-interval <seconds>`: Set OSPF hello timer
- `(config-if)#ip ospf dead-interval <seconds>`: Set OSPF dead timer
- `(config-if)#ip ospf authentication-key <key>`: Configure password for OSPF
- `(config-if)#ip ospf authentication`: Use the OSPF password

## Serial Interfaces

- `#show controllers <interface-id>`: Check which is DCE/DTE
- `(config-if)#clock rate <kbps>`: Set speed of connection on the DCE side
- `(config-if)#encapsulation ppp`: Change encapsulation method from HDLC to PPP

## HSRP

- `#show standby`: Show HSRP status
- `(config-if)#standby <group-number>`: Configure HSRP on the router
- `(config-if)#standby version 2`: Use HSRPv2
- `(config-if)#standby <group-number> ip <default-gateway>`: Set up the virtual IP address
- `(config-if)#standby <group-number> priority <number>`: Set priority on the router to determine which will be active
- `(config-if)#standby <group-number> preempt`: Make router to take the role of active router if set with higher priority

## ACL

### Standard ACLs

- `#show access-lists`: Display all configured ACLs
- `#show ip access-lists`: Display only IP ACLs
- `(config)#access-list <number> {deny|permit} <ip> <wildcard-mask>`: Configure standard ACL
  - `(config)#access-list <number> {deny|permit} host <ip>`: Configure ACL for single host
  - `(config)#access-list <number> {deny|permit} any`: Configure for all IP
- `(config)#access-list <number> remark <remark>`: Put remark to ACL to help remember it
- `(config-if)#ip access-group <number> {in|out}`: Apply ACL to the interface
- `(config)#ip access-list standard <acl-name>`: Configure standard named ACL and enter config-std-nacl mode
- `(config-std-nacl)# <entry-number> {deny|permit} <ip> <wildcard-mask>`: Configure an entry for ACL
- `(config-std-nacl)#no <entry-number>`: Remove an individual entry

### Extended ACLs

- `(config)#access-list <number> {permit|deny} <protocol> <src-ip> <dest-ip>`: Configure extended ACL based on source and destination IP
- `(config)#ip access-list extended {<name>|<number>}`: Enter extended ACL configuration mode
- `(config-ext-nacl)# <seq-num> {permit|deny} <protocol> <src-ip> <dest-ip>`: Set the entry in extended ACL
- `(config-ext-nacl)# {deny|permit} <protocol> <src-ip> <src-port-num> <dest-ip> <dest-port-num>`: Configure port number matching for extended ACL

## CDP & LLDP

- `#show {cdp|lldp}`: Show global configuration for CDP/LLDP
- `#show {cdp|lldp} traffic`: See counts of transmitted CDP/LLDP
- `#show {cdp|lldp} interfaces`: See CDP/LLDP information about the interfaces
- `#show {cdp|lldp} neighbors`: See CDP/LLDP neighbor table
- `#show {cdp|lldp} neighbors detail`: See detailed information about CDP/LLDP neighbors
- `#show {cdp|lldp} entry <name`: See detailed information about specific neighbor

- `(config)#{cdp|lldp} run`: Enable CDP/LLDP globally
- `(config-if)#cdp enable`: Enable CDP on the specific interface
- `(config-if)#lldp transmit`: Enable LLDP on Tx
- `(config-if)#lldp receive`: Enable LLDP on Rx
- `(config)#{cdp|lldp} timer <seconds>`: Configure CDP/LLDP message timer
- `(config)#{cdp|lldp} holdtime <seconds>`: Configure CDP/LLDP holdtime
- `(config)#lldp reinit <seconds>`: Configure LLDP reinitialization delay
- `(config)#cdp advertise-v2`: Enable CDPv2

## Time Related

### Device Time

- `#show clock`: Show internal clock of the device
- `#show clock detail`: See the time source
- `#clock set <time> <date>`: Configure the time on the device
- `#calendar set <time> <date>`: Configure the hardware clock
- `#clock update-calendar`: Sync calendar to clock's time
- `#clock read-calendar`: Sync clock to calendar's time
- `(config)#clock timezone <name> <offset>`: Configure timezone
- `(config)#clock summertime <name> recurring <offset> <start> <end>`: Configure recurring daylight saving time

### NTP

- `#show ntp associations`: See configured NTP servers
- `#show ntp status`: View NTP status
- `(config)#ntp server <ip> [prefer]`: Sync with a NTP server
- `(config)#ntp source <interface-id>`: Set the interface to act as NTP server
- `(config)#ntp master`: Make the device to act as NTP server
- `(config)#ntp peer <ip>`: Make the device run in symmetric active mode

- `(config)#ntp authenticate`: Enable NTP authentication
- `(config)#ntp authentication-key <number> md5 <key>`: Create NTP auth key
- `(config)#ntp trusted-key <number>`: Speicify the trusted key
- `(config)#ntp server <ip> key <key>`: Connect to server with authentication

## DNS

- `#show hosts`: Show all hosts that were configured or learned
- `(config)#ip dns server`: Make router to act as a DNS server
- `(config)#ip host <name> <ip>`: Statically configure a hostname to IP mapping
- `(config)#ip name-server <ip>`: Configure DNS server to query from if requsted record isn't in the table
- `(config)#ip domain lookup`: Perform DNS query
- `(config)#ip domain name <domain>`: Configure default domain name

## DHCP

- `#show ip dhcp binding`: Show all DHCP clients connected
- `(config)#ip dhcp excluded-address <start-ip> <end-ip>`: Specify a range of address that won't be given to DHCP clients
- `(config)#ip dhcp pool <pool-name>`: Create DHCP pool and enter dhcp-config mode
- `(dhcp-config)#network <ip> {<network-mask>|</prefix>}`: Specify the subnet of addresses to be assigned to clients
- `(dhcp-config)#dns-server <ip>`: Specify the DNS server that DHCP clients should use
- `(dhcp-config)#domain-name <domain>`: Specify the domain name of the network
- `(dhcp-config)#default-router <ip>`: Specify the default gateway
- `(dhcp-config)#lease {<time>|infinity}`: Specify the lease time
- `(config-if)#ip helper-address <ip>`: Configure IP address of the DHCP server as helper address (DHCP relay agent)
- `(config-if)#ip address dhcp`: Tell the DHCP client to use DHCP to learn its IP address

## SNMPv2c

- `(config)#snmp-server community <password> <permission>`: Configure SNMP community strings
- `(config)#snmp-server host <ip> version 2c <community-string>`: Specify NMS, version and community
- `(config)#snmp-server enable traps`: Configure trap messages

## Logging

- `#show logging`: Show logs on the device
- `(config)#logging console <level>`: Make syslog messages displayed in CLI when connected to device via console port
- `(config)#logging monitor <level>`: Make syslog messages displayed in CLI when connected to device via Telnet/SSH
  - `#terminal monitor`: Required on remost host everytime to display the logging
- `(config)#logging buffered [size] <level>`: Make syslog messages to be saved to RAM
- `(config)#logging host <server-ip>`: Make device to send syslog messages to an external server
- `(config)#logging trap <level>`: Set level for external logging

## SSH

- `#show version`: Check IOS image and see if it has K9 in name
- `#show ip ssh`: Show details about SSH configuration
- `(config)#line vty 0 15`: Configure VTY lines
- `(config-line)#transport input <protocol>`: Allow certain protocols
- `(config-line)#access-class <number>`: Apply ACL to VTY
- `(config)#crypto key generate rsa`: Generate RSA keys
- `(config)#ip ssh version 2`: Enable SSHv2
- `(config-line)#login local`: Enable user authentication

## FTP & TFTP

- `#show file systems`: View the IOS file system
- `#show flash`: View the contents of flash
- `#copy {ftp:/tftp:} flash:`: Copy the file to flash using FTP/TFTP
- `(config)#boot system <file-path>`: Use new version of IOS
- `#delete <file-path>`: Delete the file in the path
- `(config)#ip ftp <username/password>`: Configure FTP username/password that device will use when connecting to FTP server

## NAT

- `#show ip nat translations`: Show NAT entries
- `#show ip nat statistics`: Show useful metrics
- `#clear ip nat translation *`: Clear all dynamic NAT entries
- `(config-if)#ip nat {inside|outside}`: Define the interface as inside/outside
- `(config)#ip nat inside source static <inside-local-ip> <inside-global-ip>`: Configure 1-1 static IP mapping
- `(config)#access-list <number> permit <network> <wildcard-mask>`: Define the traffic that should be translated
- `(config)#ip nat pool <pool-name> <start-ip> <end-ip> {prefix-length <length>|netmask <mask>}` to define pool of inside global IPs
- `(config)#ip nat inside source list <acl-number> pool <pool-name>`: Configure dynamic NAT by mapping ACL to the pool
- `(config)#ip nat inside source list <acl-number> interface <interface-id> overload`: Use PAT out of the exit interface

## Security

- `(config)#enable password <password>`: Set password on privilege level but not secure
- `(config)#service password-encryption`: Encrypt all current and future passwords in config
- `(config)#enable secret <password>`: Set more secure password and it takes precedence over `enable password`

### Console Port Security

- `(config)#line console 0`: Enter console line config mode
- `(config-line)#password <password>`: Configure console line's password
- `(config-line)#login`: Require a user to enter configured password to access the CLI via console port
- `(config-line)#login <user-name>`: Require a user to login using one of the configured usernames on the device
- `(config-line)#exec-timeout <time>`: Log the user out after defined time of inactivity

### Port Security

- `#show port-security`: Show useful overview of port securities defined in different interfaces
- `#show port-security interface <interface-id>`: Show the port security configured on the interface
- `#show mac address-table secure`: View all the secure MAC addresses
- `(config-if)#switchport port-security`: Enable port security on switchport with default settings
- `(config-if)#switchport port-security mac-address <address>`: Manually configure allowed MAc
- `(config-if)#switchport port-security violation {shutdown|restrict|protect}`: Set the violation mode
- `(config-if)#switchport port-security aging time <minutes>`: Configure secure MAC aging
- `(config-if)#switchport port-security aging type {absolute|inactivity}`: Configure aging type
- `(config-if)#switchport port-security aging static`: Configure static MAC aging
- `(config-if)#switchport port-security mac-address sticky [<address>]`: Enable sticky secure MAC learning with optional static MAC address
- `(config)#errdisable recovery cause psecure-violation`: Re-enable the interfaces disabled by port security automatically
- `(config)#errdisable recovery interval <seconds>`: Configure the timer interval

### DHCP Snooping

- `#show ip dhcp snooping binding`: Show DHCP snooping binding table
- `(config)#ip dhcp snooping`: Enable DHCP snooping globally
- `(config)#ip dhcp snooping vlan <vlan-id>`: Enable DHCP snooping for a VLAN
- `(config-if)#ip dhcp snooping trust`: Mark the interface as trusted
- `(config-if)#ip dhcp snooping limit rate <number-per-sec>`: Set rate limiting
- `(config)#errdisable recovery cause dhcp-rate-limit`: Configure auto recovery for rate limiting
- `(config)#no ip dhcp snooping information option`: To turn off, assuming the message was received from a DHCP relay agent

### Dynamic Arp Inspection (DAI)

- `#show ip arp inspection interfaces`: Show all DAI configured on interfaces
- `(config)#ip arp inspection vlan <vlan-id>`: Enable DAI for a specific VLAN
- `(config-if)#ip arp inspection trust`: Mark the interface as trusted
- `(config-if)#ip arp inspection limit rate <messages-count> burst interval <seconds>`: Set rate limit
- `(config)#ip inspection validation {dst-mac|ip|src-mac}`: Enable optional checks
- `(config)#arp access-list <name>`: Enter ARP ACL config mode
- `(config-arp-nacl)#permit ip host <ip> mac host <mac>`: Create an ARP ACL entry
- `(config)#ip arp inspection filter <name> vlan <vlan-id>`: Apply ARP ACL to a VLAN to manually allow IP-MAC mapping not found in DHCP snooping binding table

## VRF

- `#show ip vrf`: See all VRFs configured on a router
- `#show ip route vrf <name>`: View the routing table of the VRF
- `(config)#ip vrf <name>`: Create VRF
- `(config-if)#ip vrf forwarding <vrf-name>`: Assign the interface to VRF

## PC Commands

- `arp -a`: Show ARP table
- `ping <ip-address>`: Ping the address to test reachability
- `tracert <ip-address>`: Show hops made to reach destination
- `ipconfig /all`: Show all IP related information of host
- `ipconfig /release`: Release DHCP leased address
- `ipconfig /renew`: Ask for a new IP address
