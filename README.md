# Dockerized Clarive

This is an official way to run Clarive in a docker container. This repository provides a `docker-compose` configuration
that will start `Database`, `Nginx`, `Web` and `Dispatcher` services.

## Prerequisites

You should be running `docker` daemon and having `docker-compose` installed. You can find documentation on the
[Docker](https://docs.docker.com/compose/install/) website.

## Configuration

### I don't have config file or Clarive DB

Create `docker-compose.yml` from a template:

    cp docker-compose.example.yml docker-compose.yml

Run setup to initialize the DB and follow the instructions

    docker-compose run web /opt/clarive/clarive/bin/cla setup

In the setup process:
 
- type the id of the configuration and remember it.  You'll have to use it later (i.e. xxxxxxxx)
- IMPORTANT!!
  - you should enter `db:27017` as the database server
  - Choose an URL that will take your users in the intranet or internet back into Clarive: `http://localhost:8080`

Edit `config/xxxxxx.yml` config file and remove the `host:` line

Edit docker-compose.yml and change `-c clarive` by `-c xxxxxxxx` in both the web and disp services command

### I already have a config file and Clarive DB

If you already have a configuration file and an clarive database, you just have to load the database into the
db service using the appropiate command.

Example:

- copy your DB dump in ./data/dump/clarive
- start the docker compose
- run the `mongorestore` command in the db container:

    `docker exec -ti clarive-docker-db-1 mongorestore /dump`

- stop the compose, edit the config file to point to the restored DB
- restart the compose

## Starting

    docker-compose up

or in detached mode

    docker-compose up -d

## Connecting

Open your browser and navigate to `http://localhost:8080`.
