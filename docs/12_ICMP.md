# ICMP
## ICMPv4 and ICMPv6 Messages
Although IP is only a best-effort protocol, the TCP/IP suite does provide for error messages and informational messages when communicating with another IP device. These messages are sentusing the services of ICMP. The purpose of these messages is to provide feedback about issues related to the processing of IP packets under certain conditions, not to make IP reliable. ICMP messages are not required and are often not allowed within a network for security reasons.

ICMP is available for both IPv4 and IPv6. ICMPv4 is the messaging protocol for IPv4.ICMPv6 provides these same services for IPv4 but includes additional functionalitu.

The types of ICMP messages, and the reasons why they are sent are extensive. The ICMP messages common to both ICMPv4 and ICMPv6 include:
- Host reacability
- Destination or Service Unreachable
- Time exceeded

## Host Reachability
An ICMP Echo Message can be used to test the reachability of a host on an IP network. The local host sends an ICMP Echo Request to a host. If the host is available, the destination host responds with an Echo Reply.

## Destination or Servicec Unreachable
When a host or gateway receives a packet that it cannot deliver, it can use an ICMP Destination Unreachable message to notify the source that the destination or service is unreachable. The message will include a code that indicates why the packet cannot be delivered.

Some of the Destination Unreachable codes for ICMPv4 are as follows:
- 0 - Net unreachable
- 1 - Host unreachable
- 2 - Protocol unreachable
- 3 - Port unreachable

Some of the Destination Unreachable codes for ICMPv6 are as follows:
- 0 - No route to destination
- 1 - Communication with the destination is administratively prohibited (e.g., firewall)
- 2 - Beyond scope of the source address
- 3 - Address unreachable
- 4 - Port unreachable

**Note**: ICMPv6 has similar but slightly different codes for Destination Unreachable messages.

## Time Exceeded
An ICMPv4 Time Exceeded message is used by a router to indiccate that a packet cannot be forwarded because the Time to Live (TTL) filed of a packet was decremented to 0. If a router receives a packet and decrements the TTL field in the IPv4 packet to zero, it discards the packet and sends a Time Exceeded message to the source host.

ICMPv6 also sends a Time Exceeded message if the router cannot forward an IPv6 packet because the packet has expired. Instead of the IPv4 TTL field, ICMPv6 uses the IPv6 Hop Limit field to determine if the packet has expired.

**Note**: Time Exceeded messages are used by the **traceroute** tool.

## ICMPv6 Messages
The informational and error messages found in ICMPv6 are very similar to the control and error messages implemented by ICMPv4. However, ICMPv6 has new features and improved functionality not found in ICMPv4. ICMPv6 messages are encapsulated in IPvv6.

ICMPv6 includes four new protocols as part of the Neighbor Discovery Protocol (ND or NDP).

Messaging between an IPv6 router and an IPv6 device, including dynamic address allocation are as follows:
- Router Solicitation (RS) message
- Router Advertisement (RA) message

Messaging between IPv6 devices, including duplicate address detection and address resolution are as follows
- Neighbor Solicitation (NS) message
- Neighbor Advertisement (NA) message

**Note**: ICMPv6 ND also includes the redirect message, which has a similar function to the redirect message used in ICMPv4.

# Ping and Traceroute Testing
## Ping
Ping is an IPv4 and IPv6 testing utility that uses ICMP echo request and echo reply messages to test connectivity between hosts.

To test connectivity to another host on a network, an echo request is sent to the host address using the **ping** command. If the host at the specified address receives the echo request, it responds with an echo reply. As each echo reply is received, **ping** provides feedback on the time between when the request was sent and when the reply was received. This can be measure of network performance.

Ping has a timeout value for the reply. If a reply is not received within the timeout, ping provides a message indicating that a response was not received. This may indicate that there is a problem, but could also indicate that security features blocking ping messages have been enabled on the network. It is common for the first ping to timout if address resolution (ARP or ND) needs to be performed before sending the ICMP Echo Request.

After all the requests are sent, the ping utility provides a summary that includes the success rate and average round-trip time to the destination. Type of connectivity tests performed with **ping** include:
- Pinging the local loopback
- Pinging the default gateway
- Pinging the remote host

## Ping the Loopback
Ping can be used to test the internal configuration of IPv4 or IPv6 on the local host. To perform this test, **ping** the local loopback address of 127.0.0.1 for IPv4 (::1 for IPv6).

A response from 127.0.0.1for IPv4, or ::1 for IPv6, indicates that IP is properly installed on the host. This response comes from the network layer. This response is not, however, an indication that the addresses, masks, or gateways are properly configured. Nor does it indicate anything about the status of the lower layer of the network stack. This simply tests IP down through the network layer of IP. An error message indicates that TCP/IP is not operational on the host.

## Ping the Default Gateway
**Ping** can also be use to test the ability of a host to communicate on the local network. This is generally done by pining the IP address of the default gateway of the host. A successful **ping** to the default gateway indicated that the host and the router interface serving as the default gateway are both operational on the local network.

For this test, the defauly gateway address is most often used because the router is normally always operational. If the default gateway address does not respond, a **ping** can be sent to the IP address of another host on the local network that is known to be operational.

If either the default gatewau or another host responds, then the local host can successfully communicate over the local network. If the defauly gateway does not respond but another host does, this could indicate a problem with the router interface serving as the default gateway.

One possibility is that the wrong default gateway address have been configured on the host. Another possibilty is that the router interface may be fully operational but have security applied to it that prevents it from processing or responding to ping requests.

## Ping a Remote Host
Ping can also be used to test the ability of a local host to communicate across an internetwork. The local host can ping an operational IPv4 host of a remote network. The router uses its IP routing table to forward the packets.

If this ping is successful, the operation of a large piece of the internetwork can be verified. A successful **ping** across the internetwork confirms communication on the local network, the operation of the router serving as the default gateway, and the operation of all other routers that might be in the path between the local network and the network of the remote host.

Additionally, the functionality of the remote host can be verified. If the remote host could not communicate outside of its location network, it would not have responded.

**Note**: Many network administrators limit or prohibit the entry of ICMP messages into the corporate network; therefore, the lack of a **ping** response could be due to security restrictions.

## Traceroute - Test the Path
Ping is used to test connectivity between two hosts but does not provide information about the details of devices between the hosts. Traceroute (**tracert**) is a utility that generates a list of hops that were successfully reached along the path. This list can provide important verification and troubleshooting information. If the data reaches the destination, then the trace lists the interface of every router in the path between the hosts. If the data fails at some hop along the way, the address of the last router that responded to the trace can provide an indication of where the problem or security restrictions are found.

### Round Trip Time (RTT)
Using traceroute provides rund0trip time for each hop along the path and indicates if a hop fails to respond. The round-trip time is the time a packet takes to reach the remote host and for the respons from the host to return, An asterisk (*) is used to indicate a lost or unreplied packet.

This information
