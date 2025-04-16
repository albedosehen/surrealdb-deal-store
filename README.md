# SurrealDB Surreal Deal Store

This repository is for my own personal learning journey with SurrealDB following the [SurrealDB Fundamentals course]('https://surrealdb.com/learn/fundamentals')

## Prerequisites

- [Docker]('https://www.docker.com/get-started/') To manage the images and run the `surreal` commands
- [docker-compose]('https://docs.docker.com/compose/') To manage surrealdb and infrastructure
- [Docker Desktop for Windows/WSL]('https://learn.microsoft.com/en-us/virtualization/windowscontainers/deploy-containers/set-up-linux-containers') Required for Windows users
- [Surrealist]('https://surrealdb.com/docs/surrealist')

**NOTE**: _I use [nix-direnv]('https://github.com/nix-community/nix-direnv') to manage my development environment. This also let's me use commands directly from the CLI. This is optional._

## Getting Started

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

## References

- [SurrealDB Documentation]('https://surrealdb.com/docs/surrealdb')
- [Surrealist Documentation]('https://surrealdb.com/docs/surrealist')
- [docker-compose cheatsheet]('https://devhints.io/docker-compose')
