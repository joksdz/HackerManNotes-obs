Cisco IOS is the operating system of Cisco network devices such as routers and switches. It provides features and services required to manage and operate network devices. This operating system comes in different versions and releases that vary in features, support, and performance. It offers several features required for the operation of modern networks, such as, but not limited to:

    Support for IPv6
    Quality of Service (QoS)
    Security features such as encryption and authentication
    Virtualization features such as Virtual Private LAN Service (VPLS)
    Virtual Routing and Forwarding (VRF)

Cisco IOS can be managed in several ways, depending on the network device and hardware used. The most commonly used method is the command line interface (CLI), which can also be managed in the graphical user interface (GUI). In addition, it supports various network protocols and services required for network operations. These include:

<table class="table table-striped text-left">
<thead>
<tr>
<th><strong>Protocol Type</strong></th>
<th><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td><code>Routing protocols</code></td>
<td>Such as <a href="https://en.wikipedia.org/wiki/Open_Shortest_Path_First" target="_blank" rel="noopener nofollow">OSPF</a> and <a href="https://en.wikipedia.org/wiki/Border_Gateway_Protocol" target="_blank" rel="noopener nofollow">BGP</a> are used to route data packets on a network.</td>
</tr>
<tr>
<td><code>Switching protocols</code></td>
<td>Such as <a href="https://en.wikipedia.org/wiki/VLAN_Trunking_Protocol" target="_blank" rel="noopener nofollow">VLAN Trunking Protocol</a> (<code>VTP</code>) and <a href="https://en.wikipedia.org/wiki/Spanning_Tree_Protocol" target="_blank" rel="noopener nofollow">Spanning Tree Protocol</a> (<code>STP</code>) is used to configure and manage switches on a network.</td>
</tr>
<tr>
<td><code>Network services</code></td>
<td>Such as <a href="https://en.wikipedia.org/wiki/Dynamic_Host_Configuration_Protocol" target="_blank" rel="noopener nofollow">Dynamic Host Configuration Protocol</a> (<code>DHCP</code>) are used to automatically provide clients on the network with IP addresses and other network configurations.</td>
</tr>
<tr>
<td><code>Security features</code></td>
<td>Such as <a href="https://en.wikipedia.org/wiki/Access-control_list" target="_blank" rel="noopener nofollow">Access Control Lists</a> (<code>ACLs</code>), which are used to control access to network resources and prevent security threats.</td>
</tr>
</tbody>
</table>

In Cisco IOS, different types of passwords are used for various purposes, for example:


<table class="table table-striped text-left">
<thead>
<tr>
<th><strong>Password Type</strong></th>
<th><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td><code>User</code></td>
<td>The <a href="https://www.cisco.com/c/en/us/td/docs/ios-xml/ios/security/s1/sec-s1-cr-book/sec-cr-t2.html#wp2992613898" target="_blank" rel="noopener nofollow">user</a> password is used for logging in to Cisco IOS. It is used to restrict access to the network device and its features.</td>
</tr>
<tr>
<td><code>Enable Password</code></td>
<td>The <a href="https://www.cisco.com/c/en/us/td/docs/ios-xml/ios/security/d1/sec-d1-cr-book/sec-cr-e1.html#wp3884449514" target="_blank" rel="noopener nofollow">enable password</a> is used to enter "enable" mode. The "enable" mode is the mode where you have access to advanced functions and settings.</td>
</tr>
<tr>
<td><code>Secret</code></td>
<td>The <a href="https://www.cisco.com/c/en/us/td/docs/ios-xml/ios/security/s1/sec-s1-cr-book/sec-cr-s1.html#wp2622423174" target="_blank" rel="noopener nofollow">secret</a> is a password to secure access to certain functions and services. It is often used to restrict access to remote management tools and services.</td>
</tr>
<tr>
<td><code>Enable Secret</code></td>
<td>The <a href="https://www.cisco.com/c/en/us/td/docs/ios-xml/ios/security/d1/sec-d1-cr-book/sec-cr-e1.html#wp3438133060" target="_blank" rel="noopener nofollow">enable secret</a> is an extra-secure password used to secure access to "enable" mode, and they are stored encrypted to provide additional protection.</td>
</tr>
</tbody>
</table>

# VLANs

Imagine this scenario: A startup called XQ hired a network administrator to create a network for their single-office company, and due to budget limitations, they can only afford one switch and router. The sysadmin of XQ stated that in addition to hosting the web and database servers in the network, staff from different departments will be using it. As a seasoned network security specialist, the network administrator immediately thought about the security attacks that an insider can perform, especially ones abusing broadcast traffic, such as `broadcast storms`. Therefore, to tackle this problem, the network administrator decided to logically segment the network with `Virtual Local Area Networks` (`VLANS`), conceptually breaking down one switch into smaller mini-switches.

