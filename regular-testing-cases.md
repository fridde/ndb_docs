# Sending request to Ngrok

1. Move into the folder ```scripts\ngrok```
2. Start ngrok with "ngrok http 80", using cmd
2. Note the adress
3. Go to www.hurl.it
4. Use Destination: POST and http://123abc.ngrok.io/naturskolan_database/sms/update_received_sms where you exchange "123abc" for right adress that you can see in the command line
5. Add a header with name "Content-Type" and value "application/x-www-form-urlencoded" or "application/json"
6. Add the body below or some other body
7. At the end of the url, add "?XDEBUG_SESSION_START=api"
8. Alternatively, or just to be sure, add the header with name "Cookie" and value "XDEBUG_SESSION=xdebug.api" to the request

## Body for sms testing
id=33185988&device_id=42912&message=jajamensann&status=received&send_at=0&queued_at=0&sent_at=0&delivered_at=0&expires_at=0&canceled_at=0&failed_at=0&received_at=1489061891&error=N%2FA&created_at=1489061891&contact%5Bid%5D=3678507&contact%5Bname%5D=%2B46703730778&contact%5Bnumber%5D=%2B46703730778&event=Received&secret=

## Updated groups for user
 - Destination: http://123abc.ngrok.io/naturskolan_database/mail/changed_groups_for_user
 - Body: {"receiver":"vivan.nyberg@example.net","data":{"groups":{"new":[],"removed":[1],"rest":[2]},"user_fname":"Konrad","school_url":"localhost\/naturskolan_database\/skola\/gala"},"api_key":"esGWU1pDAONX5IdK","XDEBUG_SESSION_START":"api"}

## Test cases
(X depends on settings)
- user without cookie visits school page. gets prompted
- user with cookie, but no hash visits school page. gets prompted
- user enters wrong password. gets notified and prompted
- user enters right password. enters school page.
- user changes any parameter of group. appropriate database value changes
- user changes any field on team page. appropriate database value changes.
- user changes data subscribed to by EntitySubscriber: change is created in table
- if unprocessed change exists: next calendar_rebuild is executed
- user creates a new row on team page. changes one of the values. new user appears in database.
- user with correct cookie value visits school page. sees page.
- user A adds a new user B into skola/{school_id}/team. User B gets notified within X hours.
- user has insufficient contact data (mail/mobile). Gets notified within X hours.
- user has "gained" or "lost" responsibility over a group. Gets notified within x hours.
- group has appointed visit within X days. associated user (=group leader) gets notified via mail
- group has appointed visit within X days *and* associated user has not confirmed visit *and* X hours have elapsed since last message (mail or sms). User gets notified via sms.

### Checks to perform
- chron task advances timer according to expections
- timer is reset once every week
- admin summary matches expectations and is correct
  - food changed within X days
  - info changed within X days
  - number of students changed within X days
  - inactive group visits
  - bus order is outdated
  - food order is outdated
  - unconfirmed visit within X days
  - school has wrong amount of groups active
  - non-standard user (admin etc) is group leader
  - number of students is out of bounds  
- 
