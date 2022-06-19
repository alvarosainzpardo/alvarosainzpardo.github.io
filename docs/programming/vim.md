# Vim

---

## Documentación, tutoriales, enlaces, libros

* En [vimcasts.org](http://vimcasts.org/) hay 68 tutoriales en video y 50 artículos sobre Vim. Realizados por Drew Neil, el autor del libro [Practical Vim](https://pragprog.com/book/dnvim2/practical-vim-second-edition).
* [Official Vim Documentation](https://vim.sourceforge.io/docs.php)
* [Vim Tips Wiki](http://vim.wikia.com/wiki/Vim_Tips_Wiki)
* El artículo [My experience with Vim](https://idyllic.co/blog/vim-and-moi/) tiene una lista de plugins recomendados.
* [Indenting source code](http://vim.wikia.com/wiki/Indenting_source_code)
* [Setup Vim, Powerline and iTerm2 on Mac OS X](https://coderwall.com/p/yiot4q/setup-vim-powerline-and-iterm2-on-mac-os-x)
* [Changing Vim indentation behavior by file type](https://stackoverflow.com/questions/158968/changing-vim-indentation-behavior-by-file-type)
* [Write Code Faster in Vim](https://jacobcomer.medium.com/write-code-faster-in-vim-c564ff9b9f6c)
* Artículos sobre vim de la web [The Valuable Dev](https://thevaluable.dev/)
    * [Is Vim Really Not For You? A Beginner Guide](https://thevaluable.dev/vim-beginner/): manos siempre en el teclado, mecanografia, velocidad de escritura, desactivar teclas de flechas, 
        * [atypingtest.com - Start Typing Faster](http://www.atypingtest.com/)
        * [-Snake-HJKL->](https://matthieucneude.com/snake/)
    * [A Vim Guide for Intermediate Users](https://thevaluable.dev/vim-intermediate/)
    * [A Vim Guide for Advanced Users](https://thevaluable.dev/vim-advanced/)
* [Boost Your Coding Fu With VSCode and Vim](https://www.barbarianmeetscoding.com/boost-your-coding-fu-with-vscode-and-vim)
    * [VSCodeVim](https://github.com/VSCodeVim/Vim): Vim emulation for Visual Studio Code
* The Valuable Dev: autor de [The Mouseless Dev](https://themouseless.dev/)
    * (06/04/21) [Is Vim Really Not For You? A Beginner Guide](https://thevaluable.dev/vim-beginner/): enlaces para escribir a máquina, búsquedas horizontales en la línea que estás editando
    * (28/04/21) [A Vim Guide for Intermediate Users](https://thevaluable.dev/vim-intermediate/): buffers, windows, tabs
    * (16/03/21) [A Vim Guide for Advanced Users](https://thevaluable.dev/vim-advanced/): g global command, substitute
    * (24/05/21) [A Vim Guide for Adept Users](https://thevaluable.dev/vim-adept/): folding
    * (27/06/21) [A Vim Guide For Veteran Users](https://thevaluable.dev/vim-veteran/)

### Libros

[A Byte of Vim](https://vim.swaroopch.com/) es un libro sobre Vim (versión 7). Se puede leer online en la web del libro y también está disponible su descarga gratuita en formato ebook: [pdf](https://www.gitbook.com/download/pdf/book/swaroopch/byte-of-vim), [epub](https://www.gitbook.com/download/epub/book/swaroopch/byte-of-vim) y [mobi](https://www.gitbook.com/download/mobi/book/swaroopch/byte-of-vim). El libro en formato _raw_ está disponible en su [repositorio github](https://github.com/swaroopch/byte-of-vim).

[Vim for humans](https://vimebook.com/en) es un libro introductorio cuyo objetivo es simplificar la curva de aprendizaje cuando se empieza a usar Vim. Los primeros capítulos enseñan a configurar Vim para hacerlo equivalente a otros editores de texto y que el usuario principiante no pierda tiempo. A partir de ahí, se enseña "la forma Vim de hacer las cosas", con un nivel introductorio.

[Use Vim Like A Pro](https://leanpub.com/VimLikeAPro)

[Learn Vimscript the Hard Way](http://learnvimscriptthehardway.stevelosh.com/)

---

## Neovim

### Enlaces

* [Neovim](https://neovim.io/)
* [Github de Neovim](https://github.com/neovim/neovim)
* [Wiki](https://github.com/neovim/neovim/wiki)
* [Top 23 Lua Colorscheme Projects (Jun 2022)](https://www.libhunt.com/l/lua/topic/colorscheme): Open-source Lua projects categorized as Colorscheme
* [LunarVim/nvim-basic-ide](https://github.com/LunarVim/nvim-basic-ide): A Basic Stable IDE config for Neovim
* [Neovim with Python on macOS](https://sergeykalistratov.com/neovim-with-python-on-macos/)
* [Switching to NeoVim (Part 1)](https://arusahni.net/blog/2015/03/switching-to-neovim-part-1.html)
* [Switching to NeoVim (Part 2)](https://arusahni.net/blog/2015/04/switching-to-neovim-part-2.html): con información para configurar la sección del plugin manager del `.vimrc` de forma que sea compatible con Vim y con Neovim. Su archivo `.vimrc` está [aqui](https://github.com/arusahni/dotfiles/blob/master/vimrc). He usado lo que cuenta para configurar mi `.vimrc`

### Instalación

The default config file location is:

```sh
~/.config/nvim/init.vim
```

Puede ser un nuevo archivo o un link simbólico al `~/.vimrc` existente (como en mi caso) para tener un único archivo de configuración válido para Vim y para Neovim..

```sh
$ mkdir -p ~/.config/nvim
$ ln -s ~/.vimrc ~/.config/nvim/init.vim
```

o:

```sh
$ mkdir -p ~/.config/nvim
$ ln -s ~/.vim/vimrc ~/.config/nvim/init.vim
```

#### Ubuntu

Para instalar la versión estable:

```sh
$ sudo add-apt-repository ppa:neovim-ppa/stable
```

Para instalar la última versión de desarrollo/inestable:

```sh
$ sudo add-apt-repository ppa:neovim-ppa/unstable
```

Después, ejecutar:

```sh
$ sudo apt-get update
$ sudo apt-get install neovim
```

#### macOS

```sh
$ brew install neovim
```

#### Instalar el soporte para python y node.js

```sh
$ pip2 install -U neovim
$ pip3 install -U neovim
```

Optional: To complete python integration, add the following lines to your `~/.config/nvim/init.vim`:

```vim
let g:python2_host_prog = '/path/to/binary/python'
let g:python3_host_prog = '/path/to/binary/python3'
```

```sh
$ npm install --global neovim
```

Next, you should check `:CheckHealth` command in nvim to see any issues with plugins and Python providers.

---

## Buffers, ventanas, pestañas

Son tres conceptos que se mezclan un poco en vim, sobre todo si eres un principiante.

Vim, de forma estándar, arranca con una ventana que ocupa toda el área de trabajo de vim (el emulador de terminal o la ventana del sistema operativo). En esa ventana se pueden abrir muchos archivos, por ejemplo ejecutando:

```sh
$ vim *.c
```

Después de ejecutar ese comando, en la ventana de vim sólo se mostrará el último de esos archivos que se haya abierto (posiblemente según el orden alfabético de los mismos), pero todos los archivos están abiertos en sus correspondientes buffers de edición, sólo que están ocultos, no se muestran en la ventana. En una ventana sólo se puede mostrar un buffer a la vez. Para trabajar con todos esos buffers abiertos, se puede ir cambiando el buffer que se muestra en la ventana o se pueden abrir más ventanas, dividiendo la "ventana de la aplicación vim" en varias ventanas de edición, cada ventana mostrando un buffer de edición diferente. Incluso se puede abrir el mismo buffer en dos ventanas distintas, para ver en cada ventana una zona distinta del mismo archivo.

### Ventanas

Cuando se abre una nueva ventana, se divide el área de trabajo de vim. Se puede dividir verticalmente u horizontalmente.

Se puede abrir una nueva ventana que edite un buffer nuevo o se puede abrir una ventana que también edite el buffer activo.

Para abrir una nueva ventana horizontalmente, se utiliza el comando `:new`, el comando `:vnew` abre una nueva ventana vertical. El comando `:split` divide el área de trabajo en dos ventanas, horizontalmente, editando ambas el buffer activo. Para hacer lo mismo, pero diviendo verticalmente el área de trabajo, utiliza el comando `:vsplit`.

Para moverse entre las ventanas, utiliza el comando `:w` seguido de `flecha arriba`, `flecha abajo`, etc. o seguido de `h, j, k o l`. El comando `:wh` activa la ventana de la derecha, el comando `:wj` activa la ventana de abajo, y así sucesivamente.

Para cerrar la venta activa, utiliza `:wq`, o simplemente `:q` (debe haber alguna diferencia entre los dos comandos, pero ahora mismo no la conozco). Se cierra la ventana, pero el buffer sigue abierto, aunque se queda oculto. El comando `:wo` cierra todas las ventanas abiertas, excepto la ventana activa (cierra las otras ventanas).

Para cambiar el tamaño de una ventana, se utiliza el comando `resize`, que tiene variantes en función de que la ventana sea horizontal (por tanto se aumenta o disminuye el número de líneas) o vertical (se aumenta o disminuye el número de columnas). Ejemplos:

* `:resize 30` (abreviado `:res 25`): cambia el tamaño de la ventana activa a 25 líneas
* `:vertical resize 75` o `:vert res 75`: cambia el tamaño de la ventana activa a 75 columnas
* `:res +10` añade diez filas, `:res -10` las quita
* `:vert res +10` añade 10 columnas, `:vert res -10'` quita 10 columnas

Los atajos de teclado de esos comandos son:

* `Ctrl+w` `+/-`: incrementar/decrementar altura (ej: `25 Ctrl+w +`)
* `Ctrl+w` `>/<`: incrementar/decrementar anchura (ej: `30 Ctrl+w >`)
* `Ctrl+w` `_`: establecer altura (ej: `30 Ctrl+w _`)
* `Ctrl+w` `|`: establecer anchura (ej: `40 Ctrl+w |`)
* `Ctrl+w` `=`: todas las ventanas con la misma altura/anchura

Cambiar el tamaño de las ventanas se hace mucho más cómodamente cuando está activo el modo ratón. Con el modo ratón activo, las ventanas se redimensionan pulsando en el borde de la ventana y arrastrando, igual que en un entorno gráfico. `:set mouse=n` activa el ratón en modo normal, `:set mouse=i` lo activa en modo inserción, `:set mouse=v` lo activa en modo visual y `:set mouse=a` lo activa en todos los modos. Si se está utilizando vim en una sesión de tmux, además de `:set mouse=a` hay que ejecutar el comando `:set ttyterm=xterm2`.

### Buffers

El comando `:ls` muestra la lista de los buffers abiertos, con el número de cada buffer y el archivo que le corresponde. El comando `:bn` cambia al siguiente buffer de la lista y el comando `:bp` cambia al anterior. Para seleccionar un buffer concreto, utiliza el comando `:b` seguido del número de buffer, por ejemplo `:b2`. Para editar un buffer, también se puede usar el comando `:b` seguido del nombre del archivo. Se puede escribir el nombre del archivo parcialmente y pulsar `tab` para completarlo. En caso de existir varios nombres que contengan el texto escrito, pulsando `tab` varias veces se van recorriendo cíclicamente los nombres.

Para cerrar un buffer, utiliza el comando `:bd` o `:bw`, aparentemente hacen lo mismo. Son el equivalente a `Ctrl+W` o `Cmd+W` en otros editores. Si el buffer se ha modificado y no se ha guardado, el buffer no se cerrará a menos que se añada `!`
al comando.

### Pestañas

---

## Colores / Esquemas de color

### Esquemas de color

* Base16
* Solarized
* Gruvbox
* Molokai
* Badwolf
* Wombat
* [Github](https://github.com/endel/vim-github-colorscheme)

### Base16

No es sólo un esquema de colores, es un _framework_ que proporciona un esquema de 16 colores (tiene una combinación de 16 colores por defecto pero hay muchas combinaciones diferentes) y una configuración para hacer _syntax highlighting_ muy bien diseñada.

* La web principal del proyecto es [https://github.com/chriskempson/base16](https://github.com/chriskempson/base16)
* Los diferentes temas creados con Base16 se pueden previsualizar en [https://chriskempson.github.io/base16/](https://chriskempson.github.io/base16/)
* Los temas Base16 para vim están en [https://github.com/chriskempson/base16-vim](https://github.com/chriskempson/base16-vim)

#### Instalación

Añadir lo siguiente al `vimrc` y ejecutar `PluginInstall` en Vim:

```
Plugin 'chriskempson/base16-vim'
```

Seleccionar el esquema de color deseado, por ejemplo:

```
colorscheme base16-default-dark
```

La lista de temas de color disponibles en Base16 está en https://github.com/chriskempson/base16-vim/tree/master/colors.

La página de Base16 para vim tiene bastantes recetas para configurar Base16 para vim en modo terminal. Consultar también https://github.com/chriskempson/base16-iterm2 para información sobre colores Base16 para iTerm2 y https://github.com/chriskempson/base16-shell, que es una utilidad para configurar los colores del terminal.

**[UPDATE: 02/08/17]**: parece ser que hay emuladores de terminal en los que se puede cambiar la paleta de 256 colores, por ejemplo iTerm2. En el esquema de color Base16 se puede utilizar esta opción (cambiar la paleta de 256 colores) incluso se proporciona un _shell script_ para cambiar los colores 17-21 de la paleta (para dejar los colores 0-15 sin cambiar y no afectar a otros programas) y versiones específicas de los temas de color para esta configuración. Hay más información sobre este tema en la página [How to install base16 for iTerm2?](https://vi.stackexchange.com/questions/8935/how-to-install-base16-for-iterm2).

### onedark.vim

[onedark.vim](https://github.com/joshdick/onedark.vim) es un tema para vim inspirado en el excelente tema One Dark del editor Atom. El tema [base16-onedark](https://github.com/chriskempson/base16-vim/blob/master/colors/base16-onedark.vim) del esquema de colores Base16 está inspirado en este tema. Este tema tiene versiones para _true color_ y para las paletas de 16 y 256 colores.

En la sección de instalación de la página del tema hay instrucciones para:

* detectar si el terminal tiene soporte para _true color_
* configurar tmux para usar el tema
* seleccionar las opciones de paleta de 16 y de 256 colores
* configurar vim-airline
* solucionar problemas comununes con _true color_ y las paletas de 16 y 256 colores

### True Color en el terminal

#### Enlaces

* [Colours in terminal](https://gist.github.com/XVilka/8346728): un enlace a git con una explicación muy buena sobre los diferentes modos de color de los emuladores de terminal, cómo detectar si el emulador de terminal tiene soporte para _true color_ y una lista de emuladores de terminal y programas con soporte para _true color_
* [Support for True Color (16 millions colors)](https://github.com/jonas/tig/issues/227): otro enlace a git con explicación de modos de color en los emuladores de terminal y soporte para _true color_ en diferentes programas. Tiene enlaces a utilidades interesantes, como un programa que es capaz de mostrar una imagen en el emulador de terminar cuando tiene soporte para _true color_
* [Using True Color in Vim with Tmux](https://deductivelabs.com/en/2016/03/using-true-color-vim-tmux/): una buena explicación de los diferentes modos de color en los emuladores de terminal y un buen tutorial de cómo activar el soporte para _true color_ en vim y en **tmux**

Los esquemas de color no se ven igual en versión _gui_ que en terminal. Esto es porque en la versión _gui_ vim utiliza todos los colores que proporciona el entorno gráfico (utiliza _true color_) mientras que, por defecto, vim utiliza 256 colores en modo terminal, aunque el terminal tenga soporte para _true color_.

El emulador de terminal tiene tres modos de color:

* paleta de 16 colores
* paleta de 256 colores
* paleta de colores _true color_

La paleta de 16 colores está formada por 8 colores estándar y 8 variantes "brillantes" de esos colores estándar. Los colores estándar son: negro, rojo, verde, amarillo, azul, magenta, cyan y blanco. El negro "estándar" es negro mientras que el negro "brillante" es un gris oscuro. El blanco "estándar" es un gris claro mientras que el blanco "brillante" es blanco. Muchos programas de terminal asumen esta disposición de colores. La paleta de 16 colores sí que se puede cambiar por lo que, en teoría, se pueden configurar esos 16 colores para que sean iguales a los de la paleta del esquema de color. Lo que ocurre es que es muy probable que los colores que quedan bien en vim en cuanto se sale de vim y se ejecuta otro programa (por ejemplo tmux) ya se vean mal. El motivo es que el otro programa no tiene forma de saber que se ha cambiado la paleta de 16 colores y da por sentado que se está usando la paleta estándar de 16 colores. Por este motivo, no suele usarse esta opción (cambiar la paleta de 16 colores) para cambiar los colores de vim en modo terminal.

La paleta de 256 colores es fija, no se puede cambiar. Algunos esquemas de color tienen una versión de 256 colores, en la que utilizan los colores fijos más parecidos posible a los colores _true color_ originales de la paleta. Esta es la opción más utilizada para cambiar los colores de vim en modo terminal, porque no se modifica la paleta de 16 colores y los otros programas de terminal no se ven afectados.

**[UPDATE: 02/08/17]**: parece ser que hay emuladores de terminal en los que se puede cambiar la paleta de 256 colores, por ejemplo iTerm2. En el esquema de color Base16 se puede utilizar esta opción (cambiar la paleta de 256 colores) incluso se proporciona un _shell script_ para cambiar los colores 17-21 de la paleta (para dejar los colores 0-15 sin cambiar y no afectar a otros programas) y versiones específicas de los temas de color para esta configuración.

Cuando el emulador de terminal tiene soporte para _true color_ están disponibles 32 millones de colores (colores de 24 bits) por lo que cualquier paleta de colores de cualquier programa se ve perfectamente. Es exactamente igual que lo que pasa cuando se utiliza un escritorio gráfico (Mac, Windows, etc). Esta es la opción recomendada.

Para saber si un emulador de terminal tiene soporte para _true color_ o no, el siguiente comando:

```bash
$ printf "\x1b[38;2;255;100;0mTRUECOLOR\x1b[0m\n"
```

debe escribir la palabra TRUECOLOR en color rojo en un emulador de terminal con soporte para _true color_. También se puede ejecutar el siguiente comando _awk_, que en un terminar con soporte para _true color_ debe mostrar un degradado de colores contínuo:

```awk
$ awk 'BEGIN{
    s="/\\/\\/\\/\\/\\"; s=s s s s s s s s;
    for (colnum = 0; colnum<77; colnum++) {
        r = 255-(colnum*255/76);
        g = (colnum*510/76);
        b = (colnum*255/76);
        if (g>255) g = 510-g;
        printf "\033[48;2;%d;%d;%dm", r,g,b;
        printf "\033[38;2;%d;%d;%dm", 255-r,255-g,255-b;
        printf "%s\033[0m", substr(s,colnum+1,1);
    }
    printf "\n";
}'
```

Para que vim utilice _true colors_ en modo terminal hay que añadir `set termguicolors` en `.vimrc`. Los terminales **mintty** (Cygwin), **iTerm2** (Mac) y **gnuterm** (Linux) tienen soporte para _true color_.

**[UPDATE: 12/07/2017]** Hay un problema con el _colorscheme_ **Solarized** en modo terminal con el _true color_ activado. Los colores salen totalmente cambiados, tanto con el background light como dark.

---

### Silent commands

Para suprimir los mensjes de un comando, ejecutarlo con `silent` delante. Si se quieren suprimir ademas los posibles mensjes de error, entonces ejecutarlo con `silent!` delante. Si es un comando shell, `silent` también elimina la necesidad de pulsar \<CR\> después de la ejecución del comando.

Ejemplos:

```vim
" If colorscheme one doesn't exist, no error messages are displayed
silent! colorscheme one
" Silent execution of shell commands
silent !git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim
```

### Execute

:exe[cute] {expr1} ..   Executes the string that results from the evaluation of {expr1} as an Ex command.  Multiple arguments are concatenated, with a space in between.  To avoid the extra space use the "." operator to concatenate strings into one argument.

Ejemplos:

```vim
silent execute '!mkdir -p ' . s:root_path . '/bundle'
silent execute '!git clone https://github.com/VundleVim/Vundle.vim.git ' . s:root_path . '/bundle/Vundle.vim'
```

#### Comprobar que un plugin está cargado antes de ejecutar un comando

Utilizar `if exists()` con alguna variable, función o comando proporcionado por el plugin para comprobar que está cargado.
Por ejemplo:

```vim
if exists('*SyntasticStatuslineFlag')
  set statusline+=%{SyntasticStatuslineFlag()}
endif
```

Opciones de `exists()`:

* exists('varname'): para una variable
* exists('\*funcname'): para una función
* exists(':cmdname'): para un comando
* exists('&optname'): para una opción

[How can I test for plugins and only include them if they exist in .vimrc?](https://superuser.com/questions/552323/how-can-i-test-for-plugins-and-only-include-them-if-they-exist-in-vimrc): en esta página dan varias soluciones al problema de comprobar si está cargado un plugin antes de utilizar comandos. Una solución propone crear una función para establecer opciones de plugins, ejecutar esta función después de la carga de los plugins, con `autocmd VimEnter * call <function>`

---

## Plugin managers

### Vundle

[Vundle](https://github.com/VundleVim/Vundle.vim) es un verdadero _plugin manager_, en el sentido de que, a partir de la configuración que se hace en el archivo _.vimrc_, descarga automáticamente los plugins y tiene comandos para actualizar la versión de los plugins instalados, etc. Es más completo que **Pathogen** en cuanto a funcionalidad.

#### Enlaces

* [Vundle](https://github.com/VundleVim/Vundle.vim): documentation in the README.md
* [auto installing vundle from your vimrc](https://erikzaadi.com/2012/03/19/auto-installing-vundle-from-your-vimrc/)

#### Instalación

`git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim`

Put this at the top of your `.vimrc` to use Vundle. Remove plugins you don't need, they are for illustration purposes.

 ```vim
 set nocompatible              " be iMproved, required
 filetype off                  " required

 " set the runtime path to include Vundle and initialize
 set rtp+=~/.vim/bundle/Vundle.vim
 call vundle#begin()
 " alternatively, pass a path where Vundle should install plugins
 "call vundle#begin('~/some/path/here')

 " let Vundle manage Vundle, required
 Plugin 'VundleVim/Vundle.vim'

 " The following are examples of different formats supported.
 " Keep Plugin commands between vundle#begin/end.
 " plugin on GitHub repo
 Plugin 'tpope/vim-fugitive'
 " plugin from http://vim-scripts.org/vim/scripts.html
 " Plugin 'L9'
 " Git plugin not hosted on GitHub
 Plugin 'git://git.wincent.com/command-t.git'
 " git repos on your local machine (i.e. when working on your own plugin)
 Plugin 'file:///home/gmarik/path/to/plugin'
 " The sparkup vim script is in a subdirectory of this repo called vim.
 " Pass the path to set the runtimepath properly.
 Plugin 'rstacruz/sparkup', {'rtp': 'vim/'}
 " Install L9 and avoid a Naming conflict if you've already installed a
 " different version somewhere else.
 " Plugin 'ascenator/L9', {'name': 'newL9'}

 " All of your Plugins must be added before the following line
 call vundle#end()            " required
 filetype plugin indent on    " required
 " To ignore plugin indent changes, instead use:
 "filetype plugin on
 " Put your non-Plugin stuff after this line
 ```

#### Uso

Brief help:

* :PluginList       - lists configured plugins
* :PluginInstall    - installs plugins; append `!` to update or just :PluginUpdate
* :PluginSearch foo - searches for foo; append `!` to refresh local cache
* :PluginClean      - confirms removal of unused plugins; append `!` to auto-approve removal

See `:help vundle` for more details or wiki for FAQ

### vim-plug

[vim-plug](https://github.com/junegunn/vim-plug) es otro _plugin manager_, más moderno que Vundle, que tiene varias ventajas: instalación/update en paralelo de plugins (acelera el arranque), se autoinstala de forma muy sencilla, carga diferida de plugins de forma condicional (p.e., cuando se edita un determinado tipo de archivo) lo que también acelera el arranque al cargarse menos plugins al inicio, etc.

#### Enlaces

* [Github de vim-plug](https://github.com/junegunn/vim-plug)
* [Tutorial](https://github.com/junegunn/vim-plug/wiki/tutorial)
* [Wiki](https://github.com/junegunn/vim-plug/wiki)
* [Tips](https://github.com/junegunn/vim-plug/wiki/tips)
* [FAQ](https://github.com/junegunn/vim-plug/wiki/faq)
* [How to Switch from Vundle to vim-plug](http://adam.garrett-harris.com/how-to-switch-from-vundle-to-vim-plug/): con info sobre post-update hooks (por ejemplo, para instalar jshint después de instalar el plugin syntastic)

#### Instalación

[Descargar plug.vim](https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim)
y grabarlo en el directorio "autoload".

##### Vim

```sh
curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```

#### Neovim

```sh
curl -fLo ~/.local/share/nvim/site/autoload/plug.vim --create-dirs \
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```

Se puede automatizar la instalación poniendo el comando en el archivo de configuración de Vim tal y como se sugiere [aqui](https://github.com/junegunn/vim-plug/wiki/tips#automatic-installation).

Place the following code in your .vimrc before `plug#begin()` call:

```vim
if empty(glob('~/.vim/autoload/plug.vim'))
  silent !curl -fLo ~/.vim/autoload/plug.vim --create-dirs
    \ https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
" autocmd VimEnter * PlugInstall --sync | source $MYVIMRC
  autocmd VimEnter * PlugInstall --sync
endif
```

Note that `--sync` flag is used to block the execution until the installer finishes.

(If you're behind an HTTP proxy, you may need to add `--insecure` option to the curl command. In that case, you also need to set $GIT_SSL_NO_VERIFY to true.)

#### Uso

Add a vim-plug section to your `~/.vimrc` (or `~/.config/nvim/init.vim` for Neovim):

1. Begin the section with `call plug#begin('~/.vim/plugged')` (or `call plug#begin('~/.config/nvim/plugged')` for Neovim)
1. List the plugins with `Plug` commands
1. `call plug#end()` to update `&runtimepath` and initialize plugin system
    - Automatically executes `filetype plugin indent on` and `syntax enable`.
      You can revert the settings after the call. e.g. `filetype indent off`, `syntax off`, etc.

#### Example

```vim
" Specify a directory for plugins
" - For Neovim: ~/.config/nvim/plugged
" - Avoid using standard Vim directory names like 'plugin'
call plug#begin('~/.vim/plugged')

" Make sure you use single quotes

" Shorthand notation; fetches https://github.com/junegunn/vim-easy-align
Plug 'junegunn/vim-easy-align'

" Any valid git URL is allowed
Plug 'https://github.com/junegunn/vim-github-dashboard.git'

" Multiple Plug commands can be written in a single line using | separators
Plug 'SirVer/ultisnips' | Plug 'honza/vim-snippets'

" On-demand loading
Plug 'scrooloose/nerdtree', { 'on':  'NERDTreeToggle' }
Plug 'tpope/vim-fireplace', { 'for': 'clojure' }

" Using a non-master branch
Plug 'rdnetto/YCM-Generator', { 'branch': 'stable' }

" Using a tagged release; wildcard allowed (requires git 1.9.2 or above)
Plug 'fatih/vim-go', { 'tag': '*' }

" Plugin options
Plug 'nsf/gocode', { 'tag': 'v.20150303', 'rtp': 'vim' }

" Plugin outside ~/.vim/plugged with post-update hook
Plug 'junegunn/fzf', { 'dir': '~/.fzf', 'do': './install --all' }

" Unmanaged plugin (manually installed and updated)
Plug '~/my-prototype-plugin'

" Initialize plugin system
call plug#end()
```

Reload .vimrc and `:PlugInstall` to install plugins.

### Commands

| Command                             | Description                                                        |
| ----------------------------------- | ------------------------------------------------------------------ |
| `PlugInstall [name ...] [#threads]` | Install plugins                                                    |
| `PlugUpdate [name ...] [#threads]`  | Install or update plugins                                          |
| `PlugClean[!]`                      | Remove unused directories (bang version will clean without prompt) |
| `PlugUpgrade`                       | Upgrade vim-plug itself                                            |
| `PlugStatus`                        | Check the status of plugins                                        |
| `PlugDiff`                          | Examine changes from the previous update and the pending changes   |
| `PlugSnapshot[!] [output path]`     | Generate script for restoring the current snapshot of the plugins  |

##### Actualizar plugins

Run `:PlugUpdate` to update the plugins. After the update is finished, you can review the changes by pressing `D` in the window. Or you can do it later by running `:PlugDiff`.

##### Actualizar vim-plug

Ejecutar `:PlugUpgrade` después de `:PlugUpdate`.

##### Eliminar plugins

1. Delete or comment out Plug commands for the plugins you want to remove.
1. Reload vimrc (:source ~/.vimrc) or restart Vim
1. Run :PlugClean. It will detect and remove undeclared plugins.

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

## Folding

El _folding_ está deshabilitado por defecto en vim. Además, por defecto el _folding_ es manual. Para configurar el folding de forma análoga a otros editores, o sea, folding automático activado y basado en sintaxis y con todos los niveles abiertos al abrir el archivo (sin folding), hay que añadir lo siguiente al archivo `.vimrc`:

```vim
set foldmethod=syntax
set nofoldenable
```

Otras opciones son:

```
set foldmethod=indent
set foldnestmax=10
set foldlevel=2
```
Una vez activado, los comandos más habituales para trabajar con _folds_ son:

* <kbd>z</kbd> + <kbd>o</kbd> opens a fold at the cursor.
* <kbd>z</kbd> + <kbd>Shift</kbd> + <kbd>o</kbd> opens all folds at the cursor.
* <kbd>z</kbd> + <kbd>c</kbd> closes a fold at the cursor.
* <kbd>z</kbd> + <kbd>m</kbd> increases the foldlevel by one.
* <kbd>z</kbd> + <kbd>Shift</kbd> + <kbd>m</kbd> closes all open folds.
* <kbd>z</kbd> + <kbd>r</kbd> decreases the foldlevel by one.
* <kbd>z</kbd> + <kbd>Shift</kbd> + <kbd>r</kbd> decreases the foldlevel to zero -- all folds will be open.

## Comentar lineas de código

Para comentar líneas de código, o descomentarlas, hay que hacer lo siguiente:

* Teclear <kbd>Ctrl</kbd> + <kbd>v</kbd> para entrar en modo _rectangular visual selection_
* Seleccionar el rectángulo correspondiente a los espacios en blanco del inicio de las líneas que se quieren comentar
* Sustituir (<kbd>r</kbd>) los espacios en blanco por los caracteres de comentario correspondientes al tipo de archivo
* Alternativamente a lo anterior, insertar al inicio (<kbd>Shift</kbd> + <kbd>i</kbd>) los caracteres de comentario

Para descomentar las líneas de código:

* Teclear <kbd>Ctrl</kbd> + <kbd>v</kbd> para entrar en modo _rectangular visual selection_
* Seleccionar el rectángulo correspondiente a los caracteres de comentario
* Sustituirlos por blanco (<kbd>r</kbd> + <kbd>space</kbd>) o eliminarlos (<kbd>x</kbd>)

## Macros

1. Para empezar a grabar la macro, teclear la letra <kbd>q</kbd> seguido de un caracter en minúscula que será el nombre de la macro. Por ejemplo, teclear <kbd>qa</kbd>
1. Realizar las acciones de edición que se deseen, se puede alternar entre el modo normal, el modo visual y el modo edición las veces que se quiera
1. Detener la grabación de la macro tecleando <kbd>q</kbd>
1. Ejecutar la macro tecleando <kbd>@</kbd> seguido del nombre de la macro. Siguiendo con el mismo ejemplo, teclear <kbd>@a</kbd>
1. Para repetir la ejecución de la macro un número de veces, teclear <kbd>:NN@</kbd> seguido del nombre de la macro. Por ejemplo, para ejecutar la macro anterior 15 veces seguidas, teclear <kbd>:15@a</kbd>
1. Nota: Si se quiere ejecutar una macro una vez por línea, y se quiere repetir la ejecución de la macro un número de veces, el último comando de edición de la macro tiene que mover la posición del cursor a la línea siguiente
