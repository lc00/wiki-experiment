## Concepts

* Image - Configuration with all dependencies
* Container - Running image
* Service - A production container (specifies ports, etc.)
* Stack - A collection of services that share dependencies and can be deployed together
* Swarm - A collection of docker containers spread across machines
    * Node - One machine in the swarm
    * Swarm Manager - Runs the swarm
    * Swarm Worker - Slave

## Installation

* You have to run Docker commands as sudo because they bind to a UNIX socket, unless you create a [group for it](https://askubuntu.com/questions/477551/how-can-i-use-docker-without-sudo)

## Commands

* `docker build -t <nickname> <folder-to-build>`
* `docker run -p <my-port>:<docker-port> <image-name>` - Run an image
* `docker stop <docker-container-id>` - Stop a container
    * `-d` starts the container in the background
* `docker images` - List docker images on this system
* `docker container ls` - List running docker containers on this system
* `docker login` - Login to Docker Cloud
* `docker tag <image-name> <username>/<image>:<tagname>` - Tag an image
* `docker push <username>/<image>:<tagname>` - Push to Docker Cloud
    * `<tagname>` defaults to "latest"

## Dockerfiles

* Stored in a file called `Dockerfile`

```
# Use an official Python runtime as a parent image
FROM python:2.7-slim

# Set the working directory to /app
WORKDIR /app

# Copy the current directory contents into the container at /app
ADD . /app

# Install any needed packages specified in requirements.txt
RUN pip install -r requirements.txt

# Make port 80 available to the world outside this container
EXPOSE 80

# Define environment variable
ENV NAME World

# Run app.py when the container launches
CMD ["python", "app.py"]
```
