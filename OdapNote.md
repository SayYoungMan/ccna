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

### 2. Network Access

#### 1. You are trying to reprovision a switch in a different part of your network. However, you still see the old VLANs configured from the old network. How can you rectify the problem?

- `vlan.dat` is the database for VLANs configured on a switch either manually or through VTP.
- It is persistent even if `config.text` (start-up config) is deleted, thus you must manually delete it.

#### 2. What is the normal range for VLANs before you must use extended VLAN IDs?

- The normal usable VLAN range for Cisco is 1-1001

#### 5. What is the extended VLAN range?

- The extended VLAN range is VLAN 1006-4094

#### 9. Static VLANs are being used on a switch’s interface. Which of the following statements is correct?

- `Static VLANs` are VLANs that have been manually configured.
- `Dynamic VLANs` are configured via a `VLAN Membership Policy Server (VMPS)`
- A node will not know which VLAN it is assigned to when it is statically set via the command `switchport access vlan`

#### 10. A switch is configured with a single VLAN of 12 for all interfaces. All nodes auto- negotiate at 100 Mb/s full-duplex. What is true if you add an additional VLAN to the switch?

- The addition of another VLAN will increase the effective bandwidth by adding additional broadcast domains.

#### 13. You have changed the name of VLAN 3, and you now want to check your change. Which command will you enter to verify the name change?

- To verify a VLAN name change, you would use the command `#show vlan id 3`

#### 17. You are installing a VoIP phone on the same interface as an existing computer. Which command will allow the VoIP phone to switch traffic onto its respective VLAN?

- `(config-if)#switchport voic vlan 4` will configure the interface to switch traffic with a CoS value of 5 to the voic VLAN of 4.

#### 18. Which type of port removes the VLAN ID from the frame before it egresses the interface?

- All VLAN tagging is removed from the frame before it egresses an access port to the end device.

#### 25. Why is it recommended that you do not use VLAN 1?

- A computer can be plugged into an interface defaulted to VLAN 1 and expose resources such as switch management network.

#### 28. What is the command to verify a VLAN and the port(s) it is associated with?

- The command to verify that a VLAN is created and the port it is associated with is `#show vlan`.

#### 29. You are configuring a Catalyst 9200 switch, a VLAN is not configured yet, and you mistakenly configure it on an interface with the command switch access vlan 12. What will happen?

- When the command is invoked inside of the interface, it will create the VLAN automatically.
- Traffic will forward without the need of any other configuration.

#### 32. You need to verify that an interface is in the proper VLAN. Which command will display the status of the interface, the VLAN configured, and the operational mode?

- The command `#show interfaces switchport` will display a detail of all ports in respect to VLAN operational status.
- The command will show the operational mode of the interface.

#### 35. The guest VLAN is not allowing traffic to be routed. What is the cause of the problem?

- `act/lshut` in status column of VLAN database suggests that the VLAN is disabled from forwarding traffic.

#### 39. You have just configured the network in the following exhibit. The commands you have entered configured the VLAN database and assigned the VLAN IDs to the interfaces. You cannot communicate between VLAN 2 and VLAN 4, but communication within VLAN 4 works. What is wrong?

- The broadcast domain / VLAN requires its own unique IP network addressing and a router to route between the networks.
- Therefore, you need a router for inter-VLAN communications.

#### 42. You have connected a Dell switch to the Cisco switch you are configuring and you cannot get a trunk between the two. What must be changed?

- Since Dell switch cannot support ISL, both switches need to be set up to use 802.1Q.
- VTP is a Cisco proprietary protocol

#### 43. You need to view all of the trunks on a switch and verify that they have the proper trunking protocols configured. Which command will display the information?

- `#show interfaces trunk` will display all of the configured trunks on the switch.

#### 44. What is the default VTP mode all switches are configured as by default?

- All switches are configured by default as a `VTP server`.

#### 45. You need to verify the VTP mode on a switch. Which command will display the information?

- The command to display the mode settings for VTP is `#show vtp status`

#### 48. You have a list of allowed VLANs over an existing trunk. You need to set the allowed list back to default. Which command will perform this without interruption? Refer to the following exhibit.

- `(config-if)#switchport trunk allowed vlan all` will restore the allowed VLAN list back to default

#### 49. You need to add VLAN 4 to the allowed list on a trunk interface. Currently VLANs 5 through 8 are allowed. Which command will add only this VLAN without interruption to the network?

- `(config-if)#switchport trunk allowed vlan add 4` will add VLAN 4 to the existing list of VLANs allowed.

#### 51. What is the function of the VTP?

- `VLAN Trunking Protocol (VTP)` propagates the VLAN database from an initial master copy of the server to all the clients.

#### 56. When enabling VTP pruning, where does it need to be configured?

- VTP VLAN pruning removes forwarding traffic for VLANs that are not configured on remote switches.
- This saves bandwidth on trunks because if the remote switch does not have the VLAN configured on it, the frame will not traverse the trunk.
- VTP pruning needs to be configured only on the server because clients will receive the update and turn on VTP pruning automatically.
- If VTP pruning is turned on at the client or transparent, the setting will be ignored.

#### 62. How does IEEE 802.1Q tag frames?

- 802.1Q inserts a field containing the 16-bit `Tag Protocol ID` of `0x8100`, 3-bit CoS field, 1-bit `drop-eligible indicator` and 12-bit `VLAN ID`.
- It is inserted between the source MAC address and the type field.

#### 65. You are setting up a switch. When you perform a show run, you notice that the VLANs are in the running-config. What could be concluded? Refer to the following exhibit.

- When a switch is set up with a mode of transparent, the VLAN information is stored in the running-config in lieu of the `vlan.dat` file.

#### 67. Switch A has default configuration on its interface. You need to configure Switch A for VLAN 5. Which command will configure the interface to become a member of VLAN 5?

- Switch A must change its interface to an access port with `(config-if)#switchport mode access`
- Then, you configure the access VLAN of 5 on switch A with `(config-if)#switchport access vlan 5`

#### 70. Which command is similar to show interfaces trunk but will show greater detail?

- `#show interfaces switchport` will show greater detail about the trunk than the command `#show interfaces trunk`

#### 73. You are trying to configure a trunk port on an interface for 802.1Q encapsulation. However, after entering the proper command, you receive the error % Invalid input detected at '^' marker. What is wrong?

- This error is common when configuring Cisco switches that only support 802.1Q and configuration is not necessary.

#### 77. How many bytes are used in an 802.1Q frame for tagging of VLANs?

- An 802.1Q frame is a modified Ethernet frame.
- The type field is related after the 4 bytes used for 802.1Q tagging.

#### 79. Which command will show you the native VLAN for only Fa0/15?

- `#show interface fastethernet 0/15 switchport` will show the operational mode and if configured as a trunk, it will show the native VLAN.

#### 80. You need to change the native VLAN for interface Fa0/23 from VLAN 1 to VLAN 999. Which command would you use?

- The command to change the native VLAN of a trunk is `(config-if)#switchport trunk native vlan 999`

#### 81. When you change the native VLAN of a trunk from VLAN 1 to VLAN 999 and you receive the error %CDP-4-NATIVE_VLAN_MISMATCH: Native VLAN mismatch -discovered.... What is the possible problem?

- This error is normal if it's the first interface to be changed over to the new native VLAN since the other interfaces has not been changed yet.
- If the other interface was changed already and received this error, CDP is letting you know that the other side is mismatched.

#### 91. Which command gives information that’s identical to the output of the show cdp neighbors detail command?

- `#sh cdp entry *` commandj will give output that's identical to `#show cdp neighbors detail`

#### 95. You want to disable LLDP from sending advertisements on a single interface. Which command will you use?

- When you use `(config-if)#no lldp transmit`, it will suppress LLDP messages from exiting the interface it's configured on.

#### 96. What is the default value of the LLDP holddown timer for entries?

- The default value of LLDP holddown timer for entries is 120 seconds.

#### 101. Which is a true statement about EtherChannel?

- When `EtherChannel` bonds interfaces together, they act as a single Ethernet link. Therefore, layer 2 and 3 see it as a single link.
- Etherchannel can aggregate multiple links but the links must have the same speed.

#### 106. Which mode forces the aggregation of links without the use of a control protocol?

- If you configure the EtherChannel to `on mode`, it forces the aggregation of links without the use of a control protocol.

#### 107. Which is a correct statement about aggregating ports together?

- The term `EtherChannel` is a Cisco-centric term so most vendors will not recognize the term.

#### 109. How often does PAgP send messages to control the status of the links in the bundle?

- `PAgP` sends control notifications every 30 seconds to the adjacent switch.

#### 114. What is the effect of configuring a port channel with one side set to on mode and the other side set to on mode?

- When both sides of the port channel are configured with the on mode, an unconditional port channel is created.
- This means there is no control protocol assisting the port channel.

#### 115. What is the IEEE specification for Spanning Tree Protocol (STP)?

