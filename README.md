# Docker

Run Docker commands in linux without sudo

```zsh
sudo chmod 666 /var/run/docker.sock
```

## Docker container

Create a new container

```zsh
docker container create --name <containerName> -it <imageName> sh
```

List running containers

```zsh
docker container ls
```

List stopped/running containers

```zsh

docker container ls -a
```

Start a container

```zsh
docker container start <containerName>
```

Stop a container

```zsh
docker container stop <containerName>
```

Run command line of an interactive container

```zsh
docker container attach <containerName>
```

Remove a container

```zsh
docker container rm <containerName>
```

Start and attach a container

```zsh
docker container start -ia <containerName>
```

Create, run and attach a container

```zsh
docker container run -it --name <containerName> <imageName> sh
```

Rename a container

```zsh
docker container rename <currentName> <newName>
```

Run a command without enter in container

```zsh
docker container exec <containerName> <command>
```

Copy a file from a local directory to a docker container directory

```zsh
docker container cp <localDirectory> <containerName>:<containerDirectory>
```

Copy a file from a docker container directory to a local directory

```zsh
docker container cp <containerName>:<containerDirectory> <localDirectory> 
```

Show the last commands executed in the container terminal

```zsh
docker container logs <containerName>
```

Get information about the container

```zsh
docker container inspect <containerName>
```

Create a container with a mapped directory
```zsh
docker container run -it -v <hostAbsolutePath>:<dockerPath> --name <containerName> <imageName> sh
```
- To add read only permission, add :ro after \<dockerPath>

Export a port from Docker container
```zsh
docker container run -d -p 80:80 --name <containerName> <imageName>
```

Run commands in non-interactive containers
```zsh
docker container exec -it <containerName> sh
```

Create an docker image from a container
```zsh
docker container commit <containerName> <imageName>
```

Run container and remove it when exit
```zsh
docker container run -it --rm --name <containerName> <imageName> sh
```

Force to remove a container
```zsh
docker container rm -f <containerName>
```

Run a container with a volume created
```zsh
docker container run -it --name <containerName> -v <volumeName>:<containerPath> <imageName> sh
```

Exit from an attached container without stop it

```zsh
Ctrl + P + Q
```

## Docker image

List all images
```zsh
docker image ls
```

Generate a `.tar` file from a docker image
```zsh
docker image save -o <fileName>.tar <imageName>
```

Remove image
```zsh
docker image rm <imageName>
```

Load an image from `.tar` file
```zsh
docker image load -i <fileName>.tar
```

Show the history of an image
```zsh
docker image history <imageName>
```

Create an image from a Dockerfile
```zsh
docker image build -t <imageName> <dockerfilePath>
```

List volumes
```zsh
docker volume ls
```

Show information about the volume
```zsh
docker volume inspect <volumeName>
```

Create a new volume
```zsh
docker volume create <volumeName>
```

Remove a volume
```zsh
docker volume rm <volumeName>
```