# QEMU / VFIO

## Enlaces, tutoriales, documentación

## Instalación

Manjaro: [Virt-manager](https://wiki.manjaro.org/index.php/Virt-manager) tiene buenos tips sobre la instalación y configuración de qemu, libvirt, virtio disks y la creación y optimización de maquinas virtuales Windows.

From terminal:

```bash
# Manjaro / Arch based
sudo pacman -S --needed virt-manager qemu vde2 iptables-nft dnsmasq bridge-utils openbsd-netcat edk2-ovmf swtpm
# Ubuntu / Debian based
sudo apt install qemu ...
```

Enable and start service:

```bash
sudo systemctl enable libvirtd.service
sudo systemctl start libvirtd.service
```

Add user to libvirt group to use the system-level virtual machines (qemu:///system):

```bash
sudo usermod -a -G libvirt $USER
```

> Note
> 
> 1. You don't need this step to run system-level virtual machines. However, virt-manager will prompt for sudoer's password when launch if the user is not in the libvirt group
> 2. You can also create user-level virtual machines (qemu:///session) and use without sudoer's privelige. However, some features such as VirtioFS file sharing may be unavailable in qemu:///session

## GPU passthrough