- The IEEE ratified the specification of STP as `802.1D` in 1990.
- `802.1X` is the IEEE standard for port security that requires end devices authenticate before traffic will be allowed to pass.
- `802.1w` is the IEEE standard for RSTP.
- `802.1s` is the IEEE standard for `Multiple Spanning Tree Protocol (MST)`

#### 118. What is the IEEE specification for Rapid Spanning Tree Protocol (RSTP)?

- The original STP specification was revamped in 2004 with RSTP `802.1w`
- This revamping of STP was to fix problems with the original specification to converge faster to network changes.

#### 124. Which statement is correct about RSTP?

- RSTP has three transition modes and therefore converges faster than STP, which is 50 seconds.
- It is, however, backward compatible with STP 802.1D

#### 125. How do switches participating in an STP network become aware of topology changes?

- Each switch is responsible for sensing changes to the topology.
- Whenever the topology changes, a `Topology Change Notification (TCN)` is sent out of all root ports and an acknowledgement is sent back.
- This happens until the root bridge sends back a notification.

#### 129. Which option is a correct statement about alternate ports in RSTP?

- An alternate port is a port that is in a discarding state.
- If the root port fails on the switch with the alternate port, then the alternate port becomes the root port for that switch.

#### 134. Which is a correct statement about bridge port roles in STP?

- Every switch in the entwork must have at least one `root port`.
- This is the port that leads back to the root bridge.
- The root bridge will have a dsignated port on the adjacent link back to the root bridge.

#### 137. How is the bridge ID calculated for PVST+?

- The PVST+ bridge ID comprises:
  - 4-bit `bridge priority` calculated in blocks of 4096
  - 12-bit `sys-ext-id` that is the VLAN ID for the segment
  - 6-byte MAC address for the switch

#### 138. What is the default bridge priority for all STP switches?

- The default bridge priority for STP is 32768

#### 139. Which is a correct statement about bridge port roles in STP?

- The root bridge always has all of its ports in a designated mode or forwarding mode.
- If there are redundant links, the adjacent switch to the designated port on the root bridge must be a non-designated or blocking state.

#### 140. Which is a correct statement about backup ports in RSTP?

- A backup port is a port on the same switch in a discarding state. It receives BPDUs from another port on the same switch.
- If the forwarding port fails, then the backup port will become designated so that connectivity to the segment can be restored.

#### 141. What is the default wait time for STP convergence to complete?

- 802.1D STP convergence takes 50 seconds to complete before the port is put into a state of forwarding or blocking.

#### 147. You receive a call that when computers boot up, they display an error message stating that they cannot reach a domain controller. However, after a few tries, the problem goes away, and the domain controller can be reached. Which command would you enter into the interface if you suspect spanning-tree convergence problems?

- `(config-if)#spanning-tree portfast` will turn on `PortFast` mode which will allow the interface to forward first.

#### 148. On which types of ports should you configure PortFast mode?

- PortFast should only be configured on access links where end devices are plugged in because these devices will not typically create loops in the switch topology.
- If PortFast is configured on a trunk port, you have a high risk of creating a loop if there is a misconfiguration on the switch being introduced.
- Voice ports are usually connected to VoIP phones with built-in switches that can be looped.

#### 149. What will the command spanning-tree portfast default entered in global configuration mode do?

- This command turns on PortFast globally for only access ports on the switch.

#### 152. What is the transition of states when PortFast is configured?

- PortFast mode allows an interface to bypass the blocking state and begin forwarding immediately.
- It then listens and learns of BPDUs on the interface to make a decision to continue to forward frames or enter blocking state.

#### 153. Which command would you use to configure BPDU Guard on an interface?

- `(config-if)#spanning-tree bpduguard enable` is the correct command to configure BPDU guard.

#### 155. Which option is a best practice when configuring links on an access switch?

- Configuring BPDU guard along with PortFast ensures that the end device will always be forwarding.
- BPDU guard ensures that in the event a BPDU is heard on the interface, the interface will enter into an err-disabled mode.

#### 156. Which command will show you if a port has been configured for PortFast mode?

- `#show spanning-tree interface fa 0/1` will show the spanning tree configuration for an interface.

#### 161. You require a density of 100 wireless clients in a relatively small area. Which design would be optimal?

- To achieve density and bandwidth in a relatively small area, you will need to deploy lightweight WAPs with a WLC.
- Althgouth Autonomous WAPs would work, it would be problematic due to frequency coordination and roaming.

#### 162. Which mode will allow a Cisco AP to detect interference of Bluetooth devices?

- Cisco WAPs can be placed into:
  - `Data serving mode`: AP will serve data and act as normal WAP
  - `Monitoring mode`: AP can scan the wireless spectrum and report on interference

#### 163. Which wireless mode allows for a network connection without a wireless infrastructure in place?

- `Independent Basic Service Set (IBSS)`, aka `ad hoc network`, does not require any wireless infrastructure.
- Clients connect directly to each other over the 802.11 wireless spectrum.

#### 166. You have three buildings that are separated by a number of public roads but have a relatively close proximity to each other. You need to network them together to a central point. Which type of wireless technology should you deploy?

- A `point-to-multipoint` wireless bridge will allow you to connect all 3 buildings together, tying them back to a central location.
- `mesh network` is usually designed for endpoints (clients) and not for the interconnection of buiuldings.
- `Point-to-point` bridges would allow all the buildings to connect to each other, but it would not network them together to a central point.

#### 170. You need to cover a large public area with high speed wireless coverage. Many of the areas are too far away from the wired switching equipment. What should you implement?

- A `mesh wireless network` will allow for converage of the large area.
- A mesh network will provide the highest bandwidth possible.

#### 172. You need more bandwidth to your wireless controller from the router. Currently you have one Gigabit Ethernet connection in use and both your router and wireless controller have another available Gigabit Ethernet connection. What can you do to get more bandwidth?

- You can build an EtherChannel between routers and WLC to obtain more bandwidth when using ROAS.

#### 174. You are connecting a Cisco WLC to a non-Cisco switch and need to aggregate two ports between the two devices. Which type of link should you research on the non-Cisco device?

- `Link Aggregation (LAG)` must be used between the WLC and the switch, regardless of the brand.

#### 175. How is traffic load-balanced from a WLC to a switch using LAG?

- When a LAG is created between a switch and WLC, the method of load balancing is `hash-based`, using layer 4 source and destination ports.

#### 176. What is the maximum number of ports you can bundle in a LAG between a WLC and a switch?

- Maximum number of ports that can be bundled in a LAG is 8 ports.

#### 177. You company has been contracted to implement a 802.11 wireless system for a small town. Which type of implementation is this considered?

- When a wireless system spans a town or city, it is considered a `Wireless Metro Area Network (WMAN)`.
- A `Wireless Personal Area Network (WPAN)` is a wireless network designed for personal use, usually for personal connectivity to the Internet through a `hot spot`.
- `Wireless LAN (WLAN)` is used to describe a campus-sized wireless network and not a network that spans a public area.
- `Wireless Wide Area Network (WWAN)` is a term used to describe cellular networks and not typical 802.11 wireless.

#### 178. You currently have a WLC with only two physical access ports. One port is used for guest network access and the other port is used for your business communications. You need to add several other networks to the WLC for your manufacturing and quality control departments. What is the simplest and best way to achieve this?

- Converting one of the current access ports to a trunk will allow several VLANs to be carried across the one port to the switching equipment.

#### 180. You have been asked by your manager to configure a port for a new WAP to be installed for your WLC. How should you configure the port?

- When installing a WAP onto a WLC, the port should be configured as a turnk port so that management traffic and data traffic can be tagged.

#### 183. Which port and protocol does TACACS+ use?

- `TACACS+` uses TCP and port 49 for communications between the switch or router and the AAA server.

#### 187. Which authentication system is an open standard originally proposed by the Internet Engineering Task Force (IETF)?

- `RADIUS` is an open standard originally proposed by the IETF

#### 190. What is the connection speed for console access to Cisco equipment?

- The connection for Cisco equipment should be set up as:
  - 9600 baud
  - 8 bits of data
  - No flow control
  - 1 stop bit

#### 192. Which IEEE specification defines WLAN QoS for wireless data?

- WLAN QoS is defined by IEEE `802.11e`
- `802.1q` is the wired equivalent called AVVID
- `802.11r` specification is used for BSS fast transition
- `802.11k` is used for roaming clients to locate closest WAP

#### 193. You are creating a WLAN in the GUI of the WLC. You need to make sure that only corporate hosts can connect to the newly formed WLAN. How can you achieve this?

- `MAC-based filtering` is the best way to achieve the goal of only allowing corporate hosts to connect to the network.
- Disabling SSID from broadcasting is scurity through obscurity and only a deterrent.
- Setting PSK can be leaked out
- Adding an LDAP server is the first step in setting up the web portal for user auth

#### 194. Which protocol should be enabled on a WLAN to allow a client device to download a list of neighboring WAPs?

- `802.11k` will allow client devices to download a list of neighbouring WAP and their associated wireless bands.

#### 198. Which statement is correct about Flex Connect mode versus Local mode?

