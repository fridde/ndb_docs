# Kvar att göra
* [x] implement welcome_new_user notification
* [x] enable group name change
* [x] implement batch-adding visits
* [x] build batchSetGroupCount Form
* [x] create navigation menus
* [x] fix datepicker on table visits
* [x] protect update from request forgery by introducing session variables
* document 
    * [ ] Naturskolan.php
    * [ ] PasswordHandler.php
    * [ ] Update.php
* create Kontrollcenter with Buttons
    * [ ] createMissingGroups: Response needed
    * [x] enable/disable cron tasks
* tests
    * [ ] SMS content
	* tables
	    * [ ] events end up in kalender.ics
		* [ ]
* test cron-tasks
    * [x] fire at right time
    * [ ] have right outputs (mails/sms/changed values)
    * tasks
        * [x] calendar_rebuild
        * [ ] backup
        * [x] visit_confirmation_message
        * [x] admin_summary
        * [x] changed_group_leader_mail
        * [x] new_user_mail
        * [x] update_profile_reminder
        * [ ] table_cleanup
* [x] create index page
* [x] create page to set bus&food-confirmation status
* [x] create colleague assignment page
* [x] add custom calendar events form
* [ ] add responses for admin actions (pop up etc)
* [ ] layout pages
* [ ] insert loggers
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
	
* IDEAS
    * [ ] implement calendar-view for visits on group page using jquery ui datepicker option "beforeShowDay"
	* [ ] add a "notes-link" to the calendar
	* [ ] build a page to combine bustrips with schools, using a multi-select
	
# Issues
* [x] Istället för "några minuter sen" visas “Uppgifterna sparades senast Invalid date.” på skolsidan och liknande.
* [x] validate dates from add_dates_to_topic
* [x] Debug "forgot password"
* [x] Debug cut-off menu
