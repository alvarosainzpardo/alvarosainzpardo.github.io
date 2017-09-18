# Data Science en Python

## Enlaces, tutoriales, documentación, libros

El autor Jake VanderPlas tiene una serie de artículos divulgativos en O'Reilly sobre Python y módulos de Python para data science:

* Todos los artículos están en [Posts by Jake VanderPlas](https://www.oreilly.com/people/89c9c-jake-vanderplas): Python, scikit-learn, handling missing data, Pandas, Seaborn, Support Vector Machines, etc
* [A Whirlwind Tour of Python](https://www.oreilly.com/learning/a-whirlwind-tour-of-python): tutorial de python, sintaxis, tipos de datos, módulos para data science, etc. Este artículo está disponible como ebook en formato [epub](http://www.oreilly.com/programming/free/files/a-whirlwind-tour-of-python.epub), [mobi](http://www.oreilly.com/programming/free/files/a-whirlwind-tour-of-python.mobi) y [pdf](http://www.oreilly.com/programming/free/files/a-whirlwind-tour-of-python.pdf)
* [Introduction to scikit-learn](https://www.oreilly.com/ideas/intro-to-scikit-learn)
* Varios artículos sobre Pandas: [Introducing Pandas Objects](https://www.oreilly.com/learning/introducing-pandas-objects), [Operations in Pandas](https://www.oreilly.com/learning/operations-in-pandas), [Data Indexing and Selection](https://www.oreilly.com/learning/data-indexing-and-selection), [Pivot Tables in Python](https://www.oreilly.com/learning/pivot-tables)
* [Introduction to Support Vector Machines](https://www.oreilly.com/learning/intro-to-svm)
* [Data visualization with Seaborn](https://www.oreilly.com/learning/data-visualization-with-seaborn)
* [Handling missing data](https://www.oreilly.com/learning/handling-missing-data)

El libro de Jake VanderPlas se titula [Python Data Science Handbook](http://shop.oreilly.com/product/0636920034919.do)

[An end to end implementation of a Machine Learning pipeline](https://spandan-madan.github.io/DeepLearningProject/) es un tutorial que cubre el ciclo completo de un proyecto de machine learning, empezando por la captura (_scrapping_) de datos, en este caso datos de películas obtenidos de IMDB y TMDB. El objetivo del proyecto es predecir el género de una película a partir de datos textuales y visuales (el poster de la película). Se capturan los datos, se construye un dataset a partir de los datos capturados, se crean modelos prdictivos, tanto modelos _tradicionales_ como modelos que utilizan _deep learning_. Todo el código en python está disponible en el [repositorio github del proyecto](https://github.com/Spandan-Madan/DeepLearningProject) y en el [README](https://github.com/Spandan-Madan/DeepLearningProject/blob/master/README.md) hay instrucciones de instalación. Se utiliza Python 2.7 porque TensorFlow no es compatible con Python > 3.5.

Se recomienda utilizar [Conda](https://conda.io/docs/) para instalar los paquetes científicos de análisis de datos en Python (como NumPy o SciPy). Conda es un gestor de paquetes software (tipo apt o yum) hecho en Python y multiplataforma. Sirve para gestionar paquetes de software no sólo de Python (de JavaScript, por ejemplo) aunque se utiliza fundamentalmente para Python. Por encima de Conda, se han creado distribuciones de Python que incluyen también un conjunto de paquetes ya preinstalados y configurados, como por ejemplo Anaconda. En el artículo [Conda: Myths and Misconceptions](https://jakevdp.github.io/blog/2016/08/25/conda-myths-and-misconceptions/) hay una buena explicación de Conda, las diferencias con pip+virtualenv, cuándo utilizar uno u otro y los motivos que llevaron a la creación de Conda. Cuando se usa Conda, lo primero que se hace es crear un entorno y dentro de ese entorno se instala python y los paquetes necesarios.

### Otros enlaces

* [Quick Tip: The easiest way to grab data out of a web page in Python](https://medium.com/@ageitgey/quick-tip-the-easiest-way-to-grab-data-out-of-a-web-page-in-python-7153cecfca58): tutorial para hacer _web scrapping_ usando pandas, que tiene una función que devuelve un data frame por cada tabla que tenga la página web

## Jupyter Notebook

### Enlaces

* [What is Jupyter?](https://www.oreilly.com/ideas/what-is-jupyter): es una descripción introductoria muy buena sobre Jupyter, para qué sirve, cómo instalarlo y usarlo, cómo integrarlo con Docker para resolver los problemas de distribución del software necesario para ejecurar los programas, etc. Explica el soporte que Github le da a Jupyter (si se sube un archivo .ipynb a un repositorio, Github ejecuta el código y publica una página estática con los resultados). Se menciona el entorno cloud [Binder](http://mybinder.org/) que permite ejecutar notebooks en la nube. Explica la forma de trabajar con Jupyter, Github y Docker para distribuir y compartir notebooks. Hay dockerfiles específicos de Jupyter. Hay extensiones de Jupyter para crear elementos gráficos de aplicación, para hacer dashboards, para crear mapas basados en OpenStreetMap, para hacer visualizaciones de datos en 2D y 3D, para d3.js. Explica para qué sirve la utilidad nbviewer y cómo usarla. También da una lista de notebooks en python sobre temas de data science y machine learning.
* [The Jupyter notebook](https://jupyter-notebook.readthedocs.io/): documentación oficial
* [JupyterHub](https://github.com/jupyterhub/jupyterhub): instalación multiusuario de Jupyter. Se utiliza en el courso Foundations de la UC Berkeley
* [Zero to JupyterHub](https://zero-to-jupyterhub.readthedocs.io/): documentación sobre JupyterHub
