## Demo 1 Basic Container

1. Download (pull) nginx:alpine (Linux) from docker hub.

```
docker pull nginx:alpine
## If you get an ERROR, most probably it's because of windows mode!
```

2. Create and launch container in INTERACTIVE mode (keep the prompt open)

```
docker run -it --name c1 nginx:alpine
```

3.  Open a new Command prompt and try verifying container

```
## List all running containers
docker ps
## list of PROCESSES inside the container `c1`
docker top c1
## stop the container `c1`
docker stop c1
## delete the container (writable layer & meta-data)
docker rm c1
```