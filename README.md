# ZheQuant
A framework to help build analysing system

## Notice
This project is under developing.

TODO:
- write documentation for this project and each component

## Usage
Please remember to use `git submodule update --init --recursive` to download submodules.

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
