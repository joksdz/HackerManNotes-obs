# Virtual Private Networks

---

A `Virtual Private Network` (`VPN`) is a technology that allows a secure and encrypted connection between a private network and a remote device. This allows the remote machine to access the private network directly, providing secure and confidential access to the network's resources and services. For example, an administrator from another location has to manage the internal servers so that the employees can continue to use the internal services. Many companies limit servers' access, so clients can only reach those servers from the local network. This is where VPN comes into play, where the administrator connects to the VPN server via the internet, authenticates himself, and thus creates an encrypted tunnel so that others cannot read the data transfer. In addition, the administrator's computer is also assigned a local (internal) IP address through which he can access and manage the internal servers. Administrators commonly use VPNs to provide secure and cost-effective remote access to a company's network. VPN typically uses the ports `TCP/1723` for [Point-to-Point Tunneling Protocol](https://www.lifewire.com/pptp-point-to-point-tunneling-protocol-818182) `PPTP` VPN connections and `UDP/500` for [IKEv1](https://www.cisco.com/c/en/us/support/docs/security-vpn/ipsec-negotiation-ike-protocols/217432-understand-ipsec-ikev1-protocol.html) and [IKEv2](https://nordvpn.com/blog/ikev2ipsec/) VPN connections. 
![[what-is-a-vpn-01.jpg]]

Moreover, we can use VPNs to connect multiple remote locations, such as branch offices, into a single private network, making it easier to manage and access network resources. However, several components and requirements are necessary for a VPN to work:

| `VPN Client`     | This is installed on the remote device and is used to establish and maintain a VPN connection with the VPN server. For example, this could be an OpenVPN client.        |
| ---------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `VPN Server`     | This is a computer or network device responsible for accepting VPN connections from VPN clients and routing traffic between the VPN clients and the private network.    |
| `Encryption`     | VPN connections are encrypted using a variety of encryption algorithms and protocols, such as AES and IPsec, to secure the connection and protect the transmitted data. |
| `Authentication` | The VPN server and client must authenticate each other using a shared secret, certificate, or another authentication method to establish a secure connection.           |
The VPN client and server use these ports to establish and maintain the VPN connection. At the TCP/IP layer, a VPN connection typically uses the [Encapsulating Security Payload (ESP)](https://www.ibm.com/docs/en/i/7.4?topic=protocols-encapsulating-security-payload) protocol to encrypt and authenticate the VPN traffic. This allows the VPN client and server to exchange data over the public internet securely.

## IPsec

Internet Protocol Security (IPsec) is a suit of network security protocols that provides encryption and authentication for internet communications. It is a powerful and widely-used security protocol that provides encryption and authentication for internet communications and works by encrypting the data payload of each IP packet and adding an authentication header (AH), which is used to verify the integrity and authenticity of the packet. IPsec uses a combination of two protocols to provide encryption and authentication:

- Authentication Header (AH): This protocol provides integrity and authenticity for IP packets but does not provide encryption. It adds an authentication header to each IP packet, which contains a cryptographic checksum that can be used to verify that the packet has not been tampered with.

- Encapsulating Security Payload (ESP): This protocol provides encryption and optional authentication for IP packets. It encrypts the data payload of each IP packet and optionally adds an authentication header, similar to AH.

IPsec can be used in two modes.


| Transport Mode | In this mode, IPsec encrypts and authenticates the data payload of each IP packet but does not encrypt the IP header. This is typically used to secure end-to-end communication between two hosts. |
| -------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Tunnel Mode    | With this mode, IPsec encrypts and authenticates the entire IP packet, including the IP header. This is typically used to create a VPN tunnel between two networks.                                |
For example, an administrator could place a firewall in between. In order to facilitate IPsec VPN traffic from a VPN client outside a firewall to a VPN server inside, the firewall would need to allow the following protocols:


| protocol                             | port                                     | description                                                                                                                                                                                                                                                                                               |
| ------------------------------------ | ---------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Internet Protocol (IP)               | UDP/50-51                                | This is the primary protocol that provides the foundation for all internet communication. It is used to route packets of data between the VPN client and the VPN server.                                                                                                                                  |
| `Internet Key Exchange` (`IKE`)      | UDP/500                                  | iKE is a protocol that is used to establish and maintain secure communication between the VPN client and the VPN server. It is based on the ~Diffie-Hellman key exchange algorithm, and it is used to negotiate and establish shared secret keys that can be used to encrypt and decrypt the VPN traffic. |
| Encapsulating Security Payload (ESP) | `Encapsulating Security Payload` (`ESP`) | ESP is also a protocol that provides encryption and authentication for IP datagrams. It is used to encrypt the VPN traffic between the VPN client and the VPN server, using the keys that were negotiated with IKE.                                                                                       |


Point-to-Point Tunneling Protocol (PPTP) is a network protocol that enables the creation of VPNs by establishing a secure tunnel between the VPN client and server, encapsulating the data transmitted within this tunnel. Originally an extension of the Point-to-Point Protocol (PPP), PPTP is supported by many operating systems.

However, due to its known vulnerabilities, PPTP is no longer considered secure. It can tunnel protocols such as IP, IPX, or NetBEUI via IP, but has been largely replaced by more secure VPN protocols like L2TP/IPsec, IPsec/IKEv2, and OpenVPN. Since 2012, the use of PPTP has declined because its authentication method, MSCHAPv2, employs the outdated DES encryption, which can be easily cracked with specialized hardware.

## IKE 

IPsec uses the IKE protocol to negotiate and establish secured site-to-site or remote access virtual private network (VPN) tunnels. IKE protocol is also called the Internet Security Association and Key Management Protocol (ISAKMP) (Only in Cisco).

There are two versions of IKE:

-  IKEv1: Defined in RFC 2409, The Internet Key Exchange
 - IKE version 2 (IKEv2): Defined in RFC 4306, Internet Key Exchange (IKEv2) Protocol
### IKE Phases

ISAKMP separates negotiation into two phases:

- Phase 1: The two ISAKMP peers establish a secure and authenticated tunnel, which protects ISAKMP negotiation messages. This tunnel is known as the ISAKMP SA. There are two modes defined by ISAKMP: Main Mode (MM) and Aggressive Mode.
 -   Phase 2: It negotiates key materials and algorithms for the encryption (SAs) of the data to be transferred over the IPsec tunnel. This phase is called Quick Mode.

To materialize all the abstract concepts, the Phase 1 tunnel is the Parent tunnel and phase 2 is a sub tunnel. This image illustrates the two phases as tunnels:
![[217432-understand-ipsec-ikev1-protocol-00.avif]]
full version : [link](https://www.cisco.com/c/en/us/support/docs/security-vpn/ipsec-negotiation-ike-protocols/217432-understand-ipsec-ikev1-protocol.html)
short version : [link](https://nordvpn.com/blog/ikev2ipsec/)

note : 
~Diffie-Hellman key exchange algorithm : 
Diffie–Hellman (DH) key exchangeis a mathematical method of securely exchanging cryptographic keys over a public channel and was one of the first public-key protocols as conceived by Ralph Merkle and named after Whitfield Diffie and Martin Hellman. DH is one of the earliest practical examples of public key exchange implemented within the field of cryptography. Published in 1976 by Diffie and Hellman, this is the earliest publicly known work that proposed the idea of a private key and a corresponding public key. 
![[DiffieHellman.png]]