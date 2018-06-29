# How to add visit dates to the database

1. Manually create the schedule using the physical golf-peg-calendar.
1. Take a photo of each week or two weeks in one photo.
1. Put these photos into a subfolder ```Naturskolan\Administration\Schema och mejllistor\Analog_kalender\veckovis``` and give the folder a name of the form ```status_YYMMDD```, e.g. ```status_180123```
1. Name each photo with a double-digit week number and, if the photo contains several weeks, the last week. E.g. ```23_25.jpg``` for a photo containing week 23 to 25 or ```07.jpg``` for a photo containing only week 7.
1. Open the sheet ```Èviga kalendern``` in ```Naturskolan\Administration\Schema och mejllistor```
1. Hide all "old" rows, i.e. rows with older dates that you don't need to see. Don't delete these as they might be valuable later.
1. In cell C1 and C2, edit the dates to match the interval for which you want to add dates. Example: If all the dates you want to add are in Q1 and Q2 of 2019, use ```2019-01-01``` and ```2019-06-30```
1. In row 3 (the counting row), adjust the first formula to reflect the row numbers that match the interval. Example: If the interval is Q1 and Q2 of 2019, look in which rows ```2019-01-01``` and ```2019-06-30``` are, respectively. If the first date is in row 615 and the last date is in row 815, the first formula should be ```=COUNTIF(E635:E815;"?") + COUNTIF(E635:E815;"??") * 2 + ... (etc.)```
1. Copy that formula into each of the counting cells in row 3.
1. For each day in the interval, put an "x" into the corresponding cell where a certain visit occurs. If several visits of the same type occur at the same day, enter a string of repeated "x" matching the number of visits.
    1. Example 1: One visit of the type "Universum" occurs at 2019-01-15. Let's say the row of that day is 650 and the column for "Universum" is E. Thus, in cell E560 you write one "x".
	1. Example 2: Three visits of the type "Vårvandring" occur at 2019-03-05. You determine the row of that day (let's say it's 702) and the column for "Vårvandring" (maybe F). Now you have two possibilities: Either you write "xxx" (one "x" for each visit) into cell F702 or the number "3".
1. When you have correctly entered all information and checked that the number of visits amounts to at least the number of groups, use the columns right of the yellow column. In these columns, the dates for each visit have been replicated.
    1. Go to the overview of the admin area at ```naturskolan_database/admin``` and deactivate **all** cron jobs to avoid that users are informed of the changes *before* you are sure that all visit dates are assigned correctly.
	1. Open ```naturskolan_database/admin/batch/add_dates```
    1. For each column, copy the content of the whole column into the text area in the admin panel. Use "clean up" and remove all the rows that are **not** dates, e.g. the title "Uni" and the index "2_1"
	1. Choose the corresponding topic from the selector and click "Add to database".
1. The added dates are not assigned to any group yet. Assigning the dates happens at ```naturskolan_database/admin/batch/set_visits```
    1. The groups at the left are in the order specified by the visit order. This order can be changed by reordering the rows on ```naturskolan_database/table/School``` and pressing "Spara besöksordningen".
	1. If you want to reorder visits or even individual groups to maximimize bus pooling ("samåkning") or avoid certain combinations of care-intensive groups to visit at the same day, drag and drop upwards or downwards. Grey fields are already assigned and **can't** be changed by dragging and dropping.
	1. If you are satisfied with the assignment, press "Send away".

	
## Additional remarks
- The formula counting the visits actually does the following: If the content of the cell is a pure number (0, 3, 7, etc) it uses that number. Else it uses the length of the string in the cell, including whitespace (front, middle, end). So the cell content "xbc" and "d D" and "3" all give the same result: 3.
- A visit means "1 group has a meeting of a certain type on a certain day". If two groups come at the same time to the same location, this counts as 2 (!) visits.
- Take note that the physical golf-peg-calendar only shows the number of people involved in a certain type of visits for a certain day. You have to heuristically determine how many visits this corresponds to using information about the number of people involved per group per visit and information about extra staff involved on a certain day (for training purposes or other needs). For example: For a visit of the type "Kemiska reaktioner" 3 people work with 2 groups. So if 3 people are planned for "Kemiska reaktioner" on a certain day, this day has 2 visits. 