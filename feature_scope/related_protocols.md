<!--- @file
  feature_scope/related_protiocols.md for Getting Started Guide of EDK    II HTTP Boot

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


## Related Protocols {#related-protocols}

[UEFI](http://uefi.org) 2.5 specification introduces a serial of new protocols which are related to HTTP boot in EDKII network stack:

* HTTP Service Binding Protocol – used to locate communication devices that are supported by a HTTP driver and to create and destroy instances of the HTTP child protocol.
* HTTP Protocol – used to provide HTTP service to create and transmit HTTP requests, as well as handle HTTP responses that are returned by a remote host.
* HTTP Utilities Protocol – used to build a raw HTTP message from a list of HTTP headers or to parse HTTP headers from a raw HTTP message.
* DNS4 &amp; DNS6 Service Binding Protocol– used to locate communication devices that are supported by a DNS driver and to create and destroy instances of the DNS child protocol.
* DNS4 &amp; DNS6 Protocol – used to get host name and address mapping from DNS server.
* IPv4 Configuration II Protocol – a new protocol which replaces IPv4 Configuration protocol, used to provide the mechanism to set and get various types of configuration for the EFI IPv4 network stack, including DNS server list.

Also, the _[UEFI](http://uefi.org) Specification_, revision 2.5, defines the procedure of ‘HTTP boot’ as one example of ‘boot from URI’. The procedure uses the DHCP options to identify the name and path of the NBP (Network Boot Program), which are specified as a URI string in several formats.