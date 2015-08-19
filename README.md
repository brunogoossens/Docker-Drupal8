# Development environment for Drupal 8 build with Docker Compose

## Dependencies

[Docker](https://www.docker.com/)
[Docker Compose](https://docs.docker.com/compose/install/)

## How to use

### Start docker containers

	$ docker-compose build
	$ docker-compose up

### Copy drupal code into www folder

	$ git clone --branch 8.0.x http://git.drupal.org/project/drupal.git www

### Install Drupal 8

Database settings:

	database: drupal8
	user: root
	password: root
	host: ip of boot2docker

