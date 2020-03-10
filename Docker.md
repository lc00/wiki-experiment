## Concepts

* Image - Configuration with all dependencies
* Layer - Intermediate image made during a build that docker might cache and use again during updates
* Container - Running image
* Service - A production container (specifies ports, etc.)
* Stack - A collection of services that share dependencies and can be deployed together
* Swarm - A collection of docker containers spread across machines
    * Node - One machine in the swarm
    * Swarm Manager - Runs the swarm
    * Swarm Worker - Slave

A VM is a hardware abstraction (CPU, RAM, etc), while a container is an application abstraction (OS, dependencies, etc.) You can run a container inside of a VM.

## Installation

* You have to run Docker commands as sudo because they bind to a UNIX socket, unless you create a [group for it](https://askubuntu.com/questions/477551/how-can-i-use-docker-without-sudo)

## Commands

* `docker build -t <nickname> <folder-to-build>`
* `docker stop <docker-container-id>` - Stop a container
    * `-d` starts the container in the background
* `docker image ls` - List docker images on this system
    * `docker image pull image-name-here` - Retrieves an image from the default image repo
    * `docker image image-id history` - See history of commands this image ran
* `docker login` - Login to Docker Cloud
* `docker tag <image-name> <username>/<image>:<tagname>` - Tag an image
* `docker push <username>/<image>:<tagname>` - Push to Docker Cloud
    * `<tagname>` defaults to "latest"
* `docker container run image-name commands`
* `docker run -p <my-port>:<docker-port> <image-name>` - Run an image
* `docker container run -it image-name commands` - Interactive terminal
* `docker container ls` - List running docker containers on this system
* `docker container exec container-id command` - Runs a command on a running instance

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

## Example

### Me

* `./Dockerfile`:

```docker
FROM node
WORKDIR /home
ADD . /home
RUN npm i
EXPOSE 8080
CMD npm run serve
```

* `sudo docker build -t my-image`
* `sudo docker tag my-image kylecoberly/my-image`
* `sudo docker push kylecoberly/my-image`

### Collaborator

* `git clone kylecoberly/my-image`
* `sudo docker pull kylecoberly/my-image`
* `sudo docker run -p 8080:8080 kylecoberly/my-image`

## Clean up

Images are huge. Clean up unused stuff with:

`docker system prune -a`

## Rails-Specific Issues

Dockerizing Rails stuff sucks.

* There is no official Rails docker image, you have to customize the Ruby one
* Gems need to be installed in the image
* The server needs to be bound to 0.0.0.0
* The Gem locations need to be updated
* Sometimes the correct version of bundler needs to be installed
* When creating a new app, you also need Node installed if you're using ERB
* If you want to use Docker to `rails new`, you probably need a seperate image for that vs. the one that you'll run generators with. You need your gems in the image when you generate, but you won't have a Gemfile yet when you run `rails new`.

To generate a new rails app:

```Dockerfile
FROM ruby:2.7.0
WORKDIR /app
RUN gem update --system
RUN gem install rails
```

`sudo docker run -v $(pwd):/app rails-new:latest rails new --api my-app-name`

I have one of these saved at `kylecoberly/rails-new:2.7.0`

To use your rails app:

```Dockerfile
FROM kylecoberly/rails-new:2.7.0
COPY Gemfile .
COPY Gemfile.lock .
RUN bundle install

CMD ["rails", "s", "-b", "0.0.0.0"]
```

`docker run --user `id -u`:`id -u` -v $(pwd):/app my-rails-app:latest rails g model user`

NOTE: `docker run` on Linux always creates files as root. Specify your user manually to override it.

`docker run --user `id -u`:`id -u` -p 3000:3000 -v $(pwd):/app my-rails-app:latest`
