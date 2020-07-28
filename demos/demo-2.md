## Demo 2 Basic Container

1. Download (pull) nginx:alpine (Linux) from docker hub.

```
docker pull nginx:alpine
## If you get an ERROR, most probably it's because of windows mode!
```

2. Create and launch container in DETACHED mode (keep the prompt open)

```
docker run -d --name c1 nginx:alpine
```

3.  Continue same Command prompt and try verifying container

```
## List all running containers
docker ps
## list of PROCESSES inside the container `c1`
docker top c1
## stop the container `c1`
docker stop c1
## Debugging: create an additional PROCESS inside container
docker exec -it c1 uptime
## launch new shell
docker exec -it c1 sh
```

4.  Stop and Delete the container

```
docker stop c1
docker rm c1
```