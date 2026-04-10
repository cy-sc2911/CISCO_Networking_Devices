# DNS Services
In data networks, devices are labeled with numeric IP addresses to send and receive data over networks.
Domain names were created to convert the numeric address into a simple, recognizable name.

On the internet, fully-qualified domain names (FQDNs), such as http://www.cisco.com, are much easier for people to remember than 198.133.219.25 (the actual numeric address for the server). If Cisco decides to change the numeric address of www.cisco.com, it is transparent to the user because the domain name remains the same. The new address is simply linked to the existing domain name and connectivity is maintained.

The DNS protocol defines an automated service that matches resources names with the required numeric network address. It includes the format for queries, response, and data. The DNS protocol communications use a single format called a message. This message format is used for all types of client queries and server responses, error messages, and the transfer of resource record information between servers.

## DNS Message Format
The DNS server stores different types of resource records that are used to resolve names. These records contain the name, address, and type of record. Some of these record types are:
- **A** - An end device IPv4 address
- **NS** - An authoritative name server
- **AAAA** - An end device IPv6 address (pronounced quad-A)
- **MX** - A mail exchange record

When a client makes a query, the server DNS process first looks at its own records to resolve the name. If it is unable to resolve the name by using its stored records, it contacts other servers to resolve the name. After a match is found and returned to the original requesting server, the server temporarily stores the numbered address in the event that the same name is requested again.

The DNS client service on Windows PCs also stores previously resolved names in memory. The **ipconfig / displaydns** command displays all of the cached DNS entries.

DNS uses the same message format between servers, consisting of a question, answer, authority, and additional information for all types of client queries and server responses, error messages, and transfer of resource record information.

|Question|The question for the name server|
|--------|--------------------------------|
|Answer|Resource Records answering the question|
|Authority|Resource Records poiting toward an authority|
|Additional|Resource Records holding additional information|

## DNS Hierarchy
The DNS protocol uses a hierarchical system to create a database to provide name resolution. DNS uses domain names to form the hierarchy.

The naming structure is broken down into small, manageable zones. Each DNS server maintains a specific database file and only responsible for managing name-to-IP mappings for that small portion of the entire DNS structure. When a DNS server receives a request for a name translation that is not within its DNS zone, the server forwards the request to another DNS server within the proper zone for translation. DNS is scalable because hostname resolution is spread across multiple servers.

The different top-level domains represent either the type of organization or the country of origin. Examples of top-level domains are as follows:
- **.com** - a business or industry
- **.org** - a non-profit organization
- **.au** - Australia
- **.co** - Colombia

## The nslookup Command
When configuring a network device, one or more DNS server addresses are provided that the DNS client can use for name resolution. Usually, the ISP provides the addresses to use for the DNS servers. When a user application requests to connect to a remote device by name, the requesting DNS client queries the name server to resolve the name to a numeric address.

Computer operating systems also have a utility called nslookup that allows the user to manually query the name servers to resolve a given host name. This utility can also be used to troubleshoot name resolution issues and to verify the current status of the name servers.

When the nslookup command is issued, the default DNS server configured to your host is displayed. The name of a host or domain can be entered at the nslookup prompt. The nslookup utility has many options available for extensive testing and verification of the DNS process.

    C:\Users> nslookup
    Default Server:  dns-sj.cisco.com
    Address:  171.70.168.183
    > www.cisco.com
    Server:  dns-sj.cisco.com
    Address:  171.70.168.183
    Name:    origin-www.cisco.com
    Addresses:  2001:420:1101:1::a
            173.37.145.84
    Aliases:  www.cisco.com
    > cisco.netacad.net
    Server:  dns-sj.cisco.com
    Address:  171.70.168.183
    Name:  cisco.netacad.net
    Address:  72.163.6.223
    >

# DHCP Services
## Dynamic Host Configuration Protocol
The DHCP for IPv4 service automates the assignment of IPv4 addresses, subnet masks, gateways, and other IPv4 networking parameters. This is refered to as dynamic addressing. The alternative to dynamic addressing is static addressing. When using static addressing, the network administrator manually enters IP address information on hosts.

When a host connects to the network, the DHCP server is contacted, and an address is requested. The DHCP server chooses an address from a configured range of addresses called a pool and assigns (leases) it to the host,

On larger networks, or where the user population changes frequently, DHCP is preferred for address assignment. New users may arrive and need connectionsm; others may have new computers that must be connected. Rather than use static addressing for each connection, it is more efficient to habe IPv4 addresses assigned automatically using DHCP.

DHCP can allocate IP addresses for a configurable period of time, called a lease period. The lease period is an important DHCP setting. When the lease period expires or the DHCP server gets a DHCPRELEASE message the address is returned to the DHCP pool for reuse. Users can freely move from location to location and easily re-establish network connections through DHCP.

Various types of devices can be DHCP servers. The DHCP server in most medium-to-large networks is usually a local, dedicated PC-based server. With home networks, the DHCP server is usually located on the local router that connects the home network to the ISP.

Many networks use both DHCP and static addressing. DHCP is used for general purpose hosts, such as end user devices. Static addressing is used for network devices, such as gateway routers, switches, servers, and printers.

DHCP for IPv6 (DHCPv6) provides similar services for IPv6 clients. One important difference is that DHCPv6 does not provide a default gateway address. This can only be obtained dynamically from the Router Advertisement message of the router.

## DHCP Messages
When an IPv4 DHCP-configured device boots up or connects to the network, the client broadcasts a DHCP discover (**DHCPDISCOVER**) message to identify any available DHCP servers on the network. A DHCP server replies with a DHCP offer (**DHCPOFFER**) message, which offers a lease to the client. The offer message contains the IPv4 address and subnet mask to be assigned, the IPv4 address of the DNS server, and the IPv4 address of the default gateway. The lease offer also includes the duration of the lease.

The client may receive multiple DHCPOFFER messages if there is more than one DHCP server on the local network. Therefore, it must choose between them, and sends a DHCP request (**DHCPREQUEST**) message that identifies the explicit server and lease offer that the client is accepting. A client may also choose to request an address that it had previously been allocated by the server.

Assuming that the IPv4  address requested by the client, or offered by the server is still available, the server returns a DHCP acknowledgement (**DHCPACK**) message that acknowledges to the client that the lease has been finalized. If the offer is no longer valid, then the selected server responds with a DHCP negative acknowledgement (**DHCPNAK**) message. If a DHCPNAK message is returned, then the selection process must begin again with a new DHCPDISCOVER message being transmitted. After the client has the lease, it must be renewed prior to the lease expiration through another DHCPREQUEST message.

The DHCP server ensures that all IP addresses are unique (the same IP address cannot be assigned to two different network devices simultaneously). Most ISPs use DHCP to allocate addresses to their customers.

DHCPv6 has a set of messages that is similar to those for DHCPv4. The DHCPv6 messages are **SOLICIT**, **ADVERTISE**, **INFORMATION REQUEST**, and **REPLY**.

NOTE: **DHCP** automates the assignment of IP addresses, subnet masks, gateways, and other IPv4 networking parameters. **ARP** automates the process for discovering the MAC address of the destination. **DNS** automates the process for discovering the IP address for a domain name. **NAT** automates the translation of private and public IP addresses.


