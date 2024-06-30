# Jekyll-Walkthrough

Tutorial website using Jekyll static site generator

## Prerequisites

Docker installed and running.

## Getting Started

Within a terminal, navigate to the project directory and run the following command:

```bash
docker run -it --rm -v "$PWD":/usr/src/app -p "4000:4000" starefossen/github-pages
```

This will run a Docker container with the current directory linked to the
container's `/usr/src/app` directory.

You can access the webpage via a web browser at `http://localhost:4000`.

## Notes

The Docker container uses Jekyll to build the site from the provided resources
and runs the webpage locally.
