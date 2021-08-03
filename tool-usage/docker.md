# Docker

### Pulling an image on Docker:

On your host box, run the command.

```text
sudo docker pull centos:latest
```

### To see all the Docker images installed, issue the command:

```text
sudo docker images
```

### To start the docker pulled CentOS, we need to issue a command to the OS to get a thread started. We can do this by running the following command:

```text
sudo docker run -it centos /bin/bash
```

The above command does the following things −

* Runs the CentOS Docker image.
* Runs the image in interactive mode by using the **-it** option.
* Runs the **/bin/bash** command as the initial process.

## **Docker Example Building and Usage:**

### Clone this repository

```text
git clone https://github.com/BeetleChunks/SpoolSploit
```

### Build the SpoolSploit Docker container image

```text
cd SpoolSploit
sudo docker build -t spoolsploit .
```

### Create and start the SpoolSploit Docker container

```text
sudo docker run -dit -p 445:445 --name spoolsploit spoolsploit:latest
```

### Attach to the container

```text
sudo docker exec -it spoolsploit /bin/bash
```

### Docker Compose

```text
$ cd <project directory>

$ docker compose up -d
```

