## Configure DHCPv6 server {#configure-dhcpv6-server}

The steps to configure DHCPv6 server are as follows:

1.  Install DHCPv6 server: sudo apt-get install isc-dhcp-server.

If there is no dhcpd6.conf file in /etc/dhcp/ directory, create and edit as shown below.

| default-lease-time 600; |
| --- |

Be sure that your server will listen for DHCP requests on the correct interface (Note: change the INTERFACE to match your own). Edit the /etc/default/isc-dhcp-server file:

INTERFACE = “eth0”;

Restart the DHCPv6 service: sudo service isc-dhcp-server6 restart.