<!--- @file
  enable_http_boot_for_your_system/enable_http_boot_over_ipv6_stack_on_a_platform_wit.md for Getting Started Guide of EDK    II HTTP Boot

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


## Enable HTTP Boot over IPv6 stack on a platform without EDKII network {#enable-http-boot-over-ipv6-stack-on-a-platform-without-edkii-network}

If you want to enable HTTP boot on a system without EDK II IPv6 network stack, you need add corresponding network modules to your platform files.

First, you need update the network modules to latest revision. The most convenient solution is to update MdePkg, MdeModulePkg, and NetworkPkg to latest revisions from an EDK II repository.

Then, update your platform files as follows:

1. (do steps 1-4 from the previous section) Update your platform DSC file to add following drivers:
```ini
 MdeModulePkg\Universal\Network\DpcDxe\DpcDxe.inf
 MdeModulePkg\Universal\Network\SnpDxe\SnpDxe.inf
 MdeModulePkg\Universal\Network\MnpDxe\MnpDxe.inf
 
 NetworkPkg\Ip6Dxe\Ip6Dxe.inf
 NetworkPkg\TcpDxe\TcpDxe.inf
 NetworkPkg\Udp6Dxe\Udp6Dxe.inf
 NetworkPkg\Dhcp6Dxe\Dhcp6Dxe.inf
 NetworkPkg\HttpDxe\HttpDxe.inf
 NetworkPkg\HttpBootDxe\HttpBootDxe.inf
 NetworkPkg\HttpUtilitiesDxe\HttpUtilitiesDxe.inf
 NetworkPkg\DnsDxe\DnsDxe.inf
```
2.  Update your platform DSC file to add following libraries to `[LibraryClasses]` section:
```ini
 DpcLib|MdeModulePkg\Library\DxeDpcLib\DxeDpcLib.inf
 NetLib|MdeModulePkg\Library\DxeNetLib\DxeNetLib.inf
 IpIoLib|MdeModulePkg\Library\DxeIpIoLib\DxeIpIoLib.inf
 UdpIoLib|MdeModulePkg\Library\DxeUdpIoLib\DxeUdpIoLib.inf
 TcpIoLib|MdeModulePkg\Library\DxeTcpIoLib\DxeTcpIoLib.inf
 HttpLib|MdeModulePkg\Library\DxeHttpLib\DxeHttpLib.inf
```
3. Update your platform FDF file to add following drivers:
```ini
 INF MdeModulePkg\Universal\Network\DpcDxe\DpcDxe.inf
 INF MdeModulePkg\Universal\Network\SnpDxe\SnpDxe.inf
 INF MdeModulePkg\Universal\Network\MnpDxe\MnpDxe.inf
 INF NetworkPkg\Ip6Dxe\Ip6Dxe.inf
 INF NetworkPkg\TcpDxe\TcpDxe.inf
 INF NetworkPkg\Udp6Dxe\Udp6Dxe.inf
 INF NetworkPkg\Dhcp6Dxe\Dhcp6Dxe.inf
 INF NetworkPkg\HttpDxe\HttpDxe.inf
 INF NetworkPkg\HttpBootDxe\HttpBootDxe.inf
 INF NetworkPkg\HttpUtilitiesDxe\HttpUtilitiesDxe.inf
 INF NetworkPkg\DnsDxe\DnsDxe.inf
```



**_Note:_** You also need to add your own UNDI driver to your platform files.