# Ubuntu

---

## Enlaces, documentación

* [How do you run Ubuntu Server with a GUI?](https://askubuntu.com/questions/53822/how-do-you-run-ubuntu-server-with-a-gui): en la respuesta 42 hay una explicación detallada de las diferentes opciones para instalar un entorno gráfico a un Ubuntu Server

---

## Ubuntu GNOME Flashback

Es una sesión GNOME muy ligera, basada en GTK3, que no tiene efectos 3D y que es perfecta para ejecutarse en máquinas virtuales y a través de VNC. Otra ventaja, en comparación por ejemplo con el desktop Mate, es que tiene los programas GNOME de siempre, los mismos que el Ubuntu GNOME estándar.

Para instalar GNOME Flasback desde cero, recomiendo instalar un Ubuntu usado la imagen `mini.iso`. Cuando se ejecuta `tasksel` en la instalación, no seleccionar ningún paquete.

Una vez reiniciado el sistema después de la instalación, hay varias opciones:

* Para una instalación lo más ligera posible, que ocupa en memoria unos 650KB sin ejecutar ningún programa: ejecutar `sudo apt install --no-install-recommends ubuntu-gnome-desktop`, después ejecutar `sudo apt install lightdm gnome-session-flashback`. Al instalar `lightdm` se abrirá una ventana para escoger el session manager (gdm3 o lightdm), seleccionar lightdm. Reiniciar otra vez el sistema. En la ventana del lightdm, pulsar en la rueda para seleccionar la sesión y seleccionar la sesión `GNOME Flashback`. Es una instalación muy ligera pero no se instalan muchos de los paquetes de uso habitual (calculadora, editor de textos, gestor de archivos comprimidos, etc.), que hay que instalar después a mano.
* Para tener un desktop GNOME completo, con todos los programas habituales instalados, aunque ocupe un poco más de memoria: ejecutar `sudo apt install ubuntu-gnome-desktop`, o `sudo apt install ubuntu-desktop` después ejecutar `sudo apt install lightdm gnome-session-flashback`. Al instalar `lightdm` se abrirá una ventana para escoger el session manager (gdm3 o lightdm), seleccionar lightdm. Reiniciar otra vez el sistema. En la ventana del lightdm, pulsar en la rueda para seleccionar la sesión y seleccionar la sesión `GNOME Flashback`.
* Otra opción para empezar con ella es `sudo apt install gnome-session` que instala una sesión GNOME3 sin las personalizaciones de Ubuntu y un conjunto mínimo de aplicaciones. Una diferencia entre `gnome-session` y `ubuntu-gnome-desktop` es que `gnome-session` no tiene ninguna de las personalizaciones de Ubuntu, incluido el artwork (colores, fondos de pantalla). A partir de ahí, seguir los siguientes pasos explicados anteriormente.

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
