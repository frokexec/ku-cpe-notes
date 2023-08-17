# Introduction-Practice Sets

## Questions

1. Identify the five components of a data communications system
	- ANSWER
		1. Message - Information or data to be communicated
		2. Sender
		3. Receiver
		4. Transmission medium
		5. Protocol - Set of rules that govern data communication
2. What are the three criteria necessary for an effective and efficient network?
	- ANSWER
		- Performance
		- Reliability
		- Security
3. What are the advantages of a multipoint connection over a point-to-point one?
	- ANSWER
		- **Advantage**: More than two specific devices can use the link
4. What are the two types of line configuration?
	- ANSWER
		- Point-to-Point: dedicated link between 2 devices
		- Multipoint/Multidrop: > 2 specific devices share a single link. Capacity of the channel is shared
			- Spatially: use the link simultaneously
			- Timeshared: Users must take turns
5. Categorize the four basic topologies in terms of line configuration.
	- ANSWER
		- **Mesh Topology** - Point-to-Point: 1 to many
		- **Star Topology** - each device has a dedicated Point-to-Point link only to a central controller (hub). Examples: LAN
		- **Bus Topology** - Multipoint, one long cable acts as a backbone to link all the devices and droplines for each devices
		- **Ring Topology** - Each device has a dedicated point-to-point connection with only the 2 devices on either side of it. A signal is passed along the ling in one direction, from device to device.
6. What is the difference between half-duplex and full-duplex transmission modes?
	- ANSWER
		- **Half-duplex** - Data can be transmit to any direction at separate time, both stations can transmit and receive, but not at the same time. Examples: Walkie-talkies
		- **Full-duplex** - Data can be send to any direction at the same time, both stations can transmit and receive simultaneously. Examples: telephone
7. Name the four basic network topologies, and cite an advantage of each type.
	- ANSWER
		- **Mesh Topology** - No traffic problems, robust, privacy and security
		- **Star Topology** - Robust, can monitor link problems
		- **Bus Topology** - Ease of installation (less cabling)
		- **Ring Topology** - Ease of installation, fault isolation: alarm if one device does not receive a signal within a specified period
8. For n devices in a network, what is the number of cable links required for a mesh, ring, bus, and star topology?
	- ANSWER
		- **Mesh Topology** - duplex: `n(n-1)/2`
		- **Star Topology** - `n`
		- **Bus Topology** - `1 backbone + n droplines`
		- **Ring Topology** - `n-1`
9. What are some of the factors that determine whether a communication system is a LAN or WAN?
	- ANSWER
		- **LAN** - usually privately owned and connects some hosts in a local area. It interconnects hosts.
		- **WAN** - wider than LAN, spanning a tow, a state, a country, or even the world. It interconnects devices such as switches, routers, or modems.
10. What is an internet? What is the Internet?
	- ANSWER
		- An internet is an interconnection of networks. The Internet is the name of a specific worldwide network
11. Why are protocols needed?
	- ANSWER
		- A protocol defines *what* is communicated, in *what way* and *when*. This provides accurate and timely transfer of information between different devices on a net-work
12. In a LAN with a link-layer switch (Figure 1.8b), Host 1 wants to send a message to Host 3. Since communication is through the link-layer switch, does the switch need to have an address? Explain.
	- ANSWER
		- The switch need to have an address to Host 3 so the data can be directly transmitted to from Host 1 to Host 3
13. How many point-to-point WANs are needed to connect n LANs if each LAN should be able to directly communicate with any other LAN?
	- ANSWER
		- `n(n-1)/2` just like mesh
14. When we use local telephones to talk to a friend, are we using a circuit-switched network or a packet-switched network?
15. When a resident uses a dial-up or DLS service to connect to the Internet, what is the role of the telephone company?
16. What is the first principle we discussed in this chapter for protocol layering that needs to be followed to make the communication bidirectional?
17. Explain the difference between an Internet draft and a proposed standard.
18. Explain the difference between a required RFC and a recommended RFC.
19. Explain the difference between the duties of the IETF and IRTF.

## Problems

1. What is the maximum number of characters or symbols that can be represented by Unicode?: 2^2
2. A color image uses 16 bits to represent a pixel. What is the maximum number of different colors that can be represented?: 2^16
3. Assume six devices are arranged in a mesh topology. How many cables are needed? How many ports are needed for each device? `6(6-1)/2` cables, `5` ports
4. For each of the following four networks, discuss the consequences if a connection fails.
	1. Five devices arranged in a mesh topology: Only single communication link fails
	2. Five devices arranged in a star topology (not counting the hub): Only single communication link fails
	3. Five devices arranged in a bus topology: All transmission stops if the failure is in the bus
	4. Five devices arranged in a ring topology: It disable the whole network
5. We have two computers connected by an Ethernet hub at home. Is this a LAN or a WAN? Explain the reason.: LAN
6. In the ring topology in Figure 1.7, what happens if one of the stations is unplugged?: Theoretically, in a ring topology, unplugging one station, interrupts the ring. How-ever, most ring networks use a mechanism that bypasses the station; the ring can continue its operation.
7. In the bus topology in Figure 1.6, what happens if one of the stations is unplugged?: Unplugging a station has no effect on the operation of the rest of the network.
8. Performance is inversely related to delay. When we use the Internet, which of the following applications are more sensitive to delay?
	1. Sending an e-mail: not very sensitive
	2. Copying a file: not very sensitive
	3. Surfing the Internet: sensitive
9. When a party makes a local telephone call to another party, is this a point-to-point or multi-point connection? Explain the answer.: Point-to-Point
10. Compare the telephone network and the Internet. What are the similarities? What are the differences?
		The telephone network was originally designed for voice communication; the Internet was originally designed for data communication. The two networks are similar in the fact that both are made of interconnections of small networks. The telephone network, as we will see in future chapters, is mostly a circuit-switched network; the Internet is mostly a packet-switched network.
