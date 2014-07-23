# docker-bigbluebutton

Unofficial BigBlueButton 0.81 docker image. This repository contains the Dockerfile and all other files needed to build the docker image. 

More info about BigBlueButton at: http://bigbluebutton.org/


### About this image and the Dockerfile:

This image is based on Ubuntu 10.04 x86_64, which is the [officially supported O.S](https://code.google.com/p/bigbluebutton/wiki/InstallationUbuntu#Before_You_Install). for BigBlueButton 0.81. The Dockerfile follows the [official installation instructions](https://code.google.com/p/bigbluebutton/wiki/InstallationUbuntu#Installing_BigBlueButton_0.81) found on BigblueButton's documentation, plus some fixes needed to successfully boot the container. 

You can find a prebuilt docker image from [Docker Hub](https://registry.hub.docker.com/u/juanluisbaptiste/bigbluebutton/). To be able to use it, first it has to be pulled off from the Hub:

    sudo docker pull juanluisbaptiste/bigbluebutton:latest
  
And then you can run a container from it, see instructions below on how to do it.

This is still an **alpha version** use it at your own risk. There is still some stuff about how to handle the different services that conform the BigBlueButton app inside the docker container that I need to improve.

### Build Instructions
After you clone this repository you need to build the image with the `docker` command like this:

    cd docker-bigbluebutton
    sudo docker build -t bbb_0.81 .

### How to launch the container
This `docker` command will launch a new BigBlueButton container:

    sudo docker run -d --name bbb bbb_0.81

You can attach to the container while it starts and wait for it to finish, then take the IP address from the end of the output. To attach to the container run the following `docker` command:

    sudo docker attach --sig-proxy=false bbb
    
### How to access the container
For now it's only possible to access the BigBlueButton container using the private IP address docker has assigned to it. after you attach to the container you will see an output like the following one telling you the IP address:

    *******************************************
    Use this IP address to locally access your 
    BigBlueButton container: 
    
    172.17.0.2
    
    *******************************************

Access that address from your browser and you will get to the demo page. NOTE: If you try to use the exposed ports, the bundled nginx server will show the default page instead of BigBlueButton's demo page. I'm working on this.

### TODO
* Improve configuration so BigBlueButton can be accesed from the exposed ports.
* Improve the way BigBlueButton services start using supervisord/systemd instead of using a custom script.
