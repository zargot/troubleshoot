# QEMU

## Edit vm conf

`virsh edit <vm>`

## SSH

Simply look up the NIC IP in virt-manager.

## Port forwarding

SSH forwarding example:
https://wiki.qemu.org/Documentation/Networking#How_to_get_SSH_access_to_a_guest

```
<domain type='kvm' xmlns:qemu='http://libvirt.org/schemas/domain/qemu/1.0'>
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

## Windows guest

### Copy/paste

https://www.spice-space.org/download/windows/spice-guest-tools/spice-guest-tools-latest.exe

### OpenSSH server

https://winscp.net/eng/docs/guide_windows_openssh_server
https://erwin.co/configuring-openssh-server-sshd-on-windows-11/
