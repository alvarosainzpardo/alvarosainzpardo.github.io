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
// select field1, field2, ..., fieldN from ... (with _id)
> db.mycollection.find({field1: true, field2: true, ..., fieldN: true})
> db.mycollection.find({field1: 1, field2: 1, ..., fieldN: 1})
// select field1, field2, ..., fieldN from ... (without _id)
> db.mycollection.find({_id: false, field1: true, field2: true, ..., fieldN: true})
> db.mycollection.find({_id: 0, field1: 1, field2: 1, ..., fieldN: 1})
// select * except field1, field2, ... fieldN from ...
> db.mycollection.find({field1: false, field2: false, ..., fieldN: false})
> db.mycollection.find({field1: 0, field2: 0, ..., fieldN: 0})
// delete from ...
> db.mycollection.remove({})
> db.mycollection.deleteMany({})
// drop table ...
> db.mycollection.drop()
// Recorrer el resultado de una consulta (el resultado de la consulta es una lista)
> db.mycollection.find().forEach(function(mydocument) {...})
> db.getCollectionNames().forEach(function(collectionname) {...})
```

### Operadores de comparación

```js
// select * where field = val
> db.mycollection.find({field: val})
// select * where field <> val
> db.mycollection.find({field: {$ne: val}})
// select * where field > val
> db.mycollection.find({field: {$gt: val}})
// select * where field >= val
> db.mycollection.find({field: {$gte: val}})
// select * where field < val
> db.mycollection.find({field: {$lt: val}})
// select * where field <= val
> db.mycollection.find({field: {$lte: val}})
// select * where field in (val, ...)
> db.mycollection.find({field: {$in: [val, ...]})
// select * where field not in (val, ...)
> db.mycollection.find({field: {$nin: [val, ...]}})
```

### Operadores lógicos

```js
// select * where cond1 and cond2 and ... condN
> db.mycollection.find({cond1}, {cond2}, ..., {condN})
> db.mycollection.find({$and: [{cond1}, {cond2}, ..., {condN}]})
// select * where cond1 or cond2 or ... condN
> db.mycollection.find({$or: [{cond1}, {cond2}, ..., {condN}]})
// select * where not cond
>> db.mycollection.find({$not: {cond}})
// select * where cond1 nor cond2 ... nor condN
> db.mycollection.find({$nor: [{cond1}, {cond2}, ..., {condN}]})
```

### Proyecciones (selección de atributos)

[Project Fields to Return from Query](https://docs.mongodb.com/manual/tutorial/project-fields-from-query-results/)

```js
// select _id, col1 from mycollection where cond1
> db.mycollection.find({cond1}, {col1: 1})
> db.mycollection.find({cond1}, {col1: true})
// select _id, col1, col2, ... colN from mycollection where cond1
> db.mycollection.find({cond1}, {col1: 1, col2: 1, ..., colN: 1})
// Excluir atributos de la salida
> db.mycollection.find({cond1, ..., condN}, {col1: 0, col2: 0, ..., colN: 0})
// Suprimir _id: select col1, col2, ... colN from mycollection where cond1
> db.mycollection.find({cond1}, {_id: 0, col1: 1, col2: 1, ..., colN: 1})
// No se pueden mezclar atributos con 1 y atributos con 0. Únicamente con _id
> db.groups.find({service: "castellon"}, {apikey: 0, resource: 1}).pretty()
Error: error: {
        "ok" : 0,
        "errmsg" : "Cannot do inclusion on field resource in exclusion projection",
        "code" : 31253,
        "codeName" : "Location31253"
}
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
