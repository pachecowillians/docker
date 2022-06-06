# Exercise container commit, image save and image load

## Description

<br/>

1. Run in interactive mode a container using the ubuntu image. Use `apt-get` to install the NGINX and start NGINX

2. Generate an image called ubuntu-wps using the `commit` command

3. Export the image to the ubuntu-wps.tar using the command `save`

4. Remove the ubuntu-wps image

5. Import the image from ubuntu-wps.tar using the command `load`

6. Run a container from the imported image

<br/>

## Solution

<br/>

**1\. Run in interactive mode a container using the ubuntu image. Use `apt-get` to install the NGINX and start NGINX**


First, to create the container we need to run the command below:

```zsh
docker container run -it --name container-ubuntu ubuntu sh
```

Inside the container, i'll execute the following commands to install nginx:

```zsh
apt update
apt-get install nginx
```

To start nginx service, run:

```zsh
service nginx start
```

Now, if you type the command below, you can see the ip address of the server in the `IPAddress` field. This ip address can be used to verify if nginx is working in the browser.

```zsh
docker container inspect container-ubuntu
```

<br/>

**2. Generate an image called ubuntu-wps using the `commit` command**

To generate the image from container, just run the command below:

```zsh
docker container commit container-ubuntu ubuntu-wps
```

Now, you can use the command below to see that the image was created:

```zsh
docker image ls
```

<br/>

**3. Export the image to the ubuntu-wps.tar using the command `save`**

To export an image to a `.tar` file, use the following command:

```zsh
docker image save -o ubuntu-wps.tar ubuntu-wps
```

Now, you can use the command below verify if the `.tar` file was created:

```zsh
ls
```

<br/>

**4. Remove the ubuntu-wps image**

To remove the image, run the command below:

```zsh
docker image rm ubuntu-wps
```

To stop and remove the container created previously, run the commands below:
```zsh
docker container stop container-ubuntu
docker container rm container-ubuntu
```

To verify if the image and the container was deleted, use the following commands

```zsh
docker image ls
docker container ls -a
```

<br/>

**5. Import the image from ubuntu-wps.tar using the command `load`**

To import the image from the `.tar` file, use the command below:

```zsh
docker image load -i ubuntu-wps.tar
```

To verify if the image was loaded correctly, use the following command

```zsh
docker image ls
```

<br/>

**6. Run a container from the imported image**

To run the container, exporting the port 80 from the image `ubuntu-wps`, use the following command:

```zsh
docker container run -it --rm --name container-ubuntu -p 80:80 ubuntu-wps sh
```

Now, in the container command line just type the command below to start nginx and you can verify in your browser in the ip address or `localhost` that nginx is working.

```zsh
service nginx start
```