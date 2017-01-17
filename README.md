# Docker Image Definitions

This repository holds all of the docker image definitions used in Elemental Concept.
Top level folders match names of docker images.

## Installing Docker Locally

You can install Docker by following the guide on [the official web-site](https://www.docker.com/products/overview).
Please note, that Docker is a Linux-only application and it runs in a virtual machine on other OSes.
Installing it on MacOS or Windows can be quite problematic, so the easiest way to use Docker
is to install it manually inside your favourite Linux distro running inside VirtualBox.

Make sure you login into your Docker Hub account after successful installation. To do that, run `$ docker login` and
follow on-screen instructions.

## Development Hints

Start development by creating a new image folder and putting empty *Dockerfile* inside. Write required instructions
inside the *Dockerfile*. If you need to transfer any configuration files or scripts into your Docker image,
put them inside *assets* folder and use `ADD` command to transfer them. Take a look at *angular2-cli*
for a working example. Don't forget to `$ chmod +x SCRIPTNAME` your custom scripts after copying.

To build a Docker image, run `$ docker build -t TAG_NAME .` from inside your working folder. `TAG_NAME` can be
any name, which you will use to reference your newly built image. To see all images present in your system and their IDs,
run `$ docker images`.

To run and test your image, use `$ docker run -it TAG_NAME COMMAND` where `COMMAND` is any command available from
inside the container. For example, `$ docker run -it TAG_NAME bash` will start *bash* shell.

When you're ready to publish your image, you will need to tag it properly and then push to Docker Hub.
To tag your image, run `$ docker tag IMAGE_ID elementalconcept/IMAGE_NAME:latest`. `IMAGE_ID` can be obtained from
`$ docker images` output. `IMAGE_NAME` is the name you want to present your image with to the world.
When the image is properly tagged, it's time to push it - `$ docker push elementalconcept/IMAGE_NAME`.
