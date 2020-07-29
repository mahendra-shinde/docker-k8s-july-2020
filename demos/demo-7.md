## Windows Container : User Defined Networks

1.  Switch to Windows mode

2.  Create new container network "net1" with Subnet range "162.16.0.0/16" and with Driver type ics

```
$ docker network create net1 -d ics --subnet 162.16.0.0/16
$ docker network inspect net1
```

3.  Create another container network "net2" with Subnet range "182.18.0.0/16" and with Driver type ics

```
$ docker network create net2 -d ics --subnet 182.18.0.0/16
$ docker network inspect net2
```

4.  Create another container network "net3" with Subnet range "192.19.0.0/16" and with Driver type ics

```
$ docker network create net3 -d ics --subnet 192.19.0.0/16
$ docker network inspect net3
```

5. Deploy single container in all three network.

```
$ docker stop c1 d1 x1
$ docker rm c1 d1 x1
$ docker run -d --name c1 --net net1  mcr.microsoft.com/windows/servercore/iis:latest 
$ docker run -d --name d1 --net net2  mcr.microsoft.com/windows/servercore/iis:latest 
$ docker run -d --name x1 --net net3  mcr.microsoft.com/windows/servercore/iis:latest 
$ docker exec -it c1 ping d1

```

6. Get the container IP Address for all three containers

```
## should return 162.16.0.2
$ docker inspect -f "{{.NetworkSettings.Networks.net1.IPAddress}}" c1
## should return 182.18.0.2
$ docker inspect -f "{{.NetworkSettings.Networks.net2.IPAddress}}" d1
## should return 192.19.0.2
$ docker inspect -f "{{.NetworkSettings.Networks.net3.IPAddress}}" x1
```

7. Ping containers (Should fail)

```
$ docker exec -it c1 ping d1
$ docker exec -it c1 ping 182.18.0.2
$ docker exec -it d1 ping c1
$ docker exec -it d1 ping 162.16.0.2
$ docker exec -it c1 ping x1
$ docker exec -it c1 ping 192.19.0.2
```

8. Clean--up

```
$ docker stop c1 d1 x1
$ docker rm c1 d1 x1
$ docker network rm net1 net2 net3
```