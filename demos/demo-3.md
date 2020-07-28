## Demo 3 Container port forwarding

1. Create and launch container in DETACHED mode (keep the prompt open)

```
docker run -d --name c1 -p 8081:80 nginx:alpine
```

3.  Continue same Command prompt and try verifying container

```
## List all running containers
docker ps
## list of PROCESSES inside the container `c1`
docker top c1
## stop the container `c1`
docker stop c1
## change the home page
docker exec -it c1 sh
cd /usr/share/nginx/html
echo "<h2>Hello World</h2>" > index.html
exit
```

4.  Open page in Web browser: `http://localhost:8081`

5. Copy files inside running containers

```
docker cp index.html c1:/usr/share/nginx/html/index.html
```