- `Local mode` creates a CAPWAP tunnel to the wireless LAN controller to allow switching of VLANs local to the WLC.
- All traffic in Local mode must traverse back to the WLC to get switched into the respective VLANs.
- `Flex Connect mode` does not create a CAPWAP tunnel to mode data, only control information.

#### 199. You need to set up a WLAN for connectivity to send and receive large files to roaming clients. The WLAN will exist with other WLAN traffic. Which QoS profile should the new WLAN be associated with?

- The Bronze QoS profile should be used for bulk data transfer.

#### 200. Which type of security can be implemented on a WLAN that requires the host PC to present a certificate before being allowed onto the wireless network?

- `802.1X` is a protocol that can be configured on WLC to allow only hosts that present a valid certificate on the network.
- The server that arbitrates the authentication is normally RADIUS

### 3. IP Connectivity

#### 2. How are routers managed with interior gateway protocols?

- Routers are grouped in to the same `autonomous system (AS)`.
- When they are within the same AS, they can exchange information such as routes to destination networks and converge their routing tables.

#### 3. What is the maximum hop count for RIP?

- The maximum hop count for RIP is 15.
- Hop count over 15 hops is considered unroutable or unreachable.

#### 5. Which multicast address does RIPv2 use for advertising routes?

- RIPv2: `224.0.0.9`
- OSPF hello messages: `224.0.0.5`
- OSPF hello messages for DRs and BDRs: `224.0.0.6`
- Multicast group for all routers: `224.0.0.2`

#### 7. Which routing protocol will not contain a topology of the network?

- RIP does not contain a topology table
- RIP compiles its table from multiple broadcasts or multicasts in the network from which it learns routes.
- However, it never has a full topological diagram of the network.

#### 8. Which routing loop avoidance method is used by routers to prevent routing updates from exiting an interface in which they have been learned?

- `Split horizon` prevents routing updates from exiting an interface in which they have been learned.
- This stops false information from propagating in the network, which can cause a routing loop.
- `Routing to infinity` is a way of advertising a downed route as unreachable because of the number of hops.
- `Routie poisoning` is similar to routing to infinity as it advertises a downed route as over the routable hop count.
- `Holddowns` can help stabilize a network by holding off changes until a specific amount of time has passed.

#### 11. Which command will allow you to verify routes line by line in a subset of the general route statement?

- `#show ip route 160.45.23.0 255.255.255.0 longer-prefixes` will detail all of the specific routes contained in the route for this network.

#### 32. What role does ICMP take in the routing of a packet?

- ICMP notifies the sending host if there is no viable route to the destination.
- The ICMP message sent to the sending host is a `destination unreachable` message.

#### 39. Which is a correct statement about the subnet mask?

- The subnet mask is used by the host to determine the immediate network and the destination network.
- It then decides to either route the packet or try to deliver the packet itself without the router's help.

#### 44. How does the sending host know if the destination is local or remote with respect to its immediate network?

- The sending host ANDs its subnet mask against the destination IP address, then against its IP address, and this gives a frame of reference for where it needs to go and where it is.
- The host compares the remote IP to its internal routing table after the calculation of local versus remote is performed and the host is ready to route the packet.

#### 45. What is the current method Cisco routers use for packet forwarding?

- The current method of packet forwarding used by Cisco routers is `Cisco Express Forwarding (CEF)`.
- CEF creates several cache tables used for determining the best route for the destination network.

#### 46. What is the process called at layer 2 when a packet hops from router to router and eventually to the host?

- The layer 2 process is called `frame rewrite`.
- When a packet hops from router to router, the destination frame is rewritten for the next destination MAC address.

#### 50. Which command will display the router’s ARP cache?

- The command to display the router's ARP cache is `#show ip arp`

#### 51. What is the default time an entry will live in the ARP cache?

- By default, all entries have a TTL of 240 seconds.
- They will be removed if not used during the 240 seconds.

#### 55. Which routing protocol is a distance-vector routing protocol?

- RIP is a `distance-vector` protocol
- OSPF is a `link-state` protocol
- EIGRP is a hybrid protocol that more closely resembles a link-state protocol
- BGP is a `path-vector` protocol used for Internet routing

#### 57. Which statement accurately describes a routing loop?

- `Routing loop` occurs when packets are routed between two or more routers and never make it to their destination.

#### 64. What is a disadvantage of routing between VLANs on a router’s interface?

- Bandwidth is often a consideration because everything you send to the router must come back on the same port for routing to work.

#### 72. What is an advantage of dynamic routing protocols?

- Optimized route selection is a direct advantage of using dynamic routing protocols.
- Dynamic routing is not easier to configure due to the upfront planning and configuration.

#### 75. What is a characteristic of distance-vector protocols?

- Protocols such as RIP re-advertise routes learned.
- This can be problematic because routes learned through this method are never tracked for status or double-checked for validity.

#### 78. Which dynamic routing protocol uses the Diffusing Update Algorithm as its routing algorithm?

- EIGRP: `The diffusing update algorithm (DUAL)`
- RIP: `Bellman-Ford algorithm`
- OSPF: `Dijkstra algorithm`
- BGP: `best path algorithm`

#### 81. Which is a design concept used to stop routing loops with distance-vector dynamic routing protocols?

- The use of holddown timers allows the convergence of the network routing tables.
- This is used to hold down changes to the routing table before convergence can happen and a routing decision is hastily made by RIP.
- `Counting-to-infinity` is another name for a routing loop

#### 86. Why would you need to use an EGP?

- It is used when you have a `dual-homed connection` between two ISPs.
- You would need to know the fastest path to the destination network via the Internet connection

#### 92. Which command would allow you to see the next hop information for CEF?

- The command `#show ip cef` will display all of the network prefixes and the next hope that CEF has in the `Forwarding Information Base (FIB)`.

#### 105. You type into the router ip default-gateway 192.168.11.2. Why will traffic not route out the default gateway?

- `ip default-gateway` allows the management plane of the router to egress the network the router is configured upon through a different gateway.

#### 107. When you configure an IP address on a router interface, what happens to the routing table?

- The router will create a summary route for network as well as a route for host.
- Both of these changes to the routing table will trigger an update on dynamic routing protocol.

#### 110. What is a benefit of static routing?

- `Static routing` is suited for small networks, where the central admin has a good understanding of the network layout.
- It does reduce router-to-router communications because the overhead of routing dynamic protocols will not use up bandwidth.

#### 111. Where are static routes stored?

- When you configure a static route, it is temporarily stored in the running config.
- After it is saved by using `copy running-config startup-config`, it is stored in the startup configuration and can survive reboots.

#### 121. What is the purpose of issuing the command no switchport on a layer 3 switch?

- The command `no switchport` turns the port into a `routed interface` in which an IP address can be configured.

#### 125. Which command would configure the interface on the ROAS configuration as the native VLAN?

- The command `(config-subif)#encapsulation dot1q 2` will associate the subinterface with VLAN 2.
- If you specify `native` tag after the command, it will make this sub interface the native VLAN for the trunk.

#### 126. Which commands would you use to configure an IP address on an SVI?

- You must enter the interface of the VLAN by `(config)#interface vlan 10`
- Once in the pseudo interface, you enter the `(config-if)#ip address` command and then enter `no shutdown`.

#### 130. Which command must be entered on 2960-XR switches to enable IP routing?

- On 2960-XR switches, you must enable the `Switching Database Manager (SDM)` for LAN base routing to enable routing.
- This is done by `(config)#sdm prefer lanbase-routing`.
- The switch is then required to reload before you can configure routable SVIs.

#### 135. Which command will allow you to examine a switch’s port to see if it is routed or switched?

- `#show interface gi 0/2 switchport` will show the state of a port.

#### 137. You have just configured a new VLAN and have configured the SVI with an IP address and no shutdown command on the interface. However, when you perform a show ip route, it does not show a valid directly connected route for the SVI. What is the problem?

- After configuring a VLAN and the respective SVI interface, a route will not show until at least one port is configured with the new VLAN and it is in an up status.

#### 139. Before configuring ROAS, which command should be entered in the interface connecting to the switch?

- When configuring ROAS on a router's interface, you should always issue `no ip address` command
- No IPs can be configured on the main interface and all IPs are configured on the subinterfaces.

#### 140. You have configured a ROAS and set up the switch to connect to the router. However, you cannot route between VLANs. Which command would you use on the switch to verify operations?

- Verifying the proper operation of the switch would start with verifying that the port is correctly set as a trunk to the router.
- `#show interface trunk` command will verify this

#### 147. Which type of routing technique allows for route summarization to be computed automatically by routers?

- Most dynamic routing protocols will summarize routes.
- They do this for efficiency so the least number of route statements will need to exist in the routing table.

#### 160. Why don’t link-state protocols suffer from routing loops as distance-vector protocols do?

- Link-state protocols require all routers to maintain their own topology database of the network which is why routing loops are less likely to occur.

#### 170. How do Cisco routers determine their router ID (RID)?

- Statically set RID is chosen first, then highest loopback interface IP address and then highest IP address on an active interface is chosen.

#### 172. Which statement is correct about adjacency with OSPF on a broadcast network (LAN)?

