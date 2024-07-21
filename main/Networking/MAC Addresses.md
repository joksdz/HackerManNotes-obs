MAC Addresses a short for 'Media Access Control', Devices on a network will all have a physical network interface, which is a microchip board found on the device's motherboard. This network interface is assigned a unique address at the factory it was built . The MAC address is a **twelve-character** hexadecimal number (_a base sixteen numbering system used in computing to represent numbers_) split into two's and separated by a colon. These colons are considered separators. For example, _a4:c3:f0:85:ac:2d_. The first six characters represent the company that made the network interface, and the last six is a unique number.
![[Pasted image 20240414202804.png]]

However, an interesting thing with MAC addresses is that they can be faked or "[spoofed](https://www.securew2.com/blog/how-do-mac-spoofing-attacks-work)" in a process known as spoofing. This spoofing occurs when a networked device pretends to identify as another using its MAC address. When this occurs, it can often break poorly implemented security designs that assume that devices talking on a network are trustworthy. Take the following scenario: A firewall is configured to allow any communication going to and from the MAC address of the administrator. If a device were to pretend or "spoof" this MAC address, the firewall would now think that it is receiving communication from the administrator when it isn't.

here are several different standards for the MAC address:

- Ethernet (IEEE 802.3)
- Bluetooth (IEEE 802.15)
- WLAN (IEEE 802.11)
The MAC address consists of a total of `6 bytes`. The first half (`3 bytes` / `24 bit`) is the so-called `Organization Unique Identifier` (`OUI`) defined by the `Institute of Electrical and Electronics Engineers` (`IEEE`) for the respective manufacturers.