# Database Container using Named Volumes


1. Switch to Linux containers mode

2. Download the latest (8.x) mysql for Linux

```
$ docker pull mysql
```

3. Create a new ENV file "mydb.env"

```
MYSQL_ROOT_PASSWORD=password@1234
MYSQL_DATABASE=sample1
MYSQL_PASSWORD=pass12345
MYSQL_USER=mahendra
```

## Without Volume

1. Create the container without VOLUME

```
$ docker run --name db1 -d --env-file=mydb.env mysql
## Wait for 2 mins
## Inside container, login into mysql db
$ docker exec -it db1 mysql -umahendra -ppass12345 
SQL> use sample;
SQL> show tables;
## Expect EMPTY SET
SQL> create table emp ( empid int primary key, ename varchar(20));
SQL> show tables;
# Expecting 'emp' table
SQL> exit
## stop and delete the container db1 and then recreate it
$ docker stop db1
$ docker rm db1
## Recreate
$ docker run --name db1 --env-file=mydb.env -d mysql
## Inside container, login into mysql db
$ docker exec -it db1 mysql -umahendra -ppass12345 
SQL> use sample;
SQL> show tables;
## Expect EMPTY SET !!!
## The old database files are LOST!!
SQL> exit
```

## Without Volume

1. Create the container without VOLUME

```
$ docker volume create db-data
$ docker run --name db1 -v db-data:/var/lib/mysql --env-file=mydb.env -d mysql
## Wait for 2 mins
## Inside container, login into mysql db
$ docker exec -it db1 mysql -umahendra -ppass12345 
SQL> use sample;
SQL> show tables;
## Expect EMPTY SET
SQL> create table emp ( empid int primary key, ename varchar(20));
SQL> show tables;
# Expecting 'emp' table
SQL> exit
## stop and delete the container db1 and then recreate it
$ docker stop db1
$ docker rm db1
## Recreate
$ docker run --name db1 -v db-data:/var/lib/mysql --env-file=mydb.env -d mysql
## Inside container, login into mysql db
$ docker exec -it db1 mysql -umahendra -ppass12345 
SQL> use sample;
SQL> show tables;
## get 'emp' table
## The old database files are persisted!
SQL> exit
```

