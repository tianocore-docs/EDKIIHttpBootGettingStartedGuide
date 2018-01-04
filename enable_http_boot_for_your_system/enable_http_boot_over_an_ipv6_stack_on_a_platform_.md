## Enable HTTP Boot over an IPv6 stack on a platform with EDKII network {#enable-http-boot-over-an-ipv6-stack-on-a-platform-with-edkii-network}

If your system already has EDKII IPv6 network stack, you need update the network modules to latest revision.

1.  Specifically, you need to update the MdePkg to get the new protocol definitions for UEFI 2.5\.

2. After that, update following modules:

  * NetLib Library
MdeModulePkg\Library\DxeNetLib\DxeNetLib.inf

3. Update your platform DSC file:

  * Add HTTP and DNS Drivers
```
 NetworkPkg\HttpDxe\HttpDxe.inf
 NetworkPkg\HttpBootDxe\HttpBootDxe.inf
 NetworkPkg\HttpUtilitiesDxe\HttpUtilitiesDxe.inf
 NetworkPkg\DnsDxe\DnsDxe.inf
```
  * Add HTTP Library to [LibraryClasses] section              
   `HttpLib|MdeModulePkg\Library\DxeHttpLib\DxeHttpLib.inf`

4. Finally, update your platform FDF file:
  * Add HTTP and DNS Drivers
```
  INF NetworkPkg\HttpDxe\HttpDxe.inf
  INF NetworkPkg\HttpBootDxe\HttpBootDxe.inf
  INF NetworkPkg\HttpUtilitiesDxe\HttpUtilitiesDxe.inf
  INF NetworkPkg\DnsDxe\DnsDxe.inf
```

