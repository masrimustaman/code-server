# Code Server in Docker Container

## Steps for Installing Docker:

1. Remove any Docker files that are running in the system, using the following command:
```
sudo apt-get remove docker docker-engine docker.io
```
*docker-io package is still the name used by Debian/Ubuntu for the docker release provided on their official repos. docker-ce is a certified release provided directly by docker.com and can also be built from source.*


2. Check if the system is up-to-date.
3. Install docker using 
```
sudo apt install docker.io
# To install dependencies use below command. Did not do last time
# sudo snap install docker
```

4. Before testing Docker, check the version installed using the following command:
```
$ docker --version
```

5. Pull an image from the Docker hub using the following command:
Here, hello-world is the docker image present on the Docker hub.
```
$ sudo docker run hello-world
```



6. Check if the docker image has been pulled and is present in your system using the following command:
```
$ sudo docker images
```

7. To display all the containers pulled, use the following command:
```
$ sudo docker ps -a
```

8. For code server use below docker-compose.yml file

*i have pre created the folder before running docker-compose up*

```
---
version: "2.1"
services:
  code-server:
    image: ghcr.io/linuxserver/code-server
    container_name: code-server
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=Europe/London
      - PASSWORD=password #optional
      - HASHED_PASSWORD= #optional
      - SUDO_PASSWORD=password #optional
      - SUDO_PASSWORD_HASH= #optional
    volumes:
      - ./config:/config
      - ./files:/files
    ports:
      - 8443:8443
    restart: unless-stopped

```
