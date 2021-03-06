An Xplenty **user** represents an individual signed up to use the Xplenty platform.

### User Attributes

* **id** - the user's numeric identifier
* **name** - the full name of the user
* **email** - the email of the user (also used to login)
* **gravatar_email** - the user's gravatar email
* **avatar_url** - the url for the user's avatar
* **time_zone** - the user's time zone
* **time_zone_info** - the user's time zone info
  * **name** - the user's time zone name
  * **identifier** -  the user's time zone IANA identifier (e.g. Etc/UTC)
  * **offset** - the user's time zone offset without colon (e.g. +0600)
* **location** - the user's location
* **confirmed** - indicates if the user is confirmed
* **confirmed_at** - confirmation date and time
* **notifications_count** - user's notifications count
* **unread_notifications_count** - user's unread notifications count
* **notification_settings** - user's notification settings
* **receive_newsletter** - indicates if user subscribed to recieve newsletter
* **created_at** - the date and time the user was created
* **updated_at** - the date and time the user was last updated
* **api_key** - the user's api authentication key. Returned in response only if user provided password in input parameters.
* **url** the user resource URL

