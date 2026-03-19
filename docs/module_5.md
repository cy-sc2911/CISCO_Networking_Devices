### Network Layer Characteristics

## Data Encapsulation

## The Network Layer
    Network Layer Protocols
        The network layer, or OSI Layer 3, provides services to allow end devices to exchange data across networks. IP version 4 (IPv4) and IP version 6 (IPv6) are the principle network layer communication protocols. Other network layer protocols include routing protocols such as Open Shortest Path First (OSPF) and messaging protocols such as Internet Control Message Protocols (ICMP).

        To accomplist end-to-end communications across network boundaries, network layer protocols perform four basic operations:

            Addressing end devices
                End devices must be configured with a unique IP address for identification on the network.

            Encapsulation
                The network layer encapsulates the protocol unit (PDU) from the transport layer into a packet. The encapsulation process adds IP header information, such ash the IP address of the source (sending) and destination (receiving) hosts. The encapsulation process is performed by the source of the IP packet.

            Routing
                The network layer provides services to direct the packets to a destination host on another network. To travel to other networks, the packet must be processed by a router. The role of a router is to select the best path and direct packets toward the destination host in a process known as routing. A packet may cross many routers before reaching the destination host. Each router a packet crosses to reach the destination host is called a hop.

            De-encapsulation
                When the packet arrives at the network layer of the destination host, the host checks the IP header of the packet. If the destination IP address within the header matches its own IP address, the IP header is removed from the packet. After the packet is de-encapsulated by the network layer, the resulting Layer 4 PDU is passed up to the appropriate service at the packet layer. The de-encapsulation process is performed by the destination host of the IP packet.

        Unlike the transport layer (OSI Layer 4), which manages the data transport between the processes running on each host, network layer communication protocols (i.e., IPv4 and IPv6) specify the packet structure and processing used to carry the data from one host to another host. Operating without regard to the data carried in each packet allows the network packets for multiple types of communication between multiple hosts.

            Example:
                Host A to Host B
                    Data — Layer 7 (Application)
                    Segment — Layer 4 (Transport) — TCP/UDP header added
                    Packet — Layer 3 (Network) — IP header added
                    Frame — Layer 2 (Data Link) — MAC header/trailer added
                            Layer 1 (Physical) — frame converted into Bits and physically transmitted to Host B

                    Data → Segment → Packet → Frame → Bits
                    (L7)    (L4)      (L3)     (L2)    (L1)

# IP Encapsulation
    IP encapsulates the transport layer (the layer just above the network layer) segment or other data by adding an IP header. The IP header is used to deliver the packet to the destination host.

    The process of encapsulating data layer by layer enables the services at the different layers to develop and scale without affecting the other layers. This means the transport layer segments can be readily packaged by IPv4 and IPv6 or by any new protocol that might be developed in the future.

    The IP header is examined by Layer 3 devices (i.e., routers and Layer 3 switches) as it travels across a network to its destination. It is important to note, that the IP addressing information remains the same from the time the packet leaves the source host until it arrived at the destination host, except when translated by the device performing Network Address Translation (NAT) for IPv4.

    Routers implement routing protocols to route packets between networks. The routing performed by these intermediary devices examines the network layer addressing in the packet header. In all cases, the data portion of the packet, that is, the encapsulated transport layer PDU or other data, remains unchanged during the network layer processes.


