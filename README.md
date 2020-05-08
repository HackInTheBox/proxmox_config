#!/bin/bash
# Use the commands in this file to run the appropriate updates once the ETC files have been copied to the right places.
# Do not edit these files haphazardly, as they can lock you out of the server completely.
# Your only workaround may be to physically attach a keyboard and mouse and monitor to the host and manage at the terminal.
# Good luck!

# make the "stop" command executable
chmod +x /root/stop

# Update repository after updating /etc/apt
apt update

# Optional but recommended
apt upgrade

# Install the network management packages
apt install ifupdown2 iperf3

# Reset the default interfaces after editing the DHCP in /etc/network/interfaces
# Ensure your interface names are appropriate
ifdown eno1
ifdown vmbr0
ifup eno1
ifup vmbr0

# Update boot configuration files after editing /etc/default/grub
update-grub

# Reboot to ensure all changes take effect
reboot