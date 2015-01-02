
This is a fork of https://github.com/juanluisbaptiste/docker-bigbluebutton

# Install [docker nginx reverse proxy](see the doc : https://registry.hub.docker.com/u/jwilder/nginx-proxy/)

    docker run --name nginx-proxy -d -p 80:80 -v /var/run/docker.sock:/tmp/docker.sock jwilder/nginx-proxy

# DNS

### Do not forget to update your `hosts` file if needed.
Get the container IP

    docker inspect -f "{{.NetworkSettings.IPAddress}}" nginx-proxy
    
If you are installing bbb locally, Add this in /etc/hosts

    172.17.0.xx bbb.docker # docker ip of nginx  container


# docker-bigbluebutton

Unofficial BigBlueButton 0.81 docker image. This repository contains the Dockerfile and all other files needed to build the docker image. 

More info about BigBlueButton at: http://bigbluebutton.org/


### About this image and the Dockerfile:

This image is based on Ubuntu 10.04 x86_64, which is the [officially supported O.S](https://code.google.com/p/bigbluebutton/wiki/InstallationUbuntu#Before_You_Install). for BigBlueButton 0.81. The Dockerfile follows the [official installation instructions](https://code.google.com/p/bigbluebutton/wiki/InstallationUbuntu#Installing_BigBlueButton_0.81) found on BigblueButton's documentation, plus some fixes needed to successfully boot the container. 

You can find a prebuilt docker image from [Docker Hub](https://registry.hub.docker.com/u/juanluisbaptiste/bigbluebutton/). To be able to use it, first it has to be pulled off from the Hub:

    sudo docker pull kevlys/docker-bigbluebutton:latest
  
And then you can run a container from it, see instructions below on how to do it.

This is still an **alpha version** use it at your own risk. There is still some stuff about how to handle the different services that conform the BigBlueButton app inside the docker container that I need to improve.

### How to launch the container
This `docker` command will launch a new BigBlueButton container:

    docker run -d --name bbb -e VIRTUAL_HOST=bbb.docker -e IP=bbb.docker kevlys/docker-bigbluebutton
    
You can attach to the container while it starts and wait for it to finish, then take the IP address from the end of the output. To attach to the container run the following `docker` command:

    sudo docker attach --sig-proxy=false bbb
    
### How to access the container

    http://bbb.docker

Access that address from your browser and you will get to the demo page.
