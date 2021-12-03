# Docker

- NB Also see [DRUSH](/DRUSH/README.md)

## Start docker container

- `docker-compose up -d`
- `docker-compose up -d server`
- `docker-compose up -d nginx`
- `docker-compose up -d apache`

## Run drush in docker container

- `docker-compose exec fpm bash`
- `docker-compose exec php bash`
- `docker-compose exec -u root fpm bash`

## Completely remove container (and DB)

- `docker-compose down` - Remove container

### Check to see if the containers have been removed below in two ways

- `docker ps -a | grep [project]` - Check if any parts haven't been removed. See next steps if you need to manually remove them.
- `docker rm [id or container name] [id or container name]`

### Or

- `docker volume ls` - Check if any parts haven't been removed. See next steps if you need to manually remove them.
- `docker volume rm [id or container name] [id or container name]`
