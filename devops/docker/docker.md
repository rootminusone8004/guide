# Docker

## Introduction
Docker is a platform for developers and sysadmins used to develop, deploy and run containerized applications.

**A container is a running process** that encapsulates everything an application needs to run (an only those things).

Docker makes it really easy to install and run software without worrying about setup or dependencies.

An **image** is a standalone, isolated, lightweight and executable package that contains all the required components (code, runtime, system tools, libraries, settings, etc) necessary to run an application.

The container is the runtime instance of an image. From the same images, more containers can be launched.

Images for many applications can be found on https://hub.docker.com

## Online version
If you want to play with Docker without installing it in the machine, you can play with it [online](https://labs.play-with-docker.com).

## Installation

> **Notice**: The process is described for **Debian and its derivatives**.

First we need to uninstall all the old packages.
``` bash
sudo apt purge docker.io docker-compose docker-doc podman-docker containerd runc
```

For more information for uninstallation,click [here](https://docs.docker.com/engine/install/debian/#uninstall-docker-engine).

Now add the keyrings. #curl# must be installed.
``` bash
$ sudo install -m 0755 -d /etc/apt/keyrings
$ sudo curl -fsSL https://download.docker.com/linux/debian/gpg -o /etc/apt/keyrings/docker.asc
$ sudo chmod a+r /etc/apt/keyrings/docker.asc
```

Finally install docker.
``` bash
sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```
For more information about installation, click [here](https://docs.docker.com/engine/install).

Now check the status of Docker daemon.
``` bash
systemctl status Docker
```

If the service is not started, enable it.
``` bash
sudo systemctl enable --now docker
```

Add the desired user to the docker group.
``` bash
sudo useradd -aG docker $(whoami)
```

Check if Docker is installed properly.
``` bash
docker --version
```

## docker client

To see more information, run the following command:
``` bash
docker version
```

To see system wide information including the number of containers and images, run the following command:
``` bash
docker info
```

To seek help, run this
``` bash
docker help
```

To get the help of any management command, write:
``` bash
docker <management command> help
```

For example:
``` bash
docker container help
```

### important commands

List all the available containers
``` bash
docker container ls
```

List all the available images
``` bash
docker image ls
```

To test everything is fine, run this command
``` bash
docker container run hello-world
```

We can also run this instead (#not recommended#):
``` bash
docker run hello-world
```

To see the status of docker process, run the command:
``` bash
docker ps
```

## pull images and run containers

### pull images

To search images, run this command
``` bash
docker search <image-name>
```

Check the number of stars, official tag and other necessary information associated with it.

To get image names online, visit [hub.docker.com](https://hub.docker.com)

You can pull images with associated tags. These tags can be found in the page mentioned above. Tags basically refers to the version number. This is helpful for compatibility.  
The following command is an example:
``` bash
docker image pull gitea/gitea:1.22-nightly
```
> **Notice**: If you don't mention the tag, docker will download the latest image.

### run containers

Run the container by this command:
``` bash
docker container run redis
```

The container can be stopped by `CTRL+C`

> **Note**: `run` command is the combination of `create` and `start` commands.
``` bash
$ docker container create redis
$ docker container ls -a  # see all available containers
$ docker container start 1e44df432a65  # relevant container id
```

We can also run a container and get associated shell
``` bash
docker container run -it centos
```

## More examples breakdown

### Example 1:
``` bash
docker container run -d -p 8080:80 --name mysite nginx
```
**Explanation**:
| Flag | Description |
|--|--|
| -d | The container will run in background as a daemon |
| -p | Outside port `8080` has been mapped with docker's inner assigned port `80` |
| --name | The container will be named as `mysite` |

### Example 2:
``` bash
docker container ls -a -f status=exited
```

This command will list the containers **that have exited**.

> **Note**: If you are interested only in the IDs, simply add `-q`
``` bash
docker container ls -a -f status=exited -q
```

This command will grant access to shell of an existing container:
``` bash
docker container exec -it fox2 bash # fox2 is the name of container
```

## removing images and containers

### remove containers

In order to remove a container, first we need to stop it, then remove it.
``` bash
$ docker container stop 326a # first portion of unique ID is enough
$ docker container rm 326a 
```

You can also remove it forcefully without stopping it.
``` bash
docker container rm -f 326a
```

You can also remove all the exited containers with the following command
``` bash
docker container rm $(docker container ls -a -f status=exited -q)
```

### remove images

In order to remove a image, run this command.
``` bash
docker image rm <name> # e.g: docker image rm centos
```

> **note**: if an image is used by a running container then it cannot be removed. Also in order to remove an image, all the containers of it must be removed first.

But you can always forcefully remove an image as well.
``` bash
docker image rm -f <name> 
```

### dangling images

Docker images consist of multiple layers. Dangling images are layers that have no relationship to any tagged image.  
Delete them by this command:
``` bash
docker system prune
```

If you want to delete unused images as well, use this:
``` bash
docker system prune -a
```
