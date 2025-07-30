# Containers and docker

## What is a container?

It is an isolated program/process that has the minimum dependencies to run an operating system (in most cases a flavor of linux).

- As an isolated program/process it has it's own resources, own dependencies, own kernel, etc.
- This gives us a way to make our applications more portable, since we only have to share an image and run it with our code.
- It also makes it easier to be manage, since this isolated instance behaves like a program we can kill it, stop it or rerun it as need it

For a container to work we need:

- A base image, this is just that template of what we want our container to be
- And an entrypoint of execution, this is just what we want to execute or be executing inside our container, that can be a program or an specific command
- A container runtime, a piece of software that can translate these container images into an actual container running.

Now that we have and understanding of the basics of containers we can dip ourselves into Docker the mostly preffered container runtime

## What is a docker?

Docker is a container runtime, it is just a piece of software that lets us run containers on our operating systems.

It comes with a client, a UI(if you are a coward) and API so that we can interact with it programmatically.
Most of our interactions with the runtime is with the client aka the command line interface available and it goes something like this:

- To run a docker image ``docker run hello-world`` this would run the hello-world image, but the process for this would go in different steps
  - First docker checks if the image is available in our computer
  - If it is not available it downloads it from a docker registry (It is a place where docker images live online)
  - Then builds the docker image pulled
  - Finally it runs whatever command or program was specified in the image

## Dockerfiles

Docker lets us declare the image configuration and execution with something called Dockerfiles.

This dockerfiles are just the declaration of steps that an image has to follow, via linux commands, program execution, dependency installation, etc.

A simple python dockerfile looks like this:

```Dockerfile
FROM python:3.10-rc-buster

WORKDIR /code

ENV FLASK_APP app.py
ENV FLASK_RUN_HOST 0.0.0.0

COPY requirements.txt requirements.txt

RUN pip install -r requirements.txt

COPY . .

CMD ["flask", "run"]
```

This just declares a simple docker image that could run a flask application -> Try figuring out what any of these words means. :P

After we created our Dockerfile with what we want to run we have to build it, to do that we have to be on the directory where that dockerfile lives.

To build we have to use this command

- ``docker build -t flask_app:1.0 .`` This builds a dockerfile into a docker image with the name flask_app and a version of number 1.0 and and the . makes the command to look for the dockerfile on the current directory

And at last when everything has been built, we have to run our docker image to have a fully developed docker container and for that we use this

- ``docker run -p 5000:5000 flask_app:1.0`` This command makes our image run, the command that runs is the one specified at the end of the dockerfile, in this case we have as entrypoint the command of ``flask run`` to run our flask app previously built.
