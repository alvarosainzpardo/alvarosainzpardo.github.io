# QEMU / VFIO

## Enlaces, tutoriales, documentación

* [GitHub -  bryansteiner/gpu-passthrough-tutorial](https://github.com/bryansteiner/gpu-passthrough-tutorial)
* [Linux on KVM](https://www.ibm.com/docs/en/linux-on-systems?topic=virtualization-kvm)
    * [Preparing PCI pass-through devices](https://www.ibm.com/docs/en/linux-on-systems?topic=through-pci)
    * [Configuring pass-through PCI devices](https://www.ibm.com/docs/en/linux-on-systems?topic=vfio-pass-through-pci)

## Instalación

Manjaro: [Virt-manager](https://wiki.manjaro.org/index.php/Virt-manager) tiene buenos tips sobre la instalación y configuración de qemu, libvirt, virtio disks y la creación y optimización de maquinas virtuales Windows.

From terminal:

```bash
# Manjaro / Arch based
sudo pacman -S --needed virt-manager qemu vde2 iptables-nft dnsmasq bridge-utils openbsd-netcat edk2-ovmf swtpm libguestfs
# Ubuntu / Debian based
sudo apt install qemu ...
```
### Allow Non-root User to use KVM/QEMU Virtualization

By default, only user "root" can create and manage virtual machines. To allow non-root users to create and manage virtual machines, you should follow the libvirtd configuration below.

1. Execute the following command to edit the libvirtd configuration.

```bash
sudo nano /etc/libvirt/libvirtd.conf
```

Uncomment the option "unix_sock_group" and enter the group name as "libvirt".

```
# Set the UNIX domain socket group ownership. This can be used to
# allow a 'trusted' set of users access to management capabilities
# without becoming root.
#
# This setting is not required or honoured if using systemd socket
# activation.
#
# This is restricted to 'root' by default.
unix_sock_group = "libvirt"
```

After that, uncomment the option "unix_sock_rw_perms" and leave the permission as default "0770".

```
# Set the UNIX socket permissions for the R/W socket. This is used
# for full management of VMs
#
# This setting is not required or honoured if using systemd socket
# activation.
#
# Default allows only root. If PolicyKit is enabled on the socket,
# the default will change to allow everyone (eg, 0777)
#
# If not using PolicyKit and setting group ownership for access
# control, then you may want to relax this too.
unix_sock_rw_perms = "0770"
```

Save the configuration by pressing the Ctrl+x button and type y, then enter.

2. Add user to libvirt group to use the system-level virtual machines (qemu:///system):

```bash
sudo usermod -a -G libvirt $USER
newgrp libvirt
```

> Note
> 
> 1. You don't need this step to run system-level virtual machines. However, virt-manager will prompt for sudoer's password when launch if the user is not in the libvirt group
> 2. You can also create user-level virtual machines (qemu:///session) and use without sudoer's privelige. However, some features such as VirtioFS file sharing may be unavailable in qemu:///session

### Logs

IMPORTANT: You need this for detailed logs. Add this lines at the end of the file

```
log_filters="1:qemu"
log_outputs="1:file:/var/log/libvirt/libvirtd.log"
```

### Edit qemu.conf

```bash
sudo nano /etc/libvirt/qemu.conf
```
 
Edit the following lines.

```
#user = "root" to user = "your username"
#group = "root" to group = "your username"
```

### Start libvirtd service

Enable and start service:

```bash
sudo systemctl enable libvirtd.service
sudo systemctl start libvirtd.service
```

### Enabling the virtual machine default network

Important: This will make your virsh internal network automaticly start when you start up your computer.

```bash
sudo virsh net-autostart default
```

If you prefer not to have the virtual machine network not to automaticly start you will have to run this
command ever time you start up your computer.

```bash
sudo virsh net-start default
```

### Default URI choice

[Connection URIs](https://libvirt.org/uri.html): libvirt will use the following logic to determine what URI to use. The configuration file is `/etc/libvirt/libvirt.conf` for the root user, or `$XDG_CONFIG_HOME/libvirt/libvirt.conf` for any unprivileged user.

1. The environment variable `LIBVIRT_DEFAULT_URI`
2. The client configuration file `uri_default` parameter
3. Probe each hypervisor in turn until one that works is found

## GPU passthrough

#### Enlaces

* [VFIO is not taking the GPU](https://www.reddit.com/r/VFIO/comments/79e2ll/vfio_is_not_taking_the_gpu/?sort=old)
* [vfio-pci binding audio but not gpu](https://www.reddit.com/r/VFIO/comments/592f0l/vfiopci_binding_audio_but_not_gpu/?sort=old)
* [PCI-E Bus Issues](https://www.reddit.com/r/VFIO/comments/6jk1bp/pcie_bus_issues/?sort=old)
* [ Verequies Q35 QEMU/KVM Config](https://pastebin.com/FsBXjHcw)

### Desenlazar la tarjeta de video al driver antes de ejecutar el Display Manager

Para poder desenlazar y enlazar dinámicamente la tarjeta de video a los drivers (nvidia/vfio-pci/etc.) es necesario que en el arranque del ordenador, cuando se ejecuta el display manager (gdm), la tarjeta de video NO esté enlazada al driver de video. No hace falta que la tarjeta esté enlazada al driver `vfio-pci`, pero sí es obligatorio que no esté enlazada al driver de video.

Para hacerlo, hay que ir a un VT (con Ctrl+Alt+F2/F3/etc) y ejecutar lo siguiente:

```bash
# Parar gdm
sudo systemctl stop gdm
# Desenlazar la tarjeta de video al driver de video
sudo sh -c "echo 0000:01:00.0 > /sys/bus/pci/devices/0000:01:00.0/driver/unbind"
# Arrancar gdm
sudo systemctl start gdm
```

### Enlazar dinámicamente la tarjeta de video a los drivers de video y vfio-pci

Dentro del desktop environment, abrir un terminal y ejecutar lo siguiente.

Para enlazar la tarjeta de video al driver `vfio-pci`:

```bash
# Desenlazar la tarjeta de video del driver de video
sudo sh -c "echo 0000:01:00.0 > /sys/bus/pci/devices/0000:01:00.0/driver/unbind"
# Enlazar la tarjeta de video (10de:1f91) al driver vfio-pci
sudo sh -c "echo 10de 1f91 > /sys/bus/pci/drivers/vfio-pci/new_id"
sudo sh -c "echo 10de 1f91 > /sys/bus/pci/drivers/vfio-pci/remove_id"
# Verificar el resultado
lspci -Dnnk -d 10de:1f91
```

Para enlazar la tarjeta de video al driver `nvidia`:

```bash
# Desenlazar la tarjeta de video del driver vfio-pci
sudo sh -c "echo 0000:01:00.0 > /sys/bus/pci/devices/0000:01:00.0/driver/unbind"
# Enlazar la tarjeta de video (10de:1f91) al driver nvidia
sudo sh -c "echo 10de 1f91 > /sys/bus/pci/drivers/nvidia/new_id"
sudo sh -c "echo 10de 1f91 > /sys/bus/pci/drivers/nvidia/remove_id"
# Verificar el resultado
lspci -Dnnk -d 10de:1f91
prime-run glxinfo | grep "OpenGL renderer" # El resultado tiene que ser "OpenGL renderer string: NVIDIA GeForce GTX 1650/PCIe/SSE2"
```

#### Automatizar que `vfio-pci` esté enlazado a la tarjeta gráfica antes de arrancar el display manager

Enlaces:

* [nvidia vfio-pci help](https://www.reddit.com/r/VFIO/comments/8siwno/nvidia_vfiopci_help/?sort=old): ejemplo de bind/unbind y comando `sudo lsof /dev/dri/card*`
* [Can't unbind nvidia from nvidia driver](https://www.reddit.com/r/VFIO/comments/qjm8fj/cant_unbind_nvidia_from_nvidia_driver/?sort=old): unbind vtconsoles
* [Need Some Help Unbinding My Nvidia GFX from Host for Hot-swapping](https://www.reddit.com/r/VFIO/comments/7o4y41/need_some_help_unbinding_my_nvidia_gfx_from_host/?sort=old): [comentario](https://www.reddit.com/r/VFIO/comments/7o4y41/comment/ds75tm4/?utm_source=share&utm_medium=web2x&context=3) del usuario marmeladapk con unbind vtconsoles y efi-framebuffer
* [How does the "/sys/bus/pci/drivers/*/*" interface work?](https://lore.kernel.org/linux-pci/GYS4g2uNcGZCeRW-hNJORKGDsXQAfHgFJ0AdUuap04pphi3FvRHzp09US6FzF4b7HqW1wYMPt8yIIwTWdMRDthHEVMdpQvxtzg8uuNfVS0A=@protonmail.com/T/)
* [https://www.kernel.org/doc/Documentation/ABI/testing/sysfs-bus-pci](https://www.kernel.org/doc/Documentation/ABI/testing/sysfs-bus-pci)

Varias alternativas:

* Cargar y enlazar el driver `vfio-pci` en el `initramfs` antes de que se cargue el módulo `nvidia`
* Cargar y enlazar el driver `vfio-pci` como módulo antes que el módulo del driver `nvidia`
* Ejecutar un script que desenlace de la tarjeta gráfica el driver de video (`nvidia`/`radeon`/etc) antes de arrancar el servicio del display manager (`gdm`/`lightdm`/etc)

Por defecto, en Manjaro/Arch/etc los drivers `vfio-pci` y `nvidia` se cargan como módulos. En este caso, hay que configurar que el driver `vfio-pci` se carga antes que el driver `nvidia`. En ambas alternativas (initramfs o módulo) hay que configurar que el driver `vfio-pci` se enlace con la tarjeta gráfica, la forma de hacerlo es distinta en cada caso. En el caso de `initramfs` hay que hacerlo con parámetros de GRUB. En el caso de cargar el driver como módulo, hay que hacerlo con opciones de configuración de `modprobe`.

##### Cargar `vfio-pci` en initramfs

##### Cargar `vfio-pci` como módulo

Enlaces:

* [VFIO is not taking the GPU](https://www.reddit.com/r/VFIO/comments/79e2ll/vfio_is_not_taking_the_gpu/?sort=old)
* [vfio-pci binding audio but not gpu](https://www.reddit.com/r/VFIO/comments/592f0l/vfiopci_binding_audio_but_not_gpu/?sort=old)
* [Kernel module](https://wiki.archlinux.org/title/Kernel_module)
* [modules-load.d - Configure kernel modules to load at boot](https://man.archlinux.org/man/modules-load.d.5)

```bash
$ cat /etc/modprobe.d/vfio_pci.conf
softdep nvidia pre: vfio_pci
options vfio_pci ids=10de:1f91
$ cat /etc/modules-load.d/modules.conf
vfio
vfio_iommu_type1
vfio_pci
vfio_virqfd
vhost-net
```

##### Ejecutar script que desenlaza el driver de video antes de arrancar el servicio del display manager

Enlaces:

* [VFIO is not taking the GPU](https://www.reddit.com/r/VFIO/comments/79e2ll/vfio_is_not_taking_the_gpu/?sort=old)

El usuario de reddit [Verequies](https://www.reddit.com/user/Verequies/) utiliza un [shell script](https://pastebin.com/zLQPHPQk) para desenlazar la tarjeta gráfica en el arranque y posteriormente enlazarla alternativamente al driver vfio_pci y al driver gráfico. Además de usar el filesystem `/sys/bus/pci/[drivers|devices]/*` hace llamadas a `/proc/acpi/call` para encender y apagar la tarjeta gráfica. No me funciona el script tal cual, si borro un device con `remove` ya no vuelve a aparcer nunca más, aunque haga 'echo 1 > /sys/bus/pci/rescan'.

### Audio

#### Enlaces

* [Improved Pulse Audio Driver for QEMU - Testers/coders needed!](https://www.reddit.com/r/VFIO/comments/74vokw/improved_pulse_audio_driver_for_qemu/)
* [Getting rid of audio crackling once and for all (by patching QEMU)](https://www.reddit.com/r/VFIO/comments/746t4h/getting_rid_of_audio_crackling_once_and_for_all/)
