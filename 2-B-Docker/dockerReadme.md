# Docker Notes

Frequently used Docker commands with descriptions of what each does. 

## Docker container commands

#List all active containers
docker ps           

#Lists containers (active or not)
docker ps -a        

#Removes a container
docker rm [container ID or shortname]          

#Removes a running container
docker rm --force [container ID or shortname]           

#Stops a running container
docker stop  [container ID or shortname]

#Starts a container
docker start   [container ID or shortname]    


## Docker image commands

#List all images
docker image

#To build an image and check containers run
docker build --tag [shortname] . 


## Run a Docker container

Use to start a container based on an image

Docker run --publish 8000:8080 --detach --name [shortname] [appname]     

### Flags: 
`--publish 8000:8080`   asks Docker to forward traffic incoming on the host’s port 8000 to the container’s port 8080.  

`--detach` Docker runs container in the background

`-t, --tty `       For apps that aren't running a background process, this flag allocates a pseudo-TTY





## Example Node Docker image file

A Docker image file gives Docker a list of commands to execute. Below is an example Docker file for a Node.js application.

```dockerfile
#Tells Docker to use this Node version
FROM node:12.16.3

#Tells Docker to create folder called code inside Docker image
WORKDIR /code

#Environemnt variables can be accessed inside image
ENV  PORT 80

#Copies the package.json file into code folder
COPY package.json /code/package.json


#Runs node package manager and install dependencies
RUN npm install

#Copies all code from current working directory into code directory in image
COPY . /code

````

## Resources

Getting started - Docker Docs
https://docs.docker.com/get-started/

Dockerizing a Node.js web app - Node.js Documentation
https://nodejs.org/en/docs/guides/nodejs-docker-webapp/

Docker 101: Fundamentals and Practice - FreeCodeCamp
https://www.freecodecamp.org/news/docker-101-fundamentals-and-practice-edb047b71a51/