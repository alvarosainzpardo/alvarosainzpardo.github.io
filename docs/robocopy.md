# Guia del comando _robocopy_

---

## Enlaces, documentación

* [Robocopy](https://technet.microsoft.com/en-us/library/cc733145(WS.10).aspx)
* [Robocopy and a Few Examples](https://social.technet.microsoft.com/wiki/contents/articles/1073.robocopy-and-a-few-examples.aspx)
* [Como usar el comando Robocopy en Windows, ejemplos prácticos y códigos](https://norfipc.com/comandos/como-usar-comando-robocopy-ejemplos.html)

---

## Comando para hacer backup de los contenidos de un directorio

```
C:\>robocopy <origen> <destino> /mir /sl /xjd /xa:sh /xd "AppData" /xf *.inf /copy:dat /dcopy:t /r:0 /w:1 /mt /ndl /tee /log+:\robocopy.log
```

### Explicación de las opciones

* `/mir`: realiza una copia exacta o espejo del directorio origen en el directorio destino. Si en el directorio origen se han borrado archivos, se eliminarán en el directorio destino
* `/sl`: copia los enlaces simbólicos como enlaces simbólicos en el destino
* `/xjd`: excluye _junction points_ en este caso directorios. Otras opciones pueden ser `/xjf`para excluir _junction points_ de archivos y `/xj`para excluir todos los _juntion points_, tanto archivos como directorios
* `/xa:sh`: excluye archivos de sistema (s) y ocultos (h)
* `/xd "AppData"`: excluye los (sub)directorios llamados `AppData`
* `/xf *.inf`: excluye los archivos .inf
* `/copy:dat`: copia los datos, atributos y _timestamp_ de los archivos origen
* `/dcopy:t`: copia, o mantiene, el _timestamp_ de los directorios origen
* `/r:0`: no realiza ningún reintento si se produce un error
* `/w:1`: tiempo de espera transcurrido entre reintentos (aplicable cuando /r tiene valor mayor que 0)
* `/mt`: utiliza _multithreading_ cuando la cpu tiene varios núcleos
* `/ndl`: sin lista de directorios, no registra los nombres de directorio
* `/tee`: copia la salida estándar del comando en el archivo de log
* `/log+:<archivo.log>: realiza un log en el archivo especificado, la opción `+` sirve para añadir el contenido del log si el archivo ya existe (append)
