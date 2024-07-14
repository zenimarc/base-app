# Instructions

1. the .env at the root is automatically passed to each package thanks to docker-compose, if you want to run packages without docker-compose you need to copy the .env file in each package who needs it

To start the whole project just run `docker-compose up`
ensure that db env variable in .env and in docker-compose.yml matches
