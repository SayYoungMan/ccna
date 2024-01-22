# Note

## 1. Network Devices

- A `computer network` is a digital telecommunications network which allows nodes to share resources.

### Devices in Network

#### Client & Server

- A `client` is a device that accesses a service made available by a server.
- A `server` is a device that provides functions or services for clients.
- Same device can both be a client and a server.

#### Switches / Routers

- Number of network interfaces / ports
  - Switch: Many
  - Router: Few
- Connectivity
  - Switch: to hosts within the same LAN and no connectivity between LAN or over the internet
  - Router: between LANs and used to send data over the Internet

#### Firewalls

- monitor and control network traffic based on configured rules
- can be placed inside or outside network

- `Next-generation firewalls` include more modern and advanced filtering capabilities.
- `Network firewalls` are hardware devices that filter traffic between networks.
- `Host-based firewalls` are software applications that filter traffic entering and exiting a host machine.

## 2. Interfaces and Cables

### Ethernet

- `Ethernet` is a collection of network protocols / standards.
- We need standards like Ethernet so that they have an agreed language that machines can talk to each other.
- `Ethernet standard` is defined in the IEEE 802.3 standarad in 1983.
  - IEEE is Institute of Electrical and Electronics Engineers.

| **Speed** | **Common Name**  | **IEEE Standard** | **Informal Name** | **Max Cable Length** |
| :-------: | :--------------: | :---------------: | :---------------: | :------------------: |
|  10 Mbps  |     Ethernet     |      802.3i       |     10 BASE-T     |         100m         |
| 100 Mbps  |  Fast Ethernet   |      802.3u       |    100 BASE-T     |         100m         |
|  1 Gbps   | Gigabit Ethernet |      802.3ab      |    1000 BASE-T    |         100m         |
|  10 Gbps  | 10 Gig Ethernet  |      802.3an      |    10G BASE-T     |         100m         |

- BASE refers to baseband signaling and T stands for twisted pair
- 100m is the maximum for twisted pair cables.

### UTP Cable

- `UTP (Unshielded Twisted Pair) cables` are copper wire cables under Ethernet standards.
  - No metallic shield so it's vulnerable to electrical interference.
  - But twisted pairs protect against EMI (Electrical Magnetic Interference)
- `RJ-45` is the connector used at the ends of a copper Ethernet cable.

  - Has 8 pins but 10, 100 BASE-T only use 2 pairs (4 pins) and other two use all.
  - Use pin 1 and 2 to transmit data (Tx) and 3 and 6 to receive data (Rx).
    - It's the opposite for switches.
    - Pair of pins to allow `full-duplex transmission`, meaning that both devices can send and receive data at the same time and experience no collision.
  - In 1000 BASE-T and 10G BASE-T, the pairs are bidirectional so each pair isn't dedicated specifically for transmitting or receiving.

- In `Straight-through cable`, pins are connected to the same number pin.
- `Crossover-cable` has reversed pin connections.
- Modern networking devices have a feature called `Auto MDI-X` that allows devices to automatically detect which pins their neighbour is transmitting and adjust which pins they use to transmit and recieve data.

### Fiber-Optic Connections

- `SFP (Small Form-Factor Pluggable) transceiver` is used for fiber optic cables.
- Fiber optic cables send data by sending light over glass fibers.
- There are two connectors at each end; one for transmitting and one for receiving.
- Inside of fiber-optic cable, it consists of 4 layers:
  1. Fiber glass cores: light transmitted here
  2. Cladding: reflects light
  3. Protective buffer: protects fiber glass from breaking
  4. Outer jacket

#### Multi-mode vs. Single-mode

- Multi has wider core than single.
- Multi allows multiple angles of light wave but single only allows one angle.
- Multi allows longer cable than UTP but shorter than single.
- Multi is cheaper than single due to LED based SFP and single is expensive due to laser based SFP.

#### Standards

| **Speed** | **IEEE Standard** | **Informal Name** | **Cable Type** | **Max Cable Length** |
| :-------: | :---------------: | :---------------: | :------------: | :------------------: |
|  1 Gbps   |      802.3z       |   1000 BASE-LX    | Multi / Single | 500m (MM) / 5km (SM) |
|  10 Gbps  |      802.3ae      |    10G BASE-SR    |     Multi      |         400m         |
|  10 Gbps  |      802.3ae      |    10G BASE-LR    |     Single     |         10km         |
|  10 Gbps  |      802.3ae      |    10G BASE-ER    |     Single     |         30km         |

