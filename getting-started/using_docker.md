# Using docker for development

## Docker for development environment

- Install [Docker](https://docs.docker.com/get-docker/).
- Clone the repo by running `git@github.com:qichunren/railsblocks.git`.
- `cd railsblocks`
- If using it for the first time, run `docker-compose build` to build the images.
- Run `docker-compose run --rm web bin/setup` to create and seed the database.
- Run `docker-compose up` to start the application and get things up and running.
- From now onwards, we can just run `docker-compose up` from within the root of the `railsblocks` directory to bring up the application.

## Development

    docker build -t sitebuilder-web .
