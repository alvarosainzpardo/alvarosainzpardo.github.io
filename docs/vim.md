# Vim

---

## Documentación, tutoriales, enlaces, libros

En [vimcasts.org](http://vimcasts.org/) hay 68 tutoriales en video y 50 artículos sobre Vim. Realizados por Drew Neil, el autor del libro [Practical Vim](https://pragprog.com/book/dnvim2/practical-vim-second-edition).

El artículo [My experience with Vim](https://idyllic.co/blog/vim-and-moi/) tiene una lista de plugins recomendados.

### Libros

[A Byte of Vim](https://vim.swaroopch.com/) es un libro sobre Vim (versión 7). Se puede leer online en la web del libro y también está disponible su descarga gratuita en formato ebook: [pdf](https://www.gitbook.com/download/pdf/book/swaroopch/byte-of-vim), [epub](https://www.gitbook.com/download/epub/book/swaroopch/byte-of-vim) y [mobi](https://www.gitbook.com/download/mobi/book/swaroopch/byte-of-vim). El libro en formato _raw_ está disponible en su [repositorio github](https://github.com/swaroopch/byte-of-vim).

[Vim for humans](https://vimebook.com/en) es un libro introductorio cuyo objetivo es simplificar la curva de aprendizaje cuando se empieza a usar Vim.

---

## .vimrc

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
