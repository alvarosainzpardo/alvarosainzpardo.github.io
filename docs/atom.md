# Atom

---

## Enlaces, documentación

---

## Remote Atom

El editor TextMate tiene una funcionalidad de edición remota de ficheros a través de una sesión ssh. Esta funcionalidad ha sido copiada posteriormente por otros editores, como Visual Studio Code o Atom.

Para utilizar esta funcionalidad:

* Se tiene que ejecutar una sesión ssh haciendo _remote port forwarding_ del puerto 52698:

```bash
$ ssh -R 52698:localhost:52698 <user@host>
```

* En la máquina remota, se tiene que editar el archivo ejecutando `rmate <nombre de archivo>`
* En la máquina local, el editor Atom tiene que tener instalado el paquete `Remote Atom` con el servidor arrancado

### Utilidad rmate

Existen dos versiones de este programa: la origina desarrollada por TextMate, que está implementada en Ruby, y un portado usando shell script, que es más fácil de instalar porque no tiene la dependencia de Ruby.

* [aurora/rmate](https://github.com/aurora/rmate): `rmate` implementado en shell script. Esta es la versión que yo utilizo
* [textmate/rmate](https://github.com/textmate/rmate): la versión original de TextMate, implementada en Ruby

### Paquete Remote Atom

Para instalar el paquete Remote Atom, seleccionas "Preferences...", después "+ seleccionas Install" y en la ventana de instalar paquetes buscas el paquete `remote-atom`. Hay que instalar la versión del usuario _randy3k_.
