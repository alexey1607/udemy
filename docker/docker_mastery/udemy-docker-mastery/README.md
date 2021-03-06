# Udemy Course Docker Mastery: with Kubernetes+Swarm from a Docker Captain

> Build, test, deploy containers with the best mega-course on Docker, Kubernetes, Compose, Swarm and Registry using DevOps

This repo is for use in my Udemy Courses "Docker Mastery" and "Swarm Mastery"

Get these courses for with my "cheapest on the Internet" coupon links:

https://www.bretfisher.com/courses

My other DevOps and Docker resources are at https://www.bretfisher.com/docker

Feel free to create issues or PRs if you find a problem with examples in this repo!


# Creating and Using Containers Like a Boss

## Check Our Docker Install and Config

docker version

docker info

docker

docker container run

docker run

## Starting a Nginx Web Server

docker container run --publish 80:80 nginx

docker container run --publish 80:80 --detach nginx

docker container ls

docker container stop 690

docker container ls

docker container ls -a

docker container run --publish 80:80 --detach --name webhost nginx

docker container ls -a

docker container logs webhost

docker container top

docker container top webhost

docker container --help

docker container ls -a

docker container rm 63f 690 ode

docker container ls

docker container rm -f 63f

docker container ls -a

## Container VS. VM: It's Just a Process

docker run --name mongo -d mongo

docker ps

docker top mongo

docker stop mongo

docker ps

docker top mongo

docker start mongo

docker ps

docker top mongo

## Assignment Answers: Manage Multiple Containers

docker container run -d -p 3306:3306 --name db -e MYSQL_RANDOM_ROOT_PASSWORD=yes MYSQL_RANDOM_ROOT_PASSWORD

docker container logs db

docker container run -d --name webserver -p 8080:80 httpd

docker ps

docker container run -d --name proxy -p 80:80 nginx

docker ps

docker container ls

docker container stop TAB COMPLETION

docker ps -a

docker container ls -a

docker container rm

docker ps -a

docker image ls

## What's Going On In Containers: CLI Process Monitoring

docker container run -d --name nginx nginx

docker container run -d --name mysql -e MYSQL_RANDOM_ROOT_PASSWORD=true mysql

docker container ls

docker container top mysql

docker container top nginx

docker container inspect mysql

docker container stats --help

docker container stats

docker container ls

## Getting a Shell Inside Containers: No Need for SSH

docker container run -help

docker container run -it --name proxy nginx bash

docker container ls

docker container ls -a

docker container run -it --name ubuntu ubuntu

docker container ls

docker container ls -a

docker container start --help

docker container start -ai ubuntu

docker container exec --help

docker container exec -it mysql bash

docker container ls

docker pull alpine

docker image ls

docker container run -it alpine bash

docker container run -it alpine sh

## Docker Networks: Concepts for Private and Public Comms in Containers

docker container run -p 80:80 --name webhost -d nginx

docker container port webhost

docker container inspect --format '{{ .NetworkSettings.IPAddress }}' webhost

## Docker Networks: CLI Management of Virtual Networks

docker network ls

docker network inspect bridge

docker network ls

docker network create my_app_net

docker network ls

docker network create --help

docker container run -d --name new_nginx --network my_app_net nginx

docker network inspect my_app_net

docker network --help

docker network connect

docker container inspect TAB COMPLETION

docker container disconnect TAB COMPLETION

docker container inspect

## Docker Networks: DNS and How Containers Find Each Other

docker container ls

docker network inspect TAB COMPLETION

docker container run -d --name my_nginx --network my_app_net nginx

docker container inspect TAB COMPLETION

docker container exec -it my_nginx ping new_nginx

docker container exec -it new_nginx ping my_nginx

docker network ls

docker container create --help

## Assignment Answers: Using Containers for CLI Testing

docker container run --rm -it centos:7 bash

docker ps -a

docker container run --rm -it ubuntu:14.04 bash

docker ps -a

## Assignment Answers: DNS Round Robin Testing

docker network create dude

docker container run -d --net dude --net-alias search elasticsearch:2

docker container ls

docker container run --rm -- net dude alpine nslookup search

docker container run --rm --net dude centos curl -s search:9200

docker container ls

docker container rm -f TAB COMPLETION


# Docker uses Go templates which you can use to manipulate the output format of certain commands and log drivers.

Docker provides a set of basic functions to manipulate template elements. All of these examples use the docker inspect command, but many other CLI commands have a --format flag, and many of the CLI command references include examples of customizing the output format.

## join

join concatenates a list of strings to create a single string. It puts a separator between each element in the list.
```
docker inspect --format '{{join .Args " , "}}' container
```

## json

json encodes an element as a json string.
```
docker inspect --format '{{json .Mounts}}' container
```

## lower

lower transforms a string into its lowercase representation.
```
docker inspect --format "{{lower .Name}}" container
```

## split

split slices a string into a list of strings separated by a separator.
```
docker inspect --format '{{split .Image ":"}}'
```

## title

title capitalizes the first character of a string.
```
docker inspect --format "{{title .Name}}" container
```

## upper

upper transforms a string into its uppercase representation.
```
docker inspect --format "{{upper .Name}}" container
```

## println

println prints each value on a new line.
```
docker inspect --format='{{range .NetworkSettings.Networks}}{{println .IPAddress}}{{end}}' container
```
## Hint

To find out what data can be printed, show all content as json:
```
docker container ls --format='{{json .}}'
```


# Docker-compose
# Making It Easier with Docker Compose: The Multi-Container Tool

## Docker Compose and The Docker-compose.yml File

