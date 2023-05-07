# bascic docker network commands

show networks  - docker network ls
inspect a network   - docker network inspect
create a network  - docker network create --driver
attach a network to a container - docker network connect
Dettach a network from container  - docker network disconnect

# we can create a new network 
docker network create app-net

# we can inspect a network 
docker network inspect app-net

and with this we can see those containers which are currently connected to this network

# and we can also attach an existing container to this network 
docker network connect <app-net ID> <container-name or id>

# and we can also disconnect the container from the network 
docker network disconnect <app-net ID> <container-name or id>

# having containers using the same network gives opportunity for them to communicate
# it is best to give your containers name which will serve as the DNS name as we can't relie on containers IP as it can chanhege

docker exec -it <container1> ping <container2>

The default bridge network driver allow contaytiners to communicate with each other when running on the same docker host

