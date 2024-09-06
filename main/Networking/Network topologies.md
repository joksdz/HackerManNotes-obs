# meaning 
it refers to the way that data travels between devices in a network 

# Types 
## star topology 

this his the most common topology , it uses a special middle man like a switch or a hub to connect devices between each other , although switches are mostly used since the hub transmits data to all the devices in the network even if the address was specified 

![[Pasted image 20240419161105.png]]

## Bus topology 
the bus topology is a very cost efficient topology since it only need a network cable that all the devices are linked to , however that would make transferring data much harder because all of the data is going in the same rout at same time and its much harder to troubleshoot
![[Pasted image 20240419161356.jpg]]
## Ring topology 
(aka token topology ) its a topology were devices are connected in a loop with each other in a circle and if a device wants to send data it will have to go through another device making it very insecure and very slow because if your data is going through another device it has to wait for that device to send its own data 
![[Pasted image 20240419161330.jpg]]
# What's a switch ? 
a Switch is a network device that connects ==devices== to each other through ethernet cables it comes with many port: 4, 8,16,32, 64

# What's a router?
a router is a device that connects ==networks== (switches) to each other and that how the internet flows ![[Pasted image 20240419165102.png]]

## Ethernet frame 
![[Pasted image 20240906221804.png]]
``this image shows what is in the a single ethernet frame  with the amount of bytes in each section 
the first section is the preamble : this makes sure that the receiver is in sync with the frames coming 
the second section  start frame delimiter: this tells the receiver that what's after it is the info sent by the sender 
third section the destination mac address 
forth is the source (sender) mac address 
fifth usually the length of the data being sent and could be sometimes the type 
sixth is the data it self (payload)
seventh is the frame check sequence this help to check if the frames arrived consecutively its used for error checking 
the fields of the Internet Protocol version 6 (IPv6) packet identify the source of the packet and its destination
![[Pasted image 20240906223320.png]]
# Wireless Networks

Wireless networks are computer networks that use wireless data connections between network nodes. These networks allow devices such as laptops, smartphones, and tablets to communicate with each other and the Internet without needing physical connections such as cables.

Wireless networks use radio frequency (RF) technology to transmit data between devices. Each device on a wireless network has a wireless adapter that converts data into RF signals and sends them over the air. Other devices on the network receive these signals with their own wireless adapters, and the data is then converted back into a usable form. Those can operate over various ranges, depending on the technology used. For example, a local area network (LAN) that covers a small area, such as a home or small office, might use a wireless technology called WiFi, which has a range of a few hundred feet. On the other hand, a wireless wide area network (WWAN) might use mobile telecommunication technology such as cellular data (3G, 4G LTE, 5G), which can cover a much larger area, such as an entire city or region.

Communication between devices occurs over RF in the 2.4 GHz or 5 GHz bands in a WiFi network. When a device, like a laptop, wants to send data over the network, it first communicates with the Wireless Access Point (WAP) to request permission to transmit. The WAP is a central device, like a router, that connects the wireless network to a wired network and controls access to the network. Once the WAP grants permission, the transmitting device sends the data as RF signals, which are received by the wireless adapters of other devices on the network. The data is then converted back into a usable form and passed on to the appropriate application or system.

The strength of the RF signal and the distance it can travel are influenced by factors such as the transmitter's power, the presence of obstacles, and the density of RF noise in the environment. So, to ensure reliable communication, WiFi networks use techniques such as spread spectrum transmission and error correction to overcome these challenges.

## Wifi Connection

The device must also be configured with the correct network settings, such as the network name / Service Set Identifier (SSID) and password. So, to connect to the router, the laptop uses a wireless networking protocol called ``IEEE 802.11`` This protocol defines the technical details of how wireless devices communicate with each other and with WAPs. When a device wants to join a WiFi network, it sends a request to the WAP to initiate the connection process. This request is known as a connection request frame or association request and is sent using the ``IEEE 802.11`` wireless networking protocol. The connection request frame contains various fields of information, including the following but not limited to:
	
MAC address :	A unique identifier for the device's wireless adapter.
SSID :	The network name, also known as the Service Set Identifier of the WiFi network.
Supported data rates :	A list of the data rates the device can communicate.
Supported channels : A list of the channels (frequencies) on which the device can communicate.
Supported security protocols :	A list of the security protocols that the device is capable of using, such as WPA2/WPA3. (WPA : wifi protected access )
The device then uses this information to configure its wireless adapter and connect to the WAP. Once the connection is established, the device can communicate with the WAP and other network devices. It can also access the Internet and other online resources through the WAP, which acts as a gateway to the wired network. However, the SSID can be hidden by disabling broadcasting. That means that devices that search for that specific WAP will not be able to identify its SSID. Nevertheless, the SSID can still be found in the authentication packet.