- Adjacencies are formed between the DR and the neighbors on the same area.
- This is done to ensure that all neighbor routers have the same LSDB.

#### 173. How is a DR elected for OSPF?

- The designated router is elected by the highest priority in the same area.
- If the priorities are all the same, then highest RID becomes the tiebreaker.
- OSPF will elect a DR for each broadcast network to minimize the number of adjacencies formed.

#### 174. In which database can you see all of the routers discovered in the OSPF network in which hello packets were sent and acknowledged?

- The `neighborship database` is where all the routers can be found that have responded to hello packets.
- It contains all of routers by RID and each router participating in OSPF manages its own neighborship database.

#### 178. What does the command router ospf 20 configure?

- `router ospf 20` configures a process ID of 20.
- This process identifies the databases for an OSPF process as well as its configuration.

#### 179. Which command will verify the bandwidth of an interface participating in OSPF?

- `#show interface` will display the reported bandwidth or configured bandwidth of an interface

#### 180. Which command will tune the cost of the OSPF metrics for integration with non-Cisco routers to participate in OSPF?

- When you are configuring Cisco routers to participate in OSPF with non-Cisco routers, each interface on the Cisco router needs to be configured.
- The `(config-if)#ip ospf cost` command can be tuned between 1 to 65535 and will need to be matched with the other vendor.

#### 182. What is the default number of equal-cost routes for OSPF on Cisco routers?

- By default, Cisco routes will load-balance 4 equal-cost routes with OSPF

#### 184. Which command will allow changing the number of equal-cost routes for OSPF?

- The command `(config-router)#maximum-paths 10` will configure a maxmimum of 10 routes of equal cost for load balancing.

#### 185. What is the maximum number of equal-cost routes that can be configured for OSPF on Cisco routers?

- The maximum number of equal-cost routes that can be configured for load balancing with OSPF on a Cisco router is 32.

#### 189. What is the default OSPF hello interval in which hello packets are sent out on a broadcast (multi-access) network?

- The default hello interval is 10 seconds for a broadcast (multi-access) network such as LAN

#### 194. After changing the router’s RID for OSPF, which command needs to be entered?

- After the OSPF configuration is changed, OSPF needs to be restarted.
- This is achieved by `#clear ip ospf`

#### 195. Which statement about OSPF area border routers is correct?

- Type 3 LSAs contain summary information about the networks on the other side of ABR.
- ABRs listen to Type 1 and 2 LSAs but do not exchange link state advertisement messages.

#### 210. Which command will display the DR for a LAN?

- The command `#show ip ospf interface` will display the interface details of each interface for OSPF.

#### 211. In the following exhibit, Router A will not form an adjacency with Router B. What is the problem?

- In order to form adjacency, the area IDs must match and hello/dead timers should match.

#### 216. Which is a correct statement about support for OSPF on an MPLS network?

- Both the customer edge (CE) routers and the provider edge (PE) routers can host erea0.
- However, the service provider must support area 0, called the `super backbone`, on its PE routers since all areas must be connected to area 0.

#### 218. You have changed the router’s priority for OSPF to make the router the DR, but the router has not become a DR. What must be done to force the election?

- When configuring OSPF for DR, if you configure another router with higher priority, the original DR will remain the current DR.
- OSPF does not allow for preemption, and therefore you must force the election by clearing the OSPF process on the DR by `#clear ip ospf process x`

#### 225. What is the default priority of HSRP?

- The default priority of HSRP is 100.

#### 226. What is the maximum number of HSRPv1 groups that can be created?

- You can create up to 256 HSRP groups on a router.

#### 227. Which port and protocol are used by HSRP for communications?

- HSRP routers communicate with each other on port 1985 using UDP.

#### 230. When a host sends an outgoing packet to an HSRP group, which router provides the destination address for the default gateway?

- The virtual router is responsible for host communications such as an ARP request for the host's default gateway.
- It is the virtual router's IP address and MAC address that are used for outgoing packets.

#### 231. Which timer must expire for a standby router in an HSRP group to become the active router?

- The `hold timer` must expire for the standby router to become an active router.
- The hold timer is 3 times the hello timer, so 3 hello packets must be missed before the standby becomes active.

#### 232. Which port and protocol are used by Gateway Load Balancing Protocol (GLBP) for communications?

- GLBP use the port number 3222 and the UDP protocol for router communications.

#### 233. Which is a difference between HSRPv1 and HSRPv2?

- HSRPv2 allows for timers to be configured in milliseconds in lieu of seconds.

#### 235. Which router is elected to become the GLBP active virtual gateway?

- The router with the highest priority will become the AVG.
- However, if all routers have the same priority, then the router with the highest IP address becomes the tiebreaker.

#### 238. What is the maximum number of HSRPv2 groups that can be created?

- You can create up to 4096 HSRP groups on a router with HSRPv2.

#### 240. What is the definition of preemption for HSRP?

- `Preemption` allows for the election process to happen for a newly added HSRP router.

#### 245. Which command will configure VRRP on an interface with an IP address of 10.1.2.3?

- `(config-if)#vrrp 1 ip 10.1.2.3` will configure the interface with VRRP with a virtual IP address of 10.1.2.3

#### 246. Refer to the following exhibit. You are running HSRP on Router A and Router B. You intermittently have ISP outages. What command should you configure to alert HSRP to the outage?

- The command `(config-if)#standby 1 track serial 0/0/1` tells the HSRP group of 1 to track the status of interface serial 0/0/1.

#### 247. Which command will allow you to see real-time diagnostics of HSRP?

- `#debug standby` will allow you to see real-time information from HSRP on the router on which you have entered the command.

#### 249. Which command will allow you to set the hello and hold timers for HSRPv2 to a hello of 200 milliseconds and a hold of 700 milliseconds?

- `(config-if)#standby 1 timers msec 200 msec 700` will set the HSRP group of 1 with hello timer of 200 milliseconds and hold timer of 700 milliseconds.

### 4. IP Services

#### 8. In the following exhibit, the enterprise owns the address block of 179.43.44.0/28. Which command will create a NAT pool for Dynamic NAT?

- `(config)#ip nat pool EntPool 179.23.44.2 179.43.44.15 netmask 255.255.255.0` will configure the pool called with the range of IP addresses in 179.43.44.0/28.
- The /24 is used in lieu of /28 because the serial interface is a /24 so all the IP addresses in that network are /24.

#### 15. Which command will allow you to see if the router or switch is using NTP?

- The command `#show clock detail` will display either `no time source` or `time source is NTP` if the router or switch is configured to slave off a server for time.

#### 16. Which command will allow you to view the time details from a configured server?

- `#show ntp associations detail` will show you to view the NTP clock details from the master NTP server.

#### 18. Which command will help you diagnose if the router or switch is getting an answer back from an NTP server?

- `#debug ntp packets` will allow you to verify packets received from an NTP server.

#### 24. Which command will set the router’s internal clock to 2:24 August 1, 2019?

- `#clock set 2:24:00 1 august 2019` will set the clock correctly

#### 26. Which record type is used for an IPv4 address mapping to FQDN for DNS queries?

- `PTR (Pointer record)` is used to look up IP addresses and return FQDNs that are mapped to them.

#### 33. At what point of the lease time will the client ask for a renewal of the IP address from the DHCP server?

- DHCP clients request a renewal of the lease halfway through the lease time of the IP address.

#### 34. Which statement is correct about the DHCP process?

- After the initial Discover, Offer, Request and Acknowledge, it is the client's responsibility to maintain the lease of the IP address. This includes release and renewal.
- DHCP server is not responsible for maintaining the life cycle of an IP address.

#### 47. Which command will allow you to verify the network management station that is configured to receive trap notifications?

- `#show snmp host` will display the host that is configured to receive notifications of trap or inform massages.

#### 48. When you configure SNMPv3 for a restricted OID, what is the first step?

- When you begin to configure SNMPv3 for a restricted OID, the first step is configuring a view.
- The view allows or restricts what the user will have access to.

#### 50. Which command will configure the severity level of syslog events that will be sent to the syslog server for debugging?

- The command `(config)#logging trap debugging` will configure syslog events to be sent to the syslog server for the severity levels of debugging (7) through emergency (0).

#### 52. Which command will send logging with time stamps rather than sequence numbers?

- `(config)#service timestamps log datetime` will configure syslog messages to be logged with the date and time rather than arbitrary sequence number.

#### 58. Which command will direct logging to the internal log space?

- `(config)#logging buffered` will direct buffering of log messages to RAM.

#### 60. What is the default level for syslog facility logging?

- The default syslog facility level is debugging (7).
- All debugging messages are logged to the internal buffer by default.

#### 61. Which command will allow you to verify the active DHCP server that has assigned an IP address to the router?

- `#show dhcp lease` will help you verify the IP address configured on the router, the DHCP server that served the lease and the lease time in seconds.

#### 64. Which DHCP field helps a DHCP server decide which scope to serve to the DHCP relay agent?

- `GIADDR` field is filled out by the DHCP relay agent before the DHCP packet is sent to the DHCP server.
- This field helps the DHCP server decide which scope to send an Offer message back for.
- `CIADDR` field is used for the client IP address.
- `SIADDR` field is used for the server IP address.
- `CHADDR` is the client hardware address.

