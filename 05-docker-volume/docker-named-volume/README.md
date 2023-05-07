# usually when we run some docker container that needs a volume, exampls are the databases containe e.g mysql

so when we create such container like mysql it usually create a volume, and the volume is actually where the things we have are stored, usually the volumes are persistence which means the volumes out lived the containers as containers are ephemeral , even when we delete our containers the volume still remain, until we delete it 

-- we can check our volume using    docker volume ls

# and it is best to create our own named volume so we can have the specific name we want for our volume as docker usually give random long numbers for volumes by default

docker volume create <volume-name>

so we can attach our own created volume using the below example for mysql container
Example

docker run -d --name mysql-cont -e MYSQL_ROOT_PASSWORD=opeyemi -v mysql-volume:/var/lib/mysql mysql

- so we actually use the -v to specify the volume then also the : and we specify the default mysql volume path which we can find on mysql offical image on dockerhub 

- doing this it will create a volume named mysql-volume , and the beautity of this is that we can actually attach this same volume to another mysql container 
Example 
docker run -d --name mysql-cont2 -e MYSQL_ROOT_PASSWORD=opeyemi -v mysql-volume:/var/lib/mysql mysql