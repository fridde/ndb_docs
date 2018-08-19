# How to update the remote MYSQL database

Always assume that the *data* of the remote database is the most current, but the *structure* of the local database is the most up-to-date.

* First, make a backup of the local database and, if necessary, a backup of the remote database
* go to the project folder and run  ```vendor/bin/doctrine orm:schema-tool:update --dump-sql```
* Copy the output of this command into a text editor.
* Inspect the proposed changes and execute them one by one both locally and remotely, if the data is not in danger by these changes.
* Check ```config/table_settings.yml``` for potential outdated settings.
