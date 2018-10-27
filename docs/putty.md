# PuTTY

---

## Enlaces, documentación

* [PuTTY User Manual](https://www.ssh.com/ssh/putty/putty-manuals/0.68/index.html)
    * [Starting a session from the command line](https://www.ssh.com/ssh/putty/putty-manuals/0.68/Chapter3.html#using-cmdline)
* [How to Make Putty Automatically Login with User and Password](http://jafty.com/blog/how-to-make-putty-automatically-login-with-user-and-password/)

---

## Hacer login automáticamente con user y password

Para hacer ssh a una máquina haciendo login automáticamente con user y password hay que utilizar command line options de PuTTY. En la configuración de una sesión, se puede especificar el user pero no la password. La password hay que pasarla como opción en la línea del comando.

Ejemplos:

```dos
C:\> putty -load sesion -pw password
C:\> putty -load sesion -l user -pw password
C:\> putty -ssh user@host -pw password
```

