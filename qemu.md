# QEMU

## Edit vm conf
`virsh edit <vm>`

## Copy/paste between linux-host and windows-guest
https://www.spice-space.org/download/windows/spice-guest-tools/spice-guest-tools-latest.exe

## Port forwarding
https://wiki.qemu.org/Documentation/Networking#How_to_get_SSH_access_to_a_guest

```
<domain type='kvm' xmlns:qemu='http://libvirt.org/schemas/`domain/qemu/1.0'>
...
  <qemu:commandline>
    <qemu:arg value='-device'/>
    <qemu:arg value='e1000,netdev=net0'/>
    <qemu:arg value='-netdev'/>
    <qemu:arg value='user,id=net0,hostfwd=tcp::2222-:22'/>
  </qemu:commandline>
</domain>
```

Multiple `hostfwd` can be added with a comma between.

On Windows guests, make sure the new network adapter shows up, or reboot.
