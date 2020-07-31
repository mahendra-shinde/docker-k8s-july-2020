## Declarative Docker Build

```
docker build -t <IMAGENAME> <DIRPATH>
```

eg.
1. docker build -t mydata c:\mydata\

2. cd c:\mydata 
   docker build -t mydata . 

### What Happens??
1. DOCKER CLI will simply collect all the files (except files mentioned in .dockerignore)
   and UPLOAD them to DOCKER DAEMON. (Also called BUILD CONTEXT)
2. DOCKER CLI will also create a small MANIFEST and send it to DOCKER DEAMON
3. DOCKER DAEMON, will then SEARCH FOR "Dockerfile" (Case sensitive) inside the BUILD CONTEXT.
4. If "Dockerfile" is NOT found, build fails
5. Every single NON-COMMENT line in Dockerfile is considered as STEP (BUILD STEP).
6. And, for EVERY STEP docker daemon follow this commands:
	docker run <TEMP-CONTAINER> from <TEMP-IMAGE> of previous step
        docker cp OR exec 
	docker commit <TEMP-IMAGE>
	
	