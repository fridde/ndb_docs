# Left to do
* [x] implement welcome_new_user notification
* [x] enable group name change
* [x] implement batch-adding visits
* [x] build batchSetGroupCount Form
* [x] create navigation menus
* [x] fix datepicker on table visits
* [x] protect update from request forgery by introducing session variables
* [ ] add responses for admin actions (pop up etc)

* create Kontrollcenter with Buttons
    * [x] enable/disable cron tasks
* [x] create index page
* [x] create page to set bus&food-confirmation status
* [x] create colleague assignment page
* [x] add custom calendar events form
* [ ] add 404 and 500 with smart error handling

* layout pages
	* [ ] width in tables does not exceed page width
	* positioning of elements on admin pages
		* [ ] set_visits
* [ ] insert loggers to crucial functions
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
* [ ] use Slack to notify admin about errors and interesting events

* admin-mail:
    * [x] check for redudandant mail adresses
    * [x] check for visits-in-wrong-order

## Tests

* [ ] visual inspection of pages
* [ ] SMS content
* tables
	* [ ] events end up in kalender.ics
	* adding rows
		* [ ] required fields are set
		* [ ] entities show up in database
	* [ ] reordering of schools results in new VisitOrder
	* [ ] reordering of topics results in new VisitOrder
* admin-tools
	
	* [ ] Add missing groups
	* [ ] Fill empty group names
	* [ ] assign visits to colleagues
	* [ ] Bus/Food Booking page
	* [ ] Add visit dates page
	* [ ] update group counts for schools
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
* concepts
	* [ ] How the cron tasks work
	
## IDEAS
    * [ ] implement calendar-view for visits on group page using jquery ui datepicker option "beforeShowDay"
	* [ ] add a "notes-link" to the calendar
	* [ ] build a page to combine bustrips with schools, using a multi-select
	* [ ] rewrite table-settings as an external yaml-file
	* [ ] view logg on admin-page
	* [ ] Buttons "Copy to clipboard" and "Send mail" on bus_order and food_order pages.
	
## Issues
* [x] Istället för "några minuter sen" visas “Uppgifterna sparades senast Invalid date.” på skolsidan och liknande.
* [x] validate dates from add_dates_to_topic
* [x] Debug "forgot password"
* [x] Debug cut-off menu

* [ ] .
