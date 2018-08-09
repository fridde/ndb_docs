# How to update the remote MYSQL database

Always assume that the *data* of the remote database is the most current, but the *structure* of the local database is the most up-to-date.

Thus, to make a structural update to the remote database, export only the structure of the whole database. Use the settings

- dump table "structure only"
- include "DROP TABLE"
- remove "IF NOT EXISTS"

Now export the structure of your local database (or find it in misc/SQL_data) and visually compare both the remote structure and the local structure and look for important differences in 

- column names
- new or removed columns
- removed tables (added tables will automatically be taken care of)
- new (stricter) column constraints or changed data types

After this analysis go into phpMyAdmin of the remote server and 

- remove all remote tables no longer necessary
- remove all columns no longer necessary
- add new columns and populate the corresponding column value of each row if necessary
- for each new stricter constraint, download the corresponding column, edit all values in an editor to match the new constraint and then upload them again

Now go to the SQL file containing the remote data of the database that we want to re-import after we have synchronized the structure (and thus removed all remote data).

Within that file, adapt all column names. If new columns have to be added, make sure to add a  