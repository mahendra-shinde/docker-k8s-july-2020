## Imperative approch for building new image

1. Create a new temporary container for MySQL Database, and copy [SQL files](https://github.com/mahendra-shinde/docker-k8s-july-2020/tree/master/demos/sql-files). for [env](https://raw.githubusercontent.com/mahendra-shinde/docker-k8s-july-2020/master/demos/mydb.env)
    
    > Note: make sure you have a sub-directory 'sql-files' with both data.sql and schema.sql files

```
$ docker run --name tempdb --env-file=mydb.env -d mysql
$ docker cp sql-files/schema.sql tempdb:/docker-entrypoint-initdb.d/01.sql
$ docker cp sql-files/data.sql tempdb:/docker-entrypoint-initdb.d/02.sql
```

2. Enter inside the container and run sql commands to populate my database.

```
$ docker exec -it tempdb mysql -umahendra -ppass12345
SQL> use sample1;
## Verify table
SQL> show tables;
## Verify data
SQL> select * from person;
SQL> exit
```

3. Commit the changes into NEW image

```
$ docker stop tempdb 
## Convert the R/W Layer of container into a new image-layer
## and create new image 'mydata' which contains all layers from original 'mysql' image
## plus new image populated now by commit command
$ docker commit tempdb mydata:latest
$ docker rm tempdb;
```

4. Test the newly created image.

```
## New container from new image
$ docker run --name db2 -d mydata:latest
$ docker exec -it db2 mysql -umahendra -ppass12345
SQL> use sample1;
## List all tables
SQL> show tables;
## Expected: person table
SQL> exit
$ docker stop db2
$ docker rm db2
```