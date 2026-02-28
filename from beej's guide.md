
# basics : 
## sockets 
### whats a socket : 
a way to make the program communicate with other programs using Unix file descriptors ,this is because everything in Unix is a file literally : directories are files , files are files (duh), I/O happens in files ,for example when reading an input what u are  doing is really just reading a *file descriptor*.

-----------------------------------------------------
##### File descriptor :
A **File descriptor (FD)** is a non-negative integer used as an abstract handle to access an open input/output (I/O) resource. This resource can be a regular file, a directory, a network socket, or a pipe...

------------------------------------------------------
And since a network connection is also a file ,most communication between two programs in Unix happens in terms of FDs. 
Well then , how can we use these FDs? the answer is just call socket() system routine, this returns a socket descriptor and you can communicate using socket calls like : send() , recv(), you can also use read() and write() but the first ones offer better control 


------------------------------------------------------
send - Execute a command in a different application
	  This  command  arranges  for cmd (and args) to be executed in the application named by app.  It returns the result or error from that command execution.  App may be the name of any application whose main window is on the display containing  the  sender's  main window;   it  need  not  be within the same process.  If no arg arguments are present,then the command to be executed is contained entirely within the cmd argument.If one or more args are present, they are concatenated to form the command  to  be  executed, just as for the eval command.

recv — receive a message from a connected socket
	The  recv() function shall receive a message from a connection-mode or connectionless-mode socket. It is normally used with connected sockets because it does not permit the application to retrieve the source address of received data.


you can use `man send` and `man recv` to learn more about them 

------------------------------------------------------
### types of sockets : 
 There are a lot of sockets : There are DARPA Internet addresses (Internet Sockets), path names on a local node (Unix Sockets), CCITT X.25 addresses (X.25 Sockets that you can safely ignore), and probably many others depending on which Unix flavor you run.
==NOTE:== *since these are just notes we are gonna be focused : **internet sockets.***

there are a lot of internet sockets but he we are gonna be focused only on 2.
#### Stream Sockets : 
we are gonna be referring to this as `SOCK_STREAM` 

Stream sockets are connection-oriented and stream-oriented sockets that provide a reliable, two-way communication channel between a client and a server. They guarantee that data is delivered in the order it was sent and that it is error-free. Stream sockets are commonly used for protocols such as Transmission Control Protocol (TCP), which is used for most internet communication.
If you output two items into the socket in the order “1, 2”, they will arrive in the order “1, 2” at the opposite end. 

**Example of Stream Sockets**: HTTP, HTTPS, FTP, SMTP, POP3, IMAP, SSH, Telnet, etc.

#### Datagram Sockets (connection-less sockets):
we are gonna be referring to this as `SOCK_DGRAM`

Unlike Stream Sockets, Datagram Sockets are connectionless and message-oriented sockets that provide an unreliable, two-way communication channel between a client and a server. Datagram sockets do not guarantee that data is delivered in the order it was sent or that it is error-free. Datagram sockets are commonly used for protocols such as User Datagram Protocol (UDP), which is used for real-time communication and multimedia streaming.

Why are they connectionless? Well, basically, it’s because you don’t have to maintain an open connection as you do with stream sockets. You just build a packet, slap an IP header on it with destination information, and send it out. No connection needed. 

Generally you will find programs that use UDP build other things on top of it ,for example *QUIC* protocol which is used by Google,tftp also does the same thing ,usually this works by sending back the ACK packet if the sender doesn't get it it will resend the last packets  

**Example of Datagram Sockets**: DNS, DHCP, SNMP, TFTP, NTP, etc.

## Network theory and the low level stuff 
### encapsulation : 
 a packet is born, the packet is wrapped (“encapsulated”) in a header (and rarely a footer) by
the first protocol (say, the TFTP protocol), then the whole thing (TFTP header included) is encapsulated
again by the next protocol (say, UDP), then again by the next (IP), then again by the final protocol on
the hardware (physical) layer (say, Ethernet).
When another computer receives the packet, the hardware strips the Ethernet header, the kernel strips
the IP and UDP headers, the TFTP program strips the TFTP header, and it finally has the data

its also mentioned here : [[IP Addresses]]

 basically wrapping it in headers 
![[pehl18l0.bmp]]
### OSI model :

all you need to know is here : [[OSI_model]]

All you have to do for stream sockets is send() the data out.
All you have to do for datagram sockets is encapsulate the packet in the method of your choosing and
sendto() it out. The kernel builds the Transport Layer and Internet Layer on for you and the hardware
does the Network Access Laye


## IP addresses : 
![[IP Addresses]]



![[Ports]]

### byte order (the endians)
everyone in the Internet world has generally agreed that if you want to represent the two-byte hex number, say `b34f`, you’ll store it in two sequential bytes `b3` followed by `4f`. Makes sense,This number, stored with the big end first, is called Big-Endian.

anything with an Intel or Intel-compatible processor, store the bytes reversed, so `b34f` would be stored in memory as the sequential bytes `4f` followed by `b3`. This storage method is called Little-Endian.

*How would you know how to send them ?*
You just get to assume the Host Byte Order isn’t right, and you always run the value
through a function to set it to Network Byte Order. The function will do the magic conversion if it has
to, and this way your code is portable to machines of differing endianness.

here are two types of numbers that you can convert: short (two bytes) and long (four bytes).
These functions work for the unsigned variations as well. Say you want to convert a short from Host
Byte Order to Network Byte Order. Start with “h” for “host”, follow it with “to”, then “n” for “network”,
and “s” for “short”: h-to-n-s, or htons().

![[Pasted image 20260228165506.png]]