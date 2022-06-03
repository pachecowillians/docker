# Docker

Run Docker commands in linux without sudo

```zsh
sudo chmod 666 /var/run/docker.sock
```

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

Exit from an attached container without stop it

```zsh
Ctrl + P + Q
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