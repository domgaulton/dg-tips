# Drush

* NB Also see [DOCKER](/DOCKER/README.md)

## Login to Drupal
* `drush uli` - give you login link

## Clear Cache
* `drush cr` - clear site cache

## Export config settings
* `drush cex sync -y` to save your settings to a branch that you need to put to develop (using `-y` flag to accept settings)
## Import config settings
* `drush cim sync -y` when on a new branch (using `-y` flag to accept settings)

## Export config settings
* `drush cex sync -y` to save your settings to a branch that you need to put to develop (using `-y` flag to accept settings)

## Drop / Forget Database
* `drush sql-drop`

## Sync a database
* `drush sqlc < {path/to/database.db}`