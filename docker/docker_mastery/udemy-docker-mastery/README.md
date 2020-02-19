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
