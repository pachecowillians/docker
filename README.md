# Summary

- [Docker on linux](#docker-on-linux)
- [Docker container](#docker-container)
    - [Docker container create](#docker-container-create)
    - [Docker container ls](#docker-container-ls)
    - [Docker container start](#docker-container-start)
    - [Docker container stop](#docker-container-stop)
    - [Docker container attach](#docker-container-attach)
    - [Docker container rm](#docker-container-rm)
    - [Docker container run](#docker-container-run)
    - [Docker container rename](#docker-container-rename)
    - [Docker container exec](#docker-container-exec)
    - [Docker container cp](#docker-container-cp)
    - [Docker container logs](#docker-container-logs)
    - [Docker container inspect](#docker-container-inspect)
    - [Docker container commit](#docker-container-commit)
- [Docker image](#docker-image)
- [Docker volume](#docker-volume)


## Docker on linux

Run Docker commands in linux without sudo

```zsh
sudo chmod 666 /var/run/docker.sock
```

Exit from an attached container without stop it

```zsh
Ctrl + P + Q
```

## Docker container

List of commands to manipulate containers on docker

### Docker container create

Create a new container

```zsh
docker container create --name <containerName> -it <imageName> sh
```

### Docker container ls

List running containers

```zsh
docker container ls
```

List stopped/running containers

```zsh

docker container ls -a
```

### Docker container start

Start a container

```zsh
docker container start <containerName>
```

Start and attach a container

```zsh
docker container start -ia <containerName>
```

### Docker container stop

Stop a container

```zsh
docker container stop <containerName>
```

### Docker container attach

Run command line of an interactive container

```zsh
docker container attach <containerName>
```

### Docker container rm

Remove a container

```zsh
docker container rm <containerName>
```

Force to remove a container
```zsh
docker container rm -f <containerName>
```

### Docker container run

Create, run and attach a container

```zsh
docker container run -it --name <containerName> <imageName> sh
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

Run container and remove it when exit
```zsh
docker container run -it --rm --name <containerName> <imageName> sh
```

Run a container with a volume created
```zsh
docker container run -it --name <containerName> -v <volumeName>:<containerPath> <imageName> sh
```

### Docker container rename

Rename a container

```zsh
docker container rename <currentName> <newName>
```

### Docker container exec

Run a command without enter in container

```zsh
docker container exec <containerName> <command>
```

Run commands in non-interactive containers
```zsh
docker container exec -it <containerName> sh
```

### Docker container cp

Copy a file from a local directory to a docker container directory

```zsh
docker container cp <localDirectory> <containerName>:<containerDirectory>
```

Copy a file from a docker container directory to a local directory

```zsh
docker container cp <containerName>:<containerDirectory> <localDirectory> 
```

### Docker container logs

Show the last commands executed in the container terminal

```zsh
docker container logs <containerName>
```

### Docker container inspect

Get information about the container

```zsh
docker container inspect <containerName>
```

### Docker container commit

Create an docker image from a container
```zsh
docker container commit <containerName> <imageName>
```

## Docker image

### Docker image ls

List all images
```zsh
docker image ls
```

### Docker image save

Generate a `.tar` file from a docker image
```zsh
docker image save -o <fileName>.tar <imageName>
```


### Docker image rm

Remove image
```zsh
docker image rm <imageName>
```

### Docker image load

Load an image from `.tar` file
```zsh
docker image load -i <fileName>.tar
```

### Docker image history

Show the history of an image
```zsh
docker image history <imageName>
```

### Docker image build

Create an image from a Dockerfile
```zsh
docker image build -t <imageName> <dockerfilePath>
```

## Docker volume

### Docker volume ls

List volumes
```zsh
docker volume ls
```

### Docker volume inspect

Show information about the volume
```zsh
docker volume inspect <volumeName>
```

### Docker volume create

Create a new volume
```zsh
docker volume create <volumeName>
```

### Docker volume rm

Remove a volume
```zsh
docker volume rm <volumeName>
```