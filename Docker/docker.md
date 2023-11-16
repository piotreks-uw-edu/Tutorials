### install Docker on Ubuntu
sudo apt update
sudo apt install apt-transport-https ca-certificates curl software-properties-common -y
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
apt-cache policy docker-ce

### get a detailed status report about the Docker service #
sudo systemctl status docker

### lists Docker images available on the local machine
sudo docker image ls

### install an image container, ‘-it’ means to run the container in interactive mode, with a terminal attached 
### so that we’ll be able to type commands inside the container
sudo docker run -it --rm davisengeler/docker-scala

### run docker container with own name
sudo docker run -it --name your_custom_name image_name

### If you have a Docker container that exists but is not currently running
docker start training

### enter the shell of a running Docker container
sudo docker exec -it quizzical_diffie bash

### manage and view Docker images on a system, is about the stored images (the blueprints).
sudo docker image ls

### lists currently running Docker containers, is about the running instances created from those images.
sudo docker container ls

### lists currently running Docker containersn This command is an alternative to 'docker ls'
sudo docker ps

### lists all Docker containers, whether they're running or stopped
sudo docker ps --all

### alternative to 'sudo docker ps --all', lists all Docker containers, whether they're running or stopped
sudo docker container ls --all

### delete docker image
docker rmi -f image_name_or_id

### build docker image
docker build -t yourimagename:tag .

### docker login
docker login git.wat.edu.pl:5050

# build an image without explicitly creating a Dockerfile on disk
docker run -it --name temp-container git.aaaa.edu.pl:3443/debian:11 /bin/bash
