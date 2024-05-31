![[Pasted image 20240530152349.png]]
A socket is an endpoint for communication in a network, and the Berkeley sockets API is the standard cross-platform API for managing sockets. Sockets are identified by an IP address and a port number.

- **UDP Communication**:
    
    - **Sending**: Create a socket and send data to it.
    - **Receiving**: Create a socket at a known address and read data from it.
- **TCP Communication**:
    
    - **Sending**: Create a socket, connect it to a remote socket, and send data.
    - **Receiving**: Create a socket, listen for connections, optionally create a new socket for each connection, and receive data.

A network node can engage in multiple simultaneous conversations, each managed by a separate socket. Sockets also support broadcast and multicast communications, which allow one-to-many data transmissions.

### Binding
Each socket needs a unique address. An address is a combination of an IP address and  port number

When a socket is created it assumes the IP address of the network node that created it. If a socket has an IP address but not a port number it is said to be 'unbound'. An unbound socket cannot receive data because it does not have a complete address.

When a socket has both an IP address and a port number it is said to be 'bound to a port', or 'bound to an address'. A bound socket can receive data because it has a complete address.

The process of allocating a port number to a socket is called 'binding'.

The API function [FreeRTOS_bind()](https://www.freertos.org/FreeRTOS-Plus/FreeRTOS_Plus_TCP/API/bind.html) is used to bind a FreeRTOS-Plus-TCP socket to a port number.

If [ipconfigALLOW_SOCKET_SEND_WITHOUT_BIND](https://www.freertos.org/FreeRTOS-Plus/FreeRTOS_Plus_TCP/TCP_IP_Configuration.html#ipconfigALLOW_SOCKET_SEND_WITHOUT_BIND) is set to 0 in [FreeRTOSIPConfig.h](https://www.freertos.org/FreeRTOS-Plus/FreeRTOS_Plus_TCP/TCP_IP_Configuration.html) then FreeRTOS_bind() must be used to bind a socket to a port number before the socket can be used to either send or receive data. If ipconfigALLOW_SOCKET_SEND_WITHOUT_BIND is set to 1 in FreeRTOSIPConfig.h then an unbound socket will be automatically bound to a port number the first time it attempts to send data (for UDP sockets) or connect (for TCP sockets), but can still only receive data after it has been bound.