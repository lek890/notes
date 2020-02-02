**Getting started with docker**

Say, you want an instance of nginx to be run on a container - what should you do?

1. You should find the image of nginx from docker hub or where ever it is.
2. do `docker run -d {IMAGE_NAME}`. This command automatically pulls and starts the docker on an ip. You can see the details
by running the command - `docker ps -a`. 
3. `docker ps` or `docker container ls` would list all the containers available.
4. If you want to specify the ports in which the container should provide the service you want, you can specify it as an 
argument like `docker run -d -p 2000:80`. Now the port 80 in the container is mapped to the port 2000 on the host machine 
and you can access it on the port `2000`
5. If you want to remove the container, use command `docker rm '{CONTAINER_ID}'`
6. To start the container, pretty straight forward - `docker start {CONTAINER_ID}`
7. To stop the container, again straight forward - `docker stop {CONTAINER_ID}`
8. To run the image in an interactive mode ( that is not in the background, which we specified using -d), use parameter `-it`.
9. To login into a container, you can use `docker exec -it {CONTAINER_ID}`

#todo
#samples

docker stop all containers

docker run -aq

docker delete all containers

docker rm $(docker ps -aq)

remove all images

docker rmi $(docker images -q)
