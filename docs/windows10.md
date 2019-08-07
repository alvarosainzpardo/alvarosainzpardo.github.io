# Windows 10

---

## Enlaces, documentación

* [Windows 10 Product Keys 100% Working Serial Keys](https://www.softwarebeam.com/2016/08/windows-10-product-keys-serial-keys.html)
* [Activate Windows 10 Pro Free Product Key 64 Bit 2018 | Permanently](https://www.youtube.com/watch?v=7ab_OeiROZg)
* [Reverse the scroll of mouse](https://answers.microsoft.com/en-us/windows/forum/windows_10-other_settings/reverse-the-scroll-of-mouse/334669c3-8a45-4600-830a-8df628d7415e)

---

## Instalación

Para instalar Windows 10, hay que visitar la página [Download Windows 10 Disc Image (ISO File)](https://www.microsoft.com/software-download/windows10ISO). Una vez en la página, hay que seleccionar la edición (actualmente es la April 2018 Update), el idioma y la versión de 64-bit o de 32-bit. Respecto al idioma, hay idioma español e inglés. Para el idioma inglés, seleccionar "English" (no seleccionar "Engligh (internacional)"). La versión English permite seleccionar el teclado español durante la instalación. Una vez instalado Windows 10, se puede descargar el idioma español para poder cambiar los formatos de fecha/hora.

---

## Activar Windows 10 (license keys)

Para activar Windows 10 hay que seguir estas indicaciones:

* Abrir un command prompt en modo administrador. Para ello, escribir `cmd` en el buscador de Cortana y teclear `Ctrl + Shift + Enter`. Otra opción es pulsar  botón derecho sobre el icono de Windows y seleccionar "Windows PowerShell (Admin)"
* Ejecutar los siguientes comandos:

```dos
C:\> cd c:\Windows\system32
C:\Windows\system32> cscript slmgr.vbs /ipk W269N-WFGWX-YVC9B-4J6C9-T83GX
C:\Windows\system32> cscript slmgr.vbs /skms kms.lotro.cc
C:\Windows\system32> cscript slmgr.vbs /ato
```

## Reverse the scroll of mouse (natural scrolling)

* [Reverse the scroll of mouse](https://answers.microsoft.com/en-us/windows/forum/windows_10-other_settings/reverse-the-scroll-of-mouse/334669c3-8a45-4600-830a-8df628d7415e)

There’s a workaround that can be done to still perform the said action. We’ll be using registry tweaks to reverse the scroll of your mouse, here are the steps:

_Important: This section, method, or task contains steps that tell you how to modify the registry. However, serious problems might occur if you modify the registry incorrectly. Therefore, make sure that you follow these steps carefully. For added protection, back up the registry before you modify it. Then, you can restore the registry if a problem occurs. For more information about how to back up and restore the registry, refer to the following Microsoft Knowledge Base article. [How to back up and restore the registry in Windows](https://support.microsoft.com/en-us/help/322756/how-to-back-up-and-restore-the-registry-in-windows)_

1. In the search box, type Device Manager and click on the result.
1. Select Mice and other pointing devices and double-click your mouse.
1. Go to the Details tab, select Device instance path from the drop-down menu.
1. Right-click the value that shows in the Value box and select Copy.
1. Press OK and close the Device Manager window.
1. Open a Notepad or Word so you can take note of the VID ID, then paste it from there. We’ll be using the VID ID as a reference for the next steps.
1. In the search box, type regedit and click the result.
1. Go to this registry location: HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Enue\HID.
1. This is where we’ll uses the VID ID. Click the key that matches the VID ID that was copied earlier.
1. Select Device Parameters.
1. Select and double-click FlipFlopWheel.
1. Change the Value data from 0 to 1 and press OK.
1. Close the Registry Editor windows.
1. Restart your device to reflect the changes.
1. Check the result.

---

## Cliente ssh de Windows 10 y Ncat

Para que el cliente ssh nativo de Windows 10 funcione detrás del proxy, hay que instalar la utilidad [Ncat del paquete Nmap](https://nmap.org/).

Para instalar el paquete Nmap, vas a la [página de descargas](https://nmap.org/download.html), descargas el programa de instalación y lo ejecutas. Cuando el installer pregunta qué componentes quieres instalar, desmarca los componentes Npcap, Network Performance Improvements y Zenmap. Npcap es un packet capture y Zenmap es un cliente gráfico. No son necesarios para establecer un tunel proxy con el comando ncat y además el Network Performance Improvements toca el registry de Windows. El paquete Nmap también se puede instalar manualmente, aunque yo lo he hecho automáticamente con el programa de instalación. Puedes consultar las [instrucciones detalladas para instalar Nmap en Windows](https://nmap.org/book/inst-windows.html).

ACTUALIZACIÓN: la utilidad Ncat tiene su [propia página de inicio](https://nmap.org/ncat/) dentro de Nmap. En esa página se explica que tienen una versión compilada estáticamente, de forma que se puede usar el programa sin instalar nada más. Hay una [guia de uso de Ncat](https://nmap.org/ncat/guide/index.html) y una [página de manual](https://nmap.org/book/ncat-man.html).

Una vez instalado ncat, tienes que configurar ssh para que lo utilice como ProxyCommand. Esto lo haces editando el archivo ~/.ssh/config".La configuración del comando ProxyCommand con Ncat en Windows 10 es esta:

```
Host *
  ProxyCommand C:\Program Files (x86)\Nmap\ncat.exe --proxy proxyinternet.tesa:8080 --proxy-type http --proxy-auth user:password %h %p
```

---