#### 66. Which command will allow you to diagnose DHCP relay agent messages on a router or switch?

- `#debug ip dhcp server packet` will show the details of a DHCP relay agent conversation.
- It will detail conversation between the client and router and the router and the DHCP server.

#### 67. What is DHCPv6 used for when a network is configured for Stateless Address Autoconfiguration (SLAAC)?

- `SLAAC` allows for the client to learn the network ID and calculate a host ID that is unique.
- However, SLAAC lacks the ability to configure options such as DNS time servers, etc.
- DHCPv6 allows for the configuration of these options when used in conjunction with SLAAC.

#### 69. Which statement is correct about stateful DHCPv6?

- `Stateful DHCPv6` supplies the network ID and host ID.
- The default router is discovered through the `Neighbor Discovery Protocol (NDP)`.

#### 71. What happens if you delete a current lease on the DHCP server?

- When the lease for a node is deleted on DHCP server, server is free to hand out the lease to another node.
- The client will retain the IP address until the renewal period, which will cause a duplication of IP addressing.

#### 72. What happens at the client when the lease for an IP address reaches seven-eighths of the lease cycle?

- At seven-eighths of the lease cycle, the DHCP client will perform a `rebinding`.
- The rebinding process means that the original DHCP server was down at the one-half mark of the lease, so now the client will try to rebind with any responding DHCP server.
- The client will retain the lease until the end of the lease cycle.

#### 77. Which DSCP marking has the highest priority?

- `DSCP EF 46` has the highest priority and should be used for VoIP traffic and video.

#### 78. What is the recommended maximum delay VoIP traffic should not exceed?

- The maximum delay that VoIP traffic should not exceed is 150 ms.

#### 80. Which method helps combat queue starvation for QoS queuing?

- QoS queue starvation occurs when the LLQ is given priority over the CBWFQ.
- Therefore, policing of the LLQ will help limit queue starvation and allow those queues an equal share of the total output bandwidth.

#### 84. Why should QoS policing be implemented?

- QoS policing should be implemented to adhere network traffic to a `contracted committed information rate (CIR)`.

#### 88. Which command will enable SSH version 2 for logins?

- `(config)#ip ssh version 2` will set SSH version to 2.

#### 89. Which command will configure the router or switch to allow SSH as a protocol for management with a fallback of Telnet?

- `(config-line)#transport ssh telnet` will configure the VTY line to accept as a login protocol and fall back to Telnet.

#### 91. You have created the SSH encryption keys, but you cannot enable SSH version 2. What is the problem?

- When you are configuring SSH version 2, the key strength must be at least 768 bits for the modulus.

#### 92. Which command will configure a local user for SSH access?

- `(config)#username user1 password Password20!` will create a user account called user1 with a password of Password20!.

#### 94. You want to turn on local authentication so that a user must supply a username and password when managing the switch. You have created the username and password combinations on the switch. Which command will direct SSH and Telnet to use this authentication model?

- After configuring username and password combinations, you will need to configure the line that will use local authentication.
- `(config-line)#login local` will apply to all the transport methods configured on the line.

#### 95. Which banner will be displayed first when a user connects to a Cisco device via SSH?

- The `login banner` will be displayed during initial connection to Cisco device via SSH.

#### 98. Which command will allow you to boot a router from a TFTP server for the image of c2900-universalk9-mz.SPA.151-4.M4.bin on the TFTP server of 192.168.1.2?

- `(config)#boot system c2900-universalk9-mz.SPA.151-4.M4.bin tftp://192.168.1.2` will configure the router for booting of the image from the TFTP server.
- Under normal circumstances, this should not be used in production, because the router boot process is dependent on the availability of the TFTP server.

#### 99. You’re upgrading the flash memory on a 2900 router with a brand-new flash card. What needs to be done to restore the IOS?

- When the router boots, it will not find the IOS and will boot into ROMMON mode.
- From ROMMON mode, you will configure an IP address, subnet mask, gateway, TFTP server and image and initiate a TFTP download to flash.
- Once it's downloaded, you can boot the router and verify operations.

#### 100. Which command(s) are required before you can use an FTP server for backing up configuration? Assume that the username is USER and the password is USERPASS.

- `(config)#ip ftp username USER` will configure the username USER for FTP connections
- `(config)#ip ftp password USERPASS` will configure the password USERPASS for FTP connections

### 5. Security Fundamentals

#### 1. Which term describes the outside of the corporate firewall?

- `Perimeter area` is out side of the corporate firewall.
- The perimeter area generally holds equipment necessary for routing to the ISP.

#### 10. Which method would prevent tampering of data in transit?

- `Secure Sockets Layer (SSL)` communications offer both encryption and authentication of the data via certificate signing.
- This would prevent tampering of the data end to end.

#### 15. Which attack can be used on a native VLAN?

- `Double tagging` is an attack that can be used against the native VLAN.
- The attacker will tag the native VLAN on a frame and then tag another inside that frame for the VLAN that the attacker intends to compromise.
- When the switch receives the first frame, it removes the default VLAN tag and forwards it to other switches via a trunk port.
- When the other switch receives the frame with the second VLAN tag, it forwards it to the VLAN the attacker is targeting.

#### 21. What type of filters can be placed over a monitor to prevent the data on the screen from being readable when viewed from the side?

- `Privacy filter` are either film or glass add-ons that are placed over a monitor.
- They prevent the data on the screen from being readable when viewed from the sides.

#### 23. Several office-level users have administrative privileges on the network. Which of the following is the easiest to implement to immediately add security to the network?

- By implementing `least previlege` and removing the administrative privileges from the office workers, you can easily secure the network.

#### 24. You need to protect your users from Trojans, viruses, and phishing emails. What should you implement?

- `Anti-malware software` covers a wide array of security threats to users, including Trojans, viruses and phishing emails.

#### 35. Which command will create and apply an access list to secure router or switch management?

- You must first create an access list to permit the host that will manage the router or switch with `(config)#access-list 1 permit host 192.168.1.5`
- Then, enter the VTY line in which it will be applied with the command `line vty 0 5`.
- Then apply it with the command `(config-line)#ip access-class 1 in`, which differs from the command `ip access-group`, which is used on interfaces.

#### 43. During a recent external security audit, it was determined that your enable password should be secured with SHA-256 scrypt. Which command will change the password strength on the switches and routers?

- The command `(config)#enable algorithm-type scrypt secret Password20!` will change the enable password to `Password20!` and the scrypt algorithm type.

#### 46. You need to disconnect a network admin from the switch or router. Which command would you use?

- `#clear line vty 2` will disconnect a remote admin connected to the switch.

#### 49. What is the end device that sends credentials for 802.1X called?

- The end device that sends credentials is called the `supplicant`.
- The supplicant is a piece of software in the OS that supplies the credentials for AAA authentication.

#### 50. What is the switch called in an 802.1X configuration?

- The switch is responsible for communicating with the supplicant and sending information to the authenticating server.
- This device is called the `authenticator`.

#### 51. What protocol does the supplicant communicate to the authenticator for 802.1X?

- The protocol used to communicate between the supplicants and the authenticator is `802.1X EAP`.
- `Extensible Authentication Protocol (EAP)` is a layer 2 protocol used specifically for authenticating devices to switch ports and wireless.

#### 54. A smart card is an example of which type of authentication?

- `Smart card` is an example of multifactor authentication because you must have the smart card and know the passphrase that secures the credentials stored on the card.

#### 58. Which layer 3 protocol does GRE use?

- `GRE` uses the layer 3 protocol 47.

#### 61. What is the default MTU of a GRE tunnel?

- The maximum transmission unit of a GRE tunnel is 1476 because there are 24 bytes of overhead for the GRE header.
- 20 bytes are for public IP header and 4 bytes for GRE.

#### 62. Which command will help you verify the source and destination of a GRE tunnel?

- `#show interface tunnel 0` will show in the output the source and destination of the tunnel.

#### 63. In the following exhibit, if you do a traceroute on Router A to a destination of 192.168.3.50, how many hops will show?

- If a traceroute is performed to 192.168.3.50 on Router A, it will show one hop.
- This is because the 192.168.3.0 network is on the otherside of the tunnel interface, which is one hop away.

#### 65. Which protocol helps resolve and direct traffic for DMVPN connections?

- `Next Hop Router Protocol (NHRP)` is responsible for resolving and directing traffic for DMVPN traffic.

#### 67. DMVPN is an example of which topology?

- DMVPN is an example of `hub-and-spoke` or `point-to-multipoint` topology.

#### 68. Which benefit of using a secure VPN allows verification that a packet was not tampered with in transit?

- Data integrity is one of the benefits of using a secure VPN protocol.
- To ensure its integrity, a packet is sealed with a hash that must be calculated to the same hash on the otherside when it is received and decrypted.

#### 69. Which Cisco technology is often used to create VPN tunnels between sites?

- `Cisco FTD` devices are used to create VPN tunnels between sites.
- FTD devices run the Cisco FTD software, which allows for firewalls, intrusion prevention and VPNs among other security-related functions.

