# Kimai-time-tracking

Here is an example README for the provided `docker-compose.yml` file:

# Kimai2 Docker Compose

This is a Docker Compose configuration for running [Kimai 2](https://www.kimai.org/) using Nginx as a reverse proxy and MySQL as the database.

## Requirements

- [Docker](https://docs.docker.com/engine/installation/)
- [Docker Compose](https://docs.docker.com/compose/install/)

## Usage

Clone this repository, navigate to its directory in your terminal and run:

```
$ docker-compose up -d
```

The above command will download the required images and start the containers in detached mode. You should now be able to access the application by navigating to `http://localhost:8080` in your web browser.

## Configuration

This configuration uses the following environment variables to configure the Kimai 2 container:

- `APP_ENV`: Set the application environment to `prod`.
- `TRUSTED_HOSTS`: A comma-separated list of trusted hosts (normally you would only need to set localhost).
- `ADMINMAIL`: The email address of the initial admin user.
- `ADMINPASS`: The password for the initial admin user.
- `DATABASE_URL`: The database URL in the format `mysql://user:pass@host/dbname`.

To change these values, update the `kimai` service section of the `docker-compose.yml` file and then run `docker-compose up --build` to rebuild the images with the updated configuration.

## Volumes

This Docker Compose configuration defines a volume called `public`, which is shared between the `nginx` and `kimai` services. This volume should contain any files that need to be served by the web server. By default, it is mounted to `/opt/kimai/public` inside both containers.

## Credit

This Docker Compose configuration was inspired by the [official Kimai 2 Docker images](https://github.com/kevinpapst/kimai2-docker). The Nginx image is `tobybatch/nginx-fpm-reverse-proxy`, which is a lightweight web server with PHP support. The MySQL image is the official `mysql:5.7` image from Docker Hub.
