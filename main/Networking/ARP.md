Stands for Address Resolution Protocol or ARP for short, its a protocol that allows devices to identify themselves in a network through associating their [[MAC Addresses]] with their [[IP Addresses]] on the network and each device on the network will keep a log of the Mac address associated  with other devices 
# How does it work ? 
each device has a ledger that stores info in it called ``cache `` , the cache stores identities of other devices of the AR protocol 
and in order to map these identities  the ARP sends 2 types of messages : 
- ARP Request 
- ARP Reply 
when the request is sent , the message will be sent to every device on the network to find out if its MAC address is the same for the requested IP address , if that's true then the ARP reply will be sent to the original device that sent the message and it will cache that IP address with its MAC address withing cache(an ARP entry)
![[Pasted image 20240419173005.png]]
