# Jekyll-Walkthrough

Tutorial website using Jekyll static site generator

Jekyll's walkthrough/tutorial:
[Getting Started > Step by Step Tutorial page](https://jekyllrb.com/docs/step-by-step/)

## Development Environment

Docker image provided by Starefossen's Alpine Docker GitHub
Pages Repository:
<https://github.com/Starefossen/docker-github-pages>

Docker Hub: <https://hub.docker.com/r/starefossen/github-pages/>

### Prerequisites

- Docker and Docker Compose

#### Quick installation

Download Docker's installation script:

```console
curl -fsSL https://get.docker.com -o get-docker.sh
```

Install Docker using their script:

```console
sh ./get-docker.sh
```

Add the current user to the `docker` group to run Docker without needing the
`sudo` command:

```console
sudo usermod -aG docker $USER
```

Activate the change to the `docker` group

```console
newgrp docker
```

Run Docker's `hello-world` test container:

```console
docker run hello-world
```

### Usage

A Docker container can be used to build the Jekyll site from the provided resources
and run the webpage locally.

To run the container with the terminal attached:

```console
docker compose up
```

To run the container detached from the terminal instead:

```console
docker compose up -d
```

The project's `src` directory will be run in the container's `/usr/src/app` directory.
File changes within the `src` directory will automatically trigger a rebuild
process.

You can access the webpage via a web browser at <http://localhost:4000>.

It is recommended to include within `_config.yml` several items:

```_config.yml
repository: your/repo

gems:
- jekyll-github-metadata
- jekyll-mentions
- jekyll-redirect-from
- jekyll-sitemap
- jemoji
```

This is not necessary for just simply playing around with the basic features.

Also, in order for the `{{ site.github }}` metadata variables to be populated
you need to set the JEKYLL_GITHUB_TOKEN environment variable with your GitHub
token.

This can be passed within the `docker-compose.yml` file:

```docker-compose.yml
...
    environment:
      - "JEKYLL_GITHUB_TOKEN:${JEKYLL_GITHUB_TOKEN}"
...
```

To exit and stop the container, just press `Ctrl+C`.

To start the container:

```console
docker compose up
```

To cleanup/remove the container:

```console
docker compose rm
```

To remove the container network:

```console
docker network rm jekyll-walkthrough_jekyll-frontend
```
