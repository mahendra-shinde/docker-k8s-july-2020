Named Volumes
   Created EMPTY DIRECTORIES 
   Shared by multiple containers
   Create or Delete volumes using docker volume

Create a new volume (EMPTY Directory)

 docker volume create data1

 docker volume inspect data1

Create FIRST Container for volume data1
  
 docker run --name d1 -d -v data1:c:\mydata mcr.microsoft.com/windows/servercore/iis 

Create SECOND Container for volume data1
  
 docker run --name d2 -d -v data1:c:\mydata mcr.microsoft.com/windows/servercore/iis 

Open a fresh powershell window and use this command: [KEEP WINDOW OPEN]
 docker exec -it d1 powershell
 cd mydata
 dir 
 echo "Hello World" > file1.txt 

Open a fresh powershell window and use this command: [KEEP WINDOW OPEN]
 docker exec -it d2 powershell
 cd mydata
 dir
 get-content -path file1.txt

Clean Up
docker stop d1 d2
docker rm d1 d2
docker volume rm data1