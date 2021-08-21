# Dockerbuild

touch  Dockerbuild

FROM ubuntu
MAINTAINER krushnaji <rkrushnaji@gmail.com>
RUN apt-get update

CMD ["echo", "Hello Docker Zindabad"]


docker build -t myimage1:1.0 .
docker run cd5fd5f135db


FROM ubuntu
MAINTAINER krushnaji <rkrushnaji@gmail.com>
RUN apt-get update
RUN  apt install nginx 
RUN apt install wget 
RUN apt install unzip 
RUN apt install vim  
RUN apt install net-tools
RUN apt install curl

CMD service nginx start
CMD service nginx enable


RUN apt-get update && apt-get install -y \
    aufs-tools \
    automake \
    build-essential \
    curl \
    dpkg-sig \
    libcap-dev \
    libsqlite3-dev \
    mercurial \
    reprepro \
    ruby1.9.1 \
    ruby1.9.1-dev \
    s3cmd=1.1.* \
 && rm -rf /var/lib/apt/lists/*root1

______________________________________________________________
#############################################

PS C:\Users\root> docker image ls
REPOSITORY             TAG                 IMAGE ID            CREATED             SIZE
image1                     latest              4c96d090518b   6 minutes ago    165MB
PS C:\Users\root> docker image push krushnaji/image1
The push refers to repository [docker.io/krushnaji/image1]
An image does not exist locally with the tag: krushnaji/image1
PS C:\Users\root> docker tag  image1 krushnaji/image13
PS C:\Users\root> docker image push krushnaji/image13
The push refers to repository [docker.io/krushnaji/image13]
52eb06a9d10b: Pushing [===========>                                       ]  23.69MB/101.7MB                                                                                       

docker save  6fa50e34e3a6 -o C:\Users\root\Desktop\hudas\hudaserver.tar

docker load -i C:\Users\root\Desktop\hudas\hudaserver.tar
______________________________________________________________
#############################################


 docker container stats nginx1
 docker container stop nginx1
 docker container start nginx1
docker exec -it nginx1 bash
______________________________________________________________
docker run --name mywebserver2 -d -p 8081:80 -v /G/mydatacentre:/usr/share/nginx/html nginx:latest

docker container rename 0518367280b4 cid
docker run -d -it --name myubuntu2 -p 8080:80 ubuntu
docker exec -it myubuntu2 bash
docker container port myubuntu2
output look like __>   80/tcp -> 0.0.0.0:8080
______________________________________________________________
   16  curl --version
   17  curl 172.17.0.3:80

____________________________________________________
To create Image from docker container:
docker commit myubuntu2 vicky-image:firstimage
                                             REPOSITORY:TAG
docker commit myubuntu2 krushnaji/firstimage:firstimag
______________________________________________________________
To remove docker image:
docker rmi 994984d2771b
______________________________________________________________
To Push Docker Image to Docker Hub:

docker tag 0db056012d75 krushnaji/firstimage
                    ImageID           dockerhubname/imagename i.e tag

docker tag firstimage YOUR_DOCKERHUB_NAME/firstimage

docker push krushnaji/firstimage

______________________________________________________________
Save Docker Imagge in Tar file and share it with friend without using repository

              Dont' Use:not working

docker save busybox > busybox.tar

stratos@Dev-PC:~$ docker save imageID > /media/sf_docker_vm/archiveName.tar

Copy the archiveName.tar file to your new Docker instance using whatever method works in your environment, for example FTP, SCP, etc.

Run the docker load command on your new Docker instance and specify the location of the image tar file.

stratos@Dev-PC:~$ docker load < /media/sf_docker_vm/archiveName.tar
______________________________________________________________
My office PC
                          Dont' Use:not working
PS C:\Users\root> docker image ls
REPOSITORY             TAG                 IMAGE ID            CREATED             SIZE

vicky-image2           secondimage         6fa50e34e3a6        53 minutes ago      248MB
krushnaji/firstimage   latest              0db056012d75        About an hour ago   240MB
vicky-image            firstimage          0db056012d75        About an hour ago   240MB
ubuntu                 latest              f643c72bc252        4 weeks ago         72.9MB

PS C:\Users\root> docker save 6fa50e34e3a6 > C:\Users\root\Desktop\docker-image\imagearchieve.tar
PS C:\Users\root>
______________________________________________________________

Solution For Image tar

I wanted to add that the issue probably occurs because of the difference in behaviour of STDOUT between Windows and Unix. Therefore, using the STDOUT way of saving like:

docker save [image] > file.tar followed by docker load < file.tar

will not work if the save and load are executed on a different OS. Always use:

docker save [image] -o file.tar followed by docker load -i file.tar

to prevent these issues. Comparing the TAR files produced by the different methods, you will find that they have a completely different size (303MB against 614MB for me).

______________USE_______________________________

docker save  6fa50e34e3a6 -o C:\Users\root\Desktop\hudas\hudaserver.tar

 docker load -i C:\Users\root\Desktop\hudas\hudaserver.tar

docker tag  6fa50e34e3a6 krushnaji/hudaserver

______________________________________________________________________
****************************************************************
                                                    Final
****************************************************************
______________________________________________________________________
1. to create a container from ubuntu:18.04
PS C:\Users\root> docker run --name redicon1 -d  ubuntu:18.04
fa7adddaead0090c4816f6ba70e96e4848176b7f1b899eb51100be69dea7d462

2. to create an image fromcontainer created above i.e  redicon1

PS C:\Users\root> docker commit redicon1 rediimage1
sha256:a9e6e81c1461464236c2ee5944a350a600cb50c05aa0ab14244bf4eee891a53c

3. to create a container from rediimage1 with port mapping

PS C:\Users\root> docker run -p 8080:80 -td rediimage1
6c07b5f053a9452cfc4aa9dab313de1d920f0773423cfee55232a299bc8e420c
PS C:\Users\root>

4. enter into container 
 docker exec -it redicon2 bash
____________________________________________________________________________________
PS C:\Users\root> docker image ls -a
REPOSITORY             TAG                 IMAGE ID            CREATED              SIZE
rediimage1             latest              a9e6e81c1461        About a minute ago   63.3MB
ubuntu                 18.04               2c047404e52d        4 weeks ago          63.3MB
PS C:\Users\root> docker container ls -a
CONTAINER ID        IMAGE               COMMAND             CREATED              STATUS                          PORTS                  NAMES
6c07b5f053a9        rediimage1          "/bin/bash"         54 seconds ago       Up 52 seconds     0.0.0.0:80->8080/tcp   friendly_kowalevski
fa7adddaead0        ubuntu:18.04        "/bin/bash"         About a minute ago   Exited (0) About a minute ago                          redicon1
PS C:\Users\root>

PS C:\Users\root> docker container rename  friendly_kowalevski redicon2
PS C:\Users\root> docker container ls -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS                      PORTS                  NAMES
6c07b5f053a9        rediimage1          "/bin/bash"         2 minutes ago       Up 2 minutes    0.0.0.0:80->8080/tcp   redicon2
fa7adddaead0        ubuntu:18.04        "/bin/bash"         3 minutes ago     Exited (0) 3 minutes ago                           redicon1
6413c54a1f12        0db056012d75        "/bin/bash"         45 hours ago    Exited (255) 30 hours ago   0.0.0.0:8080->80/tcp   server1
1428566c3460        ubuntu:latest       "/bin/bash"         2 days ago          Exited (0) 45 hours ago                            myubuntu

PS C:\Users\root> docker exec -it redicon2 bash
root@6c07b5f053a9:/#

______________________________________________________________________
docker run -it --name container1 -d -p 127.0.0.1:8080:80/tcp ubuntu:18.04
