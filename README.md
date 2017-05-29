# ZheQuant
A framework to help build analysing system

## Notice
This project is under developing.

TODO:
- create a new component 'ZheQuant-admin-console' to
    - insert test data and user into databse
    - report status (runtime statistics, health check ...)
    - other manage&console tasks
- write documentation for this project and each component

## Usage
Please remember to use `git submodule update --init --recursive` to download submodules.


## FAQ
- Q: Why not adding a git clone command line in Dockerfile to download ZheQuant components, instead of being git submodules into this repository?
    - Because in this way, you can add your config files and other modification into the submodules before creating docker-compose services. Otherwise you have to change the Dockerfile which is not recommend to be changed.
