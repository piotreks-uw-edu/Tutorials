### setting of the root user password
docker run --detach --name some-mariadb --env MARIADB_ROOT_PASSWORD=my-secret-pw  mariadb:latest

### Starting a MariaDB instance with a user, password, and a database
docker run --detach --name some-mariadb --env MARIADB_USER=example-user --env MARIADB_PASSWORD=my_cool_secret --env MARIADB_DATABASE=exmple-database --env MARIADB_ROOT_PASSWORD=my-secret-pw  mariadb:latest

### starting mariadb exposing port
docker run --name some-mariadb -p 3306:3306 -e MYSQL_ROOT_PASSWORD=my-secret-pw -d mariadb:tag

### install mariadb client
sudo apt-get install mariadb-client

### connect to maria-db
mysql -h 127.0.0.1 -P 3306 -u root -p

### get a list of all the current connections
SHOW PROCESSLIST

### statistics about the server operations
SHOW STATUS 