# SurrealDB Deal Store

This repository is for my own personal learning journey with SurrealDB following the [SurrealDB Fundamentals course]('https://surrealdb.com/learn/fundamentals'). I will be using this repository to learn and experiment with SurrealDB, and I will be documenting my experiences and initial impressions along the way on my website. Eventually I would like to apply this technology to a personal project, but for now I will be using it as a sandbox to learn and experiment.

_Feel free to clone or learn from this repository, but please note that it is not intended for production use._

## 📃 Table of Contents

- [SurrealDB Deal Store](#surrealdb-deal-store)
- [Table of Contents](#📃-table-of-contents)
- [Prerequisites](#👓-prerequisites)
- [Getting Started](#🦥-getting-started)
- [Resetting Docker](#🐋-resetting-docker)
- [References](#🧑‍🚀-references)
- [License](#license)

## 👓 Prerequisites

You'll basically need a working Docker environment to run the SurrealDB server.

- [Docker]('https://www.docker.com/get-started/') To manage the images and run the `surreal` commands
- [docker-compose]('https://docs.docker.com/compose/') To manage surrealdb and infrastructure
- [Docker Desktop for Windows/WSL]('https://learn.microsoft.com/en-us/virtualization/windowscontainers/deploy-containers/set-up-linux-containers') Required for Windows users
- [Surrealist]('https://surrealdb.com/docs/surrealist')

**NOTE**: _I use [nix-direnv]('https://github.com/nix-community/nix-direnv') to manage my development environment. This also let's me use commands directly from the CLI. This is optional._

## 🦥 Getting Started

1. Clone this repository and navigate to the root.
2. Create a `.env` at the root, and replace the content with your settings
   ```text
   DB_USER=<your_surrealdb_user>
   DB_PASS=<your_surrealdb_pass>
   DB_HOST=0.0.0.0
   DB_PORT=8000
   ```
3. Build and run the project: `docker-compose up --build --detach`
4. Validate `HTTP 200` status code by making a request to `localhost:8000`. Refer to your `.env` for connection details.
   - Linux: `curl -v localhost:8000`
   - Windows:
     ```powershell
         iwr "localhost:8000" | FT StatusCode, StatusDescription
     ```
5. Launch Surrealist and create a [connection to the database]('https://surrealdb.com/docs/surrealist/getting-started#connections')
6. ???
7. Profit

## 🐋 Docker

This is mostly aimed at those who utilize Docker Desktop for Windows/WSL. If you are using Docker on Linux, you can skip this section. Clearing the Docker cache doesn't always work through the Docker Desktop GUI, so you may need to use the CLI to get the job done. At least, in my own experience.. So here are some helpful commands all aimed at stopping and removing your local docker infrastructure.

- Stop all containers:
  `docker stop $(docker ps -a -q)`
- Remove all containers:
  `docker rm $(docker ps -a -q)`
- Remove all images:
  `docker rmi $(docker images -q)`
- Remove all volumes:
  `docker volume rm $(docker volume ls -q)`
- Remove all networks:
  `docker network rm $(docker network ls -q)`
- Remove all dangling volumes:
  `docker volume rm $(docker volume ls -qf dangling=true)`
- Remove all dangling networks:
  `docker network rm $(docker network ls -qf dangling=true)`
- Remove all dangling containers:
  `docker rm $(docker ps -a -q --filter "status=exited" --filter "status=created")`
- Remove all dangling images:
  `docker rmi $(docker images -f "dangling=true" -q)`
- Remove everything:
  `docker system prune -a --volumes`

## 🧑‍🚀 References

- [SurrealDB Documentation]('https://surrealdb.com/docs/surrealdb')
- [Surrealist Documentation]('https://surrealdb.com/docs/surrealist')
- [Docker Desktop]('https://www.docker.com/resources/')
- [docker-compose cheatsheet]('https://devhints.io/docker-compose')
- [Windows Subsystem for Linux (WSL)]('https://learn.microsoft.com/en-us/windows/wsl/setup/environment')
