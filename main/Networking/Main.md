A network is basically a set of connections between different devices to communicate with each other 
## Background
The first "real" network was made by Tim Berners-Lee in 1989 and he made THE World Wide Web (www) and http and html
## Types :
- public network 
- private network 
- ## [[Client-Server Relations]]

# How do we identify a device in a network ? 

- ## [[IP Addresses]] 
- ## [[MAC Addresses]] 
- # [[ARP]]


# How do we make a network ?
## [[Network topologies]]
## [[Network types]]

# How does the network work? 
## [[OSI_model]]

## [[Ports]]
## [[Proxies]]

# [Networking key terminologies ](https://academy.hackthebox.com/module/34/section/1871)


# VPNs 
## [[VPNs]]

# vendor specific 
## [[Cisco]]

# How to secure the network ?
## [[Network security]]

# what is a network made of ? 
## [[Network Components]]

# Why  do protocols matter?
Computers use rules or protocols in order to communicate with each other , just like we humans use languages 
Network protocols define many aspects of communication , this includes : 

*! when i mention messages i mean packets 

| Protocol        | description                                                                                                                                                                                                                                                                                                   |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Message format  | messages sent over a network use specific formats or structure , the message format depends on the message type and the channel that is used to send the message                                                                                                                                              |
| Message size    | there are strict rules on the size of messages , they can be different depending on the channel used, long messages are broken to small pieces of data                                                                                                                                                        |
| Timing          | timing is important when speaking of networking since it helps sync the devices that are exchanging info , as well as measuring the speed of which the data was sent                                                                                                                                          |
| encoding        | messages that are sent over a network are converted into bits by the sending host , each bit is encoded into a pattern of sound , light , electrical impulses on  the network media over which the bits are transmitted , after the message is received the receiver decodes the message in order to use it . |
| encapsulation   | refer to the [[OSI_model]]                                                                                                                                                                                                                                                                                    |
| Message pattern | some messages require an ACK message to start the communication process                                                                                                                                                                                                                                       |

# Network Standards Organization  
An internet standard is the end result of a cycle of discussion, problem solving and testing , these different standards are developed ,and maintained by a variety of orgs , when developing a new standard the process is recorded in a numbered Request For Comments (RFC) docs so that the evolution of the standard is tracked , RFCs for internet standard are published and managed by the internet Engineering Task Force (IETF)
![[Pasted image 20240822195017.png]]
