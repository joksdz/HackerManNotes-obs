(open system interconnection Model ) as the main model that is used for networking , it explains how data is sent , received , and interpreted through network devices 
it consists of 7 layers from  7 to 1 throughout each layer a lot of processes happen and pieces of information is added to the data (encapsulation)
unit exchange : APDU -application Protocol Data unit 
![[Pasted image 20240511184625.png]]
![[Pasted image 20240512220755.png]]
# Layer 7: Application 
every thing that has to do with human interactions like the GUI (graphical user interface) which decides how the data is sent and received ,protocols such as DNS ( Domain Name System) are also included in this layer ![[application-layer.webp]]

# Layer 6: presentation 
This layer acts as a translator to and from layer 7 since developers make apps differently we have to make some standards ,for example when you send an email through Gmail to some one who uses Yahoo mail he will still get the same email address (your name/email address) 
this layer includes security features such as data encryption: HTTPS (Hypertext Transfer Protocol Secure ) shows up at this layer .
unit exchange : PPDU - presentation protocol data unit 
![[Pasted image 20240512220554.jpg]]
# Layer 5: session 
This is layer creates the connection between devices through the network and thus a session while the connection is active ,the session layer sync the two computers to ensure they are on the same page before data is sent or received , to send the data the session layer divides it into small chunks called packets these chunks help ensure the data don't get lost fully if the connection is lost , data cannot travel over different session but only across each session
unit exchange : SPDU -session protocol data unit 
![[Pasted image 20240512221006.png]]
# Layer 4 : transport 
this layer handles the transport of data on the network it follows one of two protocols : 
- TCP (Transmission Control Protocol )
- UDP (User Datagram Protocol )
TCP is designed with reliability in mind it insure that the packets are fully sent and reassembled in the same order and it incorporates error checking 
## ==Advantages== :
 - Guarantees the accuracy of data 
 - syncs the devices to make sure they don't get flooded with data 
 - preformes a lot a process for reliability (error correction )
## ==Disadvantages== : 
- need a constant and a reliable connection , if the packets fails to be sent the whole data cant be used .
- slow connection can bottleneck the other device 
- its significantly slower than UDP since it has to do error correction
ex : its used for file sharing and emails as well as internet browsing 

UDP is very fast but also unreliable  since it doesn't use error correction and it misses a lot of features that TCP uses it doesn't sync between devices and doesn't guarantee that data was sent fully 
## ==Advantages== :
- UDP is much faster than TCP 
- it leaves the application layer to decide how fast the packets are sent 
- it doesn't keep a continuous connection to the device like TCP
## ==Disadvantages== :
- UDP doesn't care if the data is received fully
- its quit flexible since it lets the application layer decides how fast the packets go 
- unstable connection = GG  your F up 
ex: video streaming , small data ([DHCP](obsidian://open?vault=TryHackMe_Notes&file=main%2FNetworking%2FIP%20Addresses) ,[[ARP]] protocols )
unit exchange : segment 
![[Pasted image 20240513162708.png]]
# layer 3: Network 
in this layer routing and the reassembly of packets to form data happens ,routing finds the optimal way in which packets should be sent using protocols such as OSPF(Open Shortest Path First ) and RIP (Routing Information Protocol) this happens based on some factors : 
- what path is the shortest ? (has the less amount of devices that send packets through ) 
- what path is the most reliable ? (checks if packets have been lost on this path)
- which path have the fastest physical connection ? (Fiber vs coper )
at this layer every thing is delt with through  [[IP addresses]] and it all happens through routers 
unit exchange : packet 
![[Pasted image 20240513164900.jpg]]
The most used protocols on this layer are:

- `IPv4` / `IPv6` : [[IP Addresses]]
- `IPsec`: In computing, Internet Protocol Security is a secure network protocol suite that authenticates and encrypts packets of data to provide secure encrypted communication between two computers over an Internet Protocol network

- `ICMP` : Core protocol of the Internet Protocol suite, mainly used on IPv4 networks to indicate error messages in network operations

- `IGMP`: The Internet Group Management Protocol is a communications protocol used by hosts and adjacent routers on IPv4 networks to establish multicast group memberships. IGMP is an integral part of IP multicast and allows the network to direct multicast transmissions only to hosts that have requested them. IGMP can be used for one-to-many networking applications such as online streaming video and gaming, and allows more efficient use of resources when supporting these types of applications. IGMP is used on IPv4 networks. Multicast management on IPv6 networks is handled by Multicast Listener Discovery which is a part of ICMPv6 in contrast to IGMP's bare IP encapsulation

- `RIP` :The Routing Information Protocol is one of the oldest distance-vector routing protocols which employs the hop count as a routing metric. RIP prevents routing loops by implementing a limit on the number of hops allowed in a path from source to destination. The largest number of hops allowed for RIP is 15, which limits the size of networks that RIP can support. RIP implements the split horizon, route poisoning, and holddown mechanisms to prevent incorrect routing information from being propagated. In RIPv1 routers broadcast updates with their routing table every 30 seconds. In the early deployments, routing tables were small enough that the traffic was not significant. As networks grew in size, however, it became evident there could be a massive traffic burst every 30 seconds, even if the routers had been initialized at random times

- `OSPF`: Open Shortest Path First is a routing protocol for Internet Protocol networks. It uses a link state routing algorithm and falls into the group of interior gateway protocols, operating within a single autonomous system. OSPF gathers link state information from available routers and constructs a topology map of the network. The topology is presented as a routing table to the internet layer for routing packets by their destination IP address. OSPF supports Internet Protocol version 4 and Internet Protocol version 6 networks and is widely used in large enterprise networks. IS-IS, another LSR-based protocol, is more common in large service provider networks. Originally designed in the 1980s, OSPF version 2 is defined in RFC 2328. The updates for IPv6 are specified as OSPF version 3 in RFC 5340. OSPF supports the Classless Inter-Domain Routing addressing model

# Layer 2 : Data link 
this layer focuses on the physical addressing , it receives the packets from the network layer(IPs ) and add the [[MAC Addresses]] to it ,these are found in the Network Interface Card (NIC) inside every network enabled device and they are bunt on it so they cant be changed (except spoofed )
its also the job of the data link layer to choose the best format for the data to be sent .
unit exchange : Frame  
![[Pasted image 20240513170511.jpg]]
# Layer 1 : Physical 
this layer is basically the physical connections that make the network like ethernet cables here the data traves as binary numbers (electrical signals) . it also depends on [[Network topologies]]
unit exchange : bit 
![[Pasted image 20240513171018.jpg]]

# Packets and frames :
Packets and frames are small pieces of data that when put together make a large piece of data or a message ,Frames are found at layer 2 (data link ) while packets are found at layer 3 (network) since there are no IP addresses at layer  2 , the process of transforming packets to frames is called encapsulation where the data related to IP addresses and layer 3 protocols is striped away 
decapsulation works the same way but in reverse so it transforms the frames to packets by adding some new information ,packets are a very efficient way of transferring data since it slices it up to small pieces making it more reliable and avoiding bottlenecking the other device , the packets structure is dependent on the type of the packet it self 
ex : let examine an internet protocol (IP) packet, the packet contains parts called headers these contain a set of info added to the original info that was sent mainly :
- time to live header : this sets an expiration time so the packets fades away and doesn't clog up the network if it didn't reach the host 
- checksum : this helps validate the integrity of the packet since any change to the data will change its value .
- source address : the  sender's IP address 
- distinction address: the host IP address 
![[pehl18l0.bmp]]