### UTP vs Fiber Optic

- UTP is cheaper than fiber optic.
- UTP covers shorter distance than fiber optic.
- UTP is vulnerable to EMI but fiber optic is not.
- RJ45 is cheaper than SFP.
- UTP emits a faint signal outside which can be security risk.

## 3. OSI Model & TCP/IP Suite

- `Networking models` categorize and provide a structure for networking protocols and standards.
- `Protocols` are a set of rules defining how network devices and software should work.

### OSI (Open Systems Interconnection) Model

- A conceptual model that categorizes and standardizes the different functions in a network.
- Created by International Organization for Standardization (ISO).
- 7 Layers work together to make the network work.
  1. Physical
  2. Data Link
  3. Network
  4. Transport
  5. Session
  6. Presentation
  7. Application
- When sending data to another, the data is first processed through the OSI stack, each layer adding something to original (`encapsulation`).
- Then, at the physical layer, it's sent to another as electrical signal and it strips off the layers up the OSI stack. (`de-encapsulation`)
- Both encapsulation and de-encapsulation are examples of `adjacent-layer interaction`.
- `Same-layer interaction` is when the same layer of two systems interact.

#### Application Layer

- Layer that interacts with software applications like browser.
- HTTP and HTTPS are examples of layer 7 protocols.
- Functions:
  - Identifying communication partners
  - Synchronizing communication

#### Presentation Layer

- Translates between application and network formats.
- One example is encryption and decryption of data.
- Also it translates between different application layer formats.

#### Session Layer

- Controls dialogues (`sessions`) between communicating hosts.
- Establishes, manages and terminates connections between the local application and the remote application.

#### Transport Layer

- Segments and re-assembles data for communications between end hosts.
- Provide `host-to-host` communication.
- Layer 4 header is added at this layer and the PDU is called `segment`.

#### Network Layer

- Provides connectivity between end hosts on different networks outside LAN.
- Provides logical addressing like IP addresses.
- Provides path selection between the source and the destination.
- Routers operate at this layer.
- Layer 3 header is added with information like source and destination IP address.
- The PDU is called a `packet`.

#### Data Link Layer

- Provides `node-to-node` connectivity and data transfer.
- Defines how data is formatted for transmission over physical medium.
- Detects and corrects physical layer errors.
- Switches operate at this layer.
- Layer 2 header and trailer is added.
- The PDU is called `frame`.

#### Physical Layer

- Defines physical characteristics of the medium used to transfer data between devices, i.e. voltage levels, maximum transmission distance, cable specification, etc.
- Digital bits are converted into eletrical (for wired transmission) or radio (for wireless transmission) signals.
- PDU is called `bit`.

### TCP/IP Suite

- Conceptual model and set of communications protocols used in Internet and other networks.
- Developed by the United States Department of Defence.
- Smilar structure to OSI model but has fewer layers.
- It's in use in modern networks but OSI model still influences how network engineers think and talk about networks.

1. Link - Equivalent to data link and physical layers of OSI
2. Internet - Eqivalent to Network layer
3. Transport - Same as OSI
4. Application - All upper layers in OSI

## 4. Intro to the CLI

### Connecting to the Device

- In order to configure a device, you have to connect to the console port, which has RJ45 and USB ports.
- `Rollover cable` is used for connection, that has RJ45 and DB9 ends.
- They have 8 pins as well but they connect in different pairs of 1-8. 2-7, 3-6, 4-5.

### User EXEC mode

- This is the mode set by default, when you first enter the CLI.
- `Name>` indicates that you are in user EXEC mode.
- Users can look at things, but can't make any changes.

### Previleged EXEC mode

- By entering `enable`, user can enter previleged EXEC mode
- `Name#` indicates that you are in previleged EXEC mdoe.
- Provides complete access to view the device's configuration, restart the device, etc.
- Cannot change config itself but can save config file, etc.

### Global Configuration mode

- Enter `configure terminal` to enter global configuration mode from previleged EXEC mode.
- `Name(config)#` indicates this mode.

- You can set password by `enable password` command.
  - It uses Cisco's default 7 hash algorithm which is not too secure.
  - `service password-encryption` encrypts passwords in config.
- `enable secret` is more secure as it uses MD5 hash and it takes precedence over password

### CLI Commands

- You can type `?` to view available commands (e.g. `e?` shows all commands that start with e).
  - The commands that are all capital from suggestions of `?` indicate a variable.
  - `<cr>` indicates that there are no available commands.
