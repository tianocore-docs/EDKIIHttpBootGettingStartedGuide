## Enable HTTP Boot over an IPv4 stack on a platform without EDKII network {#enable-http-boot-over-an-ipv4-stack-on-a-platform-without-edkii-network}

If you want to enable HTTP boot on a system without EDKII IPv4 network stack, you need add corresponding network modules to your platform files.

First, you need update the network modules to latest revision. The most convenient solution is to update MdePkg, MdeModulePkg, and NetworkPkg to latest revisions from an EDKII repository.

Then, update your platform files as follows:

1.  Update your platform DSC file to add following drivers:

MdeModulePkg\Universal\Network\DpcDxe\DpcDxe.inf

MdeModulePkg\Universal\Network\SnpDxe\SnpDxe.inf

MdeModulePkg\Universal\Network\MnpDxe\MnpDxe.inf

MdeModulePkg\Universal\Network\ArpDxe\ArpDxe.inf

MdeModulePkg\Universal\Network\Ip4Dxe\Ip4Dxe.inf

MdeModulePkg\Universal\Network\Tcp4Dxe\Tcp4Dxe.inf

MdeModulePkg\Universal\Network\Udp4Dxe\Udp4Dxe.inf

MdeModulePkg\Universal\Network\Dhcp4Dxe\Dhcp4Dxe.inf

NetworkPkg\HttpDxe\HttpDxe.inf

NetworkPkg\HttpBootDxe\HttpBootDxe.inf

NetworkPkg\HttpUtilitiesDxe\HttpUtilitiesDxe.inf

NetworkPkg\DnsDxe\DnsDxe.inf

1.  Update your platform DSC file to add following libraries to [LibraryClasses] section:

DpcLib|MdeModulePkg\Library\DxeDpcLib\DxeDpcLib.inf

NetLib|MdeModulePkg\Library\DxeNetLib\DxeNetLib.inf

IpIoLib|MdeModulePkg\Library\DxeIpIoLib\DxeIpIoLib.inf

UdpIoLib|MdeModulePkg\Library\DxeUdpIoLib\DxeUdpIoLib.inf

TcpIoLib|MdeModulePkg\Library\DxeTcpIoLib\DxeTcpIoLib.inf

HttpLib|MdeModulePkg\Library\DxeHttpLib\DxeHttpLib.inf

Update your platform FDF file to add following drivers:

INF MdeModulePkg\Universal\Network\DpcDxe\DpcDxe.inf

INF MdeModulePkg\Universal\Network\SnpDxe\SnpDxe.inf

INF MdeModulePkg\Universal\Network\MnpDxe\MnpDxe.inf

INF MdeModulePkg\Universal\Network\ArpDxe\ArpDxe.inf

INF MdeModulePkg\Universal\Network\Ip4Dxe\Ip4Dxe.inf

INF MdeModulePkg\Universal\Network\Tcp4Dxe\Tcp4Dxe.inf

INF MdeModulePkg\Universal\Network\Udp4Dxe\Udp4Dxe.inf

INF MdeModulePkg\Universal\Network\Dhcp4Dxe\Dhcp4Dxe.inf

INF NetworkPkg\HttpDxe\HttpDxe.inf

INF NetworkPkg\HttpBootDxe\HttpBootDxe.inf

INF NetworkPkg\HttpUtilitiesDxe\HttpUtilitiesDxe.inf

INF NetworkPkg\DnsDxe\DnsDxe.inf

You also need add your own UNDI driver to your platform files.