#### 70. You have several remote workers who enter patient information and require a high level of security. Which technology would best suit the connectivity for these workers?

- Since you have several remote workers who telecommute, the best connectivity option would be `client SSL/VPN connectivity`.
- A product called `Cisco Any Connect Secure Mobility Clients` allow for SSL encryption for VPN tunnels back to the main site.

#### 71. Which protocol does IPsec use to encrypt data packets?

- IPsec uses `Encapsulating Security Payload (ESP)` protocol to encrypt data.

#### 79. What is the expanded range of a standard access list?

- The expanded range of a standard access list is 1300 to 1999.
- The range for an expanded extended access list is 2000 to 2699.

#### 87. Which type of ACL allows for removing a single entry without removing the entire ACL?

- `Named access control list` allows for removing and adding entries by their line number.
- Standard and extended access lists require the entire ACL to be removed and reconfigured if one entry needs to be removed.

#### 88. Which type of ACL allows you to open a port only after someone has successfully logged into the router?

- Once a successful login is performed at the router, the `dynamic access control list` is activated.
- This is also called lock and key security.

#### 98. Which command will allow you to see the output in the following exhibit with the line numbers?

- `#show ip access-list` will show all access lists with the line numbers

#### 100. Which command will create an extended named access list?

- `(config)#ip access-list extended named_list` will create an extended named access list

#### 113. You are configuring a port for port security and receive the error Command rejected: FastEthernet0/1 is a dynamic port. Which commands will help you configure the port?

- When port security is configured, the port cannot be in dynamic mode or DTP mode.

#### 119. Which command will allow you to see logged security violations for port security?

- `#show port-security` will show all ports that have logged port security violations.

#### 126. Which command will allow you to globally reset all ports with an err-disable state with minimal disruption?

- `(config)#errdisable recovery cause psecure_violation` will reset all ports with an err-disable status.

#### 130. Which is an authentication protocol for AAA servers to secure Telnet authentication?

- `TACACS+` is a protocol used for communications between a switch or router and the AAA server for authenticating users.

#### 131. Which command will configure the router to use a TACACS+ server and a backup of local for authentication of logins?

- `(config)#aaa authentication login default group tacacs+ local` will configure AAA authentication for login using the default list and a group of TACACS+ servers for TACACS+ login first and a backup of local for authentication.

#### 132. You configured the AAA authentication for login to default local but forgot to create a local AAA user. What will happen when you log out?

- The router will lock you out since you have not provided a local account to login with.

#### 133. You were routinely looking at logs and found that a security incident occurred. Which type of incident detection is described?

- Routinely looking at a log file and discovering that a security incident has occurred is an example of `passive detection`.

#### 135. Matilda is interested in securing her SOHO wireless network. What should she do to be assured that only her devices can join her wireless network?

- Enabling `MAC filtering` on the AP will allow the devices that she specifies.

#### 138. Which security mode does WPA3-Enterprise use that offers the highest level of security?

- `WPA3-Enterprise` offers a 192-bit security mode that uses 192-bit minimum strength security protocols.

#### 140. Which feature does 802.11i add to the WPA security protocol?

- The `802.11i` standard added the feature of per-frame encryption.

#### 141. Which mode of encryption does 802.11i (WPA2) introduce?

- The `802.11i (WPA2)` specification introduced a specific mode of AES encryption called Counter Mode with Cipher Block Chaining Message Authentication Code Protocol (CCMP)

#### 142. Which feature was introduced with WPA3 to enhance security?

- The WPA3 protocol introduced the feature of `Simultaneous Authentication of Equals (SAE)` authentication.

#### 143. When configuring WPA2-Enterprise mode on a wireless LAN controller, what must be configured?

- When configuring WAP2-Enterprise mode on a wireless LAN controller, you must configure a RADIUS server for authentication of the users or computers joining wireless.

#### 144. When configuring WPA2, you want to ensure that it does not fall back to the older WPA specification. What parameter should you disable?

- You should disable the `Temporal Key Integrity Protocol (TKIP)` when configuring WPA2.
- This will ensure that the WAP and client do not fall back to the older WPA.

#### 148. You are configuring a WPA2 WLAN. Which security configuration should you use for the highest level of security?

- WPA2 protocol can be configured with AES encryption to provide the highest level of security.

#### 150. Which protocol will restrict you from achieving high throughput rates?

- When a WLAN is configured with `WPA-TKIP`, it will not be able to achieve over 54 Mbps.

### 6. Automation and Programmability

#### 4. What is the term that is used to describe the framework responsible for assisting in network automation?

- The term `DevOps` is used to describe the framework responsible for assisting in network automation.
- `NetOps` refers to the network operation team's responsibility.
- `SysOps` is used to describe the control of network systems such as DNS and DHCP.
- `SecOps` refers to the security operation as it pertains to the network.

#### 5. Which management methodology is commonly used by developers for network automation?

- The management methodology that is commonly used by developers for network automation is `Lean and Agile`.
- Agile focuses on an adaptive approach for simultaneous workflows, such as configuration of default route on several routers.

#### 7. Which element of YAML defines a key-value pair?

- YAML uses `mapping` to define keys and values as pairs.

#### 12. You are developing a network automation script that retrieves information. Which interface can you implement that will act similar to an API?

- SNMP was originally created to allow retrieval of information from network devices and can be programmatically controlled similar to API.

#### 16. Which is a benefit of controller-based networking?

- A benefit of controller-based networking is increased security.
- When ACLs and filters are applied, they are applied informally to all nodes that are controlled by the controller.

#### 24. Which method for configuration is used with Cisco Prime Infrastructure?

- SNMP along with Telnet and SSH are used to configure network devices with Cisco Prime.

#### 25. Which type of architecture is used with controller-based networks?

- `Spine/Leaf` architecture model has been adopted in controller-based networks.

#### 37. On which SDN plane does CDP function?

- CDP functions on the management plane of the SDN model.
- It helps with management of routers and switches and does not directly impact the data plane.

#### 42. What is the maximum hop count of fabric switching?

- The maximum hop count on fabric switching is a total of 3 hops.
- When a host transmits, it will enter a Leaf switch; then the Leaf switch will then forward traffic to the spine and againe to leaf switch and to the destination host.

#### 45. Which WAN technology uses the overlay to connect remote offices?

- `DMVPN` is a WAN technology that allows for VPNs to be created using the overlay of SDN.

#### 48. Which next-hop packet forwarding protocol is used with SDN switching networks?

- `Equal-Cost Multi-Path routing (ECMP)` packet forwarding protocol is used to calculate next-hop forwarding with SDN switch networks.

#### 50. Which protocol is not used by the DNA discovery process for reading the inventory of a network device?

- After the Cisco DNA discovery process has found a device, it will use SSH, Telnet, SNMP, HTTP(S) and NETCONF.

#### 51. Where would you see the overall health of the network inside of the Cisco DNA Center?

- `Assurance` section of Cisco DNA Center allows you to see the overall health of network devices managed by DNA center.

#### 52. Which Cisco DNA Center feature allows you to template and apply standard configuration such as DNS servers, NTP servers, and AAA servers?

- `Plug and Play` is a feature inside Cisco DNA Center that allows you to onbaord network devices and apply standard configurations.

#### 53. You want to see how everything is connected at a particular site. Which section contains a tool to obtain this information inside of the Cisco DNA Center?

- Under the `Provision` section, you can click on the hierarchy item that contains the site, then you will select the topology icon in the result pane.
- This will allow you to view how everything is connected at a particular site.

#### 54. You need to add an OSPF area to a number of routers. What is the easiest method to achieve this with the Cisco DNA Center?

- With `DNA Command Runner Tool`, you can execute a command on a group of devices.

#### 55. In which section inside of the Cisco DNA Center can you view and manage inventory of routers, switches, APs, and WLCs?

- `Provision` section allows you to view and edit the discovered inventory of network devices.

#### 56. You are developing a Python script that will interact with the Cisco DNA Center. Which section will detail the API that you will need to use?

- You can see the details of an API for Cisco DNA Center by using the `Platform` section.

#### 57. What is the Cisco DNA Center feature that automates the fabric of the underlay and overlay of the network?

- The Cisco `SD-Access` is an automated Plug and Play solution that automates the underlay and overlay of the fabric.

#### 58. Which feature does Cisco Prime Infrastructure provide that Cisco DNA Center cannot provide?

- Cisco DNA Center cannot provide device configuration backups, which still requires Cisco Prime Infrastructure.

#### 77. Which component in an Ansible setup defines the connection information so that Ansible can perform configuration management?

- `Inventory` component defines the various hosts and their connection information in an Ansible setup.

#### 79. Which Puppet component contains the configuration for the managed hosts?

- `Manifest` component of Puppet contains the configuration for the managed hosts.

#### 81. Which Chef component collects system state information and reports back to the Chef Server component?

- `Ohai` component is responsible for monitoring system state information and reporting back to the Chef server component.

#### 84. Which Ansible tool will allow you to try commands against a host without making a Playbook?

