# Docker

* NB Also see [DRUSH](/DRUSH/README.md)

## Start docker container
* `docker-compose up -d`
* `docker-compose up -d server`
* `docker-compose up -d nginx`
* `docker-compose up -d apache`

## Run drush in docker container
* `docker-compose exec fpm bash`
* `docker-compose exec php bash`
* `docker-compose exec -u root fpm bash`
