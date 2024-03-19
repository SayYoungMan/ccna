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

#### 81. WhenyouchangethenativeVLANofatrunkfromVLAN1toVLAN999andyoureceive the error %CDP-4-NATIVE_VLAN_MISMATCH: Native VLAN mismatch -discovered.... What is the possible problem?

- This error is normal if it's the first interface to be changed over to the new native VLAN since the other interfaces has not been changed yet.
- If the other interface was changed already and received this error, CDP is letting you know that the other side is mismatched.

#### 91. Which command gives information that’s identical to the output of the show cdp neighbors detail command?

- `#sh cdp entry *` commandj will give output that's identical to `#show cdp neighbors detail`

#### 95. You want to disable LLDP from sending advertisements on a single interface. Which command will you use?

- When you use `(config-if)#no lldp transmit`, it will suppress LLDP messages from exiting the interface it's configured on.

#### 96. What is the default value of the LLDP holddown timer for entries?

- The default value of LLDP holddown timer for entries is 120 seconds.
