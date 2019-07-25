# docker-mariadb-myrocks
MariaDB with MyRocks DB engine. 

See official [MariaDB](https://hub.docker.com/_/mariadb/) documentation.

This installs MyRocks DB engine as recommended in https://github.com/docker-library/mariadb/issues/135.

Trusted build image on [dockerhub](https://cloud.docker.com/repository/registry-1.docker.io/blep/docker-mariadb-myrocks)

## Testing

Starts the server:

(notes we are using `--network=host` to make it easy to connect with the client. Don't use this in production.)

```
docker run --rm --name myrocks --network=host -e MYSQL_ROOT_PASSWORD=secret docker-mariadb-myrocks:10.3
```

Connect with the client:

```
docker run --rm -it --network=host docker-mariadb-myrocks:10.3 mysql -h 127.0.0.1 -P3306 -u root -psecret

# once connected, types command below and RocksDB should show
show plugins;
```
