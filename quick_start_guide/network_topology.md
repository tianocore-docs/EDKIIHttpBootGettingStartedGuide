<!--- @file
  quick_start_guide/network_topology.md for Getting Started Guide of EDK    II HTTP Boot

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


## Network topology {#network-topology}

Figure 1 shows a test-bed using HTTP boot. In this example, the DHCP server and DNS server are separately deployed on Ubuntu 15.10 and Windows Server 2012 R2\. These two servers and an NT32 simulator are located on the same subnet: IPv4 (192.168.10.0) / IPv6 (fec0:0:0:10::/64).

In this example, the HTTP server is deployed in another Windows Server 2012 R2 and located on a different subnet: IPv4 (192.168.20.0) / IPv6 (fec0:0:0:20::/64). The two subnets are connected by a gateway.


![](/media/Fig-01.JPG)

###### Figure 1 HTTP boot test-bed{#figure-1-http-boot-test-bed}

**_Note:_** You may use an alternative solution to establish your test-bed and configure your DHCP server, DNS server and HTTP Server. This chapter describes one such approach as a reference or guide.