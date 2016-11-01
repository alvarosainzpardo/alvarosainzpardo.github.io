# Documentación de Alvaro Sainz-Pardo.

Documentación y apuntes sobre temas diversos, relacionados con mi trabajo o con intereses personales, fundamentalmente herramientas de desarrollo y lenguajes de programación.

Este sitio web está hecho con MkDocs. Para más información, visitar [mkdocs.org](http://mkdocs.org).

---

## Guia de MkDocs

Esta documentación la mantengo en Github Pages, en el repositorio correspondiente al Github Pages de mi cuenta, o sea el repositorio alvarosainzpardo.github.io. En este repositorio tengo dos ramas (branches). La rama `master` es la que gestiona MkDocs. Los archivos fuente de la documentación los tengo en la rama `docs`.

### Comandos principales de MkDocs

* `mkdocs gh-deploy --clean` - Desplegar/Actualizar la documentación MkDocs en Github.

### Otros comandos

* `mkdocs new [dir-name]` - Create a new project.
* `mkdocs serve` - Start the live-reloading docs server.
* `mkdocs build` - Build the documentation site.
* `mkdocs help` - Print this help message.

### Project layout

    mkdocs.yml    # The configuration file.
    docs/
        index.md  # The documentation homepage.
        ...       # Other markdown pages, images and other files.
