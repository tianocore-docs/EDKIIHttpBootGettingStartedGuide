<!--- @file
  feature_scope/feature_scope.md for Getting Started Guide of EDK    II HTTP Boot

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


## Feature Scope {#feature-scope}

Current implementation adds the following new modules to the EDKII network stack:

* HTTP Boot Driver
 `NetworkPkg\HttpBootDxe\HttpBootDxe.inf`

* HTTP Driver
 `NetworkPkg\HttpDxe\HttpDxe.inf`

* HTTP Utilities Driver
 `NetworkPkg\HttpUtilitiesDxe\HttpUtilitiesDxe.inf`

* DNS Driver
 `NetworkPkg\DnsDxe\DnsDxe.inf`

* HTTP Library
 `MdeModulePkg\Library\DxeHttpLib\DxeHttpLib.inf`

Per the _UEFI Specification_, revision 2.5, the implementation can enable HTTP boot over either an IPv4 stack or an IPv6 stack, or both. The current implementation supports HTTP boot over both an IPv4 network stack and anIPv6 network stack.. The supported HTTP version is 1.1, currently in common use as of the publication of this document.

The current implementation removes the following module from an EDKII network stack, as it was used to produce the IPv4 configuration protocol (deprecated by the UEFI 2.5 Specification).

* IP4Config Driver
 
 `MdeModulePkg\Universal\Network\Ip4ConfigDxe\Ip4ConfigDxe.inf`

The current implementation updates the following module in an EDKII network stack. The updated IP4 driver produces an IPv4 configuration II protocol; also it supplies the HII configuration pages to the end user.

* IP4 Driver

  `MdeModulePkg\Universal\Network\Ip4Dxe\Ip4Dxe.inf`