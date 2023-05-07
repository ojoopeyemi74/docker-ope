# the default Dockerfile 
the efuat Docker file name start as Dockerfile with D as uppercase but if you need to specify another name then you will use -f some-dockerfile

example:   docker build -f some-dockerfile

# Dockerfile stanza

- first : Every Dockerfile starts with FROM, it usually a distribution , and we use it to save time and space, in this example we will be using Debian:jessie and we could also use Alpine
as most of the Distribution comes with steady update

FROM debian:bullseye-slim
# all images must have a FROM
# usually from a minimal Linux distribution like debian or (even better) alpine
# if you truly want to start with an empty container, use FROM scratch

- next: ENV ( which is the enviroment variable) , the EVN are the way we set key and value in a container,. as they are very important

# optional environment variable that's used in later lines and set as envvar when container is running
ENV NGINX_VERSION   1.23.0

- next: WORKDIR 
WORKDIR /usr/share/nginx/html
# change working directory to root of nginx webhost
# using WORKDIR is preferred to using 'RUN cd /some/path'

- next: COPY: we use the COPY to copy file from our local machine to our image
in this example we are copying index.html from our local machine to the image
Example 
COPY index.html index.html


- next: RUN , we could use the RUN command to execute shell commands, when you need to install software in the container , you can use the RUN command to run script in the container ,  and we use the && to chain them together to save space and time

RUN set -x \
# create nginx user/group first, to be consistent throughout docker variants
    && addgroup --system --gid 101 nginx \
    && adduser --system --disabled-login --ingroup nginx --no-create-home --home /nonexistent --gecos "nginx user" --shell /bin/false --uid 101 nginx \
    && apt-get update \


- next: EXPOSE , by default no TCP or UDP ports are opened in a container, execpt we list the ports we want here 
example : 
EXPOSE 80 443 8080
# expose these ports on the docker virtual network
# you still need to use -p or -P to open/forward these ports on host

- next: CMD
example:
CMD ["nginx", "-g", "daemon off;"]
# required: run this command when container is launched
# only one CMD allowed, so if there are multiple, last one wins

# finally ti build the image we will use 
docker build -t <container-name> . 
-t stands for tag for the container name 
and the . is use to specify that our Dockerfile is in our current directory

# best practise in building or editing a Dockerfile
- it is best to keep the things that change the list at the top of your Dockerfile while the things that change the most stay at the bottom of the Dockerfile

and the reason for that is if you edit your Dokerfile and rebuilding while the things that chnage the most are at the top , then it will rebuild from scratch, so it is best to keep the things that change least at the top of the file
