# Build, Ship & Run Containers !!
  
- Build Containers using "Dockerfile"
- Ship Container images using Docker Registry
- Run Containers using Docker CLI/Daemon


Container Image can have many NAMES (Tags) but A UNIQUE ID

`[OPTION:registry-URL][repository-name]:[TAG/version]`

`mcr.microsoft.com/windows/servercore/iis:latest`

```yaml
Registry-URL: mcr.microsoft.com
Repository:   windows/servercore/iis
TAG:		  latest
```

Images in DEFAULT registry, do not need "REGISTRY-URL"

`mahendrshinde/myweb:latest`

No Registry URL :::> from default registry index.docker.io/v1

    `docker.io/mahendrshinde/myweb:latest`
