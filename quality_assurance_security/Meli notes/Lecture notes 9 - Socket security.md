# Socket security

- Sockets are the heart of applications communicating over TCP (v6 will mitigate some of these problems)

#### Server hijacking
- An app allows a local user to intercept/manipulate info meant for a server that the local user didn't start themselves


A server starts up, creates a socket and binds that socket according to the protocol it wants to work with.
- With TCP or UDP, it binds to a port
- A port is usually represented by an unsigned short (16-bit) integer, ranging 0- 65535

```
int bind (
SOCKET s;
const struct sockaddr *name;
int namelen;//or socklen_t
);
```

If we are writing code for the v4 variant:
```
struct sockaddr_in {
short sin_family;
unsigned short sin_port;
struct in_addr sin_addr;
char sin_zero[8];
}
```


With a server, you will usually specify a port to listen on, but the problem is with sin_addr. Documentation tells us if we bind to INADDR_ANY(0), we will listen to all network interfacess.

It is possible to bind more than one socket to the same port
- The sockets library decides who wins and gets the packet via determining which binding is more specific
	- e.g. a server with IP's 157.33.32.55 and 172.100.92.45, the socket software would pass incoming data on that socket to an application binding to 172.100.92.45 rather than to another app binding to INADDR_ANY. The solution is to bind to every available ip on your server, which can be an annoyance.
### Binding Specificity

- **Specific Binding**: More precise, thus higher priority.
- **Generic Binding**: Less precise, lower priority unless no specific binding exists for that IP and port.

![[Pasted image 20240522134921.png]]
### Slide 2: SO_EXCLUSIVEADDRUSE and Security

- **Concept**: Use of the `SO_EXCLUSIVEADDRUSE` socket option.
- **Context**:
    - Windows NT SP 4: Utilizes `SO_EXCLUSIVEADDRUSE` to ensure a socket is not shared.
    - Windows 2003: Uses a Discretionary Access Control List (DACL) applied to the socket, making the previous solution unnecessary.
    - FreeBSD: No equivalent option exists, presenting a security problem.
    - Linux: Port reuse is allowed with `SO_REUSEADDR`, but without it, no possibility of reuse exists, hence no vulnerability.

### Slide 3: Transport Protocols with Sockets

- **Concept**: Sockets can be used with transport protocols that provide a message stream.
- **Example**: Datagram Congestion Control Protocol (DCCP)
    - **DCCP**: A version of UDP with congestion control, offering a message stream rather than a byte stream.
- **Context**: Sockets provide flexibility to work with various protocols, enhancing their utility in managing network communication with or without congestion control.

###### Message Stream vs Byte Stream

###### Byte Stream

- **Definition**: A continuous flow of data without any inherent message boundaries.
- **Characteristics**:
    - Data is sent and received as a continuous sequence of bytes.
    - The application is responsible for interpreting and processing the data stream correctly.
    - Common in protocols like TCP.
- **Example**:
    - When sending a file over a TCP connection, the file is split into a stream of bytes. The receiving application must reassemble these bytes correctly to reconstruct the file.

###### Message Stream

- **Definition**: Data is sent and received in discrete chunks or messages.
- **Characteristics**:
    - Each message is a self-contained unit of data.
    - The transport protocol ensures that message boundaries are preserved.
    - Common in protocols like UDP and DCCP (Datagram Congestion Control Protocol).
- **Example**:
    - Sending individual log entries as separate messages over UDP. Each log entry is a distinct message, and the boundaries are clear.


### Slide 4: Application-Specific Socket Use

- **Concept**: Applications that handle groups of related streams.
- **Example**: Web browsers fetching related objects from the same server.
- **Issue**:
    - Each object fetch uses a separate stream.
    - Congestion control applies per stream rather than across the group.
    - This approach is suboptimal because it doesn't consider the combined impact of all streams, leading to potential inefficiencies in congestion management.


TCP uses a three way handshake before a client attempts to connect with the server
- The server must first bind to and listen to app to open it up for connections. This is called a **passive open**
- Once a passive open is established, a client may initiate an active open
#### Establishing a connection TCP

Three way handshake occurs:
- SYN: The active open is performed by the client sending a SYN (synchonise packet) to the server
- SYN-ACK: in response the server replies with a SYN-ACK
- ACK: Finally the client sends back an ACK to the server


TCP window size: it is a tcp option that iss simply an advertisement of how much data (in bytes) the receiving device is willing to receive at any point in time. The receiving device can use this value to control the flow wof data


### TCP window attacck
A nasty attack allowed by the TCP RFCs is an intentional variant on the silly windows syndrome.

TCP window attack is an intentional exploitation of the TCP winddow size mechanism to disrupt normal data flow

- **Sender's Role**: The server (sender) monitors the window size advertised by the client (receiver).
- **Receiver's Role**: The client advertises its window size in TCP ACK packets to inform the server how much data it can handle.

- TCP connections use a window size decleration in ACK packets to help the server send data no faster than the client can receive it
- If the client's buffers are completely full, it can send the server a size of 0, causing the server to pause before sending any more data
- Steps for the above:
	- malicious client creates a connection
	- sets the window size to a very small number or 0, causing the server to send data very slowly and with very high overhead
	- For every few bytes of data there will be around 40 bytes worth of TCP and IP headers
		- this could cause apps to start blocking when it tries to send data, consuming your worker threads
Mitigation:
**If a client takes too much time to process what you've been sending, its time to close and shutdown the socket**

![[Pasted image 20240522140055.png]]

