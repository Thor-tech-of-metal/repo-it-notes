Container and image
====================

* Containers are an abstraction at the app layer that packages code and dependencies together.

* Virtual machines (VMs) are an abstraction of physical hardware turning one server into many servers.

* Containers virtualize the operating system instead of hardware.

* Containers take up less space than VMs (container images are typically tens of MBs in size).

Docker has a contract between the docker image and the container.
In VM we do not  have that. Every imagine is able to run in the container becuase it has being build based on a predefined contract.


 Image file
========

**FROM :** Dockerfile must start with a `FROM` instruction. The FROM instruction specifies the Base Image from which you are building

**ENTRYPOINT ["/bin/sh","/entrypoint.sh"] :**  This is the path directory [/bin/sh] where the imagine is pointing to and the file [entrypoint.sh] to be executed.

**VOLUME /tmp :** This is the file system of the imagine it is defined in memory.
A key point to be aware of here is that anything after the VOLUME instruction in a Dockerfile will not be able to make changes to that volume e.g:

```c
VOLUME /data
RUN touch /data/x
RUN chown -R foo:foo /data
```
**EXPOSE :** When writing your Dockerfiles, the instruction EXPOSE tells Docker the running container listens on specific network ports. This acts as a kind of port mapping documentation that can then be used when publishing the ports.



Docker Container commands 
=========================

####Show active containers

`docker ps`

####Show all containers

`docker ps -a`


####Stop a container

`docker stop containerID`

#### Stop a container by image id or tagName

`docker rm $(docker stop $(docker ps -a -q --filter ancestor= [imagineID or tagName]  --format="{{.ID}}"))`

for instance:
`docker rm $(docker stop $(docker ps -a -q --filter ancestor=oraclecoreapp --format="{{.ID}}"))
`

#### Delete all containers and force

`docker rm $(docker ps -a -q) -f `

#### Connecting to the container and executing  bash commands

`docker exec -it  [CONTAINDER_ID]  bash  `

or  with entry point /bin/bash 

`docker exec -it  [CONTAINDER_ID]  bash /bin/bash `


 Docker internal network for containers
========


#### Docker link

Using --link  we can connect diferents  containers. For example:

1) We can create cassandra container and named it **cassandra** with the --name option
```
docker run --name cassandra -d cassandra:latest
```
2) We can **link** another docker container using --link 

```
docker run --link cassandra  -it imagesapplication:v1 -p 9000:9000
```
#### Docker network

Another good way to connect containers is by creating a network 

1) create a docker network . It will be called **example**

```
docker network create example
```

2) Use --net command to add the network called **example**  to the container
```
docker run -d --net example --name container1 [imageName]:[imagineVersion]
docker run -d --net example --name container2 [imageName]:[imagineVersion]
```
 

Docker Images commands 
========================

#### Check all images

`docker images`


#### Build docker images

`docker build /directory/dockerFile`

output: Successfully built 60c5987c1294 ---> this is the imagine id

#### Rename a image and tag it

where 967840b69584 is the number obtained after the build

`docker tag 60c5987c1294 oraclecoreapp`

#### Build docker images and tag it with a name

`docker build . -t minion`

####Start a image in a map the ports

**Publish ports and map them to the host** :  -p flag on docker run to publish and map one or more ports,

`docker run -p 8181:8080 [imagineTag]`

`docker run -p 8181:8080 [imagineID]`

####Start a image in a map the ports and don't exit 

`docker run -it imagesapplication:v1 -p 9000:9000`

####Start a image and map it to another image 

we run a cassandra image and give the name to the container. For example **cassandra**

1)  `docker run --name cassandra -d [imageName]:[imageVersion]`

Using the container name we linked it to another the image name **cassandra**. 

2) `docker run --link cassandra  -it imagesapplication:v1 -p 9000:9000`

#### delete a image

docker rmi [docker-image-id]

`docker rmi [tag-name]`

#### Delete all images

`docker rmi $(docker images -q)`

#### Stop a container by image id or tagName

`docker rm $(docker stop $(docker ps -a -q --filter ancestor= [imagineID or tagName]  --format="{{.ID}}"))`

for instance:
`docker rm $(docker stop $(docker ps -a -q --filter ancestor=oraclecoreapp --format="{{.ID}}"))


Docker general commands 
========================

#### Find container IP address

`docker inspect --format '{{ .NetworkSettings.IPAddress }}' $(docker ps -q)`


Docker compose
=============

#### Docker compose ps

`docker-compose ps`

#### Docker compose stop server

`docker-compose up`

#### Docker compose stop server

`docker-compose down`

#### Start one service

`docker-compose up  db`
