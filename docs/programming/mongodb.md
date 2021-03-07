# MongoDB

---

## Enlaces, documentación

* [The MongoDB 3.6 Manual](https://docs.mongodb.com/v3.6/)
* [The MongoDB 4.4 Manual](https://docs.mongodb.com/manual/)
* [PyMongo Documentation](https://pymongo.readthedocs.io/)
* [The MongoDB Database Tools Documentation](https://docs.mongodb.com/database-tools/): mongodump, mongorestore, mongoexport, mongoimport
* [Back Up and Restore with MongoDB Tools](https://docs.mongodb.com/manual/tutorial/backup-and-restore-tools/)

---

## Cheat Sheet

```bash
# Conectarse a un servidor local (puerto 27017)
$ mongo
# Conectarse a un servidor remoto
$ mongo "mongodb://myhost:port/"
# Conectarse a un servidor remoto especificando base de datos
$ mongo "mongodb://myhost:port/mydatabase"
```

```js
// Mostrar bases de datos
> show dbs
// Usar/crear una base de datos
> use mydatabase
// Mostrar la base de datos activa
> db
// Eliminar (drop) base de datos
> use mydatabase
> db.dropDatabase()
// Mostrar colecciones
> show collections
> db.getCollectionNames()
["mycollection", "system.indexes"]
// Crear collection "mycollection"
> db.createCollection("mycollection")
// Una collection se crea al guardar el primer documento
> db.mycollection.insert({"name": "Alvaro"})
> db.mycollection.save({"name": "Alvaro"})
// select count(*) from ...
> db.mycollection.count()
// select * from ...
> db.mycollection.find({})
// delete from ...
> db.mycollection.remove({})
> db.mycollection.deleteMany({})
// drop table ...
> db.mycollection.drop()
// Recorrer el resultado de una consulta (el resultado de la consulta es una lista)
> db.mycollection.find().forEach(function(mydocument) {...})
> db.getCollectionNames().forEach(function(collectionname) {...})
```

---

## Comandos

### mongodump y mongorestore

```bash
# Dump de una base de datos, comprimido, especificando el archivo de salida
$ mongodump --db=mydatabase --gzip --archive=myfile.dump.gz
# Restore de un archivo comprimido
$ mongorestore --gzip --archive=myfile.dump.gz 
```
