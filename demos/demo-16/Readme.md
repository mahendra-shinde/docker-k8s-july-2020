## Docker Compose

Running a multi-container application in common context.

- Create an Isolated network for all the services.
- Can define multiple networks
- Can create shared volumes for member containers
- Can SCALE the services
- Components
    Services
    Networks
    Volumes

## Steps
1. Create an empty folder 'demo-16'
2. Create a "docker-compose.yml" file inside 'demo-16'
3. Add following inside "docker-compose.yml" 

    ```docker-compose
    version: "3.0"
    services:
    app1:
        image: nginx:alpine
        restart: unless-stopped

    app2:
        image: busybox
        command: sleep 5m 
        depends_on:
        - app1
    ```

4.  From powershell/cmd run following commands

```
$ cd demo-16
# Validate the compose file
$ docker-compose config
# No Error: Display contents of file
# Launch the solution (-d detached)
$ docker-compose up -d
# Check the instances
$ docker-compose ps
## Get INSIDE "app2"
$ docker-compose exec app2 sh
## ping app1 from inside app2
$ ping app1
$ wget -spider http://app1
$ exit
``

5.  To undeploy application, use following command:

```
$ docker-compose down
```

6.  Deploy multiple instances of app1

```
$ docker-compose up --scale app1=3 -d
$ docker-compose ps
$ docker-compose exec --index=0 hostname -i
$ docker-compose exec --index=1 hostname -i
$ docker-compose exec --index=2 hostname -i
$ docker-compose down
```