docker-compose.yml

https://docs.docker.com

## Trying Out Basic Compose Commands

pcat docker-compose.yml

docker-compose up

docker-compose up -d

docker-compose logs

docker-compose --help

docker-compose ps

docker-compose top

docker-compose down

## Assignment Answers: Build a Compose File for a Multi-Container Service

docker-compose.yml

docker pull drupal

docker image inspect drupal

docker-compose up

https://hub.docker.com

docker-compose down --help

docker-compose down -v

## Adding Image Building to Compose Files

docker-compose.yml

docker-compose up

docker-compose up --build

docker-compose down

docker image ls

docker-compose down --help

docker image rm nginx-custom

docker image ls

docker-compose up -d

docker image ls

docker-compose down --help

docker-compose down --rmi local

## Assignment Answers: Compose for Run-Time Image Building and Multi-Container Dev

docker-compose up

docker-compose down

docker-compose up


# Docker swarm

# Swarm Intro and Creating a 3-Node Swarm Cluster

## Create Your First Service and Scale it Locally

docker info

docker swarm init

docker node ls

docker node --help

docker swarm --help

docker service --help

docker service create alpine ping 8.8.8.8

docker service ls

docker service ps frosty_newton

docker container ls

docker service update TAB COMPLETION --replicas 3

docker service ls

docker service ps frosty_newton

docker update --help

docker service update --help

docker container ls

docker container rm -f frosty_newton.1.TAB COMPLETION

docker service ls

docker service ps frosty_newton

docker service rm frosty_newton

docker service ls

docker container ls

## Creating a 3-Node Swarm Cluster

http://play-with-docker.com

docker info

docker-machine

docker-machine create node1

docker-machine ssh node1

docker-machine env node1

docker info

http://get.docker.com

docker swarm init

docker swarm init --advertise-addr TAB COMPLETION

docker node ls

docker node update --role manager node2

docker node ls

docker swarm join-token manager

docker node ls

docker service create --replicas 3 alpine ping 8.8.8.8

docker service ls

docker node ps

docker node ps node2

docker service ps sleepy_brown

## Scaling Out with Overlay Networking

docker network create --driver overlay mydrupal

docker network ls

docker service create --name psql --netowrk mydrupal -e POSTGRES_PASSWORD=mypass postgres

docker service ls

docker service ps psql

docker container logs psql TAB COMPLETION

docker service create --name drupal --network mydrupal -p 80:80 drupal

docker service ls

watch docker service ls

docker service ps drupal

docker service inspect drupal

# Swarm App Lifecycle

## Using Secrets With Local Docker Compose

docker node ls

docker-compose up -d

docker-compose exec psql cat /run/secrets/psql_user

docker-compose 11

pcat docker-compose.yml

## Full App Lifecycle: Dev, Build and Deploy With a Single Compose Design

docker-compose up -d

docker inspect TAB COMPLETION

docker-compose down

docker-compose -f docker-compose.yml -f docker-compose.test.yml up -d

docker inspect TAB COMPLETION

docker-compose -f docker-compose.yml -f docker-compose.prod.yml config --help

docker-compose -f docker-compose.yml -f docker-compose.prod.yml config

docker-compose -f docker-compose.yml -f docker-compose.prod.yml config > output.yml

## Service Updates: Changing Things In Flight

docker service create -p 8088:80 --name web nginx:1.13.7

docker service ls

docker service scale web=5

docker service update --image nginx:1.13.6 web

docker service update --publish-rm 8088 --publish-add 9090:80

docker service update --force web

## Healthchecks in Dockerfiles

docker container run --name p1 -d postgres

docker container ls

docker container run --name p2 -d --health-cmd="pg_isready -U postgres || exit 1" postgres

docker container ls

docker container inspect p2

docker service create --name p1 postgres

docker service create --name p2 --health-cmd="pg_isready -U postgres || exit 1" postgres


# Container Registries: Image Storage and Distribution

## Docker Hub: Digging Deeper

https://hub.docker.com

## Docker Store: What Is It For?

https://store.docker.com

## Docker Cloud: CI/CD and Server Ops

https://cloud.docker.com

https://hub.docker.com

## Understanding Docker Registry

https://github.com/docker/distribution

https://hub.docker.com/registry

## Run a Private Docker Registry

docker container run -d -p 5000:5000 --name registry registry

docker container ls

docker image ls

docker pull hello-world

docker run hello-world

docker tag hello-world 127.0.0.1:5000/hello-world

docker image ls

docker push 127.0.0.1:5000/hello-world

docker image remove hello-world

docker image remove 127.0.0.1:5000/hello-world

docker container rm admiring_stallman

docker image remove 127.0.0.1:5000/hello-world

docker image ls

docker pull 127.0.0.1:5000/hello-world:latest

docker container kill registry

docker container rm registry

docker container run -d -p 5000:5000 --name registry -v $(pwd)/registry-data:/var/lib/registry registry TAB COMPLETION

docker image ls

docker push 127.0.0.1:5000/hello-world

## Using Docker Registry With Swarm

http://play-with-docker.com

docker node ls

docker service create --name registry --publish 5000:5000 registry

docker service ps registry

docker pull hello-world

docker tag hello-world 127.0.0.1:5000/hello-world

docker push 127.0.0.1:5000/hello-world

docker pull nginx

docker tag nginx 127.0.0.1:5000/nginx

docker push 127.0.0.1:5000/nginx

docker service create --name nginx -p 80:80 --replicas 5 --detach=false 127.0.0.1:5000/nginx

docker service ps nginx
