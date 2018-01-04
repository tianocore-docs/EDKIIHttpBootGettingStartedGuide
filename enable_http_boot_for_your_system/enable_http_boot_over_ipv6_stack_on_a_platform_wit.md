## Enable HTTP Boot over IPv6 stack on a platform without EDKII network {#enable-http-boot-over-ipv6-stack-on-a-platform-without-edkii-network}

If you want to enable HTTP boot on a system without EDKII IPv6 network stack, you need add corresponding network modules to your platform files.

First, you need update the network modules to latest revision. The most convenient solution is to update MdePkg, MdeModulePkg, and NetworkPkg to latest revisions from an EDKII repository.

Then, update your platform files as follows:

1.  Update your platform DSC file to add following drivers:

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

INF NetworkPkg\Ip6Dxe\Ip6Dxe.inf

INF NetworkPkg\TcpDxe\TcpDxe.inf

INF NetworkPkg\Udp6Dxe\Udp6Dxe.inf

INF NetworkPkg\Dhcp6Dxe\Dhcp6Dxe.inf

INF NetworkPkg\HttpDxe\HttpDxe.inf

INF NetworkPkg\HttpBootDxe\HttpBootDxe.inf

INF NetworkPkg\HttpUtilitiesDxe\HttpUtilitiesDxe.inf

INF NetworkPkg\DnsDxe\DnsDxe.inf

You also need to add your own UNDI driver to your platform files.