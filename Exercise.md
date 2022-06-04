# Exercise

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

**2. Generate an image called ubuntu-wps using the `commit` command**

To generate the image from container, just run the command below:

```zsh
docker container commit container-ubuntu ubuntu-wps
```

Now, you can use the command below to see that the image was created:

```zsh
docker image ls
```