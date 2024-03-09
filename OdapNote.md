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