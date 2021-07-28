# Web Scraping

## Enlaces, documentación, tutoriales, etc.

* [pup](https://github.com/ericchiang/pup)
* [jq](https://stedolan.github.io/jq/)
    * [jq 1.6 Manual](https://stedolan.github.io/jq/manual/v1.6/)
* [scrape](https://github.com/jeroenjanssens/dsutils/blob/master/scrape): from book "Data Science at the Command Line"
    * [dsutils](https://github.com/jeroenjanssens/dsutils)
* [Data Science at the Command Line](https://www.datascienceatthecommandline.com/)
    * [GitHub repo](https://github.com/jeroenjanssens/data-science-at-the-command-line)
    * [Data Science Toolbox](https://github.com/datasciencetoolbox/datasciencetoolbox)
    * [datasciencetoolbox/dsatcl2e (Docker image)](https://hub.docker.com/repository/docker/datasciencetoolbox/dsatcl2e)
* [Web Scraping with pup and jq](https://kevinmarsh.com/2014/11/12/web-scraping-with-pup-and-jq.html)
* [xml2json command](https://github.com/Inist-CNRS/node-xml2json-command)
* [Web Scraping Lunch and Learn](https://dev.to/bdmorin/web-scraping-lunch-and-learn-184j): scrapy, beautiful soup, pup, jq
* [CSS selectors](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Selectors)
* [Top 15 Python Packages You Must Try](https://medium.com/tech-explained/top-15-python-packages-you-must-try-c6a877ed3cd0): Dash, Pillow, JmesPath, simplejson
* [JSONPath - XPath for JSON](https://goessner.net/articles/JsonPath/)
    * [Python JSONPath Next-Generation](https://github.com/h2non/jsonpath-ng)
    * [jsonpath-ng](https://pypi.org/project/jsonpath-ng/)
* [JMESPath](https://jmespath.org/)
    * [JMESPath - PyPi page](https://pypi.org/project/jmespath/)
    * [JMESPath - GitHub page](https://github.com/jmespath/jmespath.py)
* [JSON Queries? Empower your users with JMESPath!](https://levelup.gitconnected.com/json-queries-give-your-users-jmespath-power-ef8ab0d38553)
* [simplejson](https://github.com/simplejson/simplejson)
    * [simplejson - Readthedocs page](https://simplejson.readthedocs.io/)

---

## Ejemplos, recetas

```bash
# Usa scrape, xml2json y jq
curl "http://clojurescript.net/" | scrape -be '//body/script' | xml2json | jq '.html.body.script[].src
```

wget fetches the HTML code from BBC, which is then normalized by hxnormalize to improve digestability by hxselect (both installed on Ubuntu by sudo apt-get install html-xml-utils), which then extracts the part of the code being identified by the CSS selector. Lynx finally turns the code into a layouted text that you would see in a browser.
```bash
~> echo "http://www.bbc.com" |
   wget -O- -i- | 
   hxnormalize -x | 
   hxselect -i "div.most_popular_content" |  
   lynx -stdin -dump > theMostPoupularInNews
```

```bash

```

---

## jq

### Enlaces

* [How to convert JSON to CSV from the command-line?](https://e.printstacktrace.blog/how-to-convert-json-to-csv-from-the-command-line/)
    * [jq cookbook](https://e.printstacktrace.blog/jq-cookbook/)
    * [jq YouTube videos](https://www.youtube.com/c/eprintstacktrace/search?query=jq)
* [How to transform JSON to CSV using jq in the command line](https://www.freecodecamp.org/news/how-to-transform-json-to-csv-using-jq-in-the-command-line-4fa7939558bf/)
* [jq recipes](https://remysharp.com/drafts/jq-recipes)
* [jqTerm](https://jqterm.com/)

### Recetas para APIs FIWARE

* `{devices: [.devices[] | {device_id, entity_name, entity_type, attributes, static_attributes, lazy, commands, endpoint: (.endpoint // ""), protocol}]}`: procesa la salida del get devices del iot-agent. La transforma el payload para el api de registrar devices (en otro subservicio, por ejemplo). Sirve para copiar dispositivos de un servicio/subservicio a otro. La parte `endpoint: (.endpoint // "")` es opcional. En este caso se está usando el operador "valor por defecto" (`//`): si el json de entrada no tiene el atributo endpoint o su valor es nulo, entonces se pone comillas dobles. Para que el operador "valor por defecto" funcione hay que encerrar toda la expresión entre paréntesis
* `{services: [.services[] | {protocol: [.protocol], description, apikey, entity_type, attributes, static_attributes, lazy, commands}]}`: procesa la salida de get protocols del iot-agent. La transforma en el payload para el api de crear protocolos (en otro servicio/subservicio, por ejemplo). Sirve para copiar protocolos de un servicio/subservicio en otro.
* `{devices: [.devices[] | select(.device_id | test("^THR|^AIQ") | not)] | sort_by(.device_id)}`: procesa la salida del get devices del iot-agent. Filtra por los dispositivos cuyo device_id cumple la expresión regular y los ordena por device_id
* `[.devices[] | .device_id] | join(" ")`: procesa la salida de la llamada get devices del iot-agent. Lo transforma en un array de device_id. Ese arrray lo aplana con join para dejarlo en una secuencia de device_id separada por espacio en blanco, que se puede usar en un bucle for de un shell script
* `{actionType: "DELETE", entities: [.[] | {id, type}]}`: procesa la salida de la llamada get entities del CB. La transforma en el payload de la llamada NGSI, de tipo batch, que sirve para borrar un conjunto de entidades

Do something like this:

```bash
cat file.json | jq -c '.[] | {"index": {"_index": "bookmarks", "_type": "bookmark", "_id": .id}}, .' | curl -XPOST localhost:9200/_bulk --data-binary @-
```

We’re taking the file file.json and piping its contents to jq first with the -c flag to construct compact output. Here’s the nugget: We’re taking advantage of the fact that jq can construct not only one but multiple objects per line of input. For each line, we’re creating the control JSON Elasticsearch needs (with the ID from our original object) and creating a second line that is just our original JSON object (.).

Para transformar un json en csv usando jq hay que usar la orden `@csv` al final del pipeline. Hay que generar la primera fila con los nombres de las columnas y las filas siguientes, únicamente con los valores. La orden `@csv` procesa elementos individuales, no un array de elementos. Cada elemento tiene que ser un array de valores. Hay que generar, por tanto, un primer array con los nombres de las columnas y después, un array de valores por cada elemento (por cada linea del csv). Para generar el array con los nombres de las columnas hay que usar `(first | keys_unsorted)`. La orden `first` se queda con el primer elemento. La orden `keys_unsorted` se queda únicamente con las claves, sin ordenar alfabéticamente (en el mismo orden que aparecen en el objeto json). Para generar la secuencia de arrays de valores, un array por cada objeto json, hay que usar `map([to_entries[] | .value]) | .[]`. La función `map` espera un array de objetos y aplica el filtro pasado como parámetro a cada uno de los objetos del array, generando un array resultado. La orden `to_entries[]` transforma cada clave en un objeto {key: clave, value: valor}, eso se pasa a `.value` para quedarse con el valor y se empaqueta todo en un array con `[]`. Se genera, por tanto, un array de arrays que desempaqueta después con `.[]`. Juntandolo todo, sería:

```
jq -r '(first | keys_unsorted) as $keys | map([to_entries[] | .value]) as $rows | $keys, $rows[] | @csv'
```

Una versión más compacta de lo anterior sería:

```
jq -r '(first | keys_unsorted), (map([.[]]) | .[]) | @csv' archivo.json > archivo.csv
```

Para que la orden anterior funcione, el archivo json tiene que ser un array de objetos json.

El filtro `to_entries[] | .value` es equivalente a `.[]`. Cuando se aplica a un objeto, el filtro `.[]` devuelve los valores del objeto separados por comas. El filtro `[.[]]` genera un array con los valores del objeto

---

## simplejson

What’s wrong with the native json module in Python? Nothing! In fact, Python'sjson is simplejson. Meaning, Python takes a version of simplejson and incorporates it into each release. But usingsimplejson has some advantages:

* It works on more Python versions.
* It is updated more frequently than the version shipped with Python.
* It has (optional) parts that are written in C, making it very fast.

Due to these facts, something you will often see in scripts that work with JSON is this:

```python
try:
  import simplejson as json
except ImportError:
  import json
```

I would just use the defaultjson, unless you specifically need:

* raw speed
* something that is not in the standard library

Simplejson can be a lot faster than json, because it has some critical parts implemented in C. This speed will not be of interest to you, unless you are working with millions of JSON files. In that case, also check out UltraJSON, which is supposed to be even faster because almost all of it is written in C. 

---

## Datasets

### COVID-19

* [The COVID Tracking Project](https://covidtracking.com/): The COVID Tracking Project will stop collecting data on March 7, 2021
    * [The COVID Tracking Project - GitHub Page](https://github.com/COVID19Tracking)
* [Datadista - datasets/COVID-19](https://github.com/datadista/datasets/tree/master/COVID%2019)
* [Datos oficiales de COVID-19 en España](https://github.com/rubenfcasal/COVID-19)
* [Escovid19data: Capturando colaborativamente datos de COVID-19 por provincias en España](https://lab.montera34.com/covid19/)
    * [Escovid19data - GitHub Page](https://github.com/montera34/escovid19data)
    * [Scripts para generar los datos de COVID-19 por provincias en España del proyecto Escovid19data](https://code.montera34.com:4443/numeroteca/covid19)
* [Instituto de Salud Carlos III - COVID-19 en España](https://cnecovid.isciii.es/)
    * [Situación y evolución de la pandemia de COVID-19 en España](https://cnecovid.isciii.es/covid19/)
    * [Documentación y datos](https://cnecovid.isciii.es/covid19/#documentaci%C3%B3n-y-datos)
