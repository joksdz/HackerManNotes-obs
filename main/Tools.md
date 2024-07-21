## Ping 
Ping is one of the most fundamental network tools available to us. Ping uses ICMP (Internet Control Message Protocol) packets to determine the performance of a connection between devices, for example, if the connection exists or is reliable.
The time taken for ICMP packets travelling between devices is measured by ping, such as in the screenshot below. This measuring is done using ICMP's echo packet and then ICMP's echo reply from the target device.
Pings can be performed against devices on a network, such as your home network or resources like websites. This tool can be easily used and comes installed on Operating Systems (OSs) such as Linux and Windows. The syntax to do a simple ping is `ping IP address or website URL`. Let's see this in action in the screenshot below.
![[Pasted image 20240414205453.png]]


# ``macchange
https://github.com/alobbs/macchanger

GNU MAC Changer is an utility that makes the maniputation of MAC
addresses of network interfaces easier.

for more about mac spoofing check : [[MAC Addresses]]

# ``nmcli

**nmcli** is a command-line tool for controlling NetworkManager and getting its status. It is not meant as a replacement of _nm-applet_ or other similar clients. Rather it's a complementary utility to these programs. The main _nmcli_'s usage is on servers, headless machines or just for power users who prefer the command line.
# Wireshark 
https://www.wireshark.org/
About Wireshark

Wireshark is the world's foremost network protocol analyzer. It lets you see what's happening on your network at a microscopic level. It is the de facto (and often de jure) standard across many industries and educational institutions.

Wireshark development thrives thanks to the contributions of networking experts across the globe. It is the continuation of a project that started in 1998.
## Features

   - Deep inspection of hundreds of protocols, with more being added all the time
   - Live capture and offline analysis
  - Standard three-pane packet browser
- Multi-platform: Runs on Windows, Linux, OS X, FreeBSD, NetBSD, and many others
    Captured network data can be browsed via a GUI, or via the TTY-mode TShark utility
    The most powerful display filters in the industry
    Rich VoIP analysis
    Read/write many different capture file formats: tcpdump (libpcap), Pcap NG, Catapult DCT2000, Cisco Secure IDS iplog, Microsoft Network Monitor, Network General Sniffer® (compressed and uncompressed), Sniffer® Pro, and NetXray®, Network Instruments Observer, NetScreen snoop, Novell LANalyzer, RADCOM WAN/LAN Analyzer, Shomiti/Finisar Surveyor, Tektronix K12xx, Visual Networks Visual UpTime, WildPackets EtherPeek/TokenPeek/AiroPeek, and many others
    Capture files compressed with gzip can be decompressed on the fly
    Live data can be read from Ethernet, IEEE 802.11, PPP/HDLC, ATM, Bluetooth, USB, Token Ring, Frame Relay, FDDI, and others (depending on your platform)
    Decryption support for many protocols, including IPsec, ISAKMP, Kerberos, SNMPv3, SSL/TLS, WEP, and WPA/WPA2
    Coloring rules can be applied to the packet list for quick, intuitive analysis
    Output can be exported to XML, PostScript®, CSV, or plain text

# Yrsinia
Yrsinia is a low-level protocol attack tool useful for penetration testing. It is capable of many diverse attacks over multiple protocols, such as becoming the root role in the Spanning Tree (Spanning Tree Protocol), creating virtual CDP (Cisco Discovery Protocol) neighbors, becoming the active router in a HSRP (Hot Standby Router Protocol) scenario, faking DHCP replies, and other low-level attacks. 
https://github.com/tomac/yersinia
# Scapy


Section author: Philippe Biondi  phil at secdev.org 

Scapy is a Python program that enables the user to send, sniff, dissect and forge network packets. This capability allows construction of tools that can probe, scan or attack networks.

In other words, Scapy is a powerful interactive packet manipulation program. It is able to forge or decode packets of a wide number of protocols, send them on the wire, capture them, match requests and replies, and much more. Scapy can easily handle most classical tasks like scanning, tracerouting, probing, unit tests, attacks or network discovery. It can replace hping, arpspoof, arp-sk, arping, p0f and even some parts of Nmap, tcpdump, and tshark.

Scapy also performs very well on a lot of other specific tasks that most other tools can’t handle, like sending invalid frames, injecting your own 802.11 frames, combining techniques (VLAN hopping+ARP cache poisoning, VOIP decoding on WEP encrypted channel, …), etc.

The idea is simple. Scapy mainly does two things: sending packets and receiving answers. You define a set of packets, it sends them, receives answers, matches requests with answers and returns a list of packet couples (request, answer) and a list of unmatched packets. This has the big advantage over tools like Nmap or hping that an answer is not reduced to open, closed, or filtered, but is the whole packet.
https://scapy.readthedocs.io/en/latest/index.html