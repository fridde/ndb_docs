# How to export data from mailchimp to database

1. export the whole mailchimp list (not just a segment).
1. Open excel and go to ```Data -> From Text/CSV```
1. choose ```subscribed_members_export``` from the export (after unzipping)
1. rename sheet to current date
1. open Excel sheet "Import Mailchimp-data to Naturskolan database" and copy the data to "All data". Check for bad fomatting.
1. Value adjustments:
    1. Add 2000 to the values in "StartYear"
	1. Convert "2/3" in Årskurs to "2"
1. create column "group_id", "user_id" and "school_id"
1. populate school_id using the sheet "schools" and the formula VLOOKUP(C2;schools!A:B;2;FALSE) or something like that
1. give user_id and group_id some incrementing numbers. For user_id, start at 10 (so Naturskolan's staff starts at 1).
1. try to find duplicates among users, give identical users same id. Delete user data for the superfluous users, but not the user_id (since it's linked to the group)
1. copy the sheet's content into "user" and "groups" (paste values and formatting, but not formulas)
1. Within each of these, remove the non-necessary columns.
    1. in "user"
	    1. add columns "Role", "Status" and "CreatedAt" and use values ```0, 1``` and ```2018-01-01T12:00:00+01:00``` in each row 
	    1. remove users with empty rows
	1. In "groups"
	    1. Add columns "Status" and "CreatedAt" and use values ```1``` and ```2018-01-01T12:00:00+01:00``` in each row.
1. Add the main sheet's data to the area right of the black column in the sheet "visits".
1. Delete all columns except "group_id", "Årskurs" and "D1" to "D7".
1. For each årskurs, copy the corresponding dates and user_id into the columns left of the black column.
1. To export each table, copy the relevant columns into "export" and look in "column_names" if the column names have been translated well. Copy the translated headers into the "export"-sheet.
1. Copy the comma-seperated headers to somewhere safe. 
1. Export the export-sheets as csv-documents.
1. Open the 3 files in Notepad++ and convert the encoding to UTF8. Save!
1. import it into the sql-database and use the comma-seperated headers to specify the order of the columns. Set skipped rows to 1 and column separator to ";". Disable foreign key checks.
1. add those who work at naturskolan to the database