# Welcome

This project demonstrates a simple example of running a self-contained [WordPress](https://wordpress.org/) application locally within a [Docker](https://www.docker.com/) environment.

To develop this application on your machine, you will need to have Docker and [Node.js](https://nodejs.org/en/) installed.

If you are unfamiliar with Docker, don't panic. You can download and install [Docker Desktop](https://www.docker.com/products/docker-desktop) - available for macOS and Windows.

## Getting started

To use this project, you must:

- Have an existing database export from a WordPress instance (`./database/local.sql` in this example project)
- Copy `.env.sample` to `.env` and use the MySQL credentials - including user and password - from your original/source WordPress instance

If you would like to use an existing WordPress backup as a starting point:

- Copy the `.sql` database export to the `./database` folder - updating `./docker-compose.yml` to reference the appropriate file
- Copy your WordPress application to the `./wordpress` folder - updating `./docker-compose.yml` to point to the appropriate `wp-content` directory

Assuming you have Docker installed on your machine:

```sh
$ npm run start
```

Once you have started the application for the first time, you should be able to view [http://localhost:8000/](http://localhost:8000/) and see a message: `Error establishing a database connection"

Open up the Dockerized PHP My Admin app at [http://localhost:8080/](http://localhost:8080/) - logging in with the username and password defined in your `.env` file.

Within PHP My Admin, go to the `wp_options` table and change `siteurl` and `homeurl` to http://0.0.0.0:8000

### Troubleshooting

You can verify what configuration settings are defined for a specific `docker-compose.yml` file by running the following command:

```sh
$ npm run docker:config
```
