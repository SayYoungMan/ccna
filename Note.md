# 1. Network Fundamentals (20%)

## 1.1. Explain the role and function of network components

### 1.1.a. Routers

- `Router` is a device that connects two networks and allows packets to be transmitted and received between them
- Operates at layer 3 (`Network layer`) to filter the network based on IP address
- Don't forward broadcast packets from networks so it breaks up `broadcast domain`
- Determines the best path for data packets from source to destination based on routing table information

### 1.1.b. Layer 2 and Layer 3 switches

- `Switch` is a network device that operates at layer 2 (`Data Link layer`) to perform functionalities such as filtering, flooding and forwarding frames.
- Layer 2 switching is considered hardware-based bridging because it uses specialized hardware called an `application-specific integrated circuit (ASIC)`.
  - MAC table is stored in a `TCAM (Ternary Content-Addressable Memory)`.
  - ASIC feeds the destination MAC address of frame into TCAM, which returns the matching table entry.
  - ASICs can run up to high gigabit speeds with very low latency rates.
- `Layer 3 (Multilayer)` switch is a switch that is capable of both switching and routing (layer 3 aware).
  - Can assign IP addresses to its interfaces
  - Can create virtual interfaces for each VLAN and assign IP addresses to those interface
  - Can configure routes on it to be used for inter-VLAN routing
  - Preferred over ROAS in large network because lots of traffic in one interface can cause congestion

### 1.1.c. Next-generation firewalls and IPS

- `Firewall` is a combination of hardware and software that monitors and controls network traffic based on configured rules.
  - `Network firewalls` are physical hardware firewalls and `host-based firewalls` are software firewalls.
- `Next-generation firewalls` include more modern and advanced filtering capabilities.
  - It provides full packet reassembly and deep-packet inspection up to and through layer 7.
  - It permits `application visibility and control (AVC)` as well as offer `intrusion prevention system (IPS)` policies, which monitor a network for malicious and takes action to prevent it.

### 1.1.d. Access points

- A `wireless access point (WAP)` is a networking device that allows wireless-capable devices to connect to a wired network.

### 1.1.e. Controllers (Cisco DNA Center and WLC)

- `WLAN Controller` is responsible for centrally managing multiple wireless network access points.
- In split-MAC architecture, there are 4 main WLC deployment models:

  - `Unified`: WLC is hardware appliance in a central location of the network.
  - `Cloud-based`: WLC is a VM running on a server, typically in a private cloud in a data center
  - `Embedded`: WLC is embedded within a switch
  - `Cisco Mobility Express`: WLC is embedded within an AP

- `Cisco DNA (Digital Network Architecture) Center` is the SDN controller in `SD-Access` which is Cisco's SDN solution for automating campus LANs.
  - It is an application installed on Cisco UCS server hardware
  - It has REST API that can be used to interact with DNA center.
  - It enables `Intent-Based Networking (IBN)` where engineer defines the intent of network behaviour and DNA Center will take care of the details of the configurations.

### 1.1.f. Endpoints

- `Endpoints` are the two ends of a connection for transmitting data. One end is the receiver and the other is the sender.

### 1.1.g. Servers

- `Server` is a device that provides functions or services for clients.
- `Client` is a device that accesses a service made available by a server.
- The same device can both be a client and a server.

### 1.1.h. PoE

- `Power over Ethernet (PoE)` is a protocol that allows power to be sent over unused wires in an Ethernet cable to provide power to devices.
- PoE has a process to determine if a connected device needs power and how much power it needs.

## 1.2. Describe characteristics of network topology architectures

### 1.2.a. Two-tier

- Consists of two layers: access layer and distribution layer
  - `Access Layer` is the one end hosts connect to. It is where QoS marking, security services, etc. are performed.
  - `Distribution Layer` aggregates connections from the access layer switches and it connects to services such as Internet, WAN, etc.
- Also called a `collapsed-core design` because it omits a core layer in 3-tier design
- More economical than 3-tier while being very functional in a campus environment, where the network may not grow larger over time.

