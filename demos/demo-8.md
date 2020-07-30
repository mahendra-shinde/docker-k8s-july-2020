## ENV Demo

1. Creating a single container with Single ENV Variable

```
$ docker stop c1
$ docker rm c1
$ docker run -d --rm -e "AUTHOR=Mahendra Shinde" --name c1 mcr.microsoft.com/windows/servercore/iis
$ docker exec -it c1 powershell
$ echo $ENV:AUTHOR
## You should "Mahendra Shinde"
$ exit
$ docker stop c1
## When used --rm, container would be auto-deleted on stop
```

2. Create the env file named "myvars.env"

```ini
AUTHOR=Mahendra Shinde
VER=1.0
Connection=tcp://xyz:1234
```

3. Creating a container with MULTIPLE envs from "env" file 

```
$ docker run -d --rm --env-file myvars.env --name c1 mcr.microsoft.com/windows/servercore/iis
$ docker exec -it c1 powershell
$ echo $ENV:AUTHOR
$ echo $ENV:Ver
$ echo $ENV:Connection
## You should "Mahendra Shinde", "1.0", "tcp://xyz:1234"
$ exit
$ docker stop c1
## When used --rm, container would be auto-deleted on stop
```