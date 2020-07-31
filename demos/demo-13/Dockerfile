## Pull base image
FROM alpine

## docker exec => mkdir /app => cd /app
WORKDIR /app

## copy the SCRIPT from BUILD CONTEXT to 
## ABSOLUTE PATH (FULL PATH) are NOT ALLOWED
## files outside BUILD-CONTEXT cannot be used
COPY script.sh /app/script.sh

ENV USER=mahendra
## Command to EXECUTE when DOCKER RUN on NEWIMAGE
## COMMAND RECORDED INSIDE the MANIFEST
CMD ["sh","/app/script.sh"]