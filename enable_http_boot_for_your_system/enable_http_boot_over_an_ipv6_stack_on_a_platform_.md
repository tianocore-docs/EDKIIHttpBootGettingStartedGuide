<!--- @file
  enable_http_boot_for_your_system/enable_http_boot_over_an_ipv6_stack_on_a_platform_.md for Getting Started Guide of EDK    II HTTP Boot

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


## Enable HTTP Boot over an IPv6 stack on a platform with EDKII network {#enable-http-boot-over-an-ipv6-stack-on-a-platform-with-edkii-network}

If your system already has EDKII IPv6 network stack, you need update the network modules to latest revision.

1.  Specifically, you need to update the MdePkg to get the new protocol definitions for UEFI 2.5\.

2. After that, update following modules:

  * NetLib Library
MdeModulePkg\Library\DxeNetLib\DxeNetLib.inf

3. Update your platform DSC file:

  * Add HTTP and DNS Drivers
```ini
 NetworkPkg\HttpDxe\HttpDxe.inf
 NetworkPkg\HttpBootDxe\HttpBootDxe.inf
 NetworkPkg\HttpUtilitiesDxe\HttpUtilitiesDxe.inf
 NetworkPkg\DnsDxe\DnsDxe.inf
```
  * Add HTTP Library to [LibraryClasses] section              
   `HttpLib|MdeModulePkg\Library\DxeHttpLib\DxeHttpLib.inf`

4. Finally, update your platform FDF file:
  * Add HTTP and DNS Drivers
```ini
  INF NetworkPkg\HttpDxe\HttpDxe.inf
  INF NetworkPkg\HttpBootDxe\HttpBootDxe.inf
  INF NetworkPkg\HttpUtilitiesDxe\HttpUtilitiesDxe.inf
  INF NetworkPkg\DnsDxe\DnsDxe.inf
```

