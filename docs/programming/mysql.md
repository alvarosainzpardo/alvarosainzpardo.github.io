# MySQL

---

## Enlaces, documentación

* [MySQL cheat sheet](http://staff.washington.edu/weller/mysql/)

---

## Comandos

### mysqldump

[mysqldump official documentation (5.7)](https://dev.mysql.com/doc/refman/5.7/en/mysqldump.html)

Para hacer un dump de una base de datos:

```bash
$ mysqldump -u root -p database > dump.sql
```

Para restaurar un dump:

```bash
$ mysql -u root -p < dump.sql
```

Para hacer un dump de varias bases de datos a la vez:

```bash
$ mysqldump -u root -p --databases database1 database2 ... > dump.sql
```

Para hacer un dump de todas las bases de datos (incluida la base de datos mysql):

```bash
$ mysqldump -u root -p --all-databases --flush-privileges > dump.sql
```

La opción `--flush-privileges` es necesaria siempre que se incluya la base de datos `mysql` en la lista de bases de datos de las que se va a hacer el dump.

El comando para hacer un dump completo de un servidor mysql:

```bash
$ mysqldump -u root -p --all-databases --flush-privileges --routines > dump.sql
```

Para hacer un dump de únicamente la estructura de las bases de datos (tablas, etc.) pero sin copiar los datos:

```bash
$ mysqldump -u root -p --no-data ... > dump.sql
```

Si se quiere añadir al dump una orden `DROP DATABASE ...` antes de las ordenes `CREATE DATABASE`:

```bash
$ mysqldump -u root -p --add-drop-database ... > dump.sql
```

La opción `--single-transaction` asegura un snapshot consistente entre todas las tablas porque todo el dump se realiza en una única transacción. Esta opción funciona únicamente con el storage engine InnoDB (el habitual). El comando para hacer un dump completo de un servidor asegurando consistencia sería:

```bash
$ mysqldump -u root -p --all-databases --flush-privileges --routines --single-transaction> dump.sql
```

Todos los comandos mysqldump que redirigen la salida estándar a un archivo podrían tener problemas con los conjuntos de caracteres en algunas bases de datos. Si se produce este problema, sustituir la redirección por la opción `-r`:

```bash
$ mysqldump -u root -p database -r dump.sql
```

Para hacer el restore sin ningún problema de conjuntos de caracteres (si es necesario, sustituir 'utf8' por el conjunto de caracteres que corresponda):

```bash
$ mysql -u root -p --default-character-set=utf8
mysql> set names 'utf8';
mysql> source backup.sql;
```

Para comprimir el archivo dump, enviar la salida de mysqldump a un compresor, por ejemplo:

```bash
# Comprimir un dump
$ mysqldump -u [user] -p[password]--single-transaction --quick --all-databases | gzip > alldb.sql.gz
# Restaurar un dump comprimido
$ gunzip < alldb.sql.gz | mysql -u [user] -p[password]
```

Para restaurar el dump comprimido:

```bash
```

---
