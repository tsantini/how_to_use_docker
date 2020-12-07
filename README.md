## Installing docker

If using ubuntu and apt-get:

`sudo apt update`

`sudo apt install docker`

For fedora or centos, change to yum or dnf, depending on which one you use.

## Post-installation setup
https://docs.docker.com/engine/install/linux-postinstall/

## Test in a clean version of ubuntu in the interactive mode
`docker run -it ubuntu:latest`

## Mount a local folder inside the docker with writing access
`docker run -v /home/tsantini/my_folder:/mnt/myfolder -it ubuntu:latest`

## Build a conteiner
`build -t name_of_the_conteiner folder_with_Docker_file`

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

`docker run -v local_folder:mounting_folder -rm -it tsantini/image_processing`

more information about this conteiner at https://hub.docker.com/r/tsantini/image_processing

You can request access to the Dockerfile for this conteiner.

## Useful flags
`-it` interactive mode: open the container as a terminal
`-v host_location:docker_mount_location` mount a local folder into the docker, for example: `-v /home/tsantini/my_folder:/mnt/myfolder`
`--rm` remove the content of the conteiner after exiting. It's usually the default.
