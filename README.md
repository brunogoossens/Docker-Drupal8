# Development environment for Drupal 8 build with Docker Compose

## Dependencies

* [Docker](https://www.docker.com/)
* [Docker Compose](https://docs.docker.com/compose/install/)

## How to use

### Download this repository

	$ git clone git@github.com:brunogoossens/dockercompose-drupal8.git dockercompose-drupal8
	$ cd dockercompose-drupal8

### Copy drupal code into web/app folder

Start a new terminal (because the other one is running our containers) and copy the Drupal 8 code into the ./web/app folder.

	$ git clone --branch 8.0.x http://git.drupal.org/project/drupal.git web/app

### Start the docker containers

This command will build the containers and start the web and mysql servers. All logging will be outputted on the screen.

	$ docker-compose up

### Install Drupal 8 by using drupal console

	$ docker-compose exec web drupal site:install --db-host=mysql --db-name=drupal8 --db-user=root --db-pass=root
