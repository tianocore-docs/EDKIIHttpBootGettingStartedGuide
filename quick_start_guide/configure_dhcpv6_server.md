## Configure DHCPv6 server {#configure-dhcpv6-server}

The steps to configure DHCPv6 server are as follows:

1.  Install DHCPv6 server: sudo apt-get install isc-dhcp-server.

2. If there is no dhcpd6.conf file in /etc/dhcp/ directory, create and edit as shown below.
```
 default-lease-time 600;
 max-lease-time 7200;
 log-facility local7;
 #option definitions common to all supported networks…
 option dhcp6.vendor-class code 16 = {integer 32, integer 16, string};
 subnet6 fec0:0:0:10::/64 {
         #Range for clients
         range6 fec0:0:0:10::100 feco:0:0:0:10:0:0:ffff:ffff;
         option dhcp6.domain-search “cloudbootip6.com”;
         option dhcp6.name-servers fec0:0:0:10::20;
         option dhcp6.vendor-class 0 0  “HTTPClient”;
         option dhcp6.bootfile-url “http://www.cloudbootip6.com:8080/EFI/Shell.efi”;
 }
```
3. Be sure that your server will listen for DHCP requests on the correct interface (Note: change the INTERFACE to match your own). Edit the /etc/default/isc-dhcp-server file:
```
INTERFACE = “eth0”;
```
4. Restart the DHCPv6 service: sudo service isc-dhcp-server6 restart.