- Tab will auto-complete what you are typing but you don't necessary have to type the whole thing because CLI can infer the command.
- `exit` command to exit configuration or previleged mode.
- Typing `no` in front of command will undo the command.
- `do` command executes command in previleged EXEC level from global configuration mode.

### Configuration files

- `Running-config`: current, active configuration file on the device.
- `Startup-config`: the config file that will be loaded upon restart.
- `write`, `write memory` or `copy running-config startup-config` will all write the running-config to startup-config.

## 5. Ethernet LAN Switching (1/2)

### Ethernet Frame

- Header consists of 5 parts: preamble, SFD, destination, source and type / length.
- Trailer only has FCS.
- Total of 26 bytes.

#### Preamble

- 7 bytes of alternating 1s and 0s (10101010 \* 7)
- Allows devices to synchronize receiver clocks.

#### SFD (Start Frame Delimiter)

- 1 byte of 10101011
- Marks the end of preamble and beginning of rest of the frame.

#### Destination & Source

- Indicates the devices sending and receiving the frame.
- Consist of 6 byte `MAC address` of the physical device.

#### Type / Length

- 2 byte field
- A value of 1500 or less indicates length of encapsulated packet.
- Value of 1536 or greater indicates type of the encapsulated packet.
  - IPv4 = 0x0800
  - IPv6 = 0x86DD

#### FCS

- 4 bytes
- Detects corrupted data by running `CRC (Cyclic Redundancy Check)` algorithm over the received data.

### MAC (Media Access Control) Address

- 6-byte physical address assigned to the device when it is made
- also known as `burned-in address` and is globally unique
- First 3 bytes are `OUI (Organizationally Unique Identifier)`, which is assigned to company making the device.
- Last 3 bytes are unique to the device itself.

### Finding out MAC Address

- Switch has a `MAC address table`, which saves mapping of interface to source MAC address when it receives data.
  - When MAC address is saved this way it's called `dynamic / dynamically learned MAC address`.
  - MAC addresses are removed after 5 minutes of inactivity (`aging`).
- When switch encounters a MAC address destination not saved in the table, it floods the frame, which is sending the frame to all interfaces except the source.
  - It's called `unknown unicast frame` when the MAC address is not in the table.
  - `Unicast frame` is a frame destined for a single target.
- If the received end doesn't have a matching MAC address, it simply drops the packet, but if it does, it processes it normally.

## 6. Ethernet LAN Switching (2/2)

### Minimum size of Ethernet Frame

