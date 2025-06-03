## What is Docker?

A software that allows us to create, monitor and manage containers. 

## Why use Docker?
**Business**:
- Open-source
- Reliable and compatible
- Simple and fast
- Usable on multi cloud
- Security features
**Individual**:
- No need to buy new hardware
- Run your app from anywhere
- Be prepared for the future (Docker is still growing as a DevOps tool but also among other Devs generally)
- Move towards microservices
- Abstract the dependencies (handles the dependencies for you)

## How does it work?

For hello-world:
 1. The Docker client contacts the Docker daemon.
 2. The Docker daemon pulls the "hello-world" image from the Docker Hub.
 3. The Docker daemon creates a new container from that image which runs the executable that produces the output you are currently reading.
 4. The Docker daemon streams that output to the Docker client, which sends it to your terminal.



## History
Founded 2008
Open source in 2013
Goes public March 2013
Security improvements 2016


### Commands
`docker run hello-world` runs a test container
`docker ps` lists active containers
`docker ps -a` lists all containers
`docker run ubuntu` runs an ubuntu container (will exit out after done)
`run -it ubuntu bash` runs an ubuntu container, -it means interactive, we can log in to it, run bash software.
`docker run -d ubuntu sleep 15` runs ubuntu container, -d means detached, so it won't affect your terminal, then runs the sleep command for 15 seconds. 
`docker exec <container-reference> whoami` sends a command to a specified container, you can use the container ID or the container name, recommend using the container ID though as it can be easier to refer to, you just need to use enough of the string to be unique. 
	**NB:** If the container ID was 3800130f3b4c2b6d173631bd8451faf9bdb8a9f2769d32432069cccedeff875a and you had another container that started with 38, you can still refer to this container as 380 and it would know which container to us.




#Docker