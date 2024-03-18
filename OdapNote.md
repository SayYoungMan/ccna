# Odap Note

## Jeremy's IT Lab Community Quiz

#### SW1 G0/0 is a trunk that allows VLANs 10 and 30. What is the effect of 'switchport trunk allowed vlan 20'?

```
a. G0/0 allows VLANs 10, 20, and 30
b. G0/0 allows only VLAN 20
c. G0/0 allows VLANs 10 and 30
```

<details>
  <summary>Answer</summary>

<b>b. G0/0 allows only VLAN 20</b>

'switchport trunk allowed vlan X' is used to specify the VLAN (or list of VLANs) that should be allowed on the trunk. It will overwrite the currently allowed VLAN(s). 'switchport trunk allowed vlan 20' will overwrite the current list (10, 30) to allow only VLAN 20. To add a VLAN to the current list of allowed VLANs, make sure to use the 'add' keyword: 'switchport trunk allowed vlan add 20'.

</details>

#### You issue the 'ntp server 192.168.1.1' command on R1, and R1 syncs to that NTP server. Which of the following statements is most correct?

```
a. R1 is a peer of the server
b. R1 is an NTP client
c. R1 is an NTP client and server
d. R1 is an NTP master
```

<details>
  <summary>Answer</summary>

<b>c. R1 is an NTP client and server</b>

The 'ntp server' command makes the router a client of the specified server - it will sync its time to that server. However, it also makes the router itself an NTP server - R1 can now provide the time for other NTP clients. Although the other answer 'R1 is an NTP client' is correct, this answer is better because it includes more correct information.

</details>

#### R1 learns the following routes via different routing protocols. Which route will it insert into its routing table?

```
a. 10.0.0.0/24 via EIGRP, metric 1234
b. 10.0.0.0/24 via OSPF, metric 5
c. 10.0.0.0/24 via RIP, metric 4
```

<details>
  <summary>Answer</summary>

<b>a. 10.0.0.0/24 via EIGRP, metric 1234</b>

Because all three routes are to the same destination (same network address/prefix length), R1 has to decide which to insert into its routing table. It compares their AD (administrative distance) values first: EIGRP's AD (90) is lower than OSPF's (110) and RIP's (120), so R1 selects the EIGRP route. The metric values are irrelevant in this case.

</details>

#### Which of the following protocols uses a reliable Transport Layer protocol?

```
a. DHCP
b. TFTP
c. SNMP
d. Telnet
```

<details>
  <summary>Answer</summary>

<b>d. Telnet</b>

Telnet uses TCP as its Transport Layer (Layer 4) protocol. TCP provides reliable delivery of messages, for example by confirming that each message is received by the destination host. Telnet-enabled devices listen for incoming connections on TCP port 23. The other protocols - DHCP, TFTP, and SNMP - use UDP, which does not provide reliable delivery. UDP does not confirm if messages were received by the destination host.

</details>

#### What is the minimum VTP version that supports extended range VLANs?

```
a. VTPv1
b. VTPv2
c. VTPv3
d. All versions support extended range VLANs
```

<details>
  <summary>Answer</summary>

<b>c. VTPv3</b>

VTPv1 and VTPv2 support only standard range VLANs (1-1005). To use extended range VLANs (1006-4094), you must enable VTPv3 with the 'vtp version 3' command.

</details>

#### When OSPF selects a RID, it considers physical and loopback interface IP addresses, and manual RID configuration. In which order does it consider them?

```
a. Manual > highest loopback intf IP > highest physical intf IP
b. Manual > highest physical intf IP > highest loopback intf IP
c. Manual > lowest physical intf IP > lowest loopback intf IP
d. Manual > lowest loopback intf IP > lowest physical intf IP
```

<details>
  <summary>Answer</summary>

<b>a. Manual > highest loopback intf IP > highest physical intf IP</b>

1\) If the OSPF RID (Router ID) is manually configured, OSPF will select that RID. 2) If there is no manually configured RID, OSPF will select the highest IP address on a loopback interface (in the up/up state) as the RID. 3) If there is no loopback interface in an up/up state with an IP address, OSPF will select the highest IP address on a physical interface (in the up/up state) as the RID. 4) If none of the previous options work, the OSPF process will fail to start.

</details>

#### With DHCP Snooping enabled, which DORA messages are always discarded when received on Untrusted ports?

