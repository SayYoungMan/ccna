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
