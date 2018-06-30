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


  
