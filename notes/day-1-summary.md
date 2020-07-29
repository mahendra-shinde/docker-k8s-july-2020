## Day 1 Summary

Containers are Generic packages for Applications.
A Container "contains" or "wraps" a single application and it's dependencies.
Container is an INSTANCE of Container image ( refers as "images" )
An Image is made-up of LAYERS, every layer has a meta-data and filesystem of it's own.
Layers and Images are carried in TAR balls (tar.gz).
Container registry is a service that allows you to maintain multiple image repositories on server.
Image repository refers to collection of several images of same application.
  mahendrshinde/myweb:1, mahendrshinde/myweb:2, ... 

docker is container runtime.
docker let you BUILD, SHIP & DEPLOY containers.
docker is founding member of OCI (Open Container Initiative).
docker cli (client), docker engine (daemon), docker REST api.

docker run -d --name c1 nginx:alpine

docker run -it --name c1 nginx:alpine

