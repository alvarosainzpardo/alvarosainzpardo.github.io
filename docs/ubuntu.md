# Ubuntu

---

## Enlaces, documentación

* [How do you run Ubuntu Server with a GUI?](https://askubuntu.com/questions/53822/how-do-you-run-ubuntu-server-with-a-gui): en la respuesta 42 hay una explicación detallada de las diferentes opciones para instalar un entorno gráfico a un Ubuntu Server

---

## Instalación con mini.iso

Hace una instalación de un sistema minimo. Los paquetes que se instalan se descargan, por lo que para ejecutar esta instalación hay que estar conectado a internet.

Esta instalación no se puede ejecutar en sistemas basados en UEFI, porque el `mini.iso` no tiene los archivos necesarios para arrancar el ordenador en modo UEFI. El ordenador arrancaría en _BIOS compatibility mode_, Para realizar 'instalaciones mini' en modo UEFI hay que usar Ubuntu Server.

En la [página de descripción de esta instalación](https://help.ubuntu.com/community/Installation/MinimalCD) se encuentra el [enlace de descarga del archivo mini.iso correspondiente a Ubuntu 18.04](http://archive.ubuntu.com/ubuntu/dists/bionic/main/installer-amd64/current/images/netboot/mini.iso).

Cuando se ejecuta `tasksel` en la instalación, no seleccionar ningún paquete.

Al instalar GRUB, asegurarse de que se selecciona el dispositivo correspondiente al disco duro. Normalmente, el primer dispositivo de la lista suele ser el disco USB, el disco duro es el segundo.

---

### Ubuntu GNOME Flashback

Es una sesión GNOME muy ligera, basada en GTK3, que no tiene efectos 3D y que es perfecta para ejecutarse en máquinas virtuales y a través de VNC. Otra ventaja, en comparación por ejemplo con el desktop Mate, es que tiene los programas GNOME de siempre, los mismos que el Ubuntu GNOME estándar.

Una vez reiniciado el sistema después de la instalación, hay varias opciones:

* Para una instalación lo más ligera posible, que ocupa en memoria unos 650KB sin ejecutar ningún programa: ejecutar `sudo apt install --no-install-recommends ubuntu-gnome-desktop`, después ejecutar `sudo apt install lightdm gnome-session-flashback`. Al instalar `lightdm` se abrirá una ventana para escoger el session manager (gdm3 o lightdm), seleccionar lightdm. Reiniciar otra vez el sistema. En la ventana del lightdm, pulsar en la rueda para seleccionar la sesión y seleccionar la sesión `GNOME Flashback`. Es una instalación muy ligera pero no se instalan muchos de los paquetes de uso habitual (calculadora, editor de textos, gestor de archivos comprimidos, etc.), que hay que instalar después a mano.
* Para tener un desktop GNOME completo, con todos los programas habituales instalados, aunque ocupe un poco más de memoria: ejecutar `sudo apt install ubuntu-gnome-desktop`, o `sudo apt install ubuntu-desktop` después ejecutar `sudo apt install lightdm gnome-session-flashback`. Al instalar `lightdm` se abrirá una ventana para escoger el session manager (gdm3 o lightdm), seleccionar lightdm. Reiniciar otra vez el sistema. En la ventana del lightdm, pulsar en la rueda para seleccionar la sesión y seleccionar la sesión `GNOME Flashback`.
* Otra opción para empezar con ella es `sudo apt install gnome-session` que instala una sesión GNOME3 sin las personalizaciones de Ubuntu y un conjunto mínimo de aplicaciones. Una diferencia entre `gnome-session` y `ubuntu-gnome-desktop` es que `gnome-session` no tiene ninguna de las personalizaciones de Ubuntu, incluido el artwork (colores, fondos de pantalla). A partir de ahí, seguir los siguientes pasos explicados anteriormente.

---

### NetworkManager not managing ethernet device

Seguir las instrucciones de https://askubuntu.com/questions/1112796/networkmanager-not-managing-ethernet-device y https://forum.linuxconfig.org/t/wired-unmanaged-ubuntu-desktop-issue/1574/2.

Hay que editar el archivo `/etc/netplan/01-netcfg.yaml` y dejarlo así:

```
# This file describes the network interfaces available on your system
# For more information, see netplan(5).
network:
  version: 2
  renderer: NetworkManager
  ethernets:
    enp0s3:
      dhcp4: yes
```

Una vez editado, ejecutar:

```bash
$ sudo netplan --debug generate
$ sudo netplan apply
```

### Configurar hora para que se la misma que Windows

Por defecto, Linux asume que el RTC del ordenador está en UTC, no en hora local. Sin embargo, Windows asume que el RTC está en hora local.

Para que no haya cambios de hora cuando se hace dual boot entre Linux y Windows, lo más sencillo (y con más soporte) es [configurar Linux para que asuma que el RTC está en hora local](https://www.howtogeek.com/323390/how-to-fix-windows-and-linux-showing-different-times-when-dual-booting/). Para ello, hay que ejecutar lo siguiente en distribuciones que utilizan systemd, como Ubuntu:

```bash
$ timedatectl set-local-rtc 1 --adjust-system-clock
```

Para comprobar la configuración, ejecutar `timedatectl`. Tiene que aparecer `RTC in local TZ: yes`.

Para volver a configurar la hora con el RTC en UTC:

```bash
$ timedatectl set-local-rtc 0 --adjust-system-clock
```

---

## GRUB customizer

[GRUB customizer](https://launchpad.net/grub-customizer) es un entorno gráfico para configurar las opciones de GRUB. Para [instalarlo en Ubuntu](https://launchpad.net/~danielrichter2007/+archive/ubuntu/grub-customizer), hay que ejecutar lo siguiente:

```bash
$ sudo add-apt-repository ppa:danielrichter2007/grub-customizer
$ sudo apt update
$ sudo apt install grub-customizer
```

Una vez instalado, hay que poner el timeout de GRUB a 3 segundos y seleccionar como arranque por defecto la segunda partición de Windows, normalmente en `/dev/sda2`. Es la partición donde está instalado el sistema operativo, no la partición donde está instalado el loader de Windows.

---

## Evolution

### Conexión al servidor Exchange de Office365

Instalar los paquetes `evolution` y `evolution-ews`.

```bash
$ sudo apt install evolution evolution-evs
```

Para configurar la cuenta, hay que seguir [estas instrucciones](https://rc.partners.org/kb/article/2702). Cuando se da de alta la cuenta, tienes que estar conectado directamente a internet, sin proxy, para que funcione el paso en el que se hace el 'fetch'.

Una vez configurada la cuenta, se puede volver a poner el proxy. La única opción de proxy que funciona (a fecha de Marzo 2019) es el proxy manual.

#### Instructions:

* Launch or open the Evolution application
    * If this is a new installation you will be prompted to enter your email information, otherwise to add a new account by going to Edit | Preferences and choose Add from the Mail Accounts menu.
* Click Next
* Enter your name as you'd like it to appear and your primary email address "name@partners.org" or "name@mgh.harvard.edu" or name@bwh.harvard.edu" for Email Address, then click Next
* Click the Skip button
* On the resulting window, enter the following information for each field:
    * Server Type: Exchange Web Services
    * Username: your primary email address i.e. name@partners.org
    * Host URL: https://outlook.office365.com/EWS/Exchange.asmx
* Click Fetch URL
* You will be prompted for your password. Enter your Partners password.
* Host URL and OAB URL should be successfully discovered. Click Next
* Click Next to accept Receiving Options
* Enter any name for the account name, and click Next
* Click Apply
* If prompted, enter your Partners password once more and click OK
* Setup is complete. Email and calendar data will take some time to sync

---

## OneDrive

Para intentar acceder al OneDrive for Business desde Linux, he seguido las instrucciones de [Using OneDrive with Linux](https://www.phillipsj.net/posts/using-onedrive-with-linux). He configurado [OneDrive Free Client](https://github.com/skilion/onedrive) y [Rclone](https://rclone.org/). Los dos fallan en el mismo paso: cuando hay que dar permiso de acceso a una aplicación de terceros desde la cuenta corporativa de OneDrive.

OneDrive FreeClient lo tengo descargado en `projects/onedrive`, se puede borrar el directorio si finalmente no lo uso. El programa, como tal, no llegué a instalarlo, lo probé desde ese directorio. Para poderlo compilar, tuve que instalar lo siguiente, que finalmente se puede desinstalar también:

```bash
$ sudo apt install libcurl4-openssl-dev libsqlite3-dev
$ sudo snap install --classic dmd && sudo snap install --classic dub
```

Rclone sirve para sincronizar muchos servicios de almacenamiento en la nube. Para Rclone sí que tuve que instalar un paquete deb:

```bash
$ sudo dpkg -i rclone-v1.46-linux-amd64.deb
```

Para desinstalarlo:

```bash
$ sudo apt remove/purge rclone
```

### Enlaces

* [How to Sync Microsoft OneDrive with Linux](https://www.maketecheasier.com/sync-onedrive-linux/): [Onedrive](https://github.com/abraunegg/onedrive) is a CLI-based client that allows you to sync quickly and easily with OneDrive. Explains how to install and use the abraunegg OneDrive client.
* [How To Mount OneDrive In Linux Using Rclone (Supports Business And Personal Accounts)](https://www.linuxuprising.com/2018/07/how-to-mount-onedrive-in-linux-using.html): This article explains how to mount OneDrive in Linux using [Rclone](https://rclone.org/).
* [OneDrive Client for Linux](https://github.com/abraunegg/onedrive): A free Microsoft OneDrive Client which supports OneDrive Personal, OneDrive for Business, OneDrive for Office365 and Sharepoint. This powerful and highly configurable client can run on all major Linux distributions, as a Docker container and on FreeBSD. It supports one-way and two-way sync capabilities and securely connects to Microsoft OneDrive services. This client is a 'fork' of the [skilion](https://github.com/skilion/onedrive) client which was abandoned in 2018.
* [ExpanDrive](https://www.expandrive.com/): producto comercial para sincronizar con todos los almacenamientos cloud
* [Using OneDrive with Linux](https://www.phillipsj.net/posts/using-onedrive-with-linux)
* [Rclone](https://rclone.org/)
* [OneDrive Free Client](https://github.com/skilion/onedrive)
* [How To Mount OneDrive In Linux Using Rclone (Supports Business And Personal Accounts)](https://www.linuxuprising.com/2018/07/how-to-mount-onedrive-in-linux-using.html)
* [InSync is Bringing OneDrive to Linux](https://www.omgubuntu.co.uk/2019/02/insync-support-onedrive-linux-client)
* [onedriveClient](https://github.com/derrix060/onedriveClient): A Microsoft OneDrive and OneDrive for Business client for Linux, written in Python3.
* [The 4 best unofficial Microsoft OneDrive apps for Linux](https://www.addictivetips.com/ubuntu-linux-tips/best-unofficial-microsoft-onedrive-apps-for-linux/)
* [How to Sync Microsoft OneDrive with Linux](https://www.maketecheasier.com/sync-onedrive-linux/)

---

## Aplicaciones web de emulación de terminal para el browser

Los siguientes programas son emuladores de terminal que funcionan como aplicaciones web dentro de un browser, de forma que se puede acceder a ellos en una sesion normal HTTP, no se necesita tener abierto el puerto 22 para hacer un ssh:

* [Wetty](https://github.com/krishnasrinivas/wetty)
* [Xterm.js](https://github.com/xtermjs/xterm.js)
* [GoTTY](https://github.com/yudai/gotty)
* [ttyd](https://github.com/tsl0922/ttyd)

## Bash y utilidades GUI para bash

Para añadir widgets interactivos, o elementos de interfaz gráfico de usuario (GUI) a los shell scripts, como ventanas de mensajes, checkboxes, menús, etc, estas son las utilidades principales:

* Whiptail
* [Dialog](https://invisible-island.net/dialog/)
* [Zenity](https://wiki.gnome.org/Projects/Zenity)

Whiptail y Dialog funcionan en modo texto. Dialog utiliza la librería ncurses. Whiptail utiliza la librería newt, y es la utilidad usada por las distribuciones Debian/Ubuntu en sus scripts de configuración. Zenity funciona en modo gráfico (X11) y utiliza la librería GTK. Whiptail y Dialog funcionan en cualquier sesión, local o sesión remota por ssh (siempre que en el ordenador destino esté instalado el paquete correspondiente). Zenity únicamente funciona en una sesión local y ejecutando el shell script dentro del entorno gráfico. Por lo demás, son similares en funcionamiento.

### Enlaces

* [Menu driven scripts](https://bash.cyberciti.biz/guide/Menu_driven_scripts)

### Dialog

* [Bash display dialog boxes](https://bash.cyberciti.biz/guide/Bash_display_dialog_boxes)
* [Dialog: An Introductory Tutorial](https://www.linuxjournal.com/article/2807)
    * [Listing 1: Sound Driver Configuration Utility](https://www.linuxjournal.com/files/linuxjournal.com/linuxjournal/articles/028/2807/2807l1.html)
* [dialog](http://linuxcommand.org/lc3_adv_dialog.php)
* [Dialog Widget List](https://invisible-island.net/dialog/dialog-figures.html)

### Whiptail

* [Bash Shell Scripting/Whiptail](https://en.wikibooks.org/wiki/Bash_Shell_Scripting/Whiptail)

### Zenity

* [Zenity Manual](https://help.gnome.org/users/zenity/3.32/)
* [How to Add a GUI to Linux Shell Scripts](https://www.howtogeek.com/435020/how-to-add-a-gui-to-linux-shell-scripts/)
* [How to use graphical widgets in bash scripts with zenity](https://linuxconfig.org/how-to-use-graphical-widgets-in-bash-scripts-with-zenity)

---

## Tell PulseAudio to ignore a USB device using udev

* [Tell PulseAudio to ignore a USB device using udev](https://jamielinux.com/blog/tell-pulseaudio-to-ignore-a-usb-device-using-udev/) 

### Gather USB device information

Before creating a udev rule, you need to find a unique way to identify your USB device. lsusb will list all connected USB devices:

```bash
$ lsusb
Bus 004 Device 003: ID 1852:5110 GYROCOM C&C Co., LTD
```

Use the Bus and Device numbers from above to gather more information about your device. We’re mostly interested in the idVendor and idProduct:

```bash
$ sudo lsusb -v -s 004:003
...
idVendor           0x1852 GYROCOM C&C Co., LTD
idProduct          0x5110
...
```

### Create a udev rule

Your system should have udev rules already defined in the `/lib/udev/rules.d` directory, such as `90-pulseaudio.rules`. There should also be a `/etc/udev/rules.d` directory where you can define your own rules.

The rules are parsed in lexical order. Create a file called `/etc/udev/rules.d/89-pulseaudio-usb.rules`, so that it’s parsed just before `90-pulseaudio.rules` (though you may have to experiment with the numbering if things don’t work as expected).

Open the file in your favourite editor and create a rule. Use the `idVendor` and `idProduct` numbers from earlier to uniquely match your USB device, and then set an environment variable that tells PulseAudio to ignore the device:

```bash
ATTRS{idVendor}=="1852", ATTRS{idProduct}=="5110", ENV{PULSE_IGNORE}="1"
```

Optionally, you might want to apply other changes to the device, such as access permissions or device ownership. Write each rule on a separate line:

```bash
ATTRS{idVendor}=="1852", ATTRS{idProduct}=="5110", ENV{PULSE_IGNORE}="1"
ATTRS{idVendor}=="1852", ATTRS{idProduct}=="5110", GROUP="mpd"
```

Reboot your system and PulseAudio will no longer acknowledge that your USB device exists.

---

## Teclado Apple Magic Keyboard

Emparejar el teclado bluetooth. Al finalizar el emparejamiento el teclado se comporta como un numpad, únicamente funcionan las teclas numéricas, el Enter, poco más. Para arreglar ese problema y que el teclado funcione correctamente hay que usar la utilidad `numlockx`:

```bash
sudo apt update
sudo apt install numlockx
numlockx off

*Probably it also makes sense to add 'numlock off' as startup command in 'gnome-session-properties'
```

Más información sobre el tema en:

* [How to pair Apple Magic Keyboard (A1314) on Ubuntu 18.04 and act as Numpad](https://medium.com/macoclock/how-to-pair-apple-magic-keyboard-a1314-on-ubuntu-18-04-and-act-as-numpad-42fe4402454c)
* [ArchLinux - Apple Keyboard](https://wiki.archlinux.org/index.php/Apple_Keyboard)

---

## Gestionar imagenes del iPhone

### Conectar el iPhone en Ubuntu 20.04

En Ubuntu 20.04, la libreria `libimobiledevice6` no tiene un soporte completo para las últimas versiones de iOS y al conectar un iPhone a Ubuntu ya no se puede acceder a las imágenes del teléfono. Este problema está resuelto en versiones de Ubuntu más modernas.

He encontrado en esta página: [Backup iPhone’s photos in Ubuntu 20.04](https://wuzhaojun.wordpress.com/2021/03/19/memo-of-backup-iphones-photos-in-ubuntu-20-04/) instrucciones sobre cómo poder acceder a las imágenes del iPhone usando el terminal.

En resumen, hay que ejecutar los comandos siguientes:

```bash
# Instalar las librerias y utilidades necesarias
$ sudo apt install libimobiledevice6 libimobiledevice-utils ifuse

# Conectar el iphone por USB, se debería detectar automáticamente
# Si el iPhone no se detecta, ejecutar:
$ idevicepair pair
# Optionally, expose a socket to multiplex connections from and to iPhone (only if the usbmuxd wasn’t automatically triggered by systemd when connecting the iphone to Ubuntu. aka, if usbmuxd doesn’t exist in the output of “ps -axf | grep usbmuxd”)
$ sudo usbmuxd -z -f -v

# Montar el almacenamiento del iPhone en un directorio
mkdir iphone
ifuse ~/iphone
# Copiar las imágenes
cp -r ~/iphone/DCIM ~/any-backup-folder
# Desmontar el almacenamiento del iPhone
fusermount -u ~/iphone
# Si el iPhone se tuvo que emparejar manualmente:
$ idevicepair unpair
```

### Visualizar imágenes HEIC

* [How to Open iOS HEIC Photos or Convert to JPG/PNG in Ubuntu 20.04](https://ubuntuhandbook.org/index.php/2021/06/open-heic-convert-jpg-png-ubuntu-20-04/)
* [How to view .HEIC photos from iPhone IOS 11+ on Ubuntu?](https://askubuntu.com/questions/1298595/how-to-view-heic-photos-from-iphone-ios-11-on-ubuntu)
* [Any app on Ubuntu to open and/or convert HEIF pictures (.HEIC, High Efficiency Image File Format)?](https://askubuntu.com/questions/958355/any-app-on-ubuntu-to-open-and-or-convert-heif-pictures-heic-high-efficiency-i)

Para visualizar imágenes .HEIC hay que instalar los paquetes:

```bash
sudo apt update
sudo apt install heif-gdk-pixbuf
sudo apt install heif-thumbnailer
sudo apt install libheif-examples
```
El paquete `heif-gdk-pixbuf` instala las librerías necesarias para ver imágenes .HEIC en los programas de tratamiento de imágenes (como ImageViewer), el paquete `heif-thumbnailer` instala el soporte para que aparezcan los thumbnails de las imágenes en Nautilus. El tercer paquete instala la utilidad `heif-convert`, que sirve para convertir las imágenes a JPEG.

Para convertir en modo batch un lote de imágenes .HEIC a JPG:

```bash
for file in *.HEIC; do heif-convert -q 100 $file ${file/%.HEIC/.jpg}; done
```

El parámetro `-q` sirve para especificar la calidad de la conversión, si no se usa el valor por defecto es 92.
