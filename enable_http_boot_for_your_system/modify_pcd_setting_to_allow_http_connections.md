## Modify PCD setting to allow HTTP connections {#modify-pcd-setting-to-allow-http-connections}

HTTP communication is forbidden by default due to security consideration (only HTTPS is allowed). You need to override the default PCD setting in your platform DSC file to allow HTTP connections.

1.  Update your platform DSC file to add following line to [PcdsFixedAtBuild] section:
```
gEfiNetworkPkgTokenSpaceGuid.PcdAllowHttpConnections|TRUE
```

