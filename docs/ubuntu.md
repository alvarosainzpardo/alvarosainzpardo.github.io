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

## Aplicaciones web de emulación de terminal para el browser

Los siguientes programas son emuladores de terminal que funcionan como aplicaciones web dentro de un browser, de forma que se puede acceder a ellos en una sesion normal HTTP, no se necesita tener abierto el puerto 22 para hacer un ssh:

* [Wetty](https://github.com/krishnasrinivas/wetty)
* [Xterm.js](https://github.com/xtermjs/xterm.js)
* [GoTTY](https://github.com/yudai/gotty)
