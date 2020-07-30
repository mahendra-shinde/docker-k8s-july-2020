# Volume demo

Volumes are addition filesystem layers applied to containers.
Volumes could be "persistent", means can be retained after container is removed.

## Persistent Volumes using "Volume Binding"

1. Create a directory (folder) "C:\myapp" with one html file "default.html".

2. Create a container using Volume binding to host directory "C:\myapp" to container filesystem "C:\inetput\wwwroot"

```
$ docker run --name c1 -d -v c:\myapp:c:\inetpub\wwwroot:ro mcr.microsoft.com/windows/servercore/iis
```

> Windows might prompt you to enter `Administrator` credentials to allow Docker desktop to access "C:" drive.

3. Test your container using following commands:

```pwsh
$ $IP=docker inspect -f "{{.NetworkSettings.Networks.nat.IPAddress}}" c1
$ start "http://$IP"
```

## Linux Mode

1. You need C:\myapp with default.html page

2. Create a new NGINX container

```
$ docker run -d -p 8085:80 --name c2 -v C:\MyApp:/usr/share/nginx/html/:ro nginx:alpine
$ docker ps 
$ docker logs c2
$ start chrome "http://localhost:8085/default.html"
```