### 1.2.b. Three-tier

- This architecture contains additional core layer on top of two-tier architecture design.
- `Core Layer` connects distribution layers together in large LAN.
  - Speed is important at this layer, thus CPU-intensive operation should be avoided.
  - High reliability is a key as failure in this layer can affect all users in the network.

### 1.2.c. Spine-leaf

- `Spine-leaf` architecture is an architecture used commonly in data centers.
- Every leaf switches are connected to every spine switches and every spine switches are connected to every leaf switches
- Path taken by traffic is randomly chosen to balance the traffic load among the spine switches.
- Each server is separated by same number of hops, providing consistent latency.
- This helps data center to deal with large amount of east-west traffic in distributed virtual servers.

### 1.2.d. WAN

- `WAN (Wide Area Network)` is used to connect geographically separate LANs. It uses the services of ISPs. It uses serial connections of various types to provide access to bandwidth over large geographic areas.

#### WAN Terminologies

- `Customer Premises Equipment (CPE)` is equipment that's owned by the subscriber and located on the subscriber's premises.
- `CSU/DSU (Channel ServiceUnit/Data Service Unit)` is a device that's used to connect a DTE to a digital circuit like T1/T3 line.
  - A device is considered DTE if it's either a source or destination for digital data.
- `Demarcation point` is the precise spot where the service provider's responsibility ends and CPE begins.
- `Local loop` connects the demarc to the closest central office.
- `Central office (CO)` connects the customer's network to the provider's switching network.
- `Toll network` is a trunk line inside a WAN provider's network.
- `Optical fiber converters` is used to convert optical signals into electrical signals and vice versa.

#### WAN Connection Bandwidth

| **Name** | **Description**                                        | **Bandwidth** |
| -------- | ------------------------------------------------------ | ------------- |
| DS0      | The basic digital signaling rate                       | 64 Kbps       |
| T1 (DS1) | 24 DS0 bundled together                                | 1.544 Mbps    |
| E1       | European equivalent of T1 with 30 DS0 bundled together | 2.048 Mbps    |
| T3 (DS3) | 28 DS1 bundled together                                | 44.736 Mbps   |
| OC-3     | 3 DS3 bundled together                                 | 155.52 Mbps   |
| OC-12    | 4 OC-3 bundled together                                | 622.08 Mbps   |
| OC-48    | 4 OC-12 bundled together                               | 2488.32 Mbps  |

### 1.2.e. Small office/home office (SOHO)

- `Small Office/Home Office (SOHO)` refers to the office of a small company or a small home office with few devices.
- All networking functions are typically provided by a single device, often called `wireless router`.

### 1.2.f. On-premise and Cloud

- `On-premise` infrastructure has following characteristics:
  - All servers, network devices, and other infrastructure are located on company property
  - All equipment is purchased and owned by the company using it
  - Company is responsible for necessary space, power and cooling
- `Cloud computing` is a model for enabling ubiquitous, convenient, on-demand network access to a shared pool of configurable computing resources and that can be rapidly provisioned and released with minimal management effort or service provider interaction.

#### Five Essential Characteristics of Cloud Computing

1. `On-demand self-service`: customer is able to use the service freely without direct communication to the service provider
2. `Broad network access`: service is available through standard network connections, and can be accessed through many kinds of devices
3. `Resource pooling`: When a customer requests a service, the resources are allowed from a shared pool
4. `Rapid Elasticity`: Customers can quickly expand/reduce the services from a pool of resources
5. `Measured Service`: Provider measures the customer's usage of resources and customers can measure their own as well

#### Three Service Models of Cloud

1. `Software as a Service (SaaS)`: Capability provided to consumer is to use provider's applications on a cloud infrastructure
2. `Platform as a Service (PaaS)`: Capability provided to consumer is to deploy onto the cloud infra, consumer-created applications
3. `Infrastructure as a Service (IaaS)`: Capability provided to consumer is to provision a fundamental computing resources where the consumer is able to deploy and run arbitrary software.