A `VLAN` is a logical grouping of network endpoints connected to defined ports on a switch, allowing the segmentation of networks by creating logical broadcast domains that can span multiple physical LAN segments. With `VLANs`, network administrators can segment networks based on factors such as team, function, department, or application, without worrying about the physical location of endpoints and users. A broadcast packet sent over one `VLAN` does not reach any other endpoint that is a member of another `VLAN`. Because each `VLAN` is regarded as a broadcast domain, it needs to have its own `subnet`; for example, the network administrator contracted by XQ can segment the network by departments:

<table class="table table-striped text-left">
<thead>
<tr>
<th align="center"><strong>Department</strong></th>
<th align="center"><strong>VLAN ID</strong></th>
<th align="center"><strong>Subnet</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td align="center"><code>Servers</code></td>
<td align="center"><code>VLAN 10</code></td>
<td align="center"><code>192.168.1.0/24</code></td>
</tr>
<tr>
<td align="center"><code>C-Level</code></td>
<td align="center"><code>VLAN 20</code></td>
<td align="center"><code>192.168.2.0/24</code></td>
</tr>
<tr>
<td align="center"><code>Finance</code></td>
<td align="center"><code>VLAN 30</code></td>
<td align="center"><code>192.168.3.0/24</code></td>
</tr>
<tr>
<td align="center"><code>HR</code></td>
<td align="center"><code>VLAN 40</code></td>
<td align="center"><code>192.168.4.0/24</code></td>
</tr>
<tr>
<td align="center"><code>Marketing</code></td>
<td align="center"><code>VLAN 50</code></td>
<td align="center"><code>192.168.5.0/24</code></td>
</tr>
<tr>
<td align="center"><code>Support</code></td>
<td align="center"><code>VLAN 60</code></td>
<td align="center"><code>192.168.6.0/24</code></td>
</tr>
</tbody>
</table>

A myriad of benefits is attained when using `VLANs`, including:

- `Better Organization`: Network administrators can group endpoints based on any common attribute they share.
- `Increased Security`: Network segmentation disallows unauthorized members from sniffing network packets in other `VLANs`.
- `Simplified Administration`: Network administrators do not have to worry about the physical locations of an endpoint.
- `Increased Performance`: With reduced broadcast traffic for all endpoints, more 
 bandwidth is made available for use by the network.

Cisco switches provide the `VLAN` IDs/numbers 1-4094 (`0` and `4095` are reserved IDs and 
cannot be used); IDs 1-1005 (`VLAN 1` is known as the `default VLAN` and cannot/should 
not be altered nor deleted) are known as `normal-range` `VLANs`, with IDs 1002-1005 being 
reserved for `Token Ring` and `Fiber Distributed Data Interface` (`FDDI`) `VLANs`, while 
IDs 1006-4094 are known as `extended-range` `VLANs`. By default, any customization 
applied for `normal-range` `VLANs` is saved in the `VLAN` database (the `vland.dat` file), in 
contrast to `extended-range` `VLANs`, which do not have their customizations saved. `VLANs` 
2-1001 stored in `vlan.dat` can have parameters including name, type, state, and 
maximum transmission unit (`MTU`). 

## Access and Trunk Ports

Any port on a VLAN-enabled switch must be either an access port or a trunk port. Access ports belong to and can carry the traffic of only one VLAN (or in some cases two, with the second being for voice traffic); any traffic arriving on an access port is assumed to belong to the VLAN the port was assigned. On the other hand, trunk ports can carry multiple VLANs at the same time; trunk links connect two trunk ports on two switches (or a switch and router) to allow information from multiple VLANs to be carried out across switches.

## VLAN Identification

Standard 802.3 Ethernet frames do not contain VLAN information; therefore, switches and other VLAN-enabled devices need a mechanism to keep track of all the VLAN information associated with a packet while traversing VLAN-enabled devices. Two main trunking methods are utilized to achieve this, ISL and IEEE 802.1Q.
Inter-Switch Link (ISL)

### Inter-Switch Link (ISL)
is a Cisco-proprietary protocol used for trunking between VLAN-enabled devices. Although ISL is one of the first trunking methods (predating 802.1Q), it is deprecated and not as widely used in modern Cisco switches (and routers). Instead, most only support the widely adopted 802.1Q. ISL encapsulated the entire Ethernet frame, including the original Ethernet header and the VLAN tag, adding its 26-byte header and 4-byte trailer.
### IEEE 802.1Q

To ensure interoperability of VLAN technologies from the various network-equipments vendors, the Institute of Electrical and Electronics Engineers (IEEE) developed the 802.1Q specification in 1998. The IEEE 802 committee had to change the 802.3 Ethernet frame format by adding a pair of 2-byte fields, TPID and TCI (which consists of three subfields, PCP, DEI, and VID), resulting in a VLAN-compliant 802.1Q Ethernet frame.

![[8023_Legacy_8021Q_Ethernet_Frames.webp]]
Tag protocol identifier (TPID) is a 16-bit field always set to 0x8100 to identify the Ethernet frame as an 802.1Q-tagged frame. Tag Control Information (TCI) is a 16-bit field containing Priority code point (PCP), Drop eligible indicator (DEI) (previously known as Canonical format indicator (CFI)), and VLAN identifier (VID). The main field concerning VLANs is VID, occupying the low-order 12-bits of TCI. Since it is 12 bits, it allows 2^12 - 2 = 4096 (remember, 0 and 4095 are reserved) VLAN IDs. Therefore, an 802.1Q-tagged frame can contain information for 4094 VLANs; the practice of inserting multiple 802.1Q tags within a single packet is known as Double Tagging, introduced by 802.1ad. VLAN tagging is the process of inserting VLAN information into an 802.1Q Ethernet header, while VLAN untagging is the process of removing the VLAN information from an 802.1Q-tagged Ethernet frame and forwarding the packet to the destined ports.


###  Assigning NICs a VLAN in Linux
[link for instructions :](https://academy.hackthebox.com/module/34/section/1878)
### Assigning NICs a VLAN in Windows

[link for instructions :](https://academy.hackthebox.com/module/34/section/1878)
(just below the first one)
## Analyzing VLAN Tagged Traffic
We can identify and analyze `VLAN` tagged traffic on a network with [`Wireshark`](Tools) using the [vlan](https://www.wireshark.org/docs/dfref/v/vlan.html) filter. For example, when analyzing a network packet dump, we can inspect packets with `802.1Q` tagging using the filter `vlan`:
![[Wireshark_VLAN_Filter.png]]
Moreover, we can search for packets with a specific VLAN ID; for example, to search for packets having VLAN 10, we can use the filter vlan.id == 10:
![[Wireshark_VLAN_ID_Filter.png]]

## Security Implications and VLAN Attacks

Regardless of improving a network's security posture, adversaries can still circumvent the defensive mechanisms put forth by VLANs. Although in modern switched networks, the utilization of VLANs brings numerous advantages (such as simplified network maintenance and improved performance), it also introduces potential security risks, leading to various VLAN attacks. It is essential to grasp the underlying methodologies of these attacks and implement practical mitigation approaches to safeguard networks.

### VLAN Hopping

VLAN hopping attacks enable traffic from one VLAN to be seen by another VLAN without the aid of a router. It exploits Cisco's Dynamic Trunking Protocol (DTP), a protocol used to automatically negotiate the formation of a trunk link between two Cisco devices. An adversary needs to configure a host to mimic/act like a switch to take advantage of the automatic trunking port feature enabled by default on most switch ports. To exploit VLAN hopping, an adversary must be able to physically connect with a switch port that has DTP enabled. The adversary can abuse this connection by configuring a host connected to the switch on that specific port to spoof 802.1Q signaling and the DTP packets. If successful, the switch will eventually establish a trunk link with the adversary's host, exposing the network packets, not only for a specific VLAN.

We can use tools such as [Yersinia](Tools) to perform VLAN hopping attacks:
![[Yersinia_DTP_Attack.png]]
## Double-tagging VLAN Hopping

The double-tagging VLAN hopping attack is an increasingly more sophisticated attack against VLANs. Although VLAN double-tagging is a legitimate practice that entities such as Internet Service Providers (ISPs) utilize (they can use their VLANs internally while carrying traffic from clients that are already VLAN tagged), adversaries can also attempt to abuse it. In a double-tagging VLAN hopping attack, an adversary embeds a hidden 802.1Q tag inside an Ethernet frame that already has an 802.1Q tag, allowing the frame to go to a different VLAN, which the original 802.1Q tag did not specify.

An adversary can carry out this attack following three steps. Bare in mind that this attack only works if the adversary is connected to a port residing in the same VLAN as the native VLAN of the trunk port:

The adversary sends a double-tagged 802.1Q Ethernet frame to the switch with the outer header having the VLAN ID of the adversary, which is the same as the native VLAN of the trunk port. Assume that the native VLAN is VLAN 10 and that VLAN 30 is the VLAN the adversary wants to reach, where the victim resides.
The outer 4-byte 802.1Q tag arrives on the switch, and it is seen to be destined for VLAN 10, the native VLAN. After removing the VLAN 10 tag, the frame is forwarded on all VLAN 10 ports. On the trunk port, the VLAN 10 tag is stripped (removed), and the packet is not re-tagged because it is part of the native VLAN. However, the VLAN 30 tag is still intact (not stripped), and the first switch has not inspected it.
Subsequently, the switch will look only at the inner 802.1Q tag that the adversary sent, and it decides that the frame must be forwarded for VLAN 30, which is the adversary's chosen VLAN. Now, the second switch will either send the frame to the victim port directly or flood it, depending on whether there is an existing MAC address table entry for the victim host.

[Scapy](Tools) allows carrying out the double-tagging VLAN hopping attack, in addition to Yersinia:
![[Yersinia_Double_Tagging_VLAN_Hopping_Attack.png]]
