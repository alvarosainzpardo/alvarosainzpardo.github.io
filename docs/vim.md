# Vim

---

## Documentación, tutoriales, enlaces

En [vimcasts.org](http://vimcasts.org/) hay 68 tutoriales en video y 50 artículos sobre Vim. Realizados por Drew Neil, el autor del libro [Practical Vim](https://pragprog.com/book/dnvim2/practical-vim-second-edition).

El artículo [My experience with Vim](https://idyllic.co/blog/vim-and-moi/) tiene una lista de plugins recomendados.

---

## .vimrc

---

## Colores / Esquemas de color

### True Colors en el terminal


Los esquemas de color no se ven igual en el _gui_ que en el terminal. Esto es porque, por defecto, vim utiliza 256 colores en modo terminal, aunque el terminal tenga soporte para _true color_.

Para que vim utilice _true colors_ en el terminal hay que añadir `set termguicolors` en `.vimrc`. Los terminales **mintty** (Cygwin), **iTerm2** (Mac) y **gnuterm** (Linux) tienen soporte para _true color_. Actualmente, hay un problema con el _colorscheme_ **Solarized** en terminal con el _true color_ activado. Los colores salen totalmente cambiados, tanto en background light como dark.

---

## Plugin managers

### Vundle

[Vundle](https://github.com/VundleVim/Vundle.vim) es un verdadero _plugin manager_, en el sentido de que, a partir de la configuración que se hace en el archivo _.vimrc_, descarga automáticamente los plugins y tiene comandos para actualizar la versión de los plugins instalados, etc. Es más completo que **Pathogen** en cuanto a funcionalidad.

#### Instalación

#### Uso

### Pathogen

#### Instalación

#### Uso

---

## Plugins

### Fugitive

[Fugitive](https://github.com/tpope/vim-fugitive) es un recubrimiento del comando git.

#### Tutoriales, documentación

* Hay una serie de 5 tutoriales en video en [vimcasts.org](http://vimcasts.org/). El primero de ellos es este: [Fugitive.vim - a complement to command line git](http://vimcasts.org/episodes/fugitive-vim---a-complement-to-command-line-git/)

#### Instalación

En la sección de **Vundle** de `.vimrc`, añadir:

```
Plugin 'tpope/vim-fugitive'
```
#### Uso

Los comandos de Fugitive empiezan con G (g mayúscula). Se utilizan en modo vim normal, tecleando los dos puntos (:). Los comandos más habituales son:

* **Gwrite**: guarda el archivo e invoca el commando `git add`
* **Gread**: descarta los cambios del archivo que se está editando y recupera la última versión guardada en git. Una vez recuperada, vuelve a abrirla en el buffer de edición
* **Gcommit**: invoca el comando `git commit` abriendo una ventana de edición para poder escribir el mensaje del commit
* **Gpush**: invoca el comando `git push`
* **Gpull**: invoca el comando `git pull`

---

## Mapeo de teclas

### Mapeo de teclas del sistema en OSX

En muchos tutoriales sobre vim en OSX se recomienda mapear la tecla **Caps Lock** por **Esc**. El motivo es que la tecla **Esc** en el teclado del mac está muy lejos en la esquina superior izquierda, es muy pequeña y es una tecla muy usada en vim. AVISO: Este mapeo no se puede hacer dentro de vim, se tiene que hacer a nivel de sistema operativo. De esta forma, el mapeo afectará al funcionamiento de todo el sistema, no únicamente la aplicación vim.

No tengo nada claro hacer este mapeo, precisamente porque afecta a todo el sistema, pero pongo a continuación el programa para realizarlo, para referencia futura.

El programa para mapear la tecla **Caps Lock** es [Seil](https://pqrs.org/osx/karabiner/seil.html.en). El mismo desarrollador tiene otra utilidad para hacer mapeos más generales de teclado llamada [Karabiner](https://pqrs.org/osx/karabiner/index.html.en).
