# SQLite

---

## Enlaces, documentación

* [SQLite](https://sqlite.org/)
    * [SQLite Documentation](https://sqlite.org/docs.html)
* [SQLite Tutorial](https://www.sqlitetutorial.net/)
    * [Import a CSV File Into an SQLite Table](https://www.sqlitetutorial.net/sqlite-import-csv/)
* [Command Line Shell For SQLite](https://sqlite.org/cli.html)
* [sqlitebrowser](https://sqlitebrowser.org/): DB Browser for SQLite
    * [GitHub Page](https://github.com/sqlitebrowser/sqlitebrowser)
* [SQLiteStudio](https://sqlitestudio.pl/): A free, open source, multi-platform SQLite database manager written in C++, with use of Qt framework
    * [GitHub Page](https://github.com/pawelsalawa/sqlitestudio)
    * [SQLiteStudio Releases (to install)](https://github.com/pawelsalawa/sqlitestudio/releases)
* [How To Install and Use SQLite on Ubuntu 20.04](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-sqlite-on-ubuntu-20-04)

---

## Cheat Sheet


```bash
# Instalar sqlite:
$ sudo apt install sqlite3
# Instalar sqlitebrowser
$ sudo apt install sqlitebrowser
```

```sql
# Ayuda
sqlite> .help
# Lista de tablas
sqlite> .tables
# Describe tabla
sqlite> .schema tabla
# Importar CSV
sqlite>.mode csv
sqlite>.import archivo.csv tabla
# Ejecutar sentencias de archivo
sqlite>.read archivo
```

---

## Comandos

### Importar archivo csv

```bash
# La opción -csv sirve para poner .mode csv
# Si la tabla no existe, se crea
$ sqlite3 -csv database.db ".import arvhivo.csv tabla"
```
