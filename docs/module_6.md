### IPv4 Address Structure

##
# Network and Host Portions
    IPv4 Address
        An IPV4 address is a 32-bit hierarchical address that is made up of a network portion and a host portion. When determining the network portion versus the host portion, you must look at the 32-bit stream, as shown in the figure below.

            ![IPv4 32-bit stream](images/32-bit.png)

        The bits within the network portion of the address must be identical for all devices that reside in the same network. The bits within the host portion of the address must be unique to identify a specific host within a network. If two hosts have the same bit-pattern in the specified network portion of the 32-bit stream, those two hosts will reside in the same network.

        But how do hosts know which portion of the 32-bits identifies the network and which identifies the host? That is the role of the subnet mask.

# The Subnet Mask
    Assigning an IPv4 address to a host requires the following:

        IPv4 address
            This is the unique IPv4 address of the host
        Subnet mask
            This is used to identify the network/host portion of the IPv4 address

        
