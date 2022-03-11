# WMware

### add shared folder

```
Player > Manage > Virtual Machine Settings > Options > Shared Folders > Enable
```

Then on running VM, open the terminal:\
[source](https://docs.vmware.com/en/VMware-Workstation-Pro/16.0/com.vmware.ws.using.doc/GUID-AB5C80FE-9B8A-4899-8186-3DB8201B1758.html)

```
# mount all the shares

/usr/bin/vmhgfs-fuse .host:/ /home/username/shares -o subtype=vmhgfs-fuse,allow_other
```
