# docker-bigbluebutton

Unofficial BigBlueButton 0.81 docker image. This repository contains the Dockerfile and all other files needed to build the docker image. 

More info about BigBlueButton at: http://bigbluebutton.org/


### About this image and the Dockerfile:

This image is based on Ubuntu 10.04 x86_64, which is the [officially supported O.S](https://code.google.com/p/bigbluebutton/wiki/InstallationUbuntu#Before_You_Install). for BigBlueButton 0.81. The Dockerfile follows the [official installation instruccions](https://code.google.com/p/bigbluebutton/wiki/InstallationUbuntu#Installing_BigBlueButton_0.81) found on BigblueButton's documentation, plus some fixes needed to successfully boot the container.

You can find a prebuilt docker image from [Docker Hub](https://registry.hub.docker.com/u/juanluisbaptiste/bigbluebutton/). To be able to use it, first it has to be pulled off from the Hub:

    sudo docker pull juanluisbaptiste/bigbluebutton:1.0
  
And then you can run a container from it, see instructions below on how to do it.


### Build Instructions
After you clone this repository you need to build the image with the `docker` command like this:

    cd docker-bigbluebutton
    sudo docker build -t juanluisbaptiste/bigbluebutton:1.0 .

### How to launch the container
This `docker` command will launch a new BigBlueButton container:

    sudo docker run -d --name bbb_0.81 juanluisbaptiste/bigbluebutton:1.0

You can attach to the container while it starts and wait for it to finish, then take the IP address from the end of the output. To attach to the container run the following `docker` command:

    sudo docker attach --sig-proxy=false bbb_0.81
    
    
