
## Left to do
* [x] implement welcome_new_user notification
* [x] enable group name change
* [x] implement batch-adding visits
* [x] build batchSetGroupCount Form
* [x] create navigation menus
* [x] fix datepicker on table visits
* [x] protect update from request forgery by introducing session variables
* [x] add responses for admin actions (pop up etc)
* [ ] remove "Specialkost" for fritids and åk 9
* create Kontrollcenter with Buttons
    * [x] enable/disable cron tasks
* [x] create index page
* [x] create page to set bus&food-confirmation status
* [x] create colleague assignment page
* [x] add custom calendar events form
* [x] build wrong-password modal
* [x] make Fritids topic order irrelevant
* [x] update user selector options after adding users
* [ ]
* [ ] give feedback after updating group counts in admin tools
* [ ] add tools to remove rows 
* [ ] add 404 and 500 with smart error handling
* [ ] add button to send manager mobilization mail
* [x] insert loggers to crucial functions
* layout pages
	* [x] width in tables does not exceed page width
	* positioning of elements on admin pages
		* [ ] set_visits
* [x] button to insert group names in empty groups
* [x] build "forgotten password modal"
* [x] complete mail-templates
    * [x] find images
    * [x] create headers
	* [x] admin_summary
    * [x] password_reset
    * [x] incomplete_profile
    * [x] confirm_visit
    * [x] changed_groups
    * [x] new_user_welcome
	* [ ] manager_mobilization
* [ ] Go through all TODO-tasks and complete them
* [x] use Slack to notify admin about errors and important events
* admin-mail:
    * [x] check for redudandant mail adresses
    * [x] check for visits-in-wrong-order
	* [x] check for files in temp-folder
	* [ ] notify of duplicate topics for single group (i.e. one group has Topic A twice)
	* [ ] get non-booked food or bus within X days

## Tests
* [ ] visual inspection of pages
* [ ] SMS content
* tables
	* [x] events end up in kalender.ics
	* adding rows
		* [x] required fields are set
		* [x] entities show up in database
	* [x] reordering of schools results in new VisitOrder
* admin-tools	
	* [x] update group counts for schools
	* [x] Add missing groups	
	* [x] assign visits to colleagues	
	* [ ] Add visit dates page
	* [ ] reorder visit order for topics
	* [ ] Bus booking page
	* [ ] Food ordering page
* cron-tasks
	* [x] run at right time
	* tasks
		* [x] calendar_rebuild
		* [x] backup
		* [x] visit_confirmation_message
		* [ ] admin_summary
			* [ ] wrong visit order
			* [ ] ...
		* [x] changed_group_leader_mail
		* [x] new_user_mail
		* [x] update_profile_reminder
		* [ ] table_cleanup

## Documentation
* classes
    * [ ] Naturskolan
    * [ ] Authorization
    * [ ] Update
	* [ ] Change
* concepts
	* [ ] How the cron tasks work
	* [ ] How the Auth-process works
	* [ ] How the calendar is generated
* routines
    * [x] Re-encoding the password-word-files
	
## Ideas
    * [ ] implement calendar-view for visits on group page using jquery ui datepicker option "beforeShowDay"
	* [ ] refactor js files into webpack-system
	* [ ] add a "notes-link" to the calendar
	* [x] build a page to combine bustrips with schools, using a multi-select
	* [x] rewrite table-settings as an external yaml-file
	* [ ] view logg on admin-page
	* [ ] Buttons "Copy to clipboard" and "Send mail" on bus_order and food_order pages.
	
## Issues
* [x] Istället för "några minuter sen" visas “Uppgifterna sparades senast Invalid date.” på skolsidan och liknande.
* [x] Debug cut-off menu
* [x] forgotten password mail has no FirstName and no working link to user area
* [x] direct-login-code in welcome mail does not work
* [x] dates in visits are saved with times instead of just dates
* [ ] confirm visit page has wrong return layout (json vs html)
* [ ] groups with no user show a false default value on group page. should be "Ingen" but is usually first person

* [ ] .
