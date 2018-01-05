## Enable HTTP Boot over IPv4 stack on a platform has EDKII network {#enable-http-boot-over-ipv4-stack-on-a-platform-has-edkii-network}

If your system already has EDKII IPv4 network stack, you need update the network modules to latest revision.

1.  Specifically, you need to update the MdePkg to get the new protocol definitions for UEFI 2.5\.

2. After that, update following modules:

  * IP4 Driver
 `MdeModulePkg\Universal\Network\Ip4Dxe\Ip4Dxe.inf`

  * NetLib Library
  `MdeModulePkg\Library\DxeNetLib\DxeNetLib.inf`

3. Update your platform DSC file:

  * Remove IP4Config Driver
 
    ~~MdeModulePkg\Universal\Network\Ip4ConfigDxe\Ip4ConfigDxe.inf~~

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
  * Remove IP4Config Driver
  ~~INF MdeModulePkg\Universal\Network\Ip4ConfigDxe\Ip4ConfigDxe.inf~~
  * Add HTTP and DNS Drivers
```ini
 INF NetworkPkg\HttpDxe\HttpDxe.inf
 INF NetworkPkg\HttpBootDxe\HttpBootDxe.inf
 INF NetworkPkg\HttpUtilitiesDxe\HttpUtilitiesDxe.inf
 INF NetworkPkg\DnsDxe\DnsDxe.inf
```

