## Configure DHCPv4 server {#configure-dhcpv4-server}

The steps to configure DHCPv4 server are as follows:

Install DHCPv4 server: sudo apt-get install isc-dhcp-server.

Edit /etc/dhcp/dhcpd.conf file as shown below.

| default-lease-time 600; |
| --- |

Be sure that your server will listen for DHCP requests on the correct interface (Note: change the INTERFACE to match your own). Edit the /etc/default/isc-dhcp-server file:

INTERFACE = “eth0”;

Restart the DHCPv4 service: sudo service isc-dhcp-server restart.