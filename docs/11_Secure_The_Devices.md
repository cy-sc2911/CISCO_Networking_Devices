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

Setting a password for console connectiona access is done in global configuration mode. These commands prevent unauthorized users from accessing user mode from the console part.

    witch(config)# line console 0
    Switch(config-line)# password password
    Switch(config-line)# login

When the device is connected to the network, it can be accessed over the network connection using SSH or Telnet. SSH is the preferred method because it is more secure. When the device is accessed through the network, it is considered a vty connection. The password must be assigned to the vty port. The following configuration is used to enable SSH access to the switch.

    Switch(config)# line vty 0 15
    Switch(config-line)# password password
    Switch(config-line)# transport input ssh
    Switch(config-line)# login

# Configure the Default Gateway
