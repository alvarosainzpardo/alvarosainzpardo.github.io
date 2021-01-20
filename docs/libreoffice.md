# LibreOffice

## Enlaces

* [LibreOffice Questions](https://ask.libreoffice.org/en/questions/)
* [Curso de LibreOffice Writer - 40 Tutoriales en español](https://www.youtube.com/watch?v=17qiQOzf4GU&list=PLLLaU95AMQPqAgeXCjQgXawAPABR19U2k)
* [Curso de LibreOffice Calc - Tu Hoja de Cálculo](https://www.youtube.com/watch?v=RlDfuSh69OA&list=PLLLaU95AMQPrMifyMRgiwhqKA64g7Kiea)
* [LibreOffice Writer: 27 trucos para exprimir al máximo la alternativa a Word](https://www.xataka.com/basics/libreoffice-writer-trucos-para-exprimir-al-maximo-alternativa-a-word)
* [Optimiza LibreOffice para que tenga mejor compatibilidad con Microsoft Office](https://proyectosbeta.net/2016/03/optimiza-libreoffice-para-que-tenga-mejor-compatibilidad-con-microsoft-office/)
* [Cómo instalar las fuentes clásicas, Calibri, Cambria (etc) de Microsoft en Ubuntu 16.04](https://proyectosbeta.net/2016/09/como-instalar-las-fuentes-de-microsoft-en-ubuntu-16-04/)

## Instalar fuentes de Microsoft

Instalar el paquete para TTF MS Core fonts:

```bash
$ sudo apt install ttf-mscorefonts-installer
```

Ese paquete suele instalarse como parte de la instalación del paquete `ubuntu-restricted-extras`.

Instalar las fuentes Calibri, etc. Para ello hay que descargarse el PowerPoint Viewer 2007, dentro de ese paquete estan las fuentes. Podemos extraer las fuentes manualmente, usando la utilidad `cabextract` o automatizar todo el proceso (descarga, extracción e instalación de fuentes) usando el siguiente script:

```
$ wget -qO- http://plasmasturm.org/code/vistafonts-installer/vistafonts-installer | bash
```
