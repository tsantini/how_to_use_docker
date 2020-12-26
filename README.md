## Installing docker

If using ubuntu and apt-get:

`sudo apt update`

`sudo apt install docker`

For Fedora or CentOS, change `apt` to `yum` or `dnf`, depending on which one you use.

## Post-installation setup
https://docs.docker.com/engine/install/linux-postinstall/

## Test in a clean version of ubuntu in the interactive mode
`docker run -it ubuntu:latest`

## Mount a local folder inside the docker with writing access
`docker run -v /home/tsantini/my_folder:/mnt/myfolder -it ubuntu:latest`

## Build a new conteiner
`docker build -t name_of_the_conteiner folder_with_Docker_file`

## Example of Docker file

### It has to be saved with the name `Dockerfile` inside the folder_with_Docker_file

```
FROM ubuntu:latest
RUN apt update && \
    DEBIAN_FRONTEND=noninteractive \
    apt install -y --no-install-recommends \
    vim \
    git \
    g++ \
    gcc \
    tmux \
    ca-certificates \
    make \
    cmake-curses-gui \
    file \
    dc \
    libpthread-stubs0-dev \
    parallel
```
## Running the image_processing container (available at dockerhub)

This container has several MRI image processing packages.

`docker run -v local_folder:mounting_folder --rm -it tsantini/image_processing`

To test, you can run:

`mrconvert --help`

More information about this conteiner at https://hub.docker.com/r/tsantini/image_processing

You can request access to the Dockerfile for this conteiner.

## Useful flags
`-it` interactive mode: open the container as a terminal

`-v host_location:docker_mount_location` mount a local folder into the docker, for example: `-v /home/tsantini/my_folder:/mnt/myfolder`

`--rm` remove the content of the conteiner after exiting. It's usually the default.

## Pushing container to Docker Hub

1) Login to docker hub

`docker login --username=your_user_name`

2) check the image you want to push

`docker images`

3) tag this image

`docker tag image_ID your_user_name/image_name:new_tag`

4) push the container

`docker push your_user_name/image_name`

## Reflaging a container

1) check the images

`docker images`

2) retag

`docker tag images_ID your_user_name/image_name:new_tag`

## removing flag

`docker rmi image_name:flag`
