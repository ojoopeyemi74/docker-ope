# in this section we are going to talk about bond mounting and persistent data

a bond mounting is about Mapping a host file or directory from your host(local-machine ) to a container file

- next: we have our file on our local machine and we will map it instantly to the container

- next: we can't use it in Dockerfile because we need the file directly on the hard drive of the host

- next: a bind mount doesnt require a volume to work, as the host always wins

# in this example we have a folder on our local machine

folder name : mount-directory
and inside this dir we have a Dockerfile and also an index.html file

we will be mapping the index.html life to our running container using -v

```
docker run -d -p 80:80 --name bind-cont -v $(pwd):/usr/share/nginx/html nginx
```

# we use the $(pwd) to specify our current working dir to avoid typing out all the path and the /usr/share/nginx/html is from our Dockerfile 

- next: running this command , we can actually modify our file on the local host and it will be instant on the container 