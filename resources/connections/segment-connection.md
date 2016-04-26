### Segment database Connection Attributes

* **id** - the connection's numeric identifier
* **type** - `segment`
* **name** - the descriptive name given to the connection
* **username** - the database user name
* **password** - the database user password
* **unique_id** - the unique connection's identifier
* **created_at** - the date and time the connection was created
* **updated_at** - the date and time the connection was last updated
* **database** - the name of database to use
* **host** - the name of the host to connect to
* **port** - the TCP Port to connect to. The default is 5439
* **tunnel_type** - the method to use for accessing the database. Possible values: **direct**, **reverse**
* **ssl** - determines whether to connect to the database using SSL
* **region** - the geographical location of your Segment cluster
* **url** - the connection resource URL (API)