# Docker/Django/Postgresql

This repository demonstrates how Docker and PostgreSQL work together on a Django project. Switching between SQLite database and a PostgreSQL is a mental leap for many developers initially. 
While using Docker, we don't need to be in a virtuak environment anymore. Docker is our virtual environment and our databse and more if desired. The Docker host essentially replaces our local operating system and within it we can run multiple containers, such as for our web app and for our database, which can all be isolated and run separately.

## Commands Used
1. `docker build .`
> This command creates a custom image for the container.
2. `docker-compose up`
> This command runs the Docker container.
3. `docker-compose up -d`
> This command runs the Docker container but in detached which allows docker containers to run in the background and prevents use of two different terminals.

## About Dockerfile
A Dockerfile defines the steps to create and run a custom image. It contains Python but also installs our code and has additional configuration details.
Dockerfiles are read from top-to-bottom when an image is created. The first instruction is a `FROM` command that tells Docker whwat base image we would like to use for the application. Then we use `ENV` command to set three environment variables.
- `PIP_DISABLE_PIP_VERSION_CHECK` - disables an automatic check for pip updates each time.
- `PYTHONDONTWRITEBYTECODE` - means python will not try to write .pyc files.
- `PYTHONUNBUFFERED` - ensures our console output is not buffered by Docker.
The command `WORKDIR` us used to set a default workig directory when running the rest of our commands.
The `COPY` command takes two parameters: the first parameter tells Docker what file(s) to copy intp the image and the second parameter tells Docker where you want the file(s) to be copied to.
The `RUN` command executes the `pip install` command just like in local development but this time the modules will be read from the requirements.txt file and installed into the container.