- `Ad-hoc interface` allows you to try commands against a host without making a Playbook.

#### 85. What are global variables that contain information specific to Puppet called?

- `Facts` describes global variables that contain information that is specific to Puppet.

#### 86. Once you have completed a Cookbook for Chef, where do you upload the Cookbook so it is accessible on the Chef Server?

- Once you have completed a Cookbook for Chef, you will upload the Cookbook to the `Bookshelf` located on the Chef Server.

#### 89. What function does Knife serve in the Chef configuration management utility?

- The `Knife utility` is a CLI that allows for the management of Chef.

### 7. Practice Exam 1

#### 8. What is the term that defines the access point for the service provider’s services?

- `Point of presence (PoP)` is the term that defines the access point of the provider's services.
- These services might be Internet, private WAN, or cloud resources

#### 9. You have several VMs in a public cloud. What is a benefit of creating NTP VNF in the public cloud for the VMs?

- Lowering bandwith between the premises and your VMs on the public cloud is a direct benefit of locating NTP VNF on the public cloud for VM time synchronization.

#### 10. When deciding to move DNS into the cloud for an application on the public cloud, what is the primary decision factor?

- Bandwidth is the primary decision factor for moving DNS closer to the application in the public cloud.
- However, if the majority of DNS users are on premises, then it should remain on premises for bandwidth reasons.

#### 14. What are stateless DHCPv6 servers used for?

- Stateless DHCPv6 servers are used to configure DHCP options only.
- The one option that all clients need is the DNS server.
- Default gateway and IPv6 address are configured via RS and RA packets, when a client starts up in the network.

#### 19. Which command will show the number of entries in a MAC address table?

- `#show mac address-table count` will show the current MAC address entry count and will also show the maximum number of entries the table can hold.

#### 23. Which is a correct statement about the output in the following exhibit?

- The switch has negotiated with the adjacent switch to become a trunk and set its trunking protocol to 802.1Q.
- The letter n in front of 802.1Q specifies it was negotiated.

#### 24. You have a switch with several hundred interfaces. You only want to see the running- config for one interface, Gi3/45. Which command will allow you to see the running-config for only Gi3/45?

- `#show running-config interface gi 3/45` will show the running-configuration for only interface Gi3/45.

#### 30. You are configuring an EtherChannel between two switches. You check your configuration on the first switch and are ready to configure the second switch. What mode do you need to configure on the other switch? Refer to the following exhibit.

- Since the auto mode was used on the first switch, desirable should be used on the second switch to assure forming of an EtherChannel by using the command `(config-if)#channel-group 1 mode desirable`

#### 35. Which AP mode allows for RF analysis of the 802.11ac radio spectrum?

- `Monitor mode` can be used for analysis of the radio spectrum.

#### 38. Which is a benefit of using TACACS+ for authentication of users?

- TACACS+ is a Cisco-defined protocol.
- One of the useful features is that it can authenticate a user and only allow that user to access certain commands on the router or switch.

#### 40. You want all guests to register for wireless Internet access before granting them access. What should you implement?

- `Captive portal` will allow you to require all guests to register for wireless Internet access before granting them access.
- When you connect to the SSID, they will be presented with the captive portal web page.

#### 45. Which command will allow you to see the next advertisement interval for RIPv2?

- `#show ip protocols` will display the next interval when RIPv2 advertisements are sent out.

#### 48. You have RIPv2 configured on an Internet-facing router. Which command will suppress RIPv2 advertisements on the interface link?

- `(config-router)#passive-interface serial 0/0` configured in the router instance will suppress updates from exiting interface Serial 0/0.

#### 49. Which is a problem with using RIPv2 in a network?

- RIPv2 has extremely slow convergence time. This is because the advertisement of routes is every 30 seconds.

#### 64. Which command will allow you to see the networks the current router is advertising for OSPF?

- `#show ip protocols` will list the router ID of the current router as well as the networks that are being advertised via OSPF on the current router.

#### 69. Which statement describes FQDNs?

- FQDNs are significant from right to left, starting with a period of signify the root.
- The period is normally not visible on the FQDN, but it is processed as the root lookup.

#### 70. Which protocol and port number does SNMP use for polling from the NMS?

- SNMP uses UDP port 161 for communication from the NMS to a network device for information requests.
- Uses UDP 162 for traps.

#### 75. Which command needs to be configured to enable the SSH Copy Protocol (SCP)?

- `(config)#ip scp server enable` needs to be configured to enable the `SSH Copy Protocol (SCP)`

#### 76. What is the attack in which DTP is exploited by a malicious user?

- `VLAN hopping` is an attack in which DTP is exploted.
- The attacker negotiates a trunk with the switch via DTP and can hop from VLAN to VLAN.

#### 77. Which layer 2 protocol has built-in security for WAN connections?

- `Point-to-Point Protocol (PPP)` is a layer 2 WAN protocol that supports CHAP which secures connections.

#### 82. You have been asked to recommend a private WAN technology. All of the remote offices have varied physical connectivity paths. Which private WAN technology should you recommend?

- MPLS allows for varied access links such as serial leased lines, Frame Relay, Metro Ethernet, etc.
- You can leverage the existing connectivity methods to form a private WAN.

#### 83. Which protocol does IPsec use to check integrity of data packets?

- IPSec uses `Authentication Header (AH)` protocol to check data integrity.
- This is done by creating a numerial hash of the data via SHA1, SHA2, or MD5 algorithms.

#### 89. Which protocol was released to fix WEP?

- `Wi-Fi Protected Access (WPA)` was rushed out and released to fix weak security in the `Wired Equipvalent Privacy (WEP)` wireless security protocol.
- WPA2 was formally released to address weaknesses in the RC4-TKIP security protocol.

#### 92. Which is a negative outcome from automating a configuration change across the enterprise?

- A negative outcome from automation of configuration across an enterprise is that you increase the odds of configuration conflicts.

#### 94. Which protocol is used with the Southbound interface in the SDN controller?

- `OpenFlow protocol` is an openstandard used to configure network devices via the `Southbound interface (SBI)` of the SDN controller.

#### 95. On which layer does the fabric of software defined network switch packets?

- The fabric of the SDN switches packets on layer 3.

#### 100. Which command is used to output JSON from the execution of a command on a Cisco router or switch?

- `show interface status | json-pretty native` is used to convert the output of a command to JSON in a Cisco router or switch.

### 8. Practice Exam 2

#### 5. Which sub-protocol inside of the PPP suite is responsible for tagging layer 3 protocols so that multiple protocols can be used over a PPP connection?

- `Network Control Protocol (NCP)` works at layer 3 tagging the network protocols from end to end when PPP is used.
- This gives PPP the ability to offer multiprotocol transport.

#### 10. You are running several web servers in a cloud with a server load balancer. As demand increases, you add web servers. According to the NIST standard of cloud computing, which feature can you use to increase your compute capability for demand?

- `Rapid elasticity` is the ability to add and remove compute capability in the cloud.

#### 14. What is the process of stateful DHCPv6 for IPv6?

- `Stateful DHCPv6` uses a process of Solicit, Advertise, Request, Reply.
- However, IPv6 uses DHCPv6 Solicit multicast address.

#### 15. When SLAAC is performed on an IPv6 host, which process happens first?

- Before a host can communicate via an RS packet, it first needs a valid IP address, which is a link-local address so that it can send RS packet and receive RA packet.

#### 16. In IPv6, the solicited-node multicast message is used for what?

- The `Solicited-node multicast message` is used for resolution of the MAC address for an IPv6 address.

#### 17. The following exhibit is an Ethernet frame. What is field A in the exhibit?

- The first field after `preamble` and `start frame delimiter (SFD)` is the `destination MAC address`.
- `Type` field is after two address fields and is used to define the upper-layer protocol the data belongs to.

#### 30. You have configured the command channel-group 1 mode active on a range of interfaces that will participate in an EtherChannel. Which pseudo interface is created for overall management of the EtherChannel?

- When you configure the `channel-group 1 mode active` command on the first interface, a pseudo interface is created called `port-channel 1`.

#### 35. Which AP mode requires all traffic to be centrally switched at the WLC?

- `Local mode` is a centralized switching mode in which all traffic is first sent to the WLC to be centrally switched to its intended destination.

#### 38. Which protocol will encrypt the entire packet from the switch or router to the AAA server?

- `TACACS+` protocol will encrypt the entire packet from the switch or router to the AAA server.

#### 43. Why can a route have a destination of an interface rather than an IP address?

- Serial interfaces are point-to-point connections.
- Any traffic directed down the interface will automatically appear on the adjacent router.

#### 45. What is the purpose of the RIPv2 holddown timer?

- The holddown timer's job is to allow the network to stabilize after a route had become unreachable via an update.
- This limits the potential problems related to a flapping port and allows RIPv2 to converge route updates in the entire network.
- The default holddown timer is set to 180 seconds.

#### 66. Which is a disadvantage of using NAT?

- NAT creates packet switching path delay because each address travling through NAT process requires lookup time for translation.

#### 71. Which command will configure all event logs to be sent to a syslog server?

