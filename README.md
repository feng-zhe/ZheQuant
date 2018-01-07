# ZheQuant
[![Build Status](https://img.shields.io/travis/feng-zhe/ZheQuant/master.svg)](https://travis-ci.org/feng-zhe/ZheQuant)
A framework to help build analysing system

## Notice
THIS PROJECT IS UNDER DEVELOPING!

If you want to play around, please feel free to run it with the instruction under section "Usage". But if you want to use the stable version, please check the brach "stable" (which doesn't exist now, hahaha. I will make it ASAP)

## Usage
### Prerequisits
- install [docker](https://www.docker.com/) and docker-compose. On some platform, the docker-compose will be installed with docker engine automatically
- install [pipenv](https://github.com/pypa/pipenv)
- git clone this repository and go to its directory
- use `git submodule update --init --recursive` to download submodules
### Run Server
- use `docker-compose build` to build the components' images
- use `docker-compose up -d` to run components' containers
### Run Client
- git clone [ZheQuant-client-python](https://github.com/feng-zhe/ZheQuant-client-python)
- run `pipenv install`
- run `pipenv run python main.py` or something equivalent
- run `help <command>` to understand the usage
### Clean
- use `docker-compose down -v` to stop and remove the containers and their volumes
### Play Around
- use `docker-compose run admin /bin/bash` to start the admin container. The amdin component is mainly used to manage the ZheQuant. For example, you can use `./main.py -g` to generate test data and play around. There is a user 'test' with password 'test' and some fake stock data generated. For more command, please refer to the document of [ZheQuant-admin-console](https://github.com/feng-zhe/ZheQuant-admin-console) or the `./main.py -h`.

## Technical Info
### Queue in Rabbitmq
- jobs-todo: messages containing jobs to do
    - id: the corresponding document _id in database
    - cmd: the command line for jobs
- jobs-done: messages containing finished jobs
    - id: the corresponding document _id in database
    - status: the result status which is 'done' or 'error' or 'waiting'
    - result: the job result as a string

### Database in mongodb
- stocks
    - code
    - date
    - volume
    - open
    - close
    - high
    - low
- users
- jobs-result
    - _id: the document_id
    - name: job_name
    - creator: userId
    - create_date: new Date()
    - status: 'waiting'
    - description: description
    - cmd: cmd

## FAQ
- Q: Why not adding a git clone command line in Dockerfile to download ZheQuant components, instead of being git submodules into this repository?
    - Because by git submodule, you can add your config files and other modification into the submodules before creating docker-compose services. Otherwise you have to change the Dockerfile which is not recommend to be changed.
