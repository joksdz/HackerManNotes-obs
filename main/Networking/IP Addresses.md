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
it consists of 4 layers :
1 - application layer 
2 - Transport 
3 -internet 
4 - network interface 
at each layer the more information will be added to the packet (encapsulation)
TCP is a connection-based which means that it need to establish a connection between both devices  before it start sending the data to make sure that every packet that is sent will be received by the host , (for more about the advantages and disadvantages of TCP you can look the up in the [[OSI_model]] layer 4)
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