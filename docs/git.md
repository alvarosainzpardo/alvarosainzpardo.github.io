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

Configurar el _username_. La opción `-- global` es para que la opción aplique de forma global a todos los repositorios:

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

Consultar el valor de la variable `email`:

```bash
$ git config --global user.email
```
