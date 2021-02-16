# MongoDB

---

## Enlaces, documentación

*

---

## Cheat Sheet

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
# 
```