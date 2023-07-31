# Communications in Client-Server Systems

### Sockets

Sockets are a programming interface that allows processes to communicate over a network, either locally or across different machines. They provide a standard mechanism for IPC between processes running on different devices, using different OS, or even different networks.

- Concatenation of IP address and _port_ - a number included at start of message packet to differentiate network services on a host
- Communication consists between a pair of sockets
- All ports below 1024 are used for standard services
- Special IP address 127.0.0.1 (_loopback_) to refer to system on which process is running

#### Types of sockets

- **Transmission Control Protocol (TCP)**
	- Reliable, connection-oriented
	- The data is sent _in streams_, _ensuring that all data arrives_ in the correct order and without errors.
	- Is well-suited for application that require data integrity
		- Web browsers
		- Email clients
		- File transfer applications
- **User Datagram Protocol (UDP)**
	- Unreliable, connectionless communication
	- Data is sent as _individual packets_, and there is _no guarantee_ of delivery, order, or error checking.
	- Used in applications where speed and reduced overhead are critical than data reliability
		- Video streaming
		- Online gaming
		- DNS

### Remote Procedure Calls (RPC)

A protocol that allows a program running on one device to call a subroutine or function (a procedure) on another device, as if the function was a local procedure.
In other words, RPC enables IPC between processes running on different machines over a network

- RPC abstracts procedure calls between processes on networked systems
	- Uses ports for service differentiation
- _Stubs_ - client-side proxy for the actual procedure on the server
- The _client-side stub_ locates the server and _marshalls_ the parameters
- The _server-side stub_ receives this message, unpacks the marshalled parameters, and performs the procedure on the server

_**Marshalling**_ is a specific form of serialization focused on _preparing data for network communication_

![[Pasted image 20230728225353.png]]

- Data representation handled via _External Data Representation (XDR)_ format to account for _different architectures_
	- Platform Independence
	- Data Type Representation
	- Language Independence
	- Compactness and Efficiency
	- Endianness handling
 - Messages can be delivered _exactly once_ rather than _at most once_
 - OS typically provides a rendezvous (or _matchmaker_) service to connect client and server

_**The External Data Representation (XDR)**_ defines a _standard representation for data in the network_ to support heterogeneous network computing

![[Pasted image 20230728231937.png|Execution of RPC]]