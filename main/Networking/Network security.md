## What is encryption?

Encryption is a way of scrambling data so that only authorized parties can understand the information. In technical terms, it is the process of converting human-readable plaintext to incomprehensible text, also known as ciphertext. In simpler terms, encryption takes readable data and alters it so that it appears random. Encryption requires the use of a [cryptographic key](https://www.cloudflare.com/learning/ssl/what-is-a-cryptographic-key/): a set of mathematical values that both the sender and the recipient of an encrypted message agree on.
## What is a cryptographic key?

In cryptography, a key is a string of characters used within an [encryption](https://www.cloudflare.com/learning/ssl/what-is-encryption/) algorithm for altering data so that it appears random. Like a physical key, it locks (encrypts) data so that only someone with the right key can unlock (decrypt) it.
# key exchange mechanisms 
Key exchange methods are used to exchange cryptographic keys between two parties securely. This is an essential part of many cryptographic protocols, as the security of the encryption used to protect communication relies on the secrecy of the keys. There are many key exchange methods, each with unique characteristics and strengths. Some key exchange methods are more secure than others, and the appropriate method depends on the situation's specific circumstances and requirements.

These methods typically work by allowing the two parties to agree on a `shared secret key` over an insecure communication channel that encrypts the communication between them. This is generally done using some form of mathematical operation, such as a computation based on the properties of a mathematical function or a series of simple manipulations of the key.

#### Diffie-Hellman

One common key exchange method is the [Diffie-Hellman key exchange](https://www.comparitech.com/blog/information-security/diffie-hellman-key-exchange/) it requires the two devices agree on a secret key that they can use to decrypt    the data they send to each other . It is often used as the basic for establishing secure communication channels, such as in the [Transport Layer Security](https://www.cloudflare.com/learning/ssl/transport-layer-security-tls/) (`TLS`) protocol that is used to protect web traffic. [[OSI_model]]

One of the main limitations of the `Diffie-Hellman` key exchange is that it is vulnerable to `MITM attacks`. In a MITM attack, we intercept the communication between the two parties and pretend to be one of the parties, generating a different secret key and tricking both parties into using it. This allows the attacker to read and modify the messages sent between the parties.

Another limitation is that it requires a relatively large amount of `CPU power` to generate the shared secret key. This can make it impractical for use in low-power devices or in situations where the key needs to be generated quickly.
### RSA
Another key exchange method is the [Rivest–Shamir–Adleman](https://www.venafi.com/blog/how-diffie-hellman-key-exchange-different-rsa) (`RSA`) algorithm, which uses the properties of large prime numbers to generate a shared secret key. This method relies on the fact that it is relatively easy to multiply large prime numbers together but challenging to factor the resulting number back into its prime factors. Besides these two, there are also a couple of others that we need to look at. It is also widely used in many other applications and protocols that require secure communication and data protection, including but not limited to:
-- Encrypting and signing messages to provide confidentiality and authentication

- Protecting data in transit over networks, such as in the [Secure Socket Layer](https://www.cloudflare.com/learning/ssl/what-is-ssl/) (`SSL`) and `TLS` protocols

- Generating and verifying digital signatures, which are used to provide authenticity and integrity for electronic documents and other digital data

- Authenticating users and devices, such as in the [Public Key Cryptography for Initial Authentication in Kerberos](https://www.ietf.org/rfc/rfc4556.txt) (`PKINIT`) protocol used by the Kerberos network authentication system

- Protecting sensitive information, such as in the encryption of personal data and confidential documents
### ECDH

[Elliptic curve Diffie-Hellman](https://medium.com/swlh/understanding-ec-diffie-hellman-9c07be338d4a) (`ECDH`) is a variant of Diffie-Hellman key exchange that uses elliptic curve cryptography to generate the shared secret key. It has the advantage of being more efficient and secure than the original Diffie-Hellman algorithm, including but not limited to:
- Establishing secure communication channels, such as in the `TLS` protocol
 
- Providing forward secrecy, which ensures that past communications cannot be revealed even if the private keys are compromised    
- Authenticating users and devices, such as in the [Internet Key Exchange](https://docs.oracle.com/cd/E19683-01/816-7264/6md9iem1g/index.html) (`IKE`) protocol used in VPNs
### ECDSA

The [Elliptic Curve Digital Signature Algorithm](https://www.hypr.com/security-encyclopedia/elliptic-curve-digital-signature-algorithm) (`ECDSA`) uses elliptic curve cryptography to generate digital signatures that can authenticate the parties involved in the key exchange.

Let us summarize and compare these algorithms:

<table class="table table-striped text-left">
<thead>
<tr>
<th><strong>Algorithm</strong></th>
<th><strong>Acronym</strong></th>
<th><strong>Security</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td><code>Diffie-Hellman</code></td>
<td><code>DH</code></td>
<td>Relatively secure and computationally efficient</td>
</tr>
<tr>
<td><code>Rivest–Shamir–Adleman</code></td>
<td><code>RSA</code></td>
<td>Widely used and considered secure, but computationally intensive</td>
</tr>
<tr>
<td><code>Elliptic Curve Diffie-Hellman</code></td>
<td><code>ECDH</code></td>
<td>Provides enhanced security compared to traditional Diffie-Hellman</td>
</tr>
<tr>
<td><code>Elliptic Curve Digital Signature Algorithm</code></td>
<td><code>ECDSA</code></td>
<td>Provides enhanced security and efficiency for digital signature generation</td>
</tr>
</tbody>
</table>
### Internet Key Exchange

[Internet Key Exchange](https://www.hypr.com/security-encyclopedia/internet-key-exchange) (`IKE`) is a protocol used to establish and maintain secure communication sessions, such as those used in VPNs. It uses a combination of the `Diffie-Hellman` key exchange algorithm and `other cryptographic techniques` to securely exchange keys and negotiate security parameters. 

IKE can also be used for other purposes, such as in the authentication of users and devices. It is typically used in conjunction with other protocols and algorithms, such as the RSA algorithm for key exchange and digital signatures, and the [Advanced Encryption Standard](https://www.geeksforgeeks.org/advanced-encryption-standard-aes/) (`AES`) for data encryption.

IKE operates either in `main mode` or `aggressive mode`. These modes determine the sequence and parameters of the key exchange process and can affect the security and performance of the IKE session.
#### Main Mode

The `main mode` is the default mode for `IKE` and is generally considered `more secure` than the aggressive mode. The key exchange process is performed in `three phases` in the main mode, each exchanging a different set of security parameters and keys. This allows for greater flexibility and security but can also result in slower performance compared to aggressive mode.

#### Aggressive Mode

`Aggressive mode` is an alternative mode for `IKE` that provides `faster performance` by reducing the number of round trips and message exchanges required for key exchange. In this mode, the key exchange process is performed in `two phases`, with all security parameters and keys being exchanged in the first phase. However, this can provide faster performance but may also reduce the security of the IKE session compared to the main mode since the `aggressive mode` does not provide identity protection.
#### Pre-Shared Keys

In IKE, a `Pre-Shared Key` (`PSK`) is a secret value shared between the two parties involved in the key exchange. This key is used to authenticate the parties and establish a shared secret that encrypts subsequent communication. The use of a PSK is optional in IKE, and whether or not to use one depends on the specific requirements and constraints of the situation. However, if a `PSK` is used, it must be securely exchanged between the two parties before the key exchange process begins. This can be done through a secure out-of-band channel, such as a separate communication channel, or by physically exchanging the key.

The main advantage of using a PSK is that it provides an additional layer of security by allowing the parties to authenticate with each other. However, using a PSK also has some limitations and drawbacks. For example, it can be difficult to exchange the key securely, and if the key is compromised through a MITM attack, the security of the IKE session may be compromised.

# SSL
SSL( secure socket layer) is an encryption-based internet security protocol made by ``netscape``  in 1995 as a way for authentication and privacy , SSL is the predecessor of TLS encryption . 
a website that uses SSL/TLS has the 'HTTPS on it '

![[http-vs-https-1.svg]]

## How does SSL / TLS work ?
- in order to protect the privacy of the users SSL / TLS encrypts the data that is being transmitted so that if someone intercepts the traffic he will only find encrypted data that is unreadable and nearly impossible to decrypt (brute force )
- it init a handshake between the two devices that are connected to each other 
- it also sings the data digitally so that it know that it wasn't changed 

There have been several iterations of SSL, each more secure than the last. In 1999 SSL was updated to become TLS.
## Why is SSL/TLS important?

Originally, data on the Web was transmitted in plaintext that anyone could read if they intercepted the message. For example, if a consumer visited a shopping website, placed an order, and entered their credit card number on the website, that credit card number would travel across the Internet unconcealed.

SSL was created to correct this problem and protect user privacy. By encrypting any data that goes between a user and a web server, SSL ensures that anyone who intercepts the data can only see a scrambled mess of characters. The consumer's credit card number is now safe, only visible to the shopping website where they entered it.

SSL also stops certain kinds of cyber attacks: It authenticates web servers, which is important because attackers will often try to set up fake websites to trick users and steal data. It also prevents attackers from tampering with data in transit, like a tamper-proof seal on a medicine container.

## What is an SSL certificate?

SSL can only be implemented by websites that have an SSL certificate (technically a "TLS certificate"). An SSL certificate is like an ID card or a badge that proves someone is who they say they are. SSL certificates are stored and displayed on the Web by a website's or application's server.

One of the most important pieces of information in an SSL certificate is the website's public key. The public key makes encryption and authentication possible. A user's device views the public key and uses it to establish secure encryption keys with the web server. Meanwhile the web server also has a private key that is kept secret; the private key decrypts data encrypted with the public key.

Certificate authorities (CA) are responsible for issuing SSL certificates.
## What are the types of SSL certificates?

There are several different types of SSL certificates. One certificate can apply to a single website or several websites, depending on the type:

- Single-domain: A single-domain SSL certificate applies to only one domain (a "domain" is the name of a website, like www.cloudflare.com).
- Wildcard: Like a single-domain certificate, a wildcard SSL certificate applies to only one domain. However, it also includes that domain's subdomains. For example, a wildcard certificate could cover www.cloudflare.com, blog.cloudflare.com, and developers.cloudflare.com, while a single-domain certificate could only cover the first.
- Multi-domain: As the name indicates, multi-domain SSL certificates can apply to multiple unrelated domains.

SSL certificates also come with different validation levels. A validation level is like a background check, and the level changes depending on the thoroughness of the check.

- Domain Validation: This is the least-stringent level of validation, and the cheapest. All a business has to do is prove they control the domain.
- Organization Validation: This is a more hands-on process: The CA directly contacts the person or business requesting the certificate. These certificates are more trustworthy for users.
- Extended Validation: This requires a full background check of an organization before the SSL certificate can be issued.

How does TLS work?

A TLS connection is initiated using a sequence known as the TLS handshake. When a user navigates to a website that uses TLS, the TLS handshake begins between the user's device (also known as the client device) and the web server.

During the TLS handshake, the user's device and the web server:

- Specify which version of TLS (TLS 1.0, 1.2, 1.3, etc.) they will use
- Decide on which cipher suites they will use
- Authenticate the identity of the server using the server's TLS certificate
- Generate session keys for encrypting messages between them after the handshake is complete

The TLS handshake establishes a cipher suite for each communication session. The cipher suite is a set of algorithms that specifies details such as which shared encryption keys, or session keys, will be used for that particular session. TLS is able to set the matching session keys over an unencrypted channel thanks to a technology known as public key cryptography.

The handshake also handles authentication, which usually consists of the server proving its identity to the client. This is done using public keys. Public keys are encryption keys that use one-way encryption, meaning that anyone with the public key can unscramble the data encrypted with the server's private key to ensure its authenticity, but only the original sender can encrypt data with the private key. The server's public key is part of its TLS certificate.

Once data is encrypted and authenticated, it is then signed with a message authentication code (MAC). The recipient can then verify the MAC to ensure the integrity of the data. This is kind of like the tamper-proof foil found on a bottle of aspirin; the consumer knows no one has tampered with their medicine because the foil is intact when they purchase it.
![[tls-ssl-handshake.png]]

# Authentication Protocols

Many different authentication protocols are used in networking to verify the identity of devices and users. Those protocols are essential because they provide a secure and standardized way of verifying the identity of users, devices, and other entities in a network. Without authentication protocols, it would be difficult to securely and reliably identify entities in a network, making it easy for attackers to gain unauthorized access and potentially compromise the network.

Authentication protocols also provide a means for securely exchanging information between entities in a network. This is important for ensuring the confidentiality and integrity of sensitive data and preventing unauthorized access and other security threats. Let us take a look at a few most commonly used authentication protocols:

<table class="table table-striped text-left">
<thead>
<tr>
<th><strong>Protocol</strong></th>
<th><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td><code>Kerberos</code></td>
<td>Key Distribution Center (KDC) based authentication protocol that uses tickets in domain environments.</td>
</tr>
<tr>
<td><code>SRP</code></td>
<td>This is a password-based authentication protocol that uses cryptography to protect against eavesdropping and man-in-the-middle attacks.</td>
</tr>
<tr>
<td><code>SSL</code></td>
<td>A cryptographic protocol used for secure communication over a computer network.</td>
</tr>
<tr>
<td><code>TLS</code></td>
<td>TLS is a cryptographic protocol that provides communication security over the internet. It is the successor to SSL.</td>
</tr>
<tr>
<td><code>OAuth</code></td>
<td>An open standard for authorization that allows users to grant third-party access to their web resources without sharing their passwords.</td>
</tr>
<tr>
<td><code>OpenID</code></td>
<td>OpenID is a decentralized authentication protocol that allows users to use a single identity to sign in to multiple websites.</td>
</tr>
<tr>
<td><code>SAML</code></td>
<td>Security Assertion Markup Language is an XML-based standard for securely exchanging authentication and authorization data between parties.</td>
</tr>
<tr>
<td><code>2FA</code></td>
<td>An authentication method that uses a combination of two different factors to verify a user's identity.</td>
</tr>
<tr>
<td><code>FIDO</code></td>
<td>The Fast IDentity Online Alliance is a consortium of companies working to develop open standards for strong authentication.</td>
</tr>
<tr>
<td><code>PKI</code></td>
<td>PKI is a system for securely exchanging information based on the use of public and private keys for encryption and digital signatures.</td>
</tr>
<tr>
<td><code>SSO</code></td>
<td>An authentication method that allows a user to use a single set of credentials to access multiple applications.</td>
</tr>
<tr>
<td><code>MFA</code></td>
<td>MFA is an authentication method that uses multiple factors, such as something the user knows (a password), something the user has (a phone), or something the user is (biometric data), to verify their identity.</td>
</tr>
<tr>
<td><code>PAP</code></td>
<td>A simple authentication protocol that sends a user's password in clear text over the network.</td>
</tr>
<tr>
<td><code>CHAP</code></td>
<td>An authentication protocol that uses a three-way handshake to verify a user's identity.</td>
</tr>
<tr>
<td><code>EAP</code></td>
<td>A framework for supporting multiple authentication methods, allowing for the use of various technologies to verify a user's identity.</td>
</tr>
<tr>
<td><code>SSH</code></td>
<td>This is a network protocol for secure communication between a client and a server. We can use it for remote command-line access and remote command execution, as well as for secure file transfer. SSH uses encryption to protect against eavesdropping and other attacks and can also be used for authentication.</td>
</tr>
<tr>
<td><code>HTTPS</code></td>
<td>This is a secure version of the HTTP protocol used for communication on the internet. HTTPS uses SSL/TLS to encrypt communication and provide authentication, ensuring that third parties cannot intercept and read the transmitted data. It is widely used for secure communication over the internet, particularly for web browsing.</td>
</tr>
<tr>
<td><code>LEAP</code></td>
<td>LEAP is a wireless authentication protocol developed by Cisco. It uses EAP to provide mutual authentication between a wireless client and a server and uses the RC4 encryption algorithm to encrypt communication between the two. Unfortunately, LEAP is vulnerable to dictionary attacks and other security vulnerabilities and has been largely replaced by more secure protocols such as EAP-TLS and PEAP.</td>
</tr>
<tr>
<td><code>PEAP</code></td>
<td>PEAP on the other hand is a secure tunneling protocol used for wireless and wired networks. It is based on EAP and uses TLS to encrypt communication between a client and a server. PEAP uses a server-side certificate to authenticate the server and can also be used to authenticate the client using various methods, such as passwords, certificates, or biometric data. PEAP is widely used in enterprise networks for secure authentication.</td>
</tr>
</tbody>
</table>

For example, LEAP and PEAP may be used to authenticate wireless clients when they access the wireless network or to authenticate remote employees connecting to the network via a VPN. In these cases, using SSH or HTTPS would be challenging to implement, as they are designed for different purposes. In terms of security, PEAP is generally more secure than LEAP because it uses a server-side public key certificate to authenticate the server and encrypting MSCHAPv2 hash, while LEAP relies on a shared secret that is negotiated between the client and the server and does not encrypt MSCHAPv2 hashes. PEAP also supports the use of stronger encryption algorithms, such as AES and 3DES, for encrypting the authentication information, whereas LEAP uses the weaker RC4 algorithm.

However, both protocols are vulnerable to specific attacks and have been largely replaced by more secure protocols such as EAP-TLS.

As physical connections, protocols with SSL or TLS are used by default, such as SSH or HTTPS. Both protocols use robust encryption algorithms to protect the authentication information transmitted between the client and the server. This helps to prevent interception or to tamper the authentication data, which is essential for maintaining the security of the authentication process. Also, they support using digital certificates and PKI for authenticating the server to the client. This ensures that the client can verify the server's identity and helps to prevent MITM attacks. SSH and HTTPS are widely used and well-supported protocols, with implementations available for various operating systems and devices and makes them easy to use and deploy in a variety of environments.
# Cryptography
Encryption is used on the Internet to transmit data, such as payment information, e-mails, or personal data, confidentially and protected against manipulation. Data is encrypted using various cryptographic algorithms based on mathematical operations. With the help of encryption, data can be transformed into a form that unauthorized persons can no longer read. Digital keys in symmetric or asymmetric encryption processes are used for encryption. It is easier to crack cipher texts or keys depending on the encryption methods used. If state-of-the-art cryptographic methods with extensive key lengths are used, they work very securely and are almost impossible to compromise for the time being. In principle, we can distinguish between symmetric and asymmetric encryption techniques. Asymmetric methods have only been known for a few decades. Nevertheless, they are the most frequently used methods in digital communication.

## Symmetric Encryption

Symmetric encryption, also known as secret key encryption, is a method that uses the same key to encrypt and decrypt the data. This means the sender and the receiver must have the same key to decrypt the data correctly.

If the secret key is shared or lost, the security of the data is no longer guaranteed. Critical actions for symmetric encryption methods represent the distribution, storage, and exchange of the keys. Advanced Encryption Standard ([AES](https://en.wikipedia.org/wiki/Advanced_Encryption_Standard) ) and Data Encryption Standard ([DES](https://en.wikipedia.org/wiki/Data_Encryption_Standard)) are examples of symmetric encryption algorithms. This type of encryption is often used to encrypt large amounts of data, such as files on a hard drive or data sent over a network. AES is considered to be the most secure encryption algorithm nowadays.
## Asymmetric Encryption

Asymmetric encryption, also known as public-key encryption, is a method of encryption that uses two different keys:

    a public key
    a private key

The public key is used to encrypt the data, while the private key is used to decrypt the data. This means anyone can use a public key to encrypt data for someone, but only the recipient with the associated private key can decrypt the data. Examples of asymmetric encryption methods include Rivest–Shamir–Adleman ([RSA](https://en.wikipedia.org/wiki/RSA_(cryptosystem))), Pretty Good Privacy ([PGP](https://en.wikipedia.org/wiki/Pretty_Good_Privacy)), and Elliptic Curve Cryptography ([ECC](https://en.wikipedia.org/wiki/Elliptic-curve_cryptography)). Asymmetric encryption is used in a variety of applications, some of which include:
### Public-Key Encryption

One advantage of asymmetric encryption is its security. Since the security is based on very hard-to-solve mathematical problems, simple attacks cannot crack it. Furthermore, the issue of key exchange is bypassed. This is a significant problem with symmetric encryption methods. However, since the public key can be accessible to everyone, there is no need to exchange keys secretly. In addition, the asymmetric methods open up the possibility of authentication with digital signatures.

### Data Encryption Standard

DES is a symmetric-key block cipher, and its encryption works as a combination of the one-time pad, permutation, and substitution ciphers applied to bit sequences. It uses the same key in both encrypting and decrypting data.

The key consists of 64 bits, with 8 bits used as a checksum. Therefore, the actual key length of DES is only 56 bits. And that is why one always speaks of a key length of 56 bits when referring to DES. To prevent the danger from frequency analysis, not single letters, but each 64-bit block of plaintext is encrypted to a 64-bit block of ciphertext.

An extension of DES is the so-called [Triple DES / 3DES](https://en.wikipedia.org/wiki/Triple_DES) which encrypts data more securely. The procedure for this usually consists of three keys, with the first key being used to encrypt the data, the second to decrypt the data, and the third to encrypt the data again.

3DES was considered more secure than the original DES because it provides greater security using three rounds of encryption, although using a 56-bit key still limits it. AES, the successor to DES, provides higher security using longer key lengths and is now the most widely used symmetric encryption technology.

### Advanced Encryption Standard

Compared to DES, AES uses 128-bit (AES-128), 192-bit (AES-192), or 256-bit (AES-256) keys to encrypt and decrypt data. In addition, AES is faster than DES because it has a more efficient algorithm structure. This is because it can be applied to multiple data blocks at once, making it faster. This means that AES encryption and decryption can be performed faster than DES, which is especially important when large amounts of data need to be encrypted.

For example, we can find AES in many different applications and protocols, but they are not limited to:
WLAN IEEE 802.11i |	IPsec  |	SSH
VoIP  |	PGP  |	OpenSSL
### Cipher Modes

A cipher mode refers to how a block cipher algorithm encrypts a plaintext message. A block cipher algorithm encrypts data, each using fixed-size blocks of data (usually 64 or 128 bits). A cipher mode defines how these blocks are processed and combined to encrypt a message of any length. There are several common cipher modes, including:
<table class="table table-striped text-left">
<thead>
<tr>
<th><strong>Cipher Mode</strong></th>
<th><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td><a href="https://en.wikipedia.org/wiki/Block_cipher_mode_of_operation" target="_blank" rel="noopener nofollow">Electronic Code Book</a> (<code>ECB</code>) mode</td>
<td>ECB mode is generally not recommended for use due to its susceptibility to certain types of attacks. Furthermore, it does not hide data patterns efficiently. As a result, statistical analysis can reveal elements of clear-text messages, for example, in web applications.</td>
</tr>
<tr>
<td><a href="https://en.wikipedia.org/wiki/Block_cipher_mode_of_operation#CBC" target="_blank" rel="noopener nofollow">Cipher Block Chaining</a> (<code>CBC</code>) mode</td>
<td>CBC mode is generally used to encrypt messages like disk encryption and e-mail communication. This is the default mode for AES and is also used in software like TrueCrypt, VeraCrypt, TLS, and SSL.</td>
</tr>
<tr>
<td><a href="https://en.wikipedia.org/wiki/Block_cipher_mode_of_operation#Cipher_feedback_(CFB)" target="_blank" rel="noopener nofollow">Cipher Feedback</a> (<code>CFB</code>) mode</td>
<td>CFB mode is well suited for real-time encryption of a data stream, e.g., network communication encryption or encryption/decryption of files in transit like Public-Key Cryptography Standards (PKCS) and Microsoft's BitLocker.</td>
</tr>
<tr>
<td><a href="https://en.wikipedia.org/wiki/Block_cipher_mode_of_operation#OFB" target="_blank" rel="noopener nofollow">Output Feedback</a> (<code>OFB</code>) mode</td>
<td>OFB mode is also used to encrypt a data stream, e.g., to encrypt real-time communication. However, this mode is considered better for the data stream because of how the key stream is generated. We can find this mode in PKCS but also in the SSH protocol.</td>
</tr>
<tr>
<td><a href="https://en.wikipedia.org/wiki/Block_cipher_mode_of_operation#CTR" target="_blank" rel="noopener nofollow">Counter</a> (<code>CTR</code>) mode</td>
<td>CTR mode encrypts real-time data streams AES uses, e.g., network communication, disk encryption, and other real-time scenarios where data is processed. An example of this would be IPsec or Microsoft's BitLocker.</td>
</tr>
<tr>
<td><a href="https://en.wikipedia.org/wiki/Galois/Counter_Mode" target="_blank" rel="noopener nofollow">Galois/Counter</a> (<code>GCM</code>) mode</td>
<td>GCM is used in cases where confidentiality and integrity need to be protected together, such as wireless communications, VPNs, and other secure communication protocols.</td>
</tr>
</tbody>
</table>

Each mode has its characteristics and is more suitable for certain use cases. The choice of encryption mode depends on the application's requirements and the security objectives to be achieved.
# Firewall 
## what's a firewall ?
A Firewall is a network security device that monitors ingoing and outgoing network traffic and then use a specific sets of rules to decide whether to block the traffic or not . 

Firewalls have been helping protecting networks for over 25 years , and they are essential since they act as a barrier stopping malicious ingoing traffic coming from wider networks (the internet) .

Firewalls can be hardware , software , software-as-a-service (SaaS) , public cloud , private cloud (virtual). 
## types of Firewalls
### Proxy Firewall 
An early type of firewall device, a proxy firewall serves as the gateway from one network to another for a specific application. Proxy servers can provide additional functionality such as content caching and security by preventing direct connections from outside the network. However, this also may impact throughput capabilities and the applications they can support.
![[Untitled.png]]
### stateful inspection Firewall 
this type of firewall is regarded as the "traditional firewall" , a stateful inspection firewall allows or blocks traffic based on state , port  , protocols . it monitors all the traffic since the establishment of the connection entail its closing , the filtering decisions are made based on rules made  by the admin  as well as context , which refers to using info from previous connections and  packets to the same connection 
![[images.jpg]]
### Unified  threat management Firewall (UTMF)  
A UTM device typically combines, in a loosely coupled way, the functions of a stateful inspection firewall with intrusion prevention and antivirus. It may also include additional services and often cloud management. UTMs focus on simplicity and ease of use.


![[security-threat_management-f_mobile.png]]


### Next gen Firewall (NGFW)
Firewalls have evolved beyond simple packet filtering and stateful inspection. Most companies are deploying [next-generation firewalls](https://www.cisco.com/c/en/us/products/security/firewalls/what-is-a-next-generation-firewall.html) to block modern threats such as advanced malware and application-layer attacks.

According to Gartner, Inc.’s definition, a next-generation firewall must include:

- Intelligence-based access control with stateful inspection
- Integrated intrusion prevention system (IPS)
- Application awareness and control to see and block risky apps
- Upgrade paths to include future information feeds
- Techniques to address evolving security threats
- URL filtering based on geolocation and reputation

While these capabilities are increasingly becoming the standard for most companies, NGFWs can do more.

### Threat-focused NGFW
These firewalls include all the capabilities of a traditional NGFW and also provide advanced threat detection and remediation. With a threat-focused NGFW you can:

- **Know which assets are most at risk** with complete context awareness
- **Quickly react to attacks** with intelligent security automation that sets policies and hardens your defenses dynamically
- **Better detect evasive or suspicious activity** with network and endpoint event correlation
- **Greatly decrease the time from detection to cleanup** with retrospective security that continuously monitors for suspicious activity and behavior even after initial inspection
- **Ease administration and reduce complexity** with [unified policies](https://www.cisco.com/c/en/us/products/security/what-is-network-security-policy-management.html) that protect across the entire attack continuum

[Cisco's threat-focused firewalls](https://www.cisco.com/site/us/en/products/security/firewalls/index.html).
### Virtual firewall
A virtual firewall is typically deployed as a virtual appliance in a private cloud (VMware ESXi, Microsoft Hyper-V, KVM) or public cloud (Amazon Web Services or AWS, Microsoft Azure, Google Cloud Platform or GCP, Oracle Cloud Infrastructure or OCI) to monitor and secure traffic across physical and virtual networks. A virtual firewall is often a key component in software-defined networks (SDN).

Learn about Cisco virtual firewalls for [public cloud](https://www.cisco.com/c/en/us/products/security/firewalls/firepower-public-cloud.html) and [private cloud](https://www.cisco.com/c/en/us/products/security/firewalls/firepower-private-cloud.html).
## Encryption Protocols

Wired Equivalent Privacy (WEP) and WiFi Protected Access (WPA) are encryption protocols that secure data transmitted over a WiFi network. WPA can use different encryption algorithms, including Advanced Encryption Standard (AES).
### WEP

WEP uses a 40-bit or 104-bit key to encrypt data, while WPA using AES uses a 128-bit key. Longer keys provide more robust encryption and are more resistant to attacks. However, it is vulnerable to various attacks that can allow an attacker to decrypt data transmitted over the network. In addition, WEP is not compatible with newer devices and operating systems and is generally no longer considered secure. Finally, WEP uses the [RC4](https://www.geeksforgeeks.org/rc4-encryption-algorithm/) cipher encryption algorithm, which makes it vulnerable to attacks.

However, WEP uses a shared key for authentication, which means the same key is used for encryption and authentication. There are two versions of the WEP protocol:

    WEP-40/WEP-64
    WEP-104

WEP-40, also known as WEP-64, uses a 40-bit (secret) key, while WEP-104 uses a 104-bit key. The key is divided into an Initialization Vector (IV) and a secret key.

The IV is a small value included in the packet header along with the encrypted data and is used to create the key for both WEP-40 and WEP-104 and is included to ensure that each key is unique. The secret key is a series of random bits used to encrypt the data. However, the WEP-104 has a 80-bits long secret key. Let us look at the following table to see the differences clearly:

| Protocol      | IV     | Secret Key |
| ------------- | ------ | ---------- |
| WEP-40/WEP-64 | 24-bit | 40-bit     |
| WEP-104       | 24-bit | 80-bit     |

However, since the IV in WEP is relatively small, we can brute force it, try every possible combination of characters for it, and determine the correct value. Afterward, we can use it to decrypt the data in the packet. This allows us to access the data transmitted over the wireless network and potentially compromise the network's security.
### WPA

WPA provides the highest level of security and is not susceptible to the same types of attacks as WEP. In addition, WPA uses more secure authentication methods, such as a Pre-Shared Key (PSK) or an 802.1X authentication server, which provide stronger protection against unauthorized access. Although older devices may not support WPA is compatible with most devices and operating systems. All wireless networks, especially in critical infrastructure like offices, should generally implement at least WPA2 or even WPA3 encryption.
## Authentication Protocols

Lightweight Extensible Authentication Protocol (LEAP) and Protected Extensible Authentication Protocol (PEAP) are authentication protocols used to secure wireless networks to provide a secure method for authenticating devices on a wireless network and are often used in conjunction with WEP or WPA to provide an additional layer of security.

LEAP and PEAP are both based on the Extensible Authentication Protocol (EAP), a framework for authentication used in various networking contexts. However, one key difference between LEAP and PEAP is how they secure the authentication process.

    LEAP uses a shared key for authentication, which means that the same key is used for encryption and authentication.

This can make it relatively easy for us to gain access to the network if the key is compromised.

However, PEAP uses a more secure authentication method called tunneled Transport Layer Security [TLS](https://en.wikipedia.org/wiki/Transport_Layer_Security). This method establishes a secure connection between the device and the WAP using a digital certificate, and an encrypted tunnel protects the authentication process. This provides more robust protection against unauthorized access and is more resistant to attacks.

## TACACS+

In a wireless network, when a wireless access point (WAP) sends an authentication request to a [Terminal Access Controller Access-Control System Plus](https://www.ciscopress.com/articles/article.asp?p=422947&seqNum=4) (`TACACS+`) server, it is likely that the `entire request packet` will be encrypted to protect the confidentiality and integrity of the request.

`TACACS+` is a protocol used to authenticate and authorize users accessing network devices, such as routers and switches. When a WAP sends an authentication request to a `TACACS+` server, the request typically includes the user's credentials and other information about the session.

Encrypting the authentication request helps to ensure that this sensitive information is not visible to unauthorized parties who may be able to intercept the request. At the same time, it is being transmitted over the network. It also helps prevent tampering with the request or replacing it with a malicious request of their own.

Several encryption methods may be used to encrypt the authentication request, such as `SSL`/`TLS` or `IPSec`. The specific encryption method used may depend on the configuration of the `TACACS+` server and the capabilities of the WAP.

## **Pretty Good Privacy** (**PGP**)
is an encryption program that provides cryptographic  Privacy and authentication for data communication. PGP is used for signing, encrypting, and decrypting texts, e-mails, files, directories, and whole disk partitions and to increase the security of e-mail communications. [Phil Zimmermann](https://en.wikipedia.org/wiki/Phil_Zimmermann "Phil Zimmermann") developed PGP in 1991.

PGP and similar software follow the OpenPGP standard (RFC 4880), an open standard for encrypting and decrypting data. Modern versions of PGP are interoperable with [GnuPG](https://en.wikipedia.org/wiki/GnuPG "GnuPG") and other OpenPGP-compliant systems

## Design

[![](https://upload.wikimedia.org/wikipedia/commons/thumb/4/4d/PGP_diagram.svg/500px-PGP_diagram.svg.png)](https://en.wikipedia.org/wiki/File:PGP_diagram.svg)

How PGP encryption works visually

PGP encryption uses a serial combination of [hashing](https://en.wikipedia.org/wiki/Cryptographic_hash_function "Cryptographic hash function"), data compression, symmetric-key cryptography, and finally public-key cryptography each step uses one of several supported algorithms. Each public key is bound to a username or an e-mail address. The first version of this system was generally known as a [web of trust](https://en.wikipedia.org/wiki/Web_of_trust "Web of trust") to contrast with the [X.509](https://en.wikipedia.org/wiki/X.509 "X.509") system, which uses a hierarchical approach based on [certificate authority](https://en.wikipedia.org/wiki/Certificate_authority "Certificate authority") and which was added to PGP implementations later. Current versions of PGP encryption include options through an automated key management server.

### PGP fingerprint

A [public key fingerprint](https://en.wikipedia.org/wiki/Public_key_fingerprint "Public key fingerprint") is a shorter version of a public key. From a fingerprint, someone can validate the correct corresponding public key. A fingerprint like C3A6 5E46 7B54 77DF 3C4C 9790 4D22 B3CA 5B32 FF66 can be printed on a business card.[[6]](https://en.wikipedia.org/wiki/Pretty_Good_Privacy#cite_note-6)[[7]](https://en.wikipedia.org/wiki/Pretty_Good_Privacy#cite_note-7)

### Compatibility

As PGP evolves, versions that support newer features and algorithms can create encrypted messages that older PGP systems cannot decrypt, even with a valid private key. Therefore, it is essential that partners in PGP communication understand each other's capabilities or at least agree on PGP settings.[[8]](https://en.wikipedia.org/wiki/Pretty_Good_Privacy#cite_note-8)

### Confidentiality

PGP can be used to send messages confidentially.[[9]](https://en.wikipedia.org/wiki/Pretty_Good_Privacy#cite_note-9) For this, PGP uses a [hybrid cryptosystem](https://en.wikipedia.org/wiki/Hybrid_cryptosystem "Hybrid cryptosystem") by combining symmetric-key encryption and public-key encryption. The message is encrypted using a symmetric encryption algorithm, which requires a symmetric key generated by the sender. The symmetric key is used only once and is also called a [session key](https://en.wikipedia.org/wiki/Session_key "Session key"). The message and its session key are sent to the receiver. The session key must be sent to the receiver so they know how to decrypt the message, but to protect it during transmission it is encrypted with the receiver's public key. Only the private key belonging to the receiver can decrypt the session key, and use it to symmetrically decrypt the message.
### Security quality

To the best of publicly available information, there is no known method which will allow a person or group to break PGP encryption by cryptographic, or computational means. Indeed, in 1995, cryptographer[Bruce Schneier](https://en.wikipedia.org/wiki/Bruce_Schneier "Bruce Schneier") characterized an early version as being "the closest you're likely to get to military-grade encryption."[[10]](https://en.wikipedia.org/wiki/Pretty_Good_Privacy#cite_note-10) Early versions of PGP have been found to have theoretical vulnerabilities and so current versions are recommended.[[11]](https://en.wikipedia.org/wiki/Pretty_Good_Privacy#cite_note-11) In addition to protecting [data in transit](https://en.wikipedia.org/wiki/Data_in_transit "Data in transit") over a network, PGP encryption can also be used to protect data in long-term data storage such as disk files. These long-term storage options are also known as data at rest, i.e. data stored, not in transit.

### Digital signatures

PGP supports message authentication and integrity checking. The latter is used to detect whether a message has been altered since it was completed (the _message integrity_ property) and the former, to determine whether it was actually sent by the person or entity claimed to be the sender (a _[digital signature](https://en.wikipedia.org/wiki/Digital_signature "Digital signature")_). Because the content is encrypted, any changes in the message will fail the decryption with the appropriate key. The sender uses PGP to create a digital signature for the message with either the RSA or [DSA](https://en.wikipedia.org/wiki/Digital_Signature_Algorithm "Digital Signature Algorithm") algorithms. To do so, PGP computes a hash (also called a [message digest](https://en.wikipedia.org/wiki/Message_Digest_Algorithm_5 "Message Digest Algorithm 5")) from the plaintext and then creates the digital signature from that hash using the sender's private key.
## Disassociation Attack

A [Disassociation Attack](https://www.makeuseof.com/what-are-disassociation-attacks/) is a type of `all` wireless network attack that aims to disrupt the communication between a WAP and its clients by sending disassociation frames to one or more clients.

The WAP uses disassociation frames to disconnect a client from the network. When a WAP sends a disassociation frame to a client, the client will disconnect from the network and have to reconnect to continue using the network.

We can launch the attack from `within` or `outside` the network depending on our location and network security measures. The purpose of this attack is to disrupt the communication between the WAP and its clients, causing the clients to disconnect and possibly causing inconvenience or disruption to the users. We can also use it as a precursor to other attacks, such as a MITM attack, by forcing the clients to reconnect to the network and potentially exposing them to further attacks.

## Wireless Hardening

There are many different ways to protect wireless networks. However, some examples should be considered to increase wireless networks' security dramatically. These are the following, but not limited to:

- Disabling broadcasting
- WiFi Protected Access
- MAC filtering
- Deploying EAP-TLS

#### Disabling Broadcasting

Disabling the broadcasting of the SSID is a security measure that can help harden a WAP by making it more difficult to discover and connect to the network. When the SSID is broadcasted, it is included in beacon frames regularly transmitted by the WAP to advertise the availability of the network. By disabling the broadcasting of the SSID, the WAP will not transmit beacon frames, and the network will not be visible to devices that are not already connected to the network.

#### WPA

Again, WPA provides strong encryption and authentication for wireless communications, helping protect against unauthorized network access and sensitive data interception. WPA includes two main versions:

1. WPA-Personal
2. WPA-Enterprise

WPA-Personal, designed for home and small business networks, and WPA-Enterprise, designed for larger organizations and uses a centralized authentication server (e.g., RADIUS or TACACS+) to verify the identity of clients.

#### MAC Filtering

MAC filtering is a security measure that allows a WAP to accept or reject connections from specific devices based on their MAC addresses. By configuring the WAP to accept connections only from devices with approved MAC addresses, it is possible to prevent unauthorized devices from connecting to the network.

#### Deploying EAP-TLS

EAP-TLS is a security protocol used to authenticate and encrypt wireless communications. It uses digital certificates and PKI to verify the identity of clients and establish secure connections. Deploying EAP-TLS can help to harden a WAP by providing strong authentication and encryption for wireless communications, which can protect against unauthorized access to the network and the interception of sensitive data.

