# Guia rápida de git

---

## Enlaces, documentación

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

### Crear y configurar la clave ssh para conectarse a github.com

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

Si la conexión a github.com es mediante ssh, cuando se accede detrás de un proxy hay que configurar el ssh para que utilice un proxy para las conexiones.
