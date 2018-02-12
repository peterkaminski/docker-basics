# docker-basics
A simple Docker primer

### Docker Basics

* There are "images" and "containers."  Images are analogous to AMIs, and containers are analogous to EC2 instances.
* Containers can be either running or stopped.
* Images and containers have a unique hexadecimal ID.
* Images and containers can have friendly names.  For images, they are called "tags" (because an image can have multiple tags).  Containers which aren't explicitly given a name have a name automatically assigned; it is two random words connected by an underscore.

### Inventory

* To list your images, use `docker images`
* To see your running containers, use `docker ps`
* To see all your containers, use `docker ps -a`

### Container Lifecycle

* To start a new container, use `docker run -it --name my-container --rm ubuntu:latest bash`

  * `-it` means "interactive" and "allocate a pseudo-TTY"
  * `-name` means give my container a name
  * `--rm` means remove the container as soon as it stops (otherwise it stops but doesn't go away)
  * `ubuntu:latest` means use the "ubuntu" image that was version-tagged as "latest"
  * `bash` is the startup command you want it to run

Try the run command now.  If you don't already have the ubuntu image locally, the image should be pulled automatically from Docker Hub.

You should be dumped into a root shell.  Try some Unix commands.

Type `exit` or `^D` to exit the root shell.  The container will stop, and then be deleted because of the `--rm` flag.

The core command is `docker run image_name`.  The other flags, and even the command, are sometimes used or sometimes left out, depending on what you want your container to do.

Other useful flags:

* `-v` to mount a volume.  A folder on your host machine is mounted inside your container.
* `-p` to forward a port on your host to a port inside your container.

Other commands:

* To delete a container, use `docker rm my-container`
* To start a stopped container, use `docker start my-container`
* To stop a running container, use `docker stop my-container`
* To attach to a ptty inside a running container, use `docker attach my-container`
* To run a command inside a container, use `docker exec my-container command`.  To shell into an running container, you can use `docker exec -it my-container bash`
* To persist changes made to container, create a new image with `docker commit my-container my-image:my-version-tag`

**Important:** the container commands used here are shorthand for `docker container [command]`.  Use `docker container --help` to see all the commands.

### Image Lifecycle

* To create an image from a Dockerfile in the current directory, use `docker build -t my-image .`
* To delete an image, use `docker image rm my-image`

**Important:** the image commands used here are shorthand for `docker image [command]`.  Use `docker image --help` to see all the commands.
