# Secure the Devices
## Password Recommendations
To protect network devices, it is important to use strong passwords. Below are standard guidelines to follow:
- Use a password length of at least eight characters, preferably 10 or more characters. A longer password is a more secure password.
- Make passwords complex. Include a mix of uppercase and lowercase letters, numbers, symbols, and spaces, if allowed.
- Avoid passwords based on repetition, common dictionary words, letter or number sequences, such as birthdates, ID numbers, ancestor names, or other easily identifiable pieces of information.
- Deliberately misspell a password. For example, Smith = Smyth = 5mYth or Security = 5ecur1ty.
- Change passwords often. If a password is unknowingly compromised, the window of opportunity for the threat actor to use the password is limited.
- Do not write passwords down and leave them in obvious places such as on the desk or the monitor.

## Secure Remote Access
There are multiple ways to access a device to perform  configuration tasks. One of these ways is to use a PC attached to the console port on the device. This type of connection is frequently used for initial device configuration.

Setting a password for console connection access is done in global configuration mode. These commands prevent unauthorized users from accessing user mode from the console part.

    witch(config)# line console 0
    Switch(config-line)# password password
    Switch(config-line)# login

When the device is connected to the network, it can be accessed over the network connection using SSH or Telnet. **SSH** is the preferred method because it is more secure. When the device is accessed through the network, it is considered a vty connection. The password must be assigned to the vty port. The following configuration is used to enable SSH access to the switch.

    Switch(config)# line vty 0 15
    Switch(config-line)# password password
    Switch(config-line)# transport input ssh
    Switch(config-line)# login

# Configure the Default Gateway
## Default Gateway on a Host
If a local network has only one router, it will be the gatewau router and all hosts and switches on the network must be configured with this information. If a local network has multiple routers, we must select of of them to be the default gateway router.

For an end device to communicate over the network, it must be configured with the correct IP address information, including the default gateway address. The default gateway is only used when the host wants to send a packet to a device on another network. The default gateway address is generally the router interface address attached to the local network of the host. The IP address of the host device and the router interface address must be in the same network.

## Default Gateway on a Switch
A switch that interconnects client computers is typically a Layer 2 device. As such, a Layer 2 switch does not require an IP address to function properly. However, an IP configuration can be configured on a switch to give an administrator remote access to the switch.

To connect to and manage a switch over a local IP network, it must have a switch virtual interface (SVI) configured. The SVI is configured with an IPv4 address and subnet mask on the local LAN. The switch must also have a default gateway address configured to remotely manage the switch from another network.

The default gateway address is typically configured on all devices that will communicate beyond their local network.

To configure an IPv4 default gateway on a switch, use the **default-gateway**. The *ip-address* that is configured is the IPv4 address of the local router interface connected to the switch.

**Note**: Packets originating from host computers connected to the switch must already have the default gateway address configured on their host computer operating systems.

A workgroup switch can also be configured with an IPv6 address on an SVI. However, the switch does not require the IPv6 address of the default gateway to be configured manually. The switch will automatically receive its default gateway from the ICMPv6 Router Advertisement message from the router.
