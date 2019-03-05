# Docker

---

## Enlaces, documentación

* [Control Docker with systemd](https://docs.docker.com/config/daemon/systemd/): to configure the docker daemon network proxy settings, for example. Instead of manually adding and editing a docker systemd config file, you can use the command `systemctl edit docker`, that creates the config file, if it doesn't exist, and then edits the file

---

### MySQL

To run:

```bash
$ docker volume create mysql
$ docker run --rm -d --name mysql -p 3306:3306 -v mysql:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=mysecretpassword mysql:5
```

### PostgreSQL

To run:

```bash
$ docker volume create postgresql
$ docker run --rm -d --name postgresql -p 5432:5432 -v postgresql:/var/lib/postgresql/data -e POSTGRES_PASSWORD=mysecretpassword postgresql:9-alpine
```
