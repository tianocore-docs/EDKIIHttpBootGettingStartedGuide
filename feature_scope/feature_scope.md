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

  `MdeModulePkg\Universal\Network\Ip4Dxe\Ip4Dxe.in`f