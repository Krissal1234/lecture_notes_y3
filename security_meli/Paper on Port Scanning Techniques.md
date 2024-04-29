paper reports the most important techniques used by TCP port scanners.


- Tcp port scanners are specialised programs used to determine what TCP ports of a host have processes listening on them for possible connections

- Since these scanners are often used by hackers, administrators need to know how they work and what possible weakness they exploit to be able to prevent unwanted scanning or at least to record each scanning attempt.


<font size=6>**TCP/IP Relevant issues**</font>

**end points and flags**
 the pair (ip addresss, port number) is called a socket and represents an end point of a TCP connection.  To obtain a TCP service, we need a connection between a socket on the sending machine and a socket on the receiving machine 
-  TCP connections are thus identified as two endpoints (socket1, socket2). These endpoints send each other segments

A tcp segment consists of a TCP header, optionally followed by data
TCP header includes six flag bits. One or more of them can be turned on at the same time 
![[Pasted image 20240425194155.png]]

<font size=4>TCP Connection Establishment</font>
- TCP is connection oriented, reliable transport protocol
	- connection oriented: the two applications using TCP must establish a TCP connection with each other before they can exchange data
	- Reliability is provided by TCP by the use of checksums, timers, data sequencing and acknowledgements

- TCP assigns a sequence number to every byte transferred, and requires an ack from the other end upon receipt to guarantee reliable delivery. These sequence numbers are used to ensure proper ordering of the data and to eliminate duplicate data bytes.
- In a TCP session there are usually two streams of data (every endpoint is receiving from one and sending through the other). So an ISN (initial sequence number) is assigned to each stream, when the connection is being established

Suppose C is a client wishing to connect to the server S. This is the three-way handshake![[Pasted image 20240425195117.png]]

>1. C sends a TCP message (known as a SYN request) to S with the speacial flag SYN (SYNchronise sequence numbers) set to ON. A SYN request specifies the port number of the server that the client wants to connect to and the client's ISN (XX in this example)
>2. The server responds with its own SYN containing S's ISN (YY) and acknowledging C's SYN by specifying that the next byte expected from C is the byte numbered XX+1
>3. C acknowledges  the SYN message form S and data transfer may take place


Most TCP/IP implementations follow these rules:
- when a SYN (or FIN) segment arrives at a closed port, TCP drops the segment and sends a RST. Essentially telling the sender that the port is closed
- When a RST segment arrives for a closed port, it is simply dropped
- When a RST segment arrives for a listening port, it is simply dropped
- When a segment containing an ACK arrives for a listening port, it is dropped and an RST is sent
- when a segment with teh SYN bit off arrives at a listening port , it is dropped
- when a SYN segment arrives at a listening port, the normal three-way handshake continues by replaying SYN|ACK
- When a FIN segment arrives at a listening port, it is dropped."FIN behavior" (closed port = RST, listening port = dropped) can also be seen with the PSH and URG flags, with a TCP segment with no flags, and with all the combinations of FIN|PSH|URG

most scanning techniques are built in nmap
<font size=4>Full TCP Scanning</font>
For a long time this was the fundamnetal form of TCP port scanning.
- scanning host tries to establish regular conections using the handshake with chosen ports on the target machine. 
- Connections are started using the system call connect(), for every listening port, connect() will succeed, otherwise a -1 is returned indicating the port is unreachable.
- This method is very easily implemented since no special privelages are needed like administrator, however its very easily detectable through logs  

<font size=4>TCP SYN Scanning</font>
In this technique the scanning host sends a SYN segment to a selected port on the target machine. If the response is an RST, then the port is closed and if scheduled, a different port is probed. Else if the response is a SYN|ACK, it means that the target port is indeed listening

- This technique is frequently known as half-open scanning, because a full connection is never established
- The main advantage  of SYN scanning is that even thought it can still be detected by certain loggers, it is logged less frequently than full connections
- The tradeoff to this is that the sender, under most os's needs to custom build the entire IP packet for this scanning, usually super user or to special system calls is neeed to build these custom SYN packets



<font size=6>Stealth and Indirect Scanning</font>

Stealth scanning, does not consist of any part of the standard TCP three-way handshake, so it is very difficult to log and thus more secret than SYN scanning.
- This technique uses FIN segments to probe ports, since when a FIN segment arrives at a closed port, the receiving TCP drops the segment and sends back a RST, otherwise, when it arrives at a listening port it is simply dropped (no RST)
- closed port = RST, listening port = dropped - FIN behaviour
- Other methods such as Xmas tree and null scan modes are just variations of this, as this FIN behaviour, where (closed port = RST, listening port = dropped - FIN behaviour), can also be seen with PSH and URG flags wit a tcp segment with no flags ans with all the combinations of FIN|PSH|URG
- Xmas tree, sets the FIN, URG, PSH flags, while Null scann turns off all flags
- Stealth scanning, a method used to scan ports without being detected, typically works well with UNIX targets. However, some systems (such as Cisco, BSDI, HP/UX, MVS, and IRIX) may send resets instead of dropping packets, which can foil stealth scans. On the other hand, systems running Windows95/NT are known to always send back a RST, regardless of whether the probed port is open or closed. 


<font size=4>Indirect scanning </font>
A technique for anonymous scanning. The idea is to use the (spoofed ) IP address of a third host to disguise the real scanning system.
- Since the scanned host will react by sending or not certain segments to the spoofed host, all that is needed is to monitor the IP activity of the spoofed host to know the results of the original scan 