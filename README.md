This project presents a straightforward setup for simple and reproducible development environments for your applications, based on Docker. We also provide [templates](templates/) if you want to just copy and paste some code to get you started.

At [Didomi](https://www.didomi.io), we want our new or existing developers to be able to jump straight into reading the code and changing it. No developer should have to spend hours setting up a development environment.
We use this setup to make sure that there is a standard way of getting a running bash with all the dependencies setup for each of our apps.

**Table of Contents**

- [The setup](#the-setup)
- [Getting started for developers](#getting-started-for-developers)
- [Templates](#templates)
- [Advantages](#advantages)
- [License](#license)
- [Sponsor](#sponsor)

## The setup

Our setup is based on [Docker](https://www.docker.com/) and [make](https://www.gnu.org/software/make/) so go ahead and make sure that they are installed on your computer.

The setup consists of three files that should live at the root of all your source repositories:

 - `docker-compose.yml` that describes the containers for your app and external dependencies (like databases). Ports and volumes mounted from the host to the container must be described in this file.
 - `Dockerfile` that describes how to build a Docker image with the software dependencies required by your app.
 - `Makefile` that has a set of standard commands to get the Docker containers up and running.

The basic idea is that the `docker-compose.yml` and `Dockerfile` describe the environment and dependencies that are required by your app to run in development and the `Makefile` offers commands to run the Docker container and get a bash. The commands are `make drun` to launch a container and get a bash or `make dbash` to get a new bash in an already running container.

We also set two constraints to make things even more standard across projects:

 - The current directory is mounted in `/app` so the app source code always lives there.
 - The commands in the Makefile are always the same (`drun`, `dbash`) even though they can be customized per project if needed.

As you can see, this is really simple and is a standard use of Docker and docker-compose. What matters is to make it a standard across all the projects in your company so that developers can get started on any project easily.

## Getting started for developers

For a developer, getting started is as simple as 1-2-3:

 1. Ensure that  [Docker](https://www.docker.com/) and [make](https://www.gnu.org/software/make/) are installed on your computer
 2. Clone the repository of the app that you want to run
 3. Run `make drun` in the folder and voila, you get a development 
 4. If you want to get an extra bash in the running container (from a separate terminal), run `make dbash`.

## Templates

This repository has simple templates that you can copy and paste to get you started with different stacks:

 - [Basic](templates/basic): A basic template with no specific dependency
 - [Node.js + Postgres](templates/node-postgres): A template with Node.js and Postgres setup

## Advantages

Here is a few reasons why this setup is powerful:

 - **It is standard.** Make sure that all your projets are setup the same way so that developers know that they can clone any repository and run a `make drun` to get a development environment up and running.
 - **It is simple.** You are using Docker and make and there is nothing specific about what you do with them so everyone can understand how it's setup and update the setup when required to add new dependencies.
 - **It is part of the source code.** So it can be easily modified, reviewed and kept up to date by developers.
 - **It does not depend on the developer's computer.** Because we are using Docker, developers are free to use whatever OS they want and they will still get the same environment as everyone else with a real Linux bash.

## License

There isn't much to license so whatever it is, it's under [the Unlicense](http://unlicense.org/UNLICENSE).
Be nice and share if you find a more convenient setup or if you work on a template for a stack that we don't have yet. You can reach out to tech@didomi.io or open an issue here.

## Sponsor

<a href="https://www.didomi.io">
    <img src="https://www.didomi.io/wp-content/uploads/2017/01/cropped-didomi-horizontal-1.png" alt="Logo of Didomi" width="200" />
</a>

This project is developed and maintained by [Didomi](https://www.didomi.io), an end-to-end solution for managing data privacy and user consent.