# Dockerized Clarive

This is an official way to run Clarive in a docker container. This repository provides a `docker-compose` configuration
that will start `Database`, `Web` and `Dispatcher` services.

## Prerequisites

You should be running `docker` daemon and having `docker-compose` installed. You can find documentation on the
[Docker](https://docs.docker.com/compose/install/) website.

## Configuration

Create `config/clarive.yml` config from a template:

    cp config/clarive.example.yml config/clarive.yml

Create `docker-compose.yml` from a template:

    cp docker-compose.example.yml docker-compose.yml

## Starting

    docker-compose up

or in detached mode

    docker-compose up -d

## Connecting

Open your browser and navigate to `http://localhost:8080`.
