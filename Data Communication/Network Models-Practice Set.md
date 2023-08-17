# Network Models-Practice Set

## Questions

1. What is the first principle we discussed in this chapter for protocol layering that needs to be followed to make the communication bidirectional?
	- If we want bidirectional communication, we need to make each layer so that it is able to perform two opposite tasks
2. Which layers of the TCP/IP protocol suite are involved in a link-layer switch?
	- Data Link (Layer 2)
3. A router connects three links (networks). How many of each of the following layers can the router be involved with? a. physical layer b. data-link layer c. network layer
	- Network layer
4. In the TCP/IP protocol suite, what are the identical objects at the sender and the receiver sites when we think about the logical connection at the application layer?
	- Message & segments/user datagram
5. A host communicates with another host using the TCP/IP protocol suite. What is the unit of data sent or received at each of the following layers?
	1. a. application layer: Message
	2. b. network layer: Datagram
	3. c. data-link layer: Frames
6. Which of the following data units is encapsulated in a frame?
	- datagram
7. Which of the following data units is decapsulated from a user datagram? a. a datagram b. a segment c. a message
	- message
8. Which of the following data units has an application-layer message plus the header from layer 4? a. a frame b. a user datagram c. a bit
	- user datagram
9. List some application-layer protocols mentioned in this chapter.
	1. HTTP
	2. SMTP
	3. FTP
	4. SNMP
	5. IGMP
10. If a port number is 16 bits (2 bytes), what is the minimum header size at the transport layer of the TCP/IP protocol suite?
11. What are the types of addresses (identifiers) used in each of the following layers?
	1. application layer: Names
	2. transport layer: Port
	3. network layer: IP/Logical addresses
	4. data-link layer: Link-layer addresses/MAC address
12. When we say that the transport layer multiplexes and demultiplexes application layer messages, do we mean that a transport-layer protocol can combine several messages from the application layer in one packet? Explain.
	- It does not combine multiple message into one packet. Instead, each application message is encapsulated within its own transport-layer segment, which includes the necessary header information (port).
13. Can you explain why we did not mention multiplexing/demultiplexing services for the application layer?
14. Assume we want to connect two isolated hosts together to let each host communicate with the other. Do we need a link-layer switch between the two? Explain.
15. If there is a single path between the source host and the destination host, do we need a router between the two hosts?
	- A router is not necessary between the two hosts.

## Problems

1. Answer the following questions about Figure 2.2 when the communication is from Maria to Ann:
	1. What is the service provided by layer 1 to layer 2 at Maria’s site?
	2. What is the service provided by layer 1 to layer 2 at Ann’s site?
2. Match the following to one or more layers of the TCP/IP protocol suite:
	1. route determination: ~~Transport~~ Network
	2. flow control: Data link and Transport
	3. connection to transmission media: Physical
	4. providing services for the end user: Application
3. Match the following to one or more layers of the TCP/IP protocol suite:
	1. creating user datagrams: Transport
	2. responsibility for handling frames between adjacent nodes: Data link
	3. transforming bits to electromagnetic signals: Physical
4. In Figure 2.10, when the IP protocol decapsulates the transport-layer packet, how does it know to which upper-layer protocol (UDP or TCP) the packet should be delivered?
	1. This is accomplished through the use of the protocol field in the IP header
		1. Segment - TCP
		2. User datagram - UDP
5. Assume that a private internet requires that the messages at the application layer be encrypted and decrypted for security purposes. If we need to add some information about the encryption/decryption process (such as the algorithms used in the process), does it mean that we are adding one layer to the TCP/IP protocol suite?
	1. No, the encryption and decryption can be implemented inside application layer.
![[Pasted image 20230817125155.png]]