- `(config)#logging host 192.168.1.6` will configure all logs to be sent to the syslog server.

#### 74. Which layer 3 protocol is used for marking packets with QoS?

- `DSCP` is a 6-bit values in the `Type of Service (ToS)` field of the IP header.
- The DSCP value defines the importance of packets at layer 3.

#### 86. Which command is used to view the DHCP snooping database?

- `#show ip dhcp snooping binding` will display the DHCP snooping database.
- This database will have entries for the MAC address, IP address, lease time, VLAN, and interface.

#### 88. Which authentication method will allow an authenticated user to access only certain commands on a router or switch?

- `TACACS+` will allow for authentication of users and also provides a method of restricting users to specific commands.

## CCNA Certification Study Guide

### Assessment Test

#### 4. You reload a router with a configuration register setting of 0x2101. What will the router do when it reloads?

- 2100 boots the router into ROM monitor mode
- 2101 loads the mini-IOS from ROM
- 2102 is the default and loads the IOS from flash

#### 5. Which of the following commands provides the product ID and serial number of a router?

- `#show license udi` commands displays the `unique device identifier (UDI)` of the router, which comprises the product ID and serial number of the router.

#### 6. Which command allows you to view the technology options and licenses that are supported on your router along with several status variables?

- `#show license feature` command allows you to view the technology package licenses and feature licenses that are supported on your router along with several status variables related to software activation and licensing.

#### 7. You need to look at past network data in DNA Center. How long can you look back into the DNA snapshot?

- DNA center stores the network snapshot for one week.

#### 11. What command is used to view the IPv6-to-MAC-address resolution table on a Cisco router?

- `#show ipv6 neighbor` provides the ARP cache on a router.

#### 17. When do two adjacent routers enter the 2WAY state?

- The process starts by sending out Hello packets.
- Every listening router will then add the originating router to the neighbor database.
- The responding routers will reply with all of their Hello information so that the originating router can add them to its own neighbor table.
- At this point, we will have reached the 2WAY sate.

#### 20. Which statement about GRE is not true?

- `Generic Routing Encapsulation (GRE)` has no built-in security mechanisms.

#### 28. On which interface do you configure an IP address for a switch?

- For switch, the IP address is configured under a logical interface, called a `management domain` and VLAN 1 by default.

#### 31. Your inside locals are not being translated to the inside global addresses. Which of the fol- lowing commands will show you if your inside globals are allowed to use the NAT pool?

- Once you create your pool, `(config-if)#ip nat inside source` must be used to say which inside locals are allowed to use the pool.
- To see if access list 100 is configured correctly, `#show access-list` is needed.

#### 38. Which class of IP address provides 15 bits for subnetting?

- Class A addressing provides 22 bits for host subnetting.
- Class B provides 16 bits but only 14 are available for subnetting.

#### 39. What DNS record do you need to create for APs to automatically discover the WLC.

- For the DNS method, you need to create a A record for `CISCO-CAPWAP-CONTROLLER` that points to the WLC management IP.

#### 45. What’s the default QoS queue for a WLAN?

- WLANs default to silver queue, which effectively means no QoS is being utilized.

#### 46. Where is a hub specified in the OSI model?

- Hubs regenerate electrical signals, which are specified at the Physical layer.

#### 50. 1000Base-T is which IEEE standard?

- `802.3ab` is the standard for 1 Gbps on twisted-pair.

#### 53. Which command is used to determine if an access list is enabled on a particular interface?

- `#show ip interface` will show you if any interfaces have an outbound or inbound access list set.

#### 57. You boss read about WPA3 and want you to explain it to him. What replaced the default open authentication with which of the following enhancements?

- 802.11 open authentication support has been replaced with `Opportunistic Wireless Encryption (OWE)` enhancement.

## Boson Exsim

### Practice Exam A

#### 13. Which of the following is true about IPSec configured in transport mode?

- IPSec supports two modes: transport and tunnel.
- In transport mode, only the IP packet's payload is encrypted by IPSec.
- IPSec in tunnel mode, encrypts the entire packet so it requires additional headers.

#### 14. In a split-MAC deployment, which device is responsible for prioritizing packets and responding to beacon and probe requests?

- Lightweight AP handles real-time processing of data, such as sending and receiving 802.11 traffic, responding to beacons and probe messages, encryption and packet prioritization.
- WLC handles tasks that are not time-sensitive such as security management, LAP config management and client load balancing.

#### 15. Which of the following security settings are you most likely to configure by using Layer 3 Security drop-down list box on the Layer 3 tab?

- There are two different sets of Layer 3 security feature that you can configure on a Cisco WLC: one ofr WLAN and one for Guest LAN.
- `IPSec` enables Layer 3 security of WLANs by IPSec
- `VPN Pass-through` enables Layer 3 security for WLANs by allowing a client to establish a connection with a speicifc VPN server.
- `Web Authentication` enables Layer 3 security for Guest LANs by prompting a user for name and password.
- `Web Passthrough` enables direct access to the network for Guest LANs without prompting.

#### 24. SSH configuration message question

- To enable SSH for VTY lines, you should complete the following steps:
  1. Configure host name other than default by `hostname` command
  2. Configure domain name by `ip domain-name` command
  3. Generate RSA key pair for router by `crypto key generate rsa` command
  4. Configure VTY lines to use SSH by `transport input ssh` command

#### 25. Which of the following statements about FlexConnect ACLs is true?

- `FlexConnect ACLs` are configured on WAP VLAN interfaces if the lightweight AP is operating in FlexConnect mode.
- Although it is possible to configure FlexConnect ACLs for the native VLAN, it's not possible to configure FlexConnect ACLs for the native VLAN if the VLAN configuration is inherited from a FlexConnect group.

#### 34. You want to use an HTTPS connection to access and configure a WLC.

- You should issue `config network secureweb enable` command to configure WLC to support HTTPS management connections.

#### 38. Which of the following statements is correct regarding how OSPF operates on the interface?

- Nonbroadcast and point-to-multipoint nonbroadcast networks do not allow multicast packets.
- To configure OSPF to send unicast updates, you must configure neighbour routes with `neighbor` command so they can establish adjacencies on OSPF non-broadcast networks.

#### 39. Select the following EIGRP terms and drag them to their corresponding definitions

- `Feasible Distance` is the best metric along a path to a destination.
- `Advertised Distance` is the metric that has been calculated by the next-hop router.
- `Successor` is the best path to a destination network. The route with the lowest FD is chosen as the successor.
- `Feasible successor` is a backup path that is guaranteed to be loop-free and can be used if the successor route goes down.

#### 41. Select the 802.11 MAC frame components, and drag them to their appropriate position within the 802.11 MAC frame format.

- FC - DUR - ADD1 - ADD2 - ADD3 - SEQ - ADD4 - DATA - FCS

#### 43. Which of the following are used by WPA2 to provide MICs and encryption?

- AES and CCMP are used by WPA2 to provide MICs and encryption.
- Wireless security protocols use MICs to prevent data tempering and encryption to protect confidentiality.

#### 49. Which of the following is not information provided from an IP phone to a switch by using CDP?

- Although VLAN IDs are sent using CDP to devices on network, it is the switch that sends voice VLAN ID to IP phones and not vice versa.

#### 55. Which of the following best describes what will occur when an attached PD attempts to draw more than allocated amount of power from configured interface?

- `power inline police action log` command will restart and send a log message to the console when an attached PD attempts to draw more than the cutoff power from the configured interface.

#### 58. Which of the following statements are true regarding dynamic interfaces on WLCs?

- `Dynamic interfaces` are user-defined and are typically used for client data.

#### 60. Which of the following APIs are typically used to enable communication between SDN controller and application plane?

- `REST` is a northbound API architecture that uses HTTPS to enable external resources to access and make use of programmatic methods that are exposed by the API.
- `OSGi` is a Java-based northbound API framework that is intended to enable the development of modular programs.

#### 65. Which of the following statements best describes the AAA Override feature on a Cisco WLC?

- The AAA Override feature on a Cisco WLC can be used to configure VLAN tagging, QoS and ACLs to individual clients based on RADIUS attributes.

#### 71. Which of the following is the best way to mitigate zero-day exploits?

- Hardening a system so that it provides only required functionality is the best way to mitigate zero-day exploits.
- `A zero-day vulnerability` is a vulnerability that has not yet been identified and therefore has no fix.

#### 82. You are configuring a normal WLAN by using WLC GUI. You click Create New on WLANs page. Which action are you most likely to perform first.

- To create a new normal WLAN, you should complete four steps on the WLANs > New page of WLC GUI:
  1. Select the type of WLAN you are creating from `Type` drop-down list box.
  2. Enter a 32-character or less profile name in the `Profile Name` field.
  3. Enter a 32-character or less SSID in the `SSID` field
  4. Choose a WLAN ID from the `ID` drop-down list box

#### 83. Which of the following best describes an AP deployment that connects APs to a WLC that is housed within a switch stack?

- In `Embedded AP deployment`, the WLC is embedded wihtin a stack of switching hardware instead of existing as a separate entity.
