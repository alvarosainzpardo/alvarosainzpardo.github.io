# Web Scraping

# Enlaces, documentación, tutoriales, etc.

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
* [How to convert JSON to CSV from the command-line?](https://e.printstacktrace.blog/how-to-convert-json-to-csv-from-the-command-line/)
    * [jq cookbook](https://e.printstacktrace.blog/jq-cookbook/)
    * [jq YouTube videos](https://www.youtube.com/c/eprintstacktrace/search?query=jq)
* [How to transform JSON to CSV using jq in the command line](https://www.freecodecamp.org/news/how-to-transform-json-to-csv-using-jq-in-the-command-line-4fa7939558bf/)

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

Then, do something like this:

```bash
cat file.json | jq -c '.[] | {"index": {"_index": "bookmarks", "_type": "bookmark", "_id": .id}}, .' | curl -XPOST localhost:9200/_bulk --data-binary @-
```

We’re taking the file file.json and piping its contents to jq first with the -c flag to construct compact output. Here’s the nugget: We’re taking advantage of the fact that jq can construct not only one but multiple objects per line of input. For each line, we’re creating the control JSON Elasticsearch needs (with the ID from our original object) and creating a second line that is just our original JSON object (.).

```bash

```

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