- Minimum size of Ethernet frame is 64 bytes, meaning that minimum payload size is 46 bytes (if don't count preamble and SFD as the header).
- If payload is less than 46 byes, padding bytes of all 0s are added.

### ARP (Address Resolution Protocol)

- Used to discover MAC address of a known IP address.
- Consists of two messages:
  1. `ARP request`: broadcast that is sent to all hosts, it has `FFFF.FFFF.FFFF` destination MAC address which is broadcast MAC.
  2. `ARP reply`: unicast sent only to the host
- PC stores ARPs in `ARP table`.
  - `arp -a` command to view ARP table
  - Static type is default entry in ARP table and dynamic type is the ones learned via ARP.

### Ping

- A network utility that is used to test reachability
- Measures round-trip time
- Uses two messages like ARP:
  1. `ICMP Echo Request`: sent to specific host not broadcast
  2. `ICMP Echo Reply`
- Command: `ping <ip-address>`

### Cisco Commands

- To see ARP table: `show arp`
- To view MAC address table: `show mac address-table`
- To remove MAC addresses from table: `clear mac address-table dynamic`
  - Target specific address: `clear mac address-table dynamic address <mac-address>`
  - Target specific interface: `clear mac address-table dynamic interface <interface-id>`

## 7. IPv4 Addressing (1/2)

### IPv4 Addresses

- Consists of 4 groups of 8 bits number (0 - 255)
- Written in dotted decimal for easier human understanding.
- `/24` means that first 24 bits represent the network and rest is end host.
- First end host eddress (host portion is all 0s) is the `network address` so can't be assigned.
- Last end host eddress (host portion is all 1s) is the `broadcast address` so can't be assigned.

### IPv4 Classes

| **Class** | **First Octet** | **First Octet Range** |
| :-------: | :-------------: | :-------------------: |
|     A     |    0XXXXXXX     |        0 - 127        |
|     B     |    10XXXXXX     |       128 - 191       |
|     C     |    110XXXXX     |       192 - 223       |
|     D     |    1110XXXX     |       224 - 239       |
|     E     |    1111XXXX     |       240 - 255       |

- Class D is reserved for `multicast addresses`.
- Class E is reserved for `experimental use`.

### Loopback addresses

- Has range between 127.0.0.0 - 127.255.255.255
- Used to test network stack on local device. If device sends traffic to this address, it's simply processed back up TCP/IP stack as if it were traffic received from another device.

### Netmask

| **Class** | **Prefix Length** |  **Netmask**  |
| :-------: | :---------------: | :-----------: |
|     A     |        /8         |   255.0.0.0   |
|     B     |        /16        |  255.255.0.0  |
|     C     |        /24        | 255.255.255.0 |

- `Netmask` is older way of telling which part is the network.

## 8. IPv4 Addressing (2/2)

### Network number calculation

- Maximum number of hosts per network is `2^n - 2` where n is the number of host bits.
- First usable address is the address 1 bit after network address.
- Last usable address is the address 1 bit before the broadcast address.

### `show ip interface brief`

- Gives status of each interface as well as IP addresses.
- `Interface` column lists network interfaces.
- `IP address` column shows the IP address but it will be `unassigned` if not configured.
- `OK?` column is legacy feature to tell if IP address is valid.
- `Method` column indicates the method by which the interface was assigned with IP address.
- `Status` column is layer 1 status of interface.
  - `connected` means it's up
  - `administratively down` means disabled with `shutdown` command; this is default status of router but not for the switches
- `Protocol` column is the layer 2 status. Can be up or down.

### Setting up IP address

- Can enter `configuration interface` mode by typing `interface <id>`.
- `name(config-if)#` at the beginning of the line indicates this mode.
- Setting up IP address can be done by `ip address <address> <subnet mask>`.
- `no shutdown` command is required afterwards to enable the interface.

### Other commands

- `show interfaces <interface-id>` shows extensive information mainly about layer 1 and 2 about the interface.
- `show interfaces description` shows similar information to `show interfaces brief` but has description column that can be manually set about the interface.
- `description <string>` command sets description of interface in `config-if` mode.

## 9. Switch Interfaces

- Switches have way more interfaces especially RJ45 ports than routers because it's where the end hosts are connected to.

### `show ip interface brief`

- Switch interfaces don't have the shutdown command defined so they will be up / up state by default.
- down state is different from administratively down because it means it's not connected.

### `show interfaces status`

- `Port` field lists interfaces.
- `Name` field is description of the interface.
- `Status` field will show connected / not connected.
- `VLAN` field will show the VLAN which can be used to divide LANs into smaller ones.
- `Duplex` field will show duplex status.
  - It's auto by default meaning it will negotiate with the neighbouring device and use full if possible.
  - `a-` means it's chosen automatically.
- `Speed` field shows the speed of the transmission and it's also `auto` by default.
  - It will negotiate with the device and use the fastest speed possible.
- `Type` field are all RJ45 interfaces for copper UTP cables but if they were SFP, you would see here too.

### Configuring speed and duple

- First enter `config-if` mode by entering `interfaces <id>`.
- `speed <speed>` command can set the speed.
- `duplex <mode>` command can set the duplex mode.
- `description <string>` command can set the name field.

### `interface range <range>`

- This command can enter `config-if-range` mode where my changes apply to all interfaces in this range.
- `f0/5 - 12` can apply my changes to all between 5 and 12.
- It doesn't have to be consecutive, e.g. `f0/5 - 6, f0/9 - 12`.

### Full / Half Duplex

- `Half duplex`: The device can't send and receive data at the same time. If it is receiving a frame, it must wait before sending a frame.
- `Full duplex`: The device can send and receive data at the same time. It doesn't have to wait.

### LAN Hubs

- Before switches were used, hubs were used in the old days.
- The hubs are simple repeaters that flood any frame they receive and they operate at layer 1.
- The problem with it is that when it receives frames at the same time, it will try to send them at the same time resulting in collision.
- `CSMA/CD` (Carrier Sense Multiple Access with Collision Detection) is a mechanism used to prevent this.
  - Before sending frames, devices listen to the collision domain until they detect that other devices are not sending.
  - If a collision does occur, the device sends a jamming signal to inform other devices that collision happened.
  - Each device will wait a random period of time before sending frames again.
- Devices connected together via Hub is said to belong to the same `collision domain`.
  - Switches don't try to send the message at the same time so the connected hosts are in separate collision domains.
  - This makes full-duplex possible so switch is used in these days.

### Speed / Duplex Autonegotiation

- Interfaces that can run at different speeds have default settings of speed auto and duplex auto.
- Interfaces advertise their capabilities to the neighbouring device, and they negotiate the best speed and duplex settings they are both capable of.
- If autonegotiation is disabled:
  - The switch will try to sense the speed other device is operating at.
    - If failed to sense, it will use the slowest speed.
  - If speed is 10 or 100 Mbps, it will use half duplex.
  - If speed is 1000 Mbps or higher, it will use full duplex.
- If PC operates at full jduplex but switch operate at half duplex or vise versa, duplex mismatch happens and collisions will occur.

### Interface Errors

- The following errors can be viewed via `show interfaces <interface-id>` command.
- `Runts`: frames that are smaller than the minimum frame size (64 bytes).
- `Giants`: frames that are larger than the maximum frame size (1518 bytes).
- `CRC`: frames that failed the CRC check.
- `Frame`: frames that have incorrect format due to error.
- `Input errors`: total number of various counters, such as the above four.
- `Output errors`: frames that the switch tried to send, but failed due to error.

## 10. IPv4 Header

### Version

- 4 bits
- Identifies the version of IP used
- IPv4 = 0100, IPv6 = 0110

### Internet Header Length (IHL)

- 4 bits
- The options field is variable in length so it's necessary to indicate the total length of the header.
- Identifies the length of header in 4-byte increments.
- Minimum value is 5 (=20 bytes) with no options field.
- Maximum value is 15 (=60 bytes).

### DSCP (Differentiated Services Code Point)

- 6 bits
- Used for QoS (Quality of Service)
- Used to prioritize delay-sensitive data (streaming video, voice, etc.)

### ECN (Explicit Congestion Notification)

- 2 bits
- Provides end-to-end notification of network congestion without droppping packets.
- Optional feature that requires both endpoints and underlying network infrastructure to support it.

### Total Length

- 16 bits
- Indicates the total length of the packaet (L3 header + L4 segment) measured in bytes
- Minimum value is 20
- Maximum value is 65535

### Identification

- 16 bits
- If packet is fragmented, it is used to identify which packet the fragment belongs to.
- All fragments of same packet will have same value in this field.
- Packets are fragmented if larger than `MTU (Maximum Transmission Unit)`, which is usually 1500 bytes. (Same as maximum size of Ethernet frame).
- Fragments are reassembled by the receiving host.

### Flags

- 3 bits
- Bit 0: reserved, always 0
- Bit 1: `Don't fragment (DF) bit`, used to indicate a packet that should not be fragmented
- Bit 2: `More fragments (MF) bit`, set to 1 if there are more fragments in the packet, set to 0 for the last fragment.

### Fragment Offset

- 13 bits
- Used to indicate the position of the fragment within the original unfragmented IP packet.
- Allows fragmented packets to be reassembled even if the fragments arrive out of order.

### Time to Live

- 8 bits
- Router will drop a packet with a TTL of 0.
- Used to prevent infinite loops.
- Originally designed to indicate the packet's maximum lifetime in seconds.
- In practice, it indicates `hop count`, each time the packet arrives at a router, the router decreases TTL by 1.
- Recommended default is 64.

### Protocol

- 8 bits
- Indicates the protocol of the encapsulated L4PDU.
- TCP = 6, UDP = 17, ICMP = 1, OSPF(dynamic routing protocol) = 89

### Header Checksum

- 16 bits
- Used to check for errors in IPv4 header
- When router receives packet, it calculates the checksum of header and compares with it.
- If they do not match, router drops the packet.

### Source / Destination IP Address

- 32 bits
- Contains IPv4 address of sender and receiver of the packet

### Options

- 0 - 320 bits
- Rarely used

## 11.1. Routing Fundamentals

### What is routing?

- `Routing` is a process that routers use to determine the path that IP packets should take over a network to reach their destination.
  - Routers store routes to all of known destinations in a `routing table`.
- 2 routing methods (methods that routers use to learn routes):
  - `Dynamic routing`: routers use dynamic routing protocols to share routing information with each other automatically and build their routing tables.
  - `Static routing`: Admins manually configure routes on the router.
- A route basically tells the router: to send packet to X, send it to next hop Y.
  - If destination is directly connected to router, send it to the destination.
  - If destination is router's own IP, receive the packet.

> `WAN (Wide Area Network)` is a network that extends over a large geographical area.

### `show ip route`

- `show ip route` in previleged mode of router shows the routing table.
- Codes legend lists different protocols which routers can use to learn routes.
- When you configure IP address and enable it with `no shutdown`, connected and local routes will automatically be added.

### Connected and Local Routes

- `Connected Route (C)` is a route to the network the interface is connected to.
  - It provides route to all hosts in that network.
- `Local Route (L)` is a route to the exact IP address configured on the interface.
  - /32 netmask is used to specify the exact IP address of the interface.
  - /32 means all 32 bits are fixed, so they can't change.

### Route Selection

- When there are more than one route that matches the destination IP address, it will choose the most specific matching route.
  - Most specific matching route = matching route with longest prefix length
- You will see in `show ip route`, `192.168.1.0/24 is variably subnetted 2 subnets, 2 masks`
  - This means that there are two routes to subnets that fit within the network with two different netmasks.

> Unlike switches, if router doesn't have the route in the routing table it will just drop the packet instead of flooding.

## 11.2. Static Routing

### Default Gateway

- End hosts can send packets directly to destinations in connected network.
- But to send packets outside local network, they must send to default gateway.
- Also called default route.
- The packet sent to another network will have detination IP address of host in another network but MAC address of default gateway. which can be learned via ARP request.

### Static Route Configuration

- Each router in the path need both routes of source and destination network, to ensure `two-way reachability` (can send packets both ways).
- From global config mode type `ip route <ip-address> <netmask> <next-hop>` to configure the static routes.
- Configuration can be tested via ping command and if successful, it means there is two-way reachability.
- You can configure static route with exit-interface instead of next-hop as well
  - This tells which interface it should send the packet out of.
  - Both exit-interface and next-hop can be configured (recommended).
  - Static routes with only exit-interface rely on a feature called `Proxy ARP`.

### Default Route

- If the router doesn't have any more specific routes that match a packet's destination IP address, the router will forward the packet using default route.
- It's set as a route to 0.0.0.0/0
  - It is least specific route possible because it includes all IP addresses.
- Often used to direct traffic to Internet.
- When not set, routing table will display `gateway of last resort is not set`.
- Setting default route is done by `ip route 0.0.0.0 0.0.0.0 <next-hop>`

## 12. Life of a Packet

> Each interface in device has a unique MAC address

- When PC is sending a packet to another network, it first sends it to router but when it doesn't know the MAC address of the router, it sends ARP request to find out.
- When router receives a packet it de-encapsulates and encapsulates with header of new destination MAC address.
- At each stage, if the device doesn't know the MAC address of next hop, it must send ARP first.

## 13. Subnetting (Part 1)

### IPv4 Address Classes

- The IANA (Internet Assigned Numbers Authority) awssigns IPv4 addresses to companies based on size.
  - Large company receive a class A network and small for class C.
- But this led to many wasted IP addresses
- A direct, dedicated connection between two routers is called `point-to-point network`, but it only uses two hosts so it's wasted.

### CIDR (Classless Inter-Domain Routing)

- The requirements of class networks were removed and it can be any prefix length.
- This allowed larger networks to be split into smaller networks, allowing greater efficiency.
- These smaller networks are called `subnets`.
- It is possible to use /31 subnet for point-to-point network because there is no need for network or broadcast address.
- /number notation is called `CIDR notation`.

## 14. Subnetting (Part 2)

### Subnetting Tricks

- By adding the least bit of network portion of the octet repeatedly, we can find the network addresses of each subnet.
- `2^x = number of subnets` where x = number of borrowed bits.
- When given the number of subnets to make, find the least number of borrowed bits whose number of subnets is more than required.
- Finding network address of host, based on its IP address can be done by converting all host bits to 0.
  - Similarly, broadcast address can be found by converting all host bits to 1.

## 15. Subnetting (Part 3)

### VLSM (Variable-Length Subnet Masks)

- All subnetting in part 1 and 2 were `FLSM (Fixed-Length Subnet Masks)` meaning that all the subnets use the same prefix length.
- VLSM, on the other hand, is the process of creating subnets of different sizes, to make use of network addresses more efficiently.

### VLSM - Steps

1. Assign the largest subnet at the start of address space.
2. Assign the second largest subnet after.
3. Repeat the process until all subnets have been assigned.

> For CCNA test, use /30 prefix length instead of /31, for point-to-point network connection.
