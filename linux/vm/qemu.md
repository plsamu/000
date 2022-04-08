# QEMU

{% embed url="https://www.youtube.com/watch?v=BgZHbCDFODk" %}

All explained in the video

```
sudo apt install qemu qemu-kvm
sudo apt install libvirt-daemon
sudo apt install bridge-utils
sudo apt install virt-manager

```

```
sudo systemctl start libvirtd
sudo systemctl enable libvirtd
```

```
virt-manager
```

{% embed url="https://www.iduoad.com/til/qemusystem-vs-qemusession" %}

## expose VM to LAN

{% embed url="https://linuxconfig.org/how-to-use-bridged-networking-with-libvirt-and-kvm" %}

## raw sources

```
nmtui
ip link set eth1 up
sudo ip link set wlp2s0 master virbr0

```

{% embed url="https://forum.level1techs.com/t/solved-how-to-expose-virtual-machines-to-local-network/156726/2" %}

{% embed url="https://github.com/cloudius-systems/osv/issues/707" %}

{% embed url="https://wiki.qemu.org/Features/HelperNetworking" %}

{% embed url="https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/virtualization_administration_guide/sect-attch-nic-physdev" %}
