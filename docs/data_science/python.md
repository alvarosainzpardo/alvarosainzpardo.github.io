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

---

[An end to end implementation of a Machine Learning pipeline](https://spandan-madan.github.io/DeepLearningProject/) es un tutorial que cubre el ciclo completo de un proyecto de machine learning, empezando por la captura (_scrapping_) de datos, en este caso datos de películas obtenidos de IMDB y TMDB. El objetivo del proyecto es predecir el género de una película a partir de datos textuales y visuales (el poster de la película). Se capturan los datos, se construye un dataset a partir de los datos capturados, se crean modelos prdictivos, tanto modelos _tradicionales_ como modelos que utilizan _deep learning_. Todo el código en python está disponible en el [repositorio github del proyecto](https://github.com/Spandan-Madan/DeepLearningProject) y en el [README](https://github.com/Spandan-Madan/DeepLearningProject/blob/master/README.md) hay instrucciones de instalación. Se utiliza Python 2.7 porque TensorFlow no es compatible con Python > 3.5.

Se recomienda utilizar [Conda](https://conda.io/docs/) para instalar los paquetes científicos de análisis de datos en Python (como NumPy o SciPy). Conda es un gestor de paquetes software (tipo apt o yum) hecho en Python y multiplataforma. Sirve para gestionar paquetes de software no sólo de Python (de JavaScript, por ejemplo) aunque se utiliza fundamentalmente para Python. Por encima de Conda, se han creado distribuciones de Python que incluyen también un conjunto de paquetes ya preinstalados y configurados, como por ejemplo Anaconda. En el artículo [Conda: Myths and Misconceptions](https://jakevdp.github.io/blog/2016/08/25/conda-myths-and-misconceptions/) hay una buena explicación de Conda, las diferencias con pip+virtualenv, cuándo utilizar uno u otro y los motivos que llevaron a la creación de Conda. Cuando se usa Conda, lo primero que se hace es crear un entorno y dentro de ese entorno se instala python y los paquetes necesarios.

[Using Data Science Tools for Email Audience Analysis: A Research Guide](https://shorensteincenter.org/email-analysis-research-guide/): Email is a crucial vehicle for media companies to generate reader revenue, yet the ways we talk about and measure email have not changed for almost two decades. Flawed, static measures can distract from success and lead to misguided strategies, crippling the development of new products. Using open source techniques from other fields, data scientists are able to provide a more complete picture of an organization’s readers and viewers. [The Shorenstein Center Notebooks](https://github.com/ShorensteinCenter) (written in Python and available on GitHub as a free, open-source tool) take a first step at demonstrating new ways to analyze list composition and performance in order to help editors and publishers ask and answer more nuanced questions.

### Otros enlaces

* [IBM Data Science Community: A landscape diagram for Python data](https://community.ibm.com/community/user/datascience/blogs/paco-nathan/2019/03/12/a-landscape-diagram-for-python-data): This article introduces a landscape diagram which shows 50 or so of the most popular Python libraries and frameworks used in data science. Landscape diagrams illustrate components within a technology stack alongside their complementary technologies. In other words, “How do the parts fit together?”
* [Machine Learning Plus](https://www.machinelearningplus.com/blog/): Simple and straightforward tutorials on machine learning in R and Python. No boring theory. Or never-ending technical specs.  Just simple guides with clear examples.
    * [Top 50 matplotlib Visualizations – The Master Plots (with full python code)](https://www.machinelearningplus.com/plots/top-50-matplotlib-visualizations-the-master-plots-python/)
    * [List Comprehensions in Python – My Simplified Guide](https://www.machinelearningplus.com/python/list-comprehensions-in-python/)
* [Ultimate Guide to Web Scraping with Python Part 1: Requests and BeautifulSoup](https://www.learndatasci.com/tutorials/ultimate-guide-web-scraping-w-python-requests-and-beautifulsoup/)
* [Top 10 IPython Notebook Tutorials for Data Science and Machine Learning](https://www.kdnuggets.com/2016/04/top-10-ipython-nb-tutorials.html)
* [Python para todos (3): ScyPy, NumPy, Pandas ...¿Qué librerías necesitamos?](http://data-speaks.luca-d3.com/2018/04/python-todos-3-librerias.html): contiene una descripción de librerías de data science para Python:
    * NumPy : Acrónimo de  Numerical Python. Su características más potente es que puede trabajar con matrices (array) de n dimensiones. También ofrece funciones básicas de algebra lineal, transformada de Fourier, capacidades avanzadas con números aleatorios, y herramientas de integración con otros lenguajes de bajo nivel como Fortran, C y C++
    * SciPy: Acrónimo de Scientific Python. SciPy está construida sobre la librería NumPy. Es una de las más útiles por la gran variedad que tiene de módulos de alto nivel sobre ciencia e ingeniería, como transformada discreta de Fourier, álgebre lineal, y matrices de optimización.
    * Matplotlib: es una librería de gráficos, desde histogramas, hasta gráficos de líneas o mapas de calor. También se pueden usar comandos de Latex para agregar expresiones matemáticas a tu gráfica.
    * Pandas: se utiliza para operaciones y manipulaciones de datos estructurados. Es muy habitual usarlo en la fase de depuración y preparación de los datos. Es una librería que se ha añadido recientemente, pero su gran utilidad ha impulsado el uso de Python en la comunidad científica.
    * Scikit Learn para machine learning: Construida sobre NumPy, SciPy y matplotlib, esta librería contiene un gran número de eficientes herramientas para machine learning y modelado estadístico, como por ejemplo, algoritmos de clasificación, regresión, clustering y reducción de dimensionalidad.
    * Statsmodels: para modelado estadístico. Es un módulo de Python que permite a los usuarios explorar datos, hacer estimaciones de modelos estadísticos y realizar test estadísticos. Ofrece una extensa lista de estadísticas descriptivas, test, funciones gráficas etc para diferentes tipos de datos y estimadores.
    * Seaborn: basada en matplotlib, se usa para hacer más atractivos los gráficos e información estadística en Python. Su objetivo es hacer de las situar las visualizaciones en el centro de las tareas de exploración e interpretación de los datos.
    * Bokeh: permite generar gráficos interactivos, y aplicaciones web. Permite generar gráficos 3D atractivos y puede trabajar de forma interactiva y alto rendimiento con datos en streaming,
    * Blaze: extiende las capacidades de Numpy y Pandas a datos distribuidos y en streaming. Se puede usar para acceder a datos de un gran número de fuentes como Bcolz, MongoDB, SQLAlchemy, Apache Spark, PyTables, etc.
    * Scrapy: se usa para rastrear la web. Es un entorno muy útil para obtener determinados patrones de datos. Desde la url de la home de una web, puede "bucear" en las distintas páginas del sitio para recopilar información.
    * SymPy: se usa para cálculo simbólico, desde aritmética, a cálculo, álgebra, matemáticas discretas y física cuántica. También permite formatear los resultados en código LaTeX.
    * Requests for accessing the web: trabaja de foram similar a la librería estándar urllib2, pero es más sencilla de codificar. 
* [Quick Tip: The easiest way to grab data out of a web page in Python](https://medium.com/@ageitgey/quick-tip-the-easiest-way-to-grab-data-out-of-a-web-page-in-python-7153cecfca58): tutorial para hacer _web scrapping_ usando pandas, que tiene una función que devuelve un data frame por cada tabla que tenga la página web
* [Python API tutorial - An Introduction to using APIs](https://www.dataquest.io/blog/python-api-tutorial/)
* [Python and JSON: Working with large datasets using Pandas](https://www.dataquest.io/blog/python-json-tutorial/)
* [folium - Python Data, Leaflet.js Maps](https://github.com/python-visualization/folium)
* [Are dogs appreciated fairly on @dog_rates?](https://vknight.org/unpeudemath/math/2018/03/28/rating-dog-rates.html): ejemplo de uso de varias librerías para analizar datos de una cuenta de Twitter que da puntuación a perros. La librería que usa para acceder a los datos de Twitter es [tweepy](http://www.tweepy.org/). [Repositorio Github](https://github.com/drvinceknight/DataScienceingDogRates) con un [notebook Jupyter](https://github.com/drvinceknight/DataScienceingDogRates/blob/master/main.ipynb).
* [Building a Convolutional Neural Network (CNN) in Keras](https://towardsdatascience.com/building-a-convolutional-neural-network-cnn-in-keras-329fbbadc5f5): A great way to use deep learning to classify images is to build a convolutional neural network (CNN). The Keras library in Python makes it pretty simple to build a CNN.

### Libros

* [10 Free Must-Read Books for Machine Learning and Data Science](https://www.kdnuggets.com/2017/04/10-free-must-read-books-machine-learning-data-science.html): Quick collection of such books to start your fair weather study off on the right foot. The list begins with a base of statistics, moves on to machine learning foundations, progresses to a few bigger picture titles, has a quick look at an advanced topic or 2, and ends off with something that brings it all together.
* [18 New Must Read Books for Data Scientists on R and Python](https://www.analyticsvidhya.com/blog/2016/10/18-new-must-read-books-for-data-scientists-on-r-and-python/)

---

## Jupyter Notebook

### Enlaces

* [Boost Your Jupyter Notebook Productivity](https://towardsdatascience.com/jupyter-notebook-hints-1f26b08429ad): helpful tips for boosting your productivity with Juypter.
* [What is Jupyter?](https://www.oreilly.com/ideas/what-is-jupyter): es una descripción introductoria muy buena sobre Jupyter, para qué sirve, cómo instalarlo y usarlo, cómo integrarlo con Docker para resolver los problemas de distribución del software necesario para ejecurar los programas, etc. Explica el soporte que Github le da a Jupyter (si se sube un archivo .ipynb a un repositorio, Github ejecuta el código y publica una página estática con los resultados). Se menciona el entorno cloud [Binder](http://mybinder.org/) que permite ejecutar notebooks en la nube. Explica la forma de trabajar con Jupyter, Github y Docker para distribuir y compartir notebooks. Hay dockerfiles específicos de Jupyter. Hay extensiones de Jupyter para crear elementos gráficos de aplicación, para hacer dashboards, para crear mapas basados en OpenStreetMap, para hacer visualizaciones de datos en 2D y 3D, para d3.js. Explica para qué sirve la utilidad nbviewer y cómo usarla. También da una lista de notebooks en python sobre temas de data science y machine learning.
* [The Jupyter notebook](https://jupyter-notebook.readthedocs.io/): documentación oficial
* [JupyterHub](https://github.com/jupyterhub/jupyterhub): instalación multiusuario de Jupyter. Se utiliza en el courso Foundations de la UC Berkeley
* [Zero to JupyterHub](https://zero-to-jupyterhub.readthedocs.io/): documentación sobre JupyterHub

---

## Pandas

### Enlaces

* [Intro to Pandas for Excel Super Users](https://towardsdatascience.com/intro-to-pandas-for-excel-super-users-dac1b38f12b0)
* [Common Excel Task in Python: Vlookup with Pandas Merge](https://medium.com/importexcel/common-excel-task-in-python-vlookup-with-pandas-merge-c99d4e108988)
* [Common Excel Tasks Demonstrated in Pandas](http://pbpython.com/excel-pandas-comp.html)
* [Common Excel Tasks Demonstrated in Pandas - Part 2](http://pbpython.com/excel-pandas-comp-2.html)
* [Pythoon Pandas Tutorial: A Complete Introduction for Beginners](https://www.learndatasci.com/tutorials/python-pandas-tutorial-complete-introduction-for-beginners/)

---

## Visualización de datos

### Enlaces

* [The Next Level of Data Visualization in Python](https://towardsdatascience.com/the-next-level-of-data-visualization-in-python-dd6e99039d5e): [Plotly](https://plot.ly/python/), How to make great-looking, fully-interactive plots with a single line of Python
