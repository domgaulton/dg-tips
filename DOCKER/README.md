# Docker

* NB Also see [DRUSH](/DRUSH/README.md)

## Start docker container
* `docker-compose up -d`

## Run drush in docker container
1. `docker-compose exec php bash`
2. `cd docroot/`
3. `../vendor/bin/{DRUSH COMNMAND}`