In addition to the IEEE 802.11 protocol, other networking protocols and technologies may also be used, like TCP/IP, DHCP, and WPA2, in a WiFi network to perform tasks such as assigning IP addresses to devices, routing traffic between devices, and providing security.


![Penjelasan Singkat Tentang Kode 802.11 a/b/g/n/ac/ad Pada Perangkat ...](https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fwww.siranap.com%2Fwp-content%2Fuploads%2F2016%2F08%2Fieee-802-11-wireless-lan.png&f=1&nofb=1&ipt=adae03713fc0eeeda32800149260df3be536c606202ddfa1e27fb66296010c2e&ipo=images)



## WEP Challenge-Response Handshake
WEP : wired equivalent privacy / encryption protocol 

The challenge-response handshake is a process to establish a secure connection between a WAP and a client device in a wireless network that uses the WEP security protocol. This involves exchanging packets between the WAP and the client device to authenticate the device and establish a secure connection.
- client : sends a request packet to WAP , to requesting accesses 
- WAP : sends a response packet that includes a challenge string (like asking it what's the password)
- client : sends the challenge solution 
- WAP: after validating it sends an authentication response packet back to the client 

Nevertheless, some packets can get lost, so the so-called CRC checksum has been integrated. Cyclic Redundancy Check (CRC) is an error-detection mechanism used in the WEP protocol to protect against data corruption in wireless communications. A CRC value is calculated for each packet transmitted over the wireless network based on the packet's data. It is used to verify the integrity of the data. When the destination device receives the packet, the CRC value is recalculated and compared to the original value. If the values match, the data has been transmitted successfully without any errors. However, if the values do not match, the data has been corrupted and needs to be retransmitted.

The design of the CRC mechanism has a flaw that allows us to decrypt a single packet without knowing the encryption key. This is because the CRC value is calculated using the plaintext data in the packet rather than the encrypted data. In WEP, the CRC value is included in the packet header along with the encrypted data. When the destination device receives the packet, the CRC value is recalculated and compared to the original one to ensure that the data has been transmitted successfully without any errors. However, we can use the CRC to determine the plaintext data in the packet, even if the data is encrypted.

## Security Features

WiFi networks have several security features to protect against unauthorized access and ensure the privacy and integrity of data transmitted over the network. Some of the leading security features include but are not limited to:

    Encryption
    Access Control
    Firewall

### Encryption

We can use various encryption algorithms to protect the confidentiality of data transmitted over wireless networks. The most common encryption algorithms in WiFi networks are Wired Equivalent Privacy (WEP), WiFi Protected Access 2 (WPA2), and WiFi Protected Access 3 (WPA3).

![[wpa2-3843447619.png]]
[more about WPA](https://www.securew2.com/blog/wpa3-vs-wpa2 )
[,](https://nordvpn.com/blog/wep-vs-wpa-vs-wpa2-vs-wpa3/)


### Access Control

WiFi networks are configured by default to allow authorized devices to join the network using specific authentication methods. However, these methods can be changed by requiring a password or a unique identifier (such as a MAC address) to identify authorized devices.
### Firewall

A firewall is a security system that controls incoming and outgoing network traffic based on predetermined security rules. For example, WiFi routers often have built-in firewalls that can block incoming traffic from the Internet and protect against various types of cyber threats.
![[Firewall-types.jpg]]
check  [[Network security]] for more info 



## NFC 
Near-field communication , NFC devices use electromagnetic fields in order to transmit data , it requires a really short distance between the sender and receiver usually about few centimeters away , its used a lot in cashier registry machines so the buyer can use his cellphone to pay , hotel tags also use NFC to access rooms . 

## Bluetooth 

Bluetooth is a low-power, shorter range wireless technology that is intended to replace wired connectivity for accessories such as speakers, headphones, and microphones. Bluetooth can also be used to connect a smartwatch to a smartphone. Because Bluetooth technology can be used to transmit both data and voice, it can be used to create small local networks. Bluetooth is wireless technology that allows devices to communicate over short distances. Multiple devices can be connected at the same time with Bluetooth.
## GPS 
**Global Positioning System**

The GPS uses satellites to transmit signals that cover the globe. The smartphone can receive these signals and calculate the phone’s location to an accuracy of within 10 meters.


this shows where wireless tech exist on the electromagnetic spectrum :
![[Pasted image 20240820142601.png]]