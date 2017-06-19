# Guia rápida de ssh

---

## Enlaces, documentación

* [SSH via HTTP proxy in OSX](http://www.perkin.org.uk/posts/ssh-via-http-proxy-in-osx.html)
* [Connect with SSH through a proxy](https://stackoverflow.com/questions/19161960/connect-with-ssh-through-a-proxy)

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


