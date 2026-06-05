# ICMP Messages
Although IP is only a best-effort protocol, the TCP/IP suite does provide for error messages and informational messages when communicating with another IP device. These messages are sentusing the services of ICMP. The purpose of these messages is to provide feedback about issues related to the processing of IP packets under certain conditions, not to make IP reliable. ICMP messages are not required and are often not allowed within a network for security reasons.

ICMP is available for both IPv4 and IPv6. ICMPv4 is the messaging protocol for IPv4.ICMPv6 provides these same services for IPv4 but includes additional functionalitu.

The types of ICMP messages, and the reasons why they are sent are extensive. The ICMP messages common to both ICMPv4 and ICMPv6 include:
- Host reacability
- Destination or Service Unreachable
- Time exceeded

# Host Reachability
An ICMP Echo Message can be used to test the reachability of a host on an IP network. The local host sends an ICMP Echo Request to a host. If the host is available, the destination host responds with an Echo Reply.
