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
