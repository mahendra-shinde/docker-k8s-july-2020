## Container Network Demo

1. Stop and delete existing container with name:

```
$ docker stop c1
$ docker rm c1
```

2.  Lets create container "C1" with network "none" and test it's IP

```
$ docker run -d --name c1 --net none nginx:alpine
$ docker inspect -f "{{.NetworkSettings.IPAddress}}" c1
$ docker exec -it c1 ifconfig
```

3. Lets create container "c2" & "c3" with network "host" and test it's IP

```
$ docker run -d --name c2 --net host nginx:alpine
## Below should fail
$ docker run -d --name c3 --net host nginx:alpine
$ docker inspect -f "{{.NetworkSettings.IPAddress}}" c2
$ docker inspect -f "{{.NetworkSettings.IPAddress}}" c3
$ docker exec -it c2 ifconfig
$ docker exec -it c3 ifconfig
## Check the error logs (of nginx process)
$ docker logs c3
```

4.  Lets create container "C4" with network "bridge" (DEFAULT) and test it's IP
```
$ docker run -d --name c4 --net bridge nginx:alpine
$ docker run -d --name c5 --net bridge nginx:alpine
$ docker inspect -f "{{.NetworkSettings.IPAddress}}" c4
$ docker inspect -f "{{.NetworkSettings.IPAddress}}" c5
$ docker exec -it c4 ifconfig
$ docker exec -it c5 ifconfig
$ docker network inspect bridge
```

5.  Cleaup up

```
$ docker stop c1 c2 c3 c4 c5
$ docker rm c1 c2 c3 c4 c5
```