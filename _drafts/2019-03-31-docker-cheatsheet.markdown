
# Basic Information


```bash
docker --version

# get docker detailed information in your machine
docker info

# test installation with simple Docker image
docker run hello-world
```


# Images

```bash
# list the images
docker image ls
```


# Containers


```bash
# list all running containers
docker container ls

# list containers include that not running
docker container ls --all

# list all in quite mode
docker container ls -aq

```


## Proxy server

Proxy servers can block connections to your web app once it’s up and running. If you are behind a proxy server, add the following lines to your Dockerfile, using the ENV command to specify the host and port for your proxy servers:


```bash
# Set proxy server, replace host:port with values for your servers
ENV http_proxy host:port
ENV https_proxy host:port
```


service


```bash

docker swarm init
## give your app a name
docker stack deploy -c docker-compose.yml getstartedlab
## Get the service ID for the one service in our application
docker service ls

docker stack services getstartedlab


# list the tasks for the service
docker service ps getstartedlab_web

docker container ls -q
docker swarm leave --force

```
