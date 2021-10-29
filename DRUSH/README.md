# Drush

- NB Also see [DOCKER](/DOCKER/README.md)

## Login to Drupal

- `drush uli` - give you login link.

## Clear Cache

- `drush cr` - clear site cache

## Import config settings

- `drush cim sync -y` when on a new branch (using `-y` flag to accept settings)

## Export config settings

- `drush cex sync -y` to save your settings to a branch that you need to put to develop (using `-y` flag to accept settings)

## Custom - get data from endpoint

- `drush srr` gets SR data and saves it in cache

## Drop / Forget Database

- `drush sql-drop`

## Sync a database

- `drush sqlc < {path/to/database.db}`
- `drush sql-sync {@database source} {@target}` e.g. `drush sql-sync /@prod @self` or `drush sql-sync /@dev @self`(See below for notes)

```
if you do `drush sa` in your local, you’ll see all the aliases available for the project

examples might be: `project.dev`, `project.test` and `project.prod`
which is more like: `dev`, `stg` and `prod`

@self is the environment where you are right now.
To check this check `drush status` would be the same as doing drush @self status
```

## Export Database

- `drush sql-dump --result-file=database-name.sql`
- If this fails do it within the container `docker-compose exec fpm bash` then `drush sql-dump --result-file=database-name.sql`

## Sync images

- `drush rsync @project.dev:%files/ @self:%files` where `@project.dev` is site alias

## Drush Site Alias - Login Method

- `drush sa`

```
'@project.dev':
  uri: dev.project.co.uk
  host: abc.com
  options: {  }
  paths:
    dump-dir: /mnt/tmp
  root: /var/www/html/project.dev/docroot
  user: project.dev
  ssh:
    options: '-p 22'
```

- Log in using `drush @project.dev uli`

## Run drush in docker container

- [See docker](/DOCKER/README.md#run-drush-in-docker-container)

## Drush non respondant

1. Delete `/vendor` folder
2. Run `composer install --ignore-platform-reqs` in root
3. Drush `drush cr && drush cim && drush cr` commands. Choose sync option for config import if asked.
