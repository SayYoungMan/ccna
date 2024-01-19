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
