# Dockerized Ollama Server

This repository contains a setup to run an Ollama server inside a Docker container.

## Prerequisites

- Docker installed on your system

## Files

- `Dockerfile` - Defines the Docker image and its configuration.
- `start.sh` - A startup script to launch the Ollama server.

## Usage

### Build the Docker Image

Run the following command to build the Docker image:

```sh

docker build --no-cache -t ollama-base:latest ./base/.

docker build --no-cache -t ollama-deepseek:latest ./deepseek/.
```

#### Run the Docker container
```sh
docker run -d --name deepseek-container -p 11434:11434 -v ollama-models:/root/.ollama ollama-deepseek:latest
```

