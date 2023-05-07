# we can check tag help using 
docker image tag --help

# we can change our image tag using 
docker image tag <image-name:tag> <dockerhub-username/new-imagename:tag-number if you want>

example:   docker image tag httpd opeyemiojo/httpd:mytag

# you can push your image to the dockerhub 
docker push <dockerhub-username/image-name:tag number or name if you want>
docker push opeyemiojo/httpd:mytag