#### Four deployment models of cloud

1. `Private Cloud`: exclusive use by a single organization comprising multiple consumers
2. `Community Cloud`: exclusive use by specific community of consumers from orgs with shared concerns
3. `Public Cloud`: provisioned for open use by the general public
4. `Hybrid Cloud`: composition of two or more distinct cloud infra that remain unique entities but bound together by a technology that enables data and application portability

#### Benefits of Cloud Computing

- Cost: CapEx of buying hardware and software and reduced or eliminated
- Global scale: services can be offered to customers from a geographic location close to them
- Speed / Agility: services are provided on demand quickly
- Productivity: Remove the need for many time-consuming tasks
- Reliability: Easy to back up in the cloud

## 1.3. Compare physical interface and cabling types

### 1.3.a. Single-mode fiber, multimode fiber, copper

- `UTP (Unshielded Twisted Pair) Cables` are copper wire cables under Ethernet standards.
  - `RJ-45` is the connector used at the ends of a copper Ethernet cable.
- `Fiber optic cables` send data by sending light over glass fibers.
  - `SFP (Small Form-Factor Pluggable) transceiver` is used for fiber optic cables.
  - It consists of 4 layers: `fiber glass core`, where light is transmitted, `cladding`, which reflects the light, `protective buffer` and `outer jacket`.

#### UTP vs Fiber Optic

- UTP is cheaper than fiber optic
- UTP covers shorter distance than fiber optic
- UTP is vulnerable to EMI but fiber optic is not
- UTP emits a faint signal outside the wire, which can be a security risk

#### Multimode vs single-mode

- `Single-mode` has a tighter cladding so it only allows one mode of light down the fiber whereas `multimode` is looser and allows multiple light to travel down the glass.
  - Single-mode allows longer cable than multimode.
  - Multimode is cheaper than single-mode because LED based SFP is cheaper than laser based SFP.

### 1.3.b. Connections (Ethernet shared media and point-to-point)

- `Point-to-point` connection/network is formed when exactly two computers are connected to each other with access to full channel bandwidth. It provides security and privacy because communication channel is not shared.
- `Ethernet` is a collection of network protocols and standards.
- `Ethernet standard` defines configuration of cables and speeds to be used for communication

| **Speed** | **Common Name**  | **IEEE Standard** | **Informal Name** | **Max Cable Length** |
| :-------: | :--------------: | :---------------: | :---------------: | :------------------: |
|  10 Mbps  |     Ethernet     |      802.3i       |     10 BASE-T     |         100m         |
| 100 Mbps  |  Fast Ethernet   |      802.3u       |    100 BASE-T     |         100m         |
|  1 Gbps   | Gigabit Ethernet |      802.3ab      |    1000 BASE-T    |         100m         |
|  10 Gbps  | 10 Gig Ethernet  |      802.3an      |    10G BASE-T     |         100m         |

| **Speed** | **IEEE Standard** | **Informal Name** | **Cable Type** | **Max Cable Length** |
| :-------: | :---------------: | :---------------: | :------------: | :------------------: |
|  1 Gbps   |      802.3z       |   1000 BASE-LX    | Multi / Single | 500m (MM) / 5km (SM) |
|  10 Gbps  |      802.3ae      |    10G BASE-SR    |     Multi      |         400m         |
|  10 Gbps  |      802.3ae      |    10G BASE-LR    |     Single     |         10km         |
|  10 Gbps  |      802.3ae      |    10G BASE-ER    |     Single     |         30km         |

#### Ethernet Cabling

- In `Straight-through cable`, pins are connected to the same number pin. It's used to connect host/router to switch or hub.
- `Crossover-cable` has reversed pin connections so they are used to connect devices of same pin settings, such as router to host or switch to switch.
- Modern networking devices have `Auto MDI-X` that allows devices to detect which pins their neighbour is transmitting and adjust which pins they use to transmit and receive data so cable type doesn't matter.
- `Rollover cable` is used to connect to the console port of a network device.
