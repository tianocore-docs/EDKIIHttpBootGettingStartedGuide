## Related Protocols {#related-protocols}

UEFI 2.5 specification introduces a serial of new protocols which are related to HTTP boot in EDKII network stack:

HTTP Service Binding Protocol – used to locate communication devices that are supported by a HTTP driver and to create and destroy instances of the HTTP child protocol.

HTTP Protocol – used to provide HTTP service to create and transmit HTTP requests, as well as handle HTTP responses that are returned by a remote host.

HTTP Utilities Protocol – used to build a raw HTTP message from a list of HTTP headers or to parse HTTP headers from a raw HTTP message.

DNS4 &amp; DNS6 Service Binding Protocol– used to locate communication devices that are supported by a DNS driver and to create and destroy instances of the DNS child protocol.

DNS4 &amp; DNS6 Protocol – used to get host name and address mapping from DNS server.

IPv4 Configuration II Protocol – a new protocol which replaces IPv4 Configuration protocol, used to provide the mechanism to set and get various types of configuration for the EFI IPv4 network stack, including DNS server list.

Also, the _UEFI Specification_, revision 2.5, defines the procedure of ‘HTTP boot’ as one example of ‘boot from URI’. The procedure uses the DHCP options to identify the name and path of the NBP (Network Boot Program), which are specified as a URI string in several formats.