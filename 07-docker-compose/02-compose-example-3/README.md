# in this section we are using docker compose 

we have beeb able to create a dockerfile with a custom name nginx.Dockerfile, in this file we have been able to COPY the nginx.conf which is serving as a load balancer, to our project into the /etc/nginx/conf.d/default.conf

# docker compose
in our docker compose yaml file, we have been able to build a new image telling it to build the image from the custom Dockerfile - nginx.Dockerfile 

and we also have the web service, with apache and we have been able to have a bind mount of our html file which we have locally, so if we are developing we can actually change something in the html and it will reflect on the webpage

# to refrence a docker compose file that is in another file
docker compose -f mysql-docker-compose.yml up -d