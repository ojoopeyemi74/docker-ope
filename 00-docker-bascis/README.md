# to check the process of a running container
$ docker top <container-id or container name>

# to check a container logs 

$ docker log <containername or id>

# to force remove a running container
docker rm -f <container name or id>

# to see the performance( live update) 
docker container stats   or docker stats

# to see the details of the container
docker inspect <container name or id>

# to run a container and rm while working on it we use --rm
docker run --rm -it centos:07 bash

# we use the docker inspect to see the on the image to see the metadata of the image
docker inspect <image-name>

# we could also check how the image was build using 
docker history <image-name>

# you can check your docker login details using
cat .docker/config.json