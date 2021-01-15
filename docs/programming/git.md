# Guia rápida de git

---

## Enlaces, documentación

* [Visualizing Git Concepts with D3](http://onlywei.github.io/explain-git-with-d3/)
* [A Visual Git Reference](http://marklodato.github.io/visual-git-guide/index-en.html)
* [More productive Git](https://increment.com/open-source/more-productive-git/)
* [A bunch of awesome git tutorials](https://gist.github.com/jaseemabid/1321592)
* [Git Quick Reference](http://jonas.nitro.dk/git/quick-reference.html)
* [Git Inmersion](http://gitimmersion.com/index.html): tutorial de git interactivo, inspirado en la premisa de que conocer algo es hacerlo.
* [Understanding Git Conceptually](https://www.sbf5.com/~cduan/technical/git/)
* Artículos de [Better Explained](https://betterexplained.com/) sobre sistemas de control de versiones:
    * [A Visual Guide to Version Control](https://betterexplained.com/articles/a-visual-guide-to-version-control/)
    * [Intro to Distributed Version Control (Illustrated)](https://betterexplained.com/articles/intro-to-distributed-version-control-illustrated/)
    * [Aha! Moments When Learning Git](https://betterexplained.com/articles/aha-moments-when-learning-git/)

---

## Empezar a usar git en un ordenador nuevo

Para empezar a utilizar git en un nuevo ordenador, hay que realizar dos tareas:

* Configurar git en el nuevo ordenador
* Crear y configurar la clave ssh para conectarse a github.com desde el nuevo ordenador

### Configurar git en un nuevo ordenador

Antes de crear un repositorio nuevo, o clonar uno existente, después de instalar el software de git, hay que configurar el usuario, tanto el _username_ como el _email_.

Configurar el _username_. La opción `--global` es para que la opción aplique de forma global a todos los repositorios:

```bash
$ git config --global user.name "Alvaro Sainz-Pardo"
```

Consultar el valor de la variable `user.name`:

```bash
$ git config --global user.name
```

Configurar el email:

```bash
$ git config --global user.email "alvarosainzpardo@gmail.com"
```

Consultar el valor de la variable `user.email`:

```bash
$ git config --global user.email
```

Para borrar el valor de una variable se utiliza la opción `--unset`:
```bash
$ git config --global --unset user.name
$ git config --global --unset user.email
```

Después de configurar el `user.name` y el `user.email`, es aconsejable configurar las prefencias de fin de línea para los archivos de texto, dependiendo del sistema operativo que se esté usando (Unix/Mac o Windows).

Para Unix/Mac:
```bash
$ git config --global core.autocrlf input
$ git config --global core.safecrlf true
```

Para Windows:
```bash
$ git config --global core.autocrlf true
$ git config --global core.safecrlf true
```

También es conveniente configurar un `.gitignore` global, con extensiones de archivos del sistema operativo, archivos binarios, archivos temporales del editor, etc. Para ello:

1. Crear un archivo `~/.gitignore_global`
2. Añadir al archivo las reglas deseadas. The Octocat tiene un [Gist con reglas](https://gist.github.com/octocat/9257657) adecuadas para añadir a este archivo. A esas reglas, hay que añadir `*.swp` para ignorar los archivos temporales de `vim`
3. Ejecutar el siguiente comando:

```bash
$ git config --global core.excludefile ~/.gitignore_global
```

### Crear y configurar la clave ssh para conectarse a GitHub

Hay dos tipos de URLs que se pueden utilizar para referenciar los repositorios remotos en GitHub: http y ssh.

Si se utilizan urls de tipo ssh, los pasos que hay que dar para autorizar la conexión a GitHub desde un ordenador nuevo son:

* Crear la clave en el ordenador nuevo
* Importar la clave en la cuenta de github.com
* Probar la conexión

#### Crear la clave en el ordenador nuevo

Crear la clave con el siguiente comando, poniendo la dirección de correo de la cuenta en github.com:

```bash
$ ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

Cuando pregunte por la localización del archivo, pulsar Enter:

```bash
Enter a file in which to save the key (/home/you/.ssh/id_rsa): [Press enter]
```

Cuando pregunte por la _passphrase_, teclear una _passphrase_ o pulsar Enter:

```bash
Enter passphrase (empty for no passphrase): [Type a passphrase]
Enter same passphrase again: [Type passphrase again]
```

#### Importar la clave en la cuenta de github.com

Seguir las instrucciones de [Adding a new SSH key to your GitHub account](https://help.github.com/articles/adding-a-new-ssh-key-to-your-github-account/).

#### Probar la conexión

Para probar que la nueva conexión funciona se utiliza el siguiente comando:

```bash
$ ssh -T git@github.com
```

Si hay errores de conexión, seguir las instrucciones de [Error: Permission denied (publickey)](https://help.github.com/articles/error-permission-denied-publickey/).

---

## Acceso mediante http

Si se utiliza http, no hay que crear claves de ssh ni darlas de alta en la cuenta de GitHub, simplemente hay que usar la url de tipo http al clonar el repositorio remoto. Por ejemplo:

```bash
$ git clone https://github.com/alvarosainzpardo/dotfiles.git
```

Este método de conexión funciona también si se está detrás de un proxy (ver instrucciones). La desventaja es que se pregunta el usuario y la clave de GitHub cada vez que se utiliza un comando git. Para evitar que esto ocurra, se puede utilizar un _credential helper_ que cachea el usuario/password durante un tiempo determinado.

Para activar el _credential helper_:

```bash
$ git config --global credential.helper cache
# Set git to use the credential memory cache
```

Para cambiar el tiempo predeterminado de cacheo de 15 minutos:

```bash
$ git config --global credential.helper 'cache --timeout=3600'
# Set the cache to timeout after 1 hour (setting is in seconds)
```

---

## Configurar git detrás de un proxy

Si te conectas a github.com mediante http, lo que hay que hacer es configurar la variable `http.proxy` con el valor correspondiente al proxy de la red:

```bash
$ git config --global http.proxy http://<user>:<passwd>@<proxyserver>:<port>/
```

También la variable `https.proxy`:

```bash
$ git config --global https.proxy http://<user>:<passwd>@<proxyserver>:<port>/
```

Por ejemplo:

```bash
$ git config --global http.proxy http://ds01170:<passwd>@proxyinternet.tesa:8080/
$ git config --global https.proxy http://ds01170:<passwd>@proxyinternet.tesa:8080/
```

Para eliminar el valor de las variables para el proxy, se utiliza la opción `--unset`:

```bash
$ git config --global --unset http.proxy
$ git config --global --unset https.proxy
```

Si la conexión a github.com es mediante ssh, cuando se accede detrás de un proxy hay que [configurar el ssh para que utilice un proxy](http://docs.alvarosainzpardo.com/ssh/#usar-ssh-detras-de-un-proxy) para las conexiones.

## Comandos git

### git data model

El modelo de datos de git tiene tres elementos:

* Working tree / working directory
* Staging area / index
* Repository (HEAD)

El _working tree_ el es sistema de archivos del sistema operativo, el directorio local de trabajo.

La _staging area_, también llamada _index_, es el área intermedia a la que se añaden los archivos cuando se ejecuta un `git add`.

El repositorio de git contiene el conjunto de _commits_ que se van haciendo. El repositorio de git, más específicamente, contiene:

* Un conjunto de _commit objects_
* Un conjunto de referencias a _commit objets_, que se llaman _heads_

Un _commit object_ contiene:

* Un conjunto de archivos
* Referencias a los _parent commit objects_, los _commit objects_ padres de este _commit object_
* Un hash SHA1, una cadena de 40 caracteres que identifica univocamente a este _commit object_

En todo momento, hay un último commit activo, que será el padre del nuevo commit que se haga en el repositorio. El _head_ del commit activo se denomina _HEAD_ (con mayúsculas). Dicho de otro modo, _HEAD_ siempre es la referencia (_head_) del actual commit activo, el último commit que se ha hecho, y que será el padre del nuevo commit que se haga.

### git reset (--soft, --hard, etc)

* [No comprendo la diferencia entre reset soft y reset mixed, alguien me podría explicar la diferencia?](https://platzi.com/discusiones/1170-git-github/321-53433eef-e76d-4620-9bad-103597d1d943/)
* [The difference between git reset — mixed, — soft and — hard](https://medium.com/@keshshen/the-difference-between-git-reset-mixed-soft-and-hard-299704b12a7a)
* [What's the difference between git reset --mixed, --soft, and --hard?](https://stackoverflow.com/questions/3528245/whats-the-difference-between-git-reset-mixed-soft-and-hard)
* [In plain English, what does “git reset” do?](https://stackoverflow.com/questions/2530060/in-plain-english-what-does-git-reset-do)
