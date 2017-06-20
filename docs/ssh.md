# Guia rápida de ssh

---

## Enlaces, documentación

* [SSH via HTTP proxy in OSX](http://www.perkin.org.uk/posts/ssh-via-http-proxy-in-osx.html)
* [Connect with SSH through a proxy](https://stackoverflow.com/questions/19161960/connect-with-ssh-through-a-proxy)
* [Connecting to Your Linux Instance Using SSH](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AccessingInstancesLinux.html)

---

## Usar ssh detrás de un proxy

El comando para realizar una conexión ssh a través de un servidor proxy es:

```bash
$ ssh <user>@<host> -o "ProxyCommand=nc -X connect -x <proxyhost>:<proxyport> %h %p"
```

Por ejemplo:

```bash
$ ssh asainz@sulaco.ttcloud.net -o "ProxyCommand=nc -X connect -x proxyinternet.tesa:8080 %h %p"
```

Para que este comando funcione, el servidor proxy tiene que aceptar el método de conexión `CONNECT` y el comando `nc` tiene que estar instalado en el sistema.

Para usar un proxy socks5 el comando es:

```bash
$ ssh <user>@<host> -o "ProxyCommand=nc -X 5 -x <proxyhost>:<proxyport> %h %p"
```

Y para usar un proxy socks4 se utilizaría la opción `-X 4`.

Para no tener que teclear el comando cada vez que se utiliza el cliente ssh se puede configurar esta opción en el archivo de configuración de ssh, `~/.ssh/config`.

Se puede añadir la opción para todos los hosts:

	Host *
		ProxyCommand          nc -X connect -x proxyhost:proxyport %h %p
		ServerAliveInterval   10

O para un host en concreto:

	Host sulaco.ttcloud.net
		ProxyCommand          nc -X connect -x proxyhost:proxyport %h %p
		ServerAliveInterval   10

La opción `ServerAliveInterval`es para que el proxy no desconecte después de un periodo de inactividad.

---

## Autenticación con clave privada (archivos .pem)

Para conectarse a máquinas virtuales de Amazon y Fiware, hay que utilizar la autenticación con clave privada (archivos .pem)

### Configuración del cliente

* [SSH Config Files](https://michaelheap.com/ssh-config-files/)

La opción para conectarse a un servidor que requiere autenticación por clave privada es `-i <archivo.pem>`:

```bash
$ ssh <user>@<host> -i <path/file.pem>
```

El archivo .pem tiene que tener permisos de lectura únicamente para el propietario del archivo (`chmod 400 <archivo.pem>`).

La configuracíón equivalente en el archivo `~/.ssh/config`sería:

	Host <host>
		IdentityFile <path/file.pem>

### Configuración del servidor

Cuando el servidor ssh está configurado para aceptar únicamente conexiones sin password mediante clave privada, en el directorio `.ssh` del usuario hay que copiar el archivo `authorized_keys` que se haya generado para el usuario por defecto de la maquina virtual.

El directorio `.ssh` tiene que tener permisos de lectura/escritura/ejecución sólo para el propietario (`chmod 700 ~/.ssh`) y el archivo `authorized_keys` permisos de lectura/escritura únicamente para el propietario (`chmod 600 authorized_keys`).

Además, hay que comprobar que el el archivo de configuración del servidor sshd (`/etc/ssh/sshd_config`) esté autorizado el acceso por ssh para el nuevo usuario. Esto hay que hacerlo **obligatoriamente en las máquinas virtuales Ubuntu de Fiware**.