```
a. REQUEST, ACK
b. DISCOVER, OFFER
c. DISCOVER, REQUEST
d. OFFER, ACK
```

<details>
  <summary>Answer</summary>

<b>d. OFFER, ACK</b>

OFFER and ACK are messages from DHCP servers. DHCP Snooping always discards DHCP server messages when received on Untrusted ports. If a DHCP server is connected to a port, you should configure it as a Trusted port. DISCOVER and REQUEST are messages from DHCP clients. DHCP Snooping does not always discard them, but instead inspects the messages to determine if they should be forwarded or discarded.

</details>

#### Which command is used to control logging to a Syslog server?

```
a. logging trap
b. logging monitor
c. logging console
d. logging server
```

<details>
  <summary>Answer</summary>

<b>a. logging trap</b>

The 'logging trap' command can be used to control logging to a Syslog server - to enable/disable it, or to specify the severity level of messages that should be sent to the server. 'logging console' = logging to the console line, 'logging monitor' = logging to the VTY lines, 'logging buffered' = logging to the logging buffer (in the local device's RAM).

</details>

## CCNA Certification Study Guide: Exam 200-301

### 1. Network Fundamentals

#### 6. Which component acts as a distribution switch for the physical data center?

- The `End of Row (EoR)` switch acts as a distribution switch for `Top of Rack (ToR)` switches which sit at the top of the rack and create an access method for all the equipment in the rack.
- `Core switch` is a term used for aggregation and core switching functions of all distribution switches.
- `Virtual switch` is a term used for switching inside of a hypervisor, in which software switching occurs.

#### 7. Which advantage(s) are gained using switches?

- Switches allow for low latency because frames are forwarded with ASIC hardware-based switching and have low cost.

#### 13. Given the information in the following exhibit, which statement is true when Computer A needs to communicate with Computer F?

- The router does not perform forward/filter decisions, so the frame will not be flooded further on Router A.

#### 14. When firewalls are placed in a network, which zone contains Internet-facing services?

- `DMZ (Demilitarized Zone)` is where Internet-facing servers are placed.
- `Outside zone` is where the public Internet connection is connected and is least trusted.
- The `enterprise network zone` is considered the `inside zone`, which is highly trusted.

#### 16. Which is a false statement about firewalls?

- Firewalls are not commonly deployed to protect from internal attacks but from external attacks or attacks emanating from the outside or directed towards the Internet.
- Firwalls can control application traffic by port number and higher-layer attributes.

#### 18. What is the reason firewalls are considered stateful?

- Firewalls keep track of the TCP conversation before and after the three-way handshake
- This is done so that an attack on TCP/UDP flow is not executed and also DoS attacks, such as SYN flood, can be thwarted.

#### 19. You have an Adaptive Security Appliance (ASA) and two separate Internet connections via different providers. How could you apply the same policies to both connections?

- ASAs allow for zones to be created and the conntections applied to the zones.
- This methodology allows for security rules to be applied uniformly to the outside zone.

#### 21. Which type of device will detect but not prevent unauthorized access?

- An `IDS (Intrusion Detection System)` will detect unauthorized access but will not prevent it.
- An `IPS (Intrusion Protection System)` will detect the presence of an intrusion and alert an administrator.
- `Honey pot` will attract a malicious user so that their tactics can be observed.

#### 24. Which component allows wireless clients to roam between access points and maintain authentication?

- `Wireless LAN Controller (WLC)` is responsible for centralized authentication of users and/or computers on a wireless network.
- When a wireless device is roaming, the WLC is responsible for maintaining the authentication between access points.

#### 25. Why would you use Multiprotocol Label Switching (MPLS) as a connectivity option?

- Requirement for multiple protocols is a reason to use MPLS.
- The protocols moving accross MPLS nodes are irrelevant to the technology.
- This is because layer 3 information is not examined to route packets.

#### 28. Which allows for seamless wireless roaming between access points?

- WLC keeps track of which LWAP a client has associated with and centrally forwards the packets to the LWAP that's appropriate for a client to access while roaming

#### 30. Which should only be performed at the core layer?

- Only switching between distribution switches should be performed at the core layer
- Nothing should be done to slow down forwarding traffic, such as using ACLs, supporting clients, or routing between VLANs.
- Routing of data should be performed at the distribution layer of Cisco 3-tier model.

#### 36. Which topology does the collapsed core layer switch use in a two-tier design model?

- The collapsed core layer switch uses a star topology connecting outward to the access layer switches.

#### 42. Core layer switches in the three-tier design model perform which task?

- Core layer switches connect campuses together via the distribution layer switches.
- Distribution layer switches connect to access layer switches and core switches to provide redundancy.
- Access layer switches connect to users and are edge network devices.
- Both distribution layer and corelayer can connect the Internet to the network.

#### 47. Which technology provides for a hub-and-spoke design?

- The `E-Tree services` of Metro Ethernet allow for a root to be established to serve the remote sites or leaf endpoints.
- The root can communicate to the leaves and the leaf endpoints cannot communicate with each other.
- `Wireless WAN` provides connectivity by using a star topology
- `E-Line` and `E-LAN` services provide services in a `point-to-point` or `point-to-multipoint` topology.

#### 49. Which WAN connectivity technology is always configured in a hub-and-spoke topology?

- The Cisco `Dynamic Multipoint Virtual Private Network (DMVPN)` is always configured in a hub-and-spoke topology.
- The central router creates a multiport GRE connection between all of the branch routers.
- `IPsec` uses a point-to-point topology for connectivity.
- `MPLS` and `Metro Ethernet` use a point-to-point or point-to-multipoint topology for connectivity.

#### 50. Which sub-protocol inside of the PPP suite is responsible for authentication?

- The `Link Control Protocol (LCP)` provides the authentication phase of a PPP connection.
- The `Network Control Protocol (NCP)` allows for multiple upper-layer protocols to be used with PPP.

#### 52. Which authentication method used with PPP uses a nonce (random number) to hash the password and prevent replay attacks?

- `The Challenge Handshake Authentication Protocol (CHAP)` works by sending a random number called the challenge.
- `Password Authentication Protocol (PAP)` transmits the username and password in clear text.
- `Lightweight Directory Access Protocol (LDAP)` is a protocol used to look up data.

#### 53. Which sub-protocol inside of the PPP suite facilitates multilink connections?

- `Link Control Protocol (LCP)` provides the facility for multilink connections.

#### 54. Which is a benefit of using MLPPP?

- `MultiLink PPP (MLPPP)` simplifies layer 3 configuration by bundling the connections together at layer 2.
- It provides a pseudo interface representing the individual interface where all layer 3 configuration is applied.

#### 57. In the following exhibit, what does the line LCP closed mean?

- The LDP closed line states that the LCP process has not completed due to reasons like conflicting options or authentication failure.
- If the serial line was disconnected, the interface would show as down with a line protocol of down

#### 58. You have obtained an ADSL circuit at a remote office for central office connectivity. What will you need to configure on the remote office router?

- `Asymmetrical Digital Subscriber Line (ADSL)` connectivity typically uses PPPoE to authenticate subscribers.
- The sbuscriber's credentials are often relayed to a RADIUS server for subscription checks.
- PPP does not need to be configured for use over an ADSL connection, but the authentication portion of PPPoE must be configured.

#### 61. Which is not a NIST criterion for cloud computing?

- The 5 NIST criteria for cloud computing are `on-demand serlf-service`, `broad network access`, `resource pooling`, `rapid elasticity` and `measured service`.

#### 63. What is the role of a cloud services catalog?

- A `cloud services catalog` satisfies the self-service aspect of cloud computing.
- It does this by listing all available VMs that can be created in the cloud environment.

#### 67. Which option is not a consideration when converting to an email SaaS application if the majority of users are internal? (Choose two.)

- `External bandwidth` rather than internal should be considered since internal users will access the application through the Internet.
- Location of users should also be a deciding factor in moving to an SaaS.

#### 71. Which fiber optic standard utilizes a 50 micron core?

- `Multi-mode` fiber can be either 50 or 62.5 microns at its core.
- `Single-mode` fiber-optic cable is around 7 microns thick.

#### 72. Which type of cable would be used to connect a computer to a switch for management of the switch?

- Management via the console port requires a `rolled cable` and an EIA/TIA 232 adapter.

#### 81. In the following exhibit, what can you conclude about the interface or node?

- The most probable cause is that there is a duplex mismatch since there are a large number of late collisions.

#### 85. A router is connected to the switch via a Fast Ethernet interface. Intermittently you experience an outage. What should be done first to remedy the problem? Refer to the following exhibit.

- It is recommended to set all servers statically for speed and duplex.
- If a network interface flaps, auto-negotiation of speed and duplex will be performed again, which could create a service outage.

#### 86. In the following exhibit, what can you conclude about the interface or node?

- The txload and rxload counters are high, which depicts that the interface is not fast enough for the data being transferred. Therefore, is is recommended to upgrade the node's NIC.

#### 88. You have auto-negotiation turned off on the node, but it is turned on at the switch’s interface connecting the node. The interface is a 10/100/1000 Mb/s interface and the node is 100 Mb/s full-duplex. What will the outcome be when you plug in the node?

- Cisco switches can auto-detect speed and only if it can't detect the speed, it will fall back to 10 Mb/s.
- If the speed is 10Mb/s or 100Mb/s, the duplex will be half-duplex with auto-negotiation turned off.

#### 122. You plug a laptop into a network jack. When you examine the IP address, you see 169.254.23.43. What can you conclude?

- Any address in the range of `169.254.0.0/16` is a `link-local address`.
- It means that the computer has sensed that a network connection is present but no DHCP is present.
- The network only allos local communications and no routing.

#### 125. Which protocol allows multicast switches to join computers to the multicast group?

- `IGMP (Internet Group Messaging Protocol)` allows switches to join computers to the multicast group table.
- This allows the selective process of snooping to occur when a transmission is sent.

#### 137. You need to verify connectivity to the IPv6 address fc00:0000:0000:0000:0000:0000: 0000:0004. Which command would you use?

- The command to ping an IPv6 address is `ping ipv6`

#### 149. Which command would configure a single anycast address on a router’s interface?

- The command to configure an anycast address on an interface would be `Router(config-if)#ipv6 address 2001:db8:1:1:1::12/128 anycast`
- /128 defines a single IP address to advertise in routing tables.

#### 167. Which wireless frequency spectrum is shared with Bluetooth?

- The 2.4 GHz frequency spectrum is where Bluetooth operates, and the frequency is also shared with 802.11.
- 900 MHz is used by `Zigbee`, which is an IoT communication technology.

#### 170. Which option describes a VM best?

- A VM is an OS that is running on hardware but is not directly attached to the hardware.
- Hypervisor creates an abstraction layer between the hardware and the OS.

#### 172. Which component connects the VM NIC to the physical network?

- A `virtual switch` connects the virtual machine NIC to the physical network.
- `vNIC` is the virtualized network card presented to the virtual machine.

#### 173. Which of the following is a virtual network function (VNF) device?

- A `virtual firewall` or `virtual router` is an example of VNF.
- These devices perform basic network functionality and run as virtual machines or virtual instances.
- Virtual switch is not considered a VNF because it's an elemental part of the hypervisor.

#### 174. You need to scale out some web servers to accommodate load. Which method would you use?

- If you want to scale a web server out to several other webservers, you would use `Server Load Balancing as a Server (SLBaaS)` from your cloud provider.
- Adding resources like `vCPUs` and `vRAM` is scaling a server up, not out.

#### 175. Which is a correct statement about MAC addresses?

- When the `Individual/Group (I/G)` bit is set to 1, the frame is a boardcast or multicast transmission.

#### 178. Which is a consequence of not using loop avoidance with layer 2 switching?

- When loop avoidance such as STP is not employed and loops exist, you will get `duplicate unicast frames` and `broadcast storms`
- This will inevitable thrash the MAC address table and degrade bandwidth.

#### 179. Which switching method checks the CRC as the frame is received by the switch?

- `Store-and-forward` receives the frame, calculates the CRC and makes a forwarding decision.
- `Cut-through` mode allows the switch to make a forward/filter decision immediately after destination MAC is received.
- `Frag-free` mode inspects the first 64 bytes of an incoming frame, before forward/filter decision is made.
- `Fast switching` is when a caching table is created for MAC so switching can be made faster.

#### 184. In the following exhibit, what will happen if the computers on ports Fa0/2 (Computer A) and Fa0/3 (Computer B) are swapped?

- Computer A's frames will be forwarded to its new port since the entries will be cleared out when the cables are disconnected and relearned.

#### 188. You need to change the default MAC address aging time on a switch to 400 seconds. Which command would you use?

- MAC address aging time can be configured via `#mac-address-table aging-time <seconds>`

#### 197. Which statement is true of an ARP request entering into a switch?

- The destination MAC address for broadcasts is all fs and source MAC address of the frame will be the specific MAC address of the host.
