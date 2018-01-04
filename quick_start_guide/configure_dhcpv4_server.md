## Configure DHCPv4 server {#configure-dhcpv4-server}

The steps to configure DHCPv4 server are as follows:

1. Install DHCPv4 server: sudo apt-get install isc-dhcp-server.

2. Edit /etc/dhcp/dhcpd.conf file as shown below.
```
 default-lease-time 600;
 max-lease-time 7200;
 ddns-update-style none;
 log-facility local7;
 \#option definitions common to all supported networks…
 option domain-name “cloudboot.com”;
 option domain-name-servers 192.168.10.20;
 option routers 192.168.10.1;
 option vendor-class-identifier “HTTPClient”;
 option bootfile-name “http://www.cloudboot.com:8080/EFI/Shell.efi”;
 \#This declaration allows BOOTP clients to get dynamic address.
 subnet 192.168.10.0 netmask 255.255.255.0 {
        range 192.168.10.100 192.168.10.250;
        option subnet-mask 255.255.255.0;
        option broadcast-address 192.168.10.255;
 }
```
3. Be sure that your server will listen for DHCP requests on the correct interface (Note: change the INTERFACE to match your own). Edit the /etc/default/isc-dhcp-server file:
```
INTERFACE = “eth0”;
```
4. Restart the DHCPv4 service: sudo service isc-dhcp-server restart.