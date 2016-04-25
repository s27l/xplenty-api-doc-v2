## Create Account Connection

### Description
Information about an existing connection. Xplenty provides tha following types of connections:

* **Database**:
  * [Bigquery](https://github.com/xplenty/xplenty-api-doc-v2/blob/master/resources/connections/bigquery-connection.md)
  * [Google Cloud SQL Database](https://github.com/xplenty/xplenty-api-doc-v2/blob/master/resources/connections/googlecloud.md)
  * [Hana](https://github.com/xplenty/xplenty-api-doc-v2/blob/master/resources/connections/hana-connection.md)
  * [Heroku](https://github.com/xplenty/xplenty-api-doc-v2/blob/master/resources/connections/heroku-connection.md)
  * [MongoDB](https://github.com/xplenty/xplenty-api-doc-v2/blob/master/resources/connections/mongo-connection.md)
  * [MySQL](https://github.com/xplenty/xplenty-api-doc-v2/blob/master/resources/connections/mysql-connection.md)
  * [PostgreSQL](https://github.com/xplenty/xplenty-api-doc-v2/blob/master/resources/connections/postgres-connection.md)
  * [Redshift](https://github.com/xplenty/xplenty-api-doc-v2/blob/master/resources/connections/redshift-connection.md)
  * [Redis](https://github.com/xplenty/xplenty-api-doc-v2/blob/master/resources/connections/redis-connection.md)
  * [Segment](https://github.com/xplenty/xplenty-api-doc-v2/blob/master/resources/connections/segment-connection.md)
  * [SQL Server](https://github.com/xplenty/xplenty-api-doc-v2/blob/master/resources/connections/sqlserver-connection.md)
* **Cloud Storage**:
  * [Bingads](https://github.com/xplenty/xplenty-api-doc-v2/blob/master/resources/connections/cloud_storage/bingads-connection.md)
  * [Google Storage](https://github.com/xplenty/xplenty-api-doc-v2/blob/master/resources/connections/cloud_storage/gs-connection.md)
  * [Google AdWords](https://github.com/xplenty/xplenty-api-doc-v2/blob/master/resources/connections/cloud_storage/adwords-connection.md)
  * [Google Analytics](https://github.com/xplenty/xplenty-api-doc-v2/blob/master/resources/connections/cloud_storage/analytics-connection.md)
  * [Hadoop Distributed File System](https://github.com/xplenty/xplenty-api-doc-v2/blob/master/resources/connections/cloud_storage/hdfs-connection.md)
  * [Rackspace](https://github.com/xplenty/xplenty-api-doc-v2/blob/master/resources/connections/cloud_storage/rackspace-connection.md)
  * [Amazon S3](https://github.com/xplenty/xplenty-api-doc-v2/blob/master/resources/connections/cloud_storage/s3-connection.md)
  * [Salesforce](https://github.com/xplenty/xplenty-api-doc-v2/blob/master/resources/connections/cloud_storage/salfesforce-connection.md)
  * [SSH File Transfer Protoco](https://github.com/xplenty/xplenty-api-doc-v2/blob/master/resources/connections/cloud_storage/sftp-connection.md)
  * [Softlayer](https://github.com/xplenty/xplenty-api-doc-v2/blob/master/resources/connections/cloud_storage/softlayer-connection.md)
  * [Swift](https://github.com/xplenty/xplenty-api-doc-v2/blob/master/resources/connections/cloud_storage/swift-connection.md)


### Input Parameters
The **connection type** and **connection ID** must be supplied at the end of the request URL.


### Request (Curl Call) Syntax
```shell
$ curl -X GET -u api_key: "https://api.xplenty.com/:account_id/api/connections/:type/:connection_id" \
  -H "Accept: application/vnd.xplenty+json, version=2"
```

### Response Example
```HTTP
HTTP/1.1 200 OK
```

```json
{
  "id":53,
  "name":"Amazon S3 sample connection",
  "unique_id":"S3_CONNECTION_53",
  "created_at":"2016-04-21T13:55:43Z",
  "updated_at":"2016-04-21T13:55:43Z",
  "type":"s3"
  "url":"https://api.xplenty.com/:account_id/api/connections/:type/:connection_id
}
```