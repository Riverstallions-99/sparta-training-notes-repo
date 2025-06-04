## What is Docker?

A software that allows us to create, monitor and manage containers. 
#TODO : Continue notes
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

#TODO : Diagram

The hello-world image is a test container, we'll use it to learn about how Docker works

For hello-world:
 1. The Docker client contacts the Docker daemon.
 2. The Docker daemon pulls the "hello-world" image from the Docker Hub.
 3. The Docker daemon creates a new container from that image which runs the executable that produces the output you are currently reading.
 4. The Docker daemon streams that output to the Docker client, which sends it to your terminal.

## History of Docker
Founded 2008
Open source in 2013
Goes public March 2013
Security improvements 2016

## Docker CLI
### Commands
- `docker run hello-world` runs a test container
- `docker pull <image>` pulls images from the registry (DockerHub)
- `docker build` builds using image
- `docker ps` lists active containers
- `docker ps -a` lists all containers
- `docker run ubuntu` runs an ubuntu container (will exit out after done)
- `run -it ubuntu bash` runs an ubuntu container, -it means interactive, we can log in to it, run bash software.
- `docker run -d ubuntu sleep 15` runs ubuntu container, -d means detached, so it won't affect your terminal, then runs the sleep command for 15 seconds. 
- `docker exec <container-ref> whoami` sends a command to a specified container, you can use the container ID or the container name, recommend using the container ID though as it can be easier to refer to, you just need to use enough of the string to be unique. 
	- **NB:** If the container ID was 3800130f3b4c2b6d173631bd8451faf9bdb8a9f2769d32432069cccedeff875a and you had another container that started with 38, you can still refer to this container as 380 and it would know which container to us.
- `docker attach <container-ref>` reattach into a running container (can't Ctrl+C to get out of this so run in a new terminal window)
- `docker stop <container-ref>` stop a docker container
- `docker rm <container-ref>` remove a non running container (can list additional containers to remove more than one at once)
- `docker images` list images installed locally
- `docker rmi <image-ref>` remove image/s, can only remove images when container is removed, not just stopped (image ref can be the Image ID or the Image name)
- `docker run -d -p 80:5000` runs on detached container, maps ports specified (container:5000 maps to localhost:80 which is where nginx runs automatically)
- `docker run --name my_container -d` runs container with a name you specify, rather than randomly generating one
- `docker cp index.html my_website:/usr/share/nginx/html/` copy file into container, if no new name specified, file name will stay the same
- `docker commit <container-ref> <image-name>` creates a local image based off of the container and names it whatever you put for image-name
- `docker commit <container-ref> <user>/<image-name>:latest` creates an image and saves to your user's repo, uses latest as default but good to be specific
- `docker push <user>/<image-name>:latest` pushes your local repo image to your cloud repo, uses latest as default but good to be specific
- `docker run -it --name <container-name> -d -p 80:80 <image-ref>`
- `docker build . -t riverstallions/<image-name>`
- 

outside:inside 
so 80:3000 allows you to go to localhost:80 (or just localhost as :80 is the default) and it will map to the app port 3000 inside the container

`docker run --name my-app-container -d -p 80:3000 docker-app-image:latest bash -c "cd /root/app && pm2 start app.js && tail -f /dev/null"` to deploy my app image to the container, and run the app and keep the container running


Flags:
```docker
-d
-p
--name
-it 
```


## Docker Compose
### Why use Docker Compose?
- For multi-container Docker applications
- YAML to define what you need
- use Docker Compose to easily start/stop/manage services defined in the YAML file.
- 

docker-compose.yaml/yml

#Docker [[BeckyWhiteObsidian/Job & Career/Tech Stack Index/Docker|Docker]]