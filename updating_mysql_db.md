# How to update the remote MYSQL database

Always assume that the *data* of the remote database is the most current, but the *structure* of the local database is the most up-to-date.

Thus, to make a structural update to the remote database, export only the structure of the whole database. Use the settings

- dump table "structure only"
- remove "Show comments"
- include "DROP TABLE"
- remove "IF NOT EXISTS"

Now export the structure of your local database (or find the latest backup in misc/SQL_data) and visually compare both the remote structure and the local structure and look for important differences in 

- column names
- new or removed columns
- removed tables (added tables will automatically be taken care of)
- new (stricter) column constraints or changed data types

After this analysis go into phpMyAdmin of the remote server and 

- remove all remote tables no longer necessary
- remove all columns no longer necessary
- alter column names that have changed
- add new columns and populate the corresponding column value of each row if necessary
- for each new stricter constraint, download the corresponding column, edit all values in an editor to match the new constraint and then upload them again

Download the remote structure again (using the settings above) and check again. Repeat until you are sure that the settings match.

If you want to be extra sure, run ```dbrecreate``` in the root folder of the root folder of the dev version of the app, then run ```run_deploy```, but only the first part to export the structure again and then compare the structures again.

