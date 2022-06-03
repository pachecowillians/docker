# Docker

Run Docker commands in linux without sudo

```bash
sudo chmod 666 /var/run/docker.sock
```

Create a new container

```
docker container create --name <containerName> -it <imageName> sh
```

List running containers

```
docker container ls
```

List stopped/running containers

```
docker container ls -a
```

Start a container

```
docker container start <containerName>
```

Stop a container

```
docker container stop <containerName>
```

Run command line of an interactive container

```
docker container attach <containerName>
```

Remove a container

```
docker container rm <containerName>
```

Start and attach a container

```
docker container start -ia <containerName>
```

Create, run and attach a container

```
docker container run -it --name <containerName> <imageName> sh
```

Rename a container

```
docker container rename <currentName> <newName>
```

Run a command without enter in container

```
docker container exec <containerName> <command>
```

Copy a file from a local directory to a docker container directory

```
docker container cp <localDirectory> <containerName>:<containerDirectory>
```

Copy a file from a docker container directory to a local directory

```
docker container cp <containerName>:<containerDirectory> <localDirectory> 
```

Exit from an attached container without stop it

```
Ctrl + P + Q
```

Show the last commands executed in the container terminal

```sh
docker container logs <containerName>
```

Get information about the container

```console
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