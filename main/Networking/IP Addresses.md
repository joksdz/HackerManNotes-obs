IP is a short for internet protocol , IP addresses lets us identify a device for a short period of time so as when we disconnect our device another device can use the same IP address later 
An **IP** address is a set of numbers that are divided into four octets. The value of each octet will summaries to be the IP address of the device on the network. This number is calculated through a technique known as [IP addressing & subnetting](https://learn.microsoft.com/en-us/troubleshoot/windows-client/networking/tcpip-addressing-and-subnetting)
`IANA` :Internet Assigned Numbers Authority (`IANA`) is responsible for assigning IPv4 and IPv6 addresses and their associated network portions

# The properties of an `IP` Address 

![[Pasted image 20240414195425.png]]

# Types of IP Addresses:

- ## Public IP:
A public IP lets us identify a device on the internet and its given by the ISP ( internet service provider) and any data that a device sends or receives will be throughout that public IP address 
- ## Private IP:
A private IP lets us identify a device within a closed network so like a home network and its used between devices to communicate with each other in that network

**Network address translation** (**NAT**) is a method that translates the private IP address into the public IP address . 
![[NAT_Concept-en.svg.png]]

# Versions Of IP Addresses 

![[Pasted image 20240414201655.png]]
## IPV4
This is the older technology and its based on a numbering system of 2^32 meaning there can be only 4.29 billion devices connected at the same time which is bad since there are much more devices than that and they keep increasing 
## IPV6 

IPv6 is a new iteration of the Internet Protocol addressing scheme to help tackle this issue. Although it is seemingly more daunting, it boasts a few benefits:

- Supports up to 2^128 of IP addresses (340 undecillion "3.4*10^38" ), resolving the issues faced with IPv4
- More efficient due to new methodologies`IPv6` is a protocol with many new features, which also has many other advantages over IPv4:


- Address self-configuration (SLAAC : Stateless Address Autoconfiguration it was designed to be a simpler and more straight-forward approach to IPv6 auto-addressing. In its current implementation as defined in RFC 4862, SLAAC does not provide DNS server addresses to hosts and that is why it is not widely adopted at the moment.)

- Multiple IPv6 addresses per interface
- Faster routing
- End-to-end encryption (IPsec)
- Data packages up to 4 GByte

An IPv6 address can look like this:

- Full IPv6: `fe80:0000:0000:0000:dd80:b1a9:6687:2d3b/64`
- Short IPv6: `fe80::dd80:b1a9:6687:2d3b/64`

An IPv6 address consists of two parts:

- `Network Prefix` (network part)
- `Interface Identifier` also called `Suffix` (host part)

The `Network Prefix` identifies the network, subnet, or address range. The `Interface Identifier` is formed from the `48-bit MAC` address (which we will discuss later) of the interface and is converted to a `64-bit address` in the process. The default prefix length is `/64`. However, other typical prefixes are `/32`, `/48`, and `/56`. If we want to use our networks, we get a shorter prefix (e.g. `/56`) than `/64` from our provider.

In RFC 5952, the aforementioned IPv6 address notation was defined:

- All alphabetical characters are always written in lower case.
- All leading zeros of a block are always omitted.
- One or more consecutive blocks of `4 zeros` (hex) are shortened by two colons (`::`).
- The shortening to two colons (`::`) may only be performed `once` starting from the left.
# Packets and frames :
Packets and frames are small pieces of data that when put together make a large piece of data or a message ,Frames are found at layer 2 (data link ) while packets are found at layer 3 (network) since there are no IP addresses at layer  2 , the process of transforming packets to frames is called encapsulation where the data related to IP addresses and layer 3 protocols is striped away 
decapsulation works the same way but in reverse so it transforms the frames to packets by adding some new information ,packets are a very efficient way of transferring data since it slices it up to small pieces making it more reliable and avoiding bottlenecking the other device , the packets structure is dependent on the type of the packet it self 
ex : let examine an internet protocol (IP) packet, the packet contains parts called headers these contain a set of info added to the original info that was sent mainly :
- time to live header : this sets an expiration time so the packets fades away and doesn't clog up the network if it didn't reach the host 
- checksum : this helps validate the integrity of the packet since any change to the data will change its value .
- source address : the  sender's IP address 
- distinction address: the host IP address 
![[pehl18l0.bmp]]
# IP Packets

An Internet Protocol (IP) packet is the data area used by the network layer of the Open Systems Interconnection [[OSI_model]] to transmit data from one computer to another. It consists of a header and the payload, the actual payload data.

We can also think of the IP packet as a letter sent in an envelope. The envelope contains the header, which includes information on the sender and the recipient, as well as instructions for routing the letter, i.e., via which post offices the letter should be sent. The letter itself is the payload, the actual payload data.

## IP header

The header of an IP packet contains several fields that have important information.

<table class="table table-striped text-left">
<thead>
<tr>
<th><strong>Field</strong></th>
<th><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td><code>Version</code></td>
<td>Indicates which version of the IP protocol is being used</td>
</tr>
<tr>
<td><code>Internet Header Length</code></td>
<td>Indicates the size of the header in 32-bit words</td>
</tr>
<tr>
<td><code>Class of Service</code></td>
<td>Means how important the transmission of the data is</td>
</tr>
<tr>
<td><code>Total length</code></td>
<td>Specifies the total length of the packet in bytes</td>
</tr>
<tr>
<td><code>Identification (ID)</code></td>
<td>Is used to identify fragments of the packet when fragmented into smaller parts</td>
</tr>
<tr>
<td><code>Flags</code></td>
<td>Used to indicate fragmentation</td>
</tr>
<tr>
<td><code>Fragment Offset</code></td>
<td>Indicates where the current fragment is placed in the packet</td>
</tr>
<tr>
<td><code>Time to Live</code></td>
<td>Specifies how long the packet may remain on the network</td>
</tr>
<tr>
<td><code>Protocol</code></td>
<td>Specifies which protocol is used to transmit the data, such as TCP or UDP</td>
</tr>
<tr>
<td><code>Checksum</code></td>
<td>Is used to detect errors in the header</td>
</tr>
<tr>
<td><code>Source/Destination</code></td>
<td>Indicate where the packet was sent from and where it is being sent to</td>
</tr>
<tr>
<td><code>Options</code></td>
<td>Contain optional information for routing</td>
</tr>
<tr>
<td><code>Padding</code></td>
<td>Pads the packet to a full word length</td>
</tr>
</tbody>
</table>

We may see a computer with multiple IP addresses in different networks. Here we should pay attention to the IP ID field. It is used to identify fragments of an IP packet when fragmented into smaller parts. It is a 16-bit field with a unique number ranging from 0-65535.

If a computer has multiple IP addresses, the IP ID field will be different for each packet sent from the computer but very similar. In TCPdump, the network traffic might look something like this:

### Network Sniffing
<div class="window_content">
                      <div class="window_top">
                          <span class="window_dot bg-danger"></span>
                          <span class="window_dot bg-warning"></span>
                          <span class="window_dot bg-success"></span>
                          <span class="window_title">TCP/UDP Connections</span>
                      </div>
                  <pre class=" language-shell-session" style="line-height: 0px;"><code class=" language-shell-session"><span class="token output">IP 10.129.1.100.5060 &gt; 10.129.1.1.5060: SIP, length: 1329, id 1337
IP 10.129.1.100.5060 &gt; 10.129.1.1.5060: SIP, length: 1329, id 1338
IP 10.129.1.100.5060 &gt; 10.129.1.1.5060: SIP, length: 1329, id 1339
IP 10.129.2.200.5060 &gt; 10.129.1.1.5060: SIP, length: 1329, id 1340
IP 10.129.2.200.5060 &gt; 10.129.1.1.5060: SIP, length: 1329, id 1341
IP 10.129.2.200.5060 &gt; 10.129.1.1.5060: SIP, length: 1329, id 1342
</span></code></pre></div>
as we can see there are two IP addresses sending to the same location (10.129.1.1.5060) even tho their IDs are different they are continues which mean they are likely to be from the same sender .

## IP Record-Route Field

The Record-Route field in the IP header also records the route to a destination device. When the destination device sends back the ICMP(==internet control message protocol==) Echo Reply packet, the IP addresses of all devices that pass through the packet are listed in the Record-Route field of the IP header. This happens when we use the following command, for example:

```
TGDEV@htb[/htb]$ ping -c 1 -R 10.129.143.158

PING 10.129.143.158 (10.129.143.158) 56(124) bytes of data.
64 bytes from 10.129.143.158: icmp_seq=1 ttl=63 time=11.7 ms
RR: 10.10.14.38
        10.129.0.1
        10.129.143.158
        10.129.143.158
        10.10.14.1
        10.10.14.38


--- 10.129.143.158 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 11.688/11.688/11.688/0.000 ms
```

The output indicates that a ping request was sent and a response was received from the destination device and also shows the Record-Route field in the IP header of the ICMP Echo Request packet. The Record Route field contains the IP addresses of all devices that passed through the ICMP Echo Request packet on the way to the destination device. In this case, the Record-Route field contains the IP addresses:
<table class="table table-striped text-left">
<thead>
<tr>
<th></th>
<th></th>
<th></th>
</tr>
</thead>
<tbody>
<tr>
<td>10.10.14.38</td>
<td>10.129.0.1</td>
<td>10.129.143.158</td>
</tr>
<tr>
<td>10.129.143.158</td>
<td>10.10.14.1</td>
<td>10.10.14.38</td>
</tr>
</tbody>
</table>

The traceroute tool can also be used to trace the route to a destination more accurately, which uses the TCP timeout method to determine when the route has been fully traced.

- We send a TCP SYN packet to the destination device with a TTL(Time-Of-Life) of 1 in the IP header.

When the TCP SYN packet with a TTL greater than 1 reaches a router, the value of the TTL is decreased by 1, and the packet is forwarded to the next device. If the TCP SYN packet with a TTL of 1 reaches a router, the packet is dropped, and the router sends an ICMP Time-Exceeded packet back to us.
ex :
// 
192.168.1.11 , TTL = 3    ---> 192.168.1.12 , TTL = 2  ---> 192.168.1.20 ,TTL = 1  ---> 10.12.123.2 , ICMP time-exceeded get returned back to 192.168.1.11
192.168.1.23 , TTL = 1  ---> 192.124.2,212 ICMP returns Time-exceeded 
//

- We receive the ICMP Time-Exceeded packet and note the IP address of the router that sent the packet.

- After that, we send another TCP SYN packet to the destination, increasing the TTL by 1.

The process repeats until the TCP SYN packet reaches the destination host and receives a TCP SYN/ACK or a TCP RST response from the target. Once we receive a response from the destination device, we know that we have traced the route to the destination and ended the traceroute process.
## IP Payload(Data)

The payload (also referred to as IP Data) is the actual payload of the packet. It contains the data from various protocols, such as TCP or UDP, that are being transmitted, just like the contents of the letter in the envelope.
## TCP
TCP packets, also known as segments, are divided into several sections called headers and payloads. The TCP segments are wrapped in the sent IP packet.

The header contains several fields that contain important information. ``The source port`` indicates the computer from which the packet was sent. ``The destination port`` indicates to which computer the packet is sent. ``The sequence number`` indicates the order in which the data was sent. ``The confirmation number`` is used to confirm that all data was received successfully. ``The control flags`` indicate whether the packet marks the end of a message, whether it is an acknowledgment that data has been received, or whether it contains a request to repeat data. ``The window size``indicates how much data the receiver can receive. ``The checksum is used to detect errors in the header and payload. The Urgent Pointer alerts the receiver that important data is in the payload.

The payload is the actual payload of the packet and contains the data that is being transmitted, just like the content of a conversation between two people.
## UDP

UDP transfers datagrams (small data packets) between two hosts. It is a connectionless protocol, meaning it does not need to establish a connection between the sender and the receiver before sending data. Instead, the data is sent directly to the target host without any prior connection.

When traceroute is used with UDP, we will receive a Destination Unreachable and Port Unreachable message when the UDP datagram packet reaches the target device. Generally, UDP packets are sent using traceroute on Unix hosts.

# Blind Spoofing

Blind spoofing, is a method of data manipulation attack in which an attacker sends false information on a network without seeing the actual responses sent back by the target devices. It involves manipulating the IP header field to indicate false source and destination addresses. For example, we send a TCP packet to the target host with false source and destination port numbers and a false Initial Sequence Number (ISN). The ISN is a field in the TCP header that is used to specify the sequence number of the first TCP packet in a connection. The ISN is set by the sender of a TCP packet and sent to the receiver in the TCP header of the first packet. This can cause the target host to establish a connection with us without receiving the connection.

This attack is commonly used to disrupt the integrity of network connections or to break connections between network devices. It can also be used to monitor network traffic or to intercept information sent by network devices.
# Subnetting 
it mean splitting up a network into smaller networks to help us send the correct amount of data to each one its mostly used in business ![[what-is-a-subnet-how-subnetting-works-2.webp]]
the host address range is (1,254)
the default gateway: its has a special address  mostly 1 or 254 and its given to a device that is capable of sending info to another network (a ``wifi router `` for example 192.168.1.1 to change configuration )  
network address: its used to identify the network existence 192.168.1.0
a lot more info here : [info](https://academy.hackthebox.com/module/34/section/306)

# DHCP
Dynamic Host Configuration Protocol  or simply DHCP is a protocol that allows a device to have an IP address automatically without the admin having to set it manually
## How does is work ?
when a device connects to a network it sends a DHCP discover wish is  a message to check if there is any DHCP server in the network , if it finds one the DHCP server then sends a DHCP offer which is an IP address that the device can use ,after that the device confirms the offer by sending a DHCP request ,and lastly the server confirms the IP (DHCP ACK*) and now that device owns the IP and can start using it in the network 
**DHCPv6** (The Dynamic Host Configuration Protocol version 6) - The most widely adopted protocol for dynamically assigning addresses to hosts. Requires a DHCP server on the network and additional configuration.

*ACK: a short for Acknowledge ![[Pasted image 20240421113032.jpg]]


# TCP/IP (the three way handshake):

TCP : (transmition control protocol ) is one of the most use networking protocols (rules )
much like the [[OSI_model]]
it consists of 4 layers :
1 - application layer 
2 - Transport 
3 -internet 
4 - network interface 
at each layer the more information will be added to the packet (encapsulation)
TCP is a connection-based which means that it need to establish a connection between both devices  before it start sending the data to make sure that every packet that is sent will be received by the host , (for more about the advantages and disadvantages of TCP you can look the up in the [[OSI_model]] layer 4)
![[Pasted image 20240822200808.png]]
The TCP packet contains these following headers [Img](obsidian://open?vault=TryHackMe_Notes&file=Pasted%20image%2020240526185059.png)
![[Pasted image 20240526185059.png]]

##  the three way handshake :
its a method to establish a connection between 2 devices using special messages :
- SYN message: the SYN message is a simple packet sent by the client and it's used to initiate syncing and a connection between  the two devices 
- ACK/SYN: this message is sent by the receiver of the first message to acknowledge the synchronization .
- ACK : can be sent by both of the devices to acknowledge that the messages were sent 
then : 
- DATA : the data it self (the img , file ......)
- FIN : this is used to terminate the connection between the two devices cleanly 
- RST : this message is send suddenly to close connection ,its used when an error happens  [img](obsidian://open?vault=TryHackMe_Notes&file=images%2FPasted%20image%2020240526190745.png)
![[Pasted image 20240526190745.png]]
## TCP closing a connection :
TCP closes the connection when the data is fully sent or one of the devices disconnects 
its best practice to close TCP as fast as possible since it uses a lot of system resource (compared to UDP, and other protocols) 
finally the client send a FIN message to the server which ACK it 

# UDP/IP :
UDP : user Datagram protocol 
unlike TCP, UDP is stateless so it doesn't require a connection to be made which leads to the loss of data (it doesn't use the three way handshake and no syncing is made )
``for more about the advantages and disadvantages of UDP check the ``[[OSI_model]] ``layer 4``
UDP packets are much simpler than TCP packets : [img](obsidian://open?vault=TryHackMe_Notes&file=Pasted%20image%2020240526193250.png)
![[Pasted image 20240526193250.png]]
the only messages that are exchanged in a UDP connection are : request and respond (data)
## CIDR

`Classless Inter-Domain Routing` (`CIDR`) is a method of representation and replaces the fixed assignment between IPv4 address and network classes (A, B, C, D, E). The division is based on the subnet mask or the so-called `CIDR suffix`, which allows the bitwise division of the IPv4 address space and thus into `subnets` of any size. The `CIDR suffix` indicates how many bits from the beginning of the IPv4 address belong to the network. It is a notation that represents the `subnet mask` by specifying the number of `1`-bits in the subnet mask.

Let us stick to the following IPv4 address and subnet mask as an example:

- IPv4 Address: `192.168.10.39`
    
- Subnet mask: `255.255.255.0`
    

Now the whole representation of the IPv4 address and the subnet mask would look like this:

- CIDR: `192.168.10.39/24`

The CIDR suffix is, therefore, the sum of all ones in the subnet mask.