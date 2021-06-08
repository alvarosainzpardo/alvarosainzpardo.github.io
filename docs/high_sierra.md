# High Sierra

## Enlaces

* [dosdude1](http://www.dosdude1.com/)
* [EveryMac.com](https://everymac.com/)
* [macOS Mojave - Technical Specifications](https://support.apple.com/kb/SP777?locale=en_US)
* [How to Install macOS 10.14 Mojave on an Unsupported Mac](https://www.youtube.com/watch?v=v9sE_FhSdT8)
* [mas-cli](https://github.com/mas-cli/mas)
* [iCloud.com - Safari 13 unable to login, also Apple Support idmsa issues](https://discussions.apple.com/thread/251247486)
* [How I solved the Safari 13 and High Sierra problem with idmsa.apple.com unsecure connection (all Apple logins)](https://discussions.apple.com/thread/251211674)
* [Unable to establish secure connection to idmsa.apple.com](https://discussions.apple.com/thread/251210686?answerId=252326921022#252326921022)

### Anti-aliasing, Sub-pixel rendering

* [Understanding Sub-Pixel (LCD Screen) Anti-Aliased Font Rendering](http://alienryderflex.com/sub_pixel/)
* [Fix MacOS Catalina or macOS Big Sur Fonts After Upgrade](https://colinstodd.com/posts/tech/fix-macos-catalina-fonts-after-upgrade.html)
* [Fix macOS Mojave Font Rendering Issue | Big Sur Update](https://ahmadawais.com/fix-macos-mojave-font-rendering-issue/)
* (26/09/18) [How to Fix Blurry Fonts in MacOS Mojave for Non-Retina Displays](https://osxdaily.com/2018/09/26/fix-blurry-thin-fonts-text-macos-mojave/)
* (30/10/18) [How to Fix Blurry Fonts on macOS Mojave (With Subpixel Antialiasing)](https://www.howtogeek.com/358596/how-to-fix-blurry-fonts-on-macos-mojave-with-subpixel-antialiasing/)
* [The subpixel-AA debacle and font rendering](https://forums.macrumors.com/threads/the-subpixel-aa-debacle-and-font-rendering.2184484/)
* [macOS Catalina vs Mojave sub-pixel antialiasing](https://discussions.apple.com/thread/250998388)

### Big Sur patch

* [BigSurPatcher](https://www.reddit.com/r/BigSurPatcher/)
* [What DosDude1 thinks about Big Sur (in terms of a new patcher)](https://www.reddit.com/r/CatalinaPatcher/comments/he0tco/what_dosdude1_thinks_about_big_sur_in_terms_of_a/)
* big-sur-micropatcher
    * [How to install macOS Big Sur on an old unsupported Mac](https://www.macworld.co.uk/how-to/install-macos-old-mac-3654960/)
    * [big-sur-micropatcher](https://github.com/barrykn/big-sur-micropatcher)
* Patched Sur
    * [Patched Sur](https://github.com/BenSova/Patched-Sur)

## Rsync

Las opciones de rsync para preservar fechas de creación, modificación, ACLs, metadatos, etc. son: `rsync -avAX origen destino`. La opción `-v` es para verbose. Si origen es un directorio hay diferencia entre si el directorio termina o no en slash (/). Si el directorio no termina en slash (`rsync -avAX origen destino`), se crea el directorio origen en destino y se copia su contenido. Si el directorio origen termina en slash (`rsync -avAX origen/ destino`) el comando lo que hace es copiar en destino el contenido de origen. La opción `--delete` borra de destino los archivos de origen que hubiesen sido borrados, sirve para mantener totalmente sincronizados los contenidos de origen y destino, propagando los borrados de origen.

## Fonts

Para instalar fonts, hay que copiarlas a `~/Library/Fonts`. Hay que copiar el directorio 'Telefonica' y el directorio ''.

## Brew

Brew no está ya soportado en High Sierra pero se instala bien y por ahora no me ha dado problemas.

Para instalarlo, hay que ejecutar el script de instalación. Este script instala las command-line tools de Xcode, pero es mejor instalar Xcode completo, creo que incluso antes que instalar Brew (quizá así Brew no instala las command-line tools). Macvim da error al compilar si no está instalado Xcode completo.

## Xcode

La última versión de Xcode compatible con High Sierra (macOS 10.13.6) es la versión 10.1. Esta versión ya no se puede descargar de la App Store. Para descargar Xcode 10.1 hay que ir a https://developer.apple.com/download/more/, autenticarse con el Apple Id,  y buscar "Xcode 10.1", la descarga es del 23 de Octubre de 2019. Se descarga un archivo con extensión `.xip`, haciendo doble click en el archivo se descomprime y se extrae la aplicación Xcode, que hay que mover al directorio de Aplicaciones.

En la página [Xcode 10.2 on High Sierra – Step by Step](https://codewithchris.com/xcode-update/) hay instrucciones detalladas sobre cómo conseguir ejecutar la versión 10.2.1 de Xcode en High Sierra. En los comentarios de la página hay gente que reporta que, siguiendo las mismas instrucciones, han conseguido ejecutar la versión 10.3 de Xcode.

He descargado Xcode 10.1, Xcode 10.2.1 y Xcode 10.3.

## iTerm2

La última versión de iTerm2 compatible con High Sierra es la 3.3.12. Me la he descargado.

Para configurarlo, tengo que crear un profile llamado 'asainz (132x43)'. En este profile, tengo que hacer lo siguiente:

* Ponerlo como profile por defecto
* Tamaño de ventana 132x43
* Seleccionar la font 'Meslo LG S for Powerline' Regular de tamaño 14
* Importar los color presets `One Dark.itermcolors` y `One Light.itermcolors`. Seleccionar el color preset 'One Dark'
* Activar transparencia (muy poca)
* Activar el blur por defecto
