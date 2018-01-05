<!--- @file
  quick_start_guide/configure_dhcpv4_server.md for Getting Started Guide of EDK    II HTTP Boot

  Copyright (c) 2018, Intel Corporation. All rights reserved.<BR>

  Redistribution and use in source (original document form) and 'compiled'
  forms (converted to PDF, epub, HTML and other formats) with or without
  modification, are permitted provided that the following conditions are met:

  1) Redistributions of source code (original document form) must retain the
     above copyright notice, this list of conditions and the following
     disclaimer as the first lines of this file unmodified.

  2) Redistributions in compiled form (transformed to other DTDs, converted to
     PDF, epub, HTML and other formats) must reproduce the above copyright
     notice, this list of conditions and the following disclaimer in the
     documentation and/or other materials provided with the distribution.

  THIS DOCUMENTATION IS PROVIDED BY TIANOCORE PROJECT "AS IS" AND ANY EXPRESS OR
  IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF
  MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO
  EVENT SHALL TIANOCORE PROJECT  BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL,
  SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO,
  PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS;
  OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY,
  WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR
  OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS DOCUMENTATION, EVEN IF
  ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

-->


## Configure DHCPv4 server {#configure-dhcpv4-server}

The steps to configure DHCPv4 server are as follows:

1. Install DHCPv4 server: sudo apt-get install isc-dhcp-server.

2. Edit /etc/dhcp/dhcpd.conf file as shown below.
```ini
 default-lease-time 600;
 max-lease-time 7200;
 ddns-update-style none;
 log-facility local7;
 #option definitions common to all supported networks…
 option domain-name “cloudboot.com”;
 option domain-name-servers 192.168.10.20;
 option routers 192.168.10.1;
 option vendor-class-identifier “HTTPClient”;
 option bootfile-name “http://www.cloudboot.com:8080/EFI/Shell.efi”;
 #This declaration allows BOOTP clients to get dynamic address.
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