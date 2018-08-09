# Re-encrypting the word files

If you feel unsure about the security of the word-files or it has been more than a year since last re-encryption, run 
    
	http://localhost/naturskolan_database/misc/scripts/encrypt_word_files.php
	
on localhost. This opens each word file found in config/words/ , de-encrypts the content using the current key found in ```.key``` and encrypts these files directly with a new random key and saves them afterwards. That new key is saved again in ```.key```

Afterwards, run the deploy script again to update the ```.key``` file and word files on the production server.

# Initializing passwords at first upload

## Creating an AuthKey if there is none

Run

    sigtunanaturskola.se/ndb/task/createNewAuthKey
	
in your browser and check that the result on the page says *Find the AuthKey in /temp/auth_key*  .

Use Filezilla or some other method to open the file ```auth_key``` on the remote server. Copy the key to some place safe (locally) and delete the file afterwards.

## Create passwords

To create new passwords (if there are none) run

    sigtunanaturskola.se/ndb/task/createNewPasswords/<<AuthKey>>
	
in your browser where you exchange ```<<AuthKey>>``` with the actual AuthKey you stored somewhere safe before.

This will go through all the schools and will check if for each school there is a hash stored in the SQL table "hashes" that expires *after half a year from now* (actually half of the *password validity duration* given in the settings)

**If not**, a new password and corresponding hash are created. The hash is saved in the SQL table "hashes" and the password is saved in ````/temp/``` as ```new_<<date>>``` where <<date>> corresponds to the current time and date.

Using your ftp tool of choice, copy this file to somewhere safe (locally) and then remove it from the server. A good idea is to rename the local copy to something more recognizable.

Now try to navigate to 

    sigtunanaturskola.se/ndb/skola/natu
	
and log in with the password given in the file mentioned above.