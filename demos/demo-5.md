## Container Network (Windows NAT)

1. Switch Docker Desktop to Use "Windows Containers"

2. Download the latest IIS image 

```
$ docker pull mcr.microsoft.com/windows/servercore/iis:latest
```

3. Create TWO containers using the above image, both in default "nat" network.

```
$ docker run --name c1 -d mcr.microsoft.com/windows/servercore/iis:latest
$ docker run --name c2 -d mcr.microsoft.com/windows/servercore/iis:latest
# Ping c2 from c1 and c1 from c2 // Check if both containers can communicate
$ docker exec -it c1 ping c2
$ docker exec -it c2 ping c1
$ docker container inspect -f "{{.NetworkSettings.Networks.nat.IPAddress}}" c1
$ docker container inspect -f "{{.NetworkSettings.Networks.nat.IPAddress}}" c2
$ docker network inspect nat
```

4.  Use Container IP address to access web pages from local web browser

    `http://{C1-IPADDRESS}`
    `http://{C2-IPADDRESS}`

    > Don't forget to replace C1-IPADDRESS with IP Address of c1 container without curly braces
    > Don't forget to replace C1-IPADDRESS with IP Address of c2 container without curly braces


5.  Using DOCKER EXEC to Test IIS Service

```
$ docker exec -it c1 powershell
$ iwr -UseBasicParsing http://localhost 
$ exit
```

6.  Clean up

```
$ docker stop c1 c2
$ docker rm c1 c2
```
