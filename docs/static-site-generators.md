# Static site generators

## Enlaces

* [Start a Blog in 2019 with Gatsby.js and Netlify](https://daveceddia.com/start-blog-gatsby-netlify/)
* [Gatsby Tutorial](https://www.gatsbyjs.com/docs/tutorial/)
* [A Step-by-Step Guide: Nanoc on Netlify](https://www.netlify.com/blog/2016/03/08/a-step-by-step-guide-nanoc-on-netlify/#main)
* [Nanoc Tutorial](https://nanoc.ws/doc/tutorial/)
* [Deploying Nanoc sites](https://nanoc.ws/doc/deploying/)
* [Working with GitHub Pages](https://docs.github.com/en/github/working-with-github-pages)

## Introducción

Los generadores de sitios web estáticos (en inglés, _static site generators_) son una categoría especial de CMS que generan webs totalmente estáticas a partir del contenido almacenado en el repositorio. Al ser contenido totalmente estático, los sitios web pueden desplegarse en cualquier CDN. Normalmente, los propios static site generators tienen un repositorio basado únicamente en archivos. De esta forma, el propio sitio se puede guardar en Github, por ejemplo, y desplegarse en un servicio de alojamiento a partir de ahí.

Las páginas web se pueden escribir en diferentes lenguajes de marcado, comúnmente se usa Markdown.

Los static site generatos se usan mucho en portales web modernos, porque son muy rápidos, al ser el contenido totalmente estático.

El concepto, así como todas las tecnologías de site generators, se explica en la web [Jamstack](https://jamstack.org/). Los principios fundamentales son:

* Desacoplamiento de las capas que componen el site, en particular desacoplamiento total entre el backend y en frontend
* Pre-renderización de todo el frontend, de forma que todo el frontend está compuesto por páginas estáticas

Plataformas:

* [Ghost](https://ghost.org/): es un headless CMS, que es algo distinto a un static site generator, pero que se utiliza también para el concepto Jamstack. Un headless CMS únicamente se ocupa del backend, está desacoplado del frontend, que en el concepto Jamstack se pre-renderiza totalmente en páginas estáticas
* [Jekyll](https://jekyllrb.com/): El site generator de Github. Hecho en Ruby.
* [Gatsby](https://www.gatsbyjs.com/)
* [Hugo](https://gohugo.io/)
* [Nanoc](https://nanoc.ws/): hecho con Ruby
* [Eleventy](https://www.11ty.dev/): es lo que utiliza Jamstack
* [Next.js](https://nextjs.org/)
* [Mkdocs](https://www.mkdocs.org/)

Alojamiento:

* [Github Pages](https://pages.github.com/)
* [Netlify](https://www.netlify.com/)
