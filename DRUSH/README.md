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
* `drush sql-sync {@database source} {@target}` e.g. `drush sql-sync /@prod @self` or `drush sql-sync /@dev @self`(See below for notes)

```
if you do `drush sa` in your local, you’ll see all the aliases available for the project

examples might be: `dev`, `test` and `prod`
which is more like: `dev`, `stg` and `prod`

@self is the environment where you are right now. 
To check this check `drush status` would be the same as doing drush @self status
```