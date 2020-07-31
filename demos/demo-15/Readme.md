## Building ASP.NET Core Application Image

Pre-requisites:
1. DOTNET SDK 3.1 Installed [Installer](https://dotnet.microsoft.com/download/dotnet-core/thank-you/sdk-3.1.302-windows-x64-installer)

2. Docker Desktop Installed

## Steps

1. Created a folder 'demo-15' and using Powershell inside 'demo-15' folder, try creating a new asp.net core MVC project

```
$ cd demo-15
$ dotnet new mvc
## Build and publish application to subdirectory 'publish'
$ dotnet publish -o publish
```

2.  Create a Dockerfile inside 'demo-15' directory.

```Dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1

WORKDIR /app

COPY publish /app/

CMD ["dotnet","demo-15.dll"]
```

3.  Build and create a custom image

```
$ docker build -t aspapp1 .
```

4.  Test Run Application image

```
$ docker run -d --name a1 -p 8085:80 aspapp1
$ start chrome "http://localhost:8085"
# docker rm -f a1
```

5.  Signup at https://hub.docker.com and use new docker-id to publish image to docker-hub.

    Lets assume, docker-id is `mahendrshinde` [Please replace this with your docker-id]

```
$ docker login
Enter Username: mahendrshinde
Enter Password: <PASSWORD-WON'T BE VISIBLE>
$ docker tag aspapp1 mahendrshinde/aspapp1
$ docker push mahendrshinde/aspapp1
```

6.  Verify if image is uploaded to docker-hub. Visit URL https://hub.docker.com/u/mahendrshinde/

    > Replace username 'mahendrshinde' with your docker-id

