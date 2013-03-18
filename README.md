## Introduction

The Xplenty API provides functions for controlling and monitoring Xplenty clusters and jobs.
After defining an Xplenty data processing package using the Xplenty web application, you can call the Xplenty API to create Hadoop clusters, run jobs, monitor their progress, and terminate jobs and clusters.

You can choose to use the [Xplenty REST API](https://github.com/xplenty/xplenty-api-doc/blob/master/README.md#XplentyAPI), or one of its wrappers: the [Java wrapper](https://github.com/xplenty/xplentydoc/wiki/Xplenty-Java-Wrapper) or the [Python wrapper](https://github.com/xplenty/xplentydoc/wiki/Xplenty-Python-Wrapper).

## Getting Started

For a quick overview of how to get started with the Xplenty REST API, you can read:
* [Xplenty Control and Monitoring Tasks](https://github.com/xplenty/xplenty-api-doc/blob/master/sections/Xplenty%20Control%20and%20Monitoring%20Tasks.md)
* [Xplenty Typical Workflow](https://github.com/xplenty/xplenty-api-doc/blob/master/sections/Xplenty%20Typical%20Workflow.md)

## Xplenty Terms

Here are some of the terms you will encounter in the Xplenty API documentation.

### Package

An Xplenty **package** is a data flow definition that you define in the Xplenty web application. 
It describes the data to process (location, schema, fields), data manipulation to perform, and the output destinations (location, schema). The package's workflow is implemented by jobs.

An Xplenty package is a data flow definition that you define in the Xplenty web application. 

### Job
An Xplenty **job** is a process that is responsible for performing a data flow according to a specific package on a Hadoop cluster. The job is a batch process that runs on a finite amount of data and then terminates. Several jobs can run the same package simultaneously.
When you call the Xplenty API to run a new job, you supply the name of the package whose workflow the job should perform, and the cluster on which to run.

### Cluster and Cluster Plan

An Xplenty **cluster** is a Hadoop cluster - a group of machines (nodes) that that is allocated exclusively to your account's users. You can create one or more clusters, and you can run one or more jobs on each cluster. A cluster that you've created remains allocated to your account until you request to terminate the cluster.

A **cluster plan** is a definition of a cluster type, which includes the number of nodes in the cluster and its pricing. Cluster plan details can be viewed in the Xplenty web application. When you create a new cluster, you specify its cluster plan. You  may choose different cluster plans for different types of jobs and packages, depending on the computing power you require.

### Account and User
An Xplenty **account** represents a related group (usually a company) of Xplenty **users**.
An account is created when the user signs up to use the Xplenty service, and an API key is generated for the account, which must be supplied when calling the Xplenty API.

## REST Interface Specifications

### Using the Xplenty REST API

The Xplenty REST API conforms to the design principles of [Representational State Transfer (REST)](http://en.wikipedia.org/wiki/Representational_State_Transfer).

To get a quick start with the Xplenty API, we recommend using the [curl](http://curl.haxx.se) command-line utility.

All URLs start with: 
    https://api.xplenty.com/{account_id}/api/

Parameter values should be converted to UTF-8 and [URL encoded](http://en.wikipedia.org/wiki/Percent_encoding).

All Xplenty APIs support jsonp, which is the json format with a callback specified, such as:

    callback=callback_method

All date parameters will be treated as UTC and their formats must be in ISO 8601 format: 

    YYYY-MM-DDTHH:MM:SSZ

All published date and time objects are UTC based and returned in ISO 8601 format:

    YYYY-MM-DDTHH:MM:SSZ

### Mime Types

The API presently supports the [JSON](http://en.wikipedia.org/wiki/Json) format only.
Specify a custom mime type in the [Accept] header as follows:

    application/vnd.xplenty+json

Unless you specify a version, the latest representation of resources will always be returned in the response. If you’re building an application and want to ensure a consistent response format, specify a version as follows:

    application/vnd.xplenty+json; version=1


### CORS (Cross Origin Resource Sharing)

The Xplenty API supports Cross Origin Resource Sharing.

You can read the [CORS W3C working draft](http://www.w3.org/TR/cors), or [this introduction](http://www.w3.org/TR/cors) from the HTML 5 Security Guide.

The latest version of the Xplenty API (V1) supports CORS requests from any domain.

### Response Codes and Error Messages

**HTTP Status Codes**

These are the HTTP status codes that the Xplenty API can return:
 
* **200 OK**: Request succeeded.
* **201 Created**: The requested resource was created successfully.
* **304 Not Modified**: There was no new data to return.
* **400 Bad Request**: The request was invalid.  An accompanying error message will explain why.
* **401 Unauthorized**: You are attempting to access the API with invalid credentials.
* **402 Payment Required**: You must confirm your billing info to use this API.
* **403 Forbidden**: The request has been refused.  An accompanying error message will explain why.
* **404 Not Found**: The URI requested is invalid or the resource requested does not exist.
* **406 Not Acceptable**: The requested mime-type is not acceptable.
* **415 Unsupported Media Type**: The specified media type is not supported.
* **422 Unprocessable Entity**: You have sent invalid fields.
* **429 Too Many Requests**: The request exceeded the rate limitations.
* **500 Internal Server Error**: An internal error occurred in the service. 
* **502 Bad Gateway**: Xplenty is down or being upgraded.
* **503 Service Unavailable**: The Xplenty servers are up, but overloaded with requests. Try again later.

**Error Responses**

When the API returns an error messages, it does so in your requested format. For example, an error from a JSON method might look like this:

    {"message":"Item not found."}

## Security

### Encrypted Communication (SSL)

Xplenty provides all REST API methods over SSL. Whenever your code might be operating on a non-secure network (that is, if you're developing a client application), please make use of SSL for all authenticated or sensitive requests. For example, requesting cluster information should be performed by an Xplenty client over SSL. Service-to-service communication may not benefit from SSL if you trust your hosting provider (or if you are your own hosting provider).

### Authentication
Most of the Xplenty API calls require authentication, supplied in the form of the API key which is generated for each account.

Once you have an API key, you can either attach it to each request as a "key" parameter, or use HTTP Basic Authentication with a blank username and the API key as a password. Here's an example using curl (the colon separates the username and password):

    curl -H "Accept: application/vnd.xplenty+json" -u apikeyhere: https://api.xplenty.com/clusters

## Xplenty REST API

<a id="XplentyAPI">
### Xplenty API Methods
</a>
These are the methods supported by the Xplenty API:

* [List Cluster Plans](https://github.com/xplenty/xplentydoc/wiki/List-Cluster-Plans)
* [Create Cluster](https://github.com/xplenty/xplentydoc/wiki/Create-Cluster)
* [List Clusters](https://github.com/xplenty/xplentydoc/wiki/List-Clusters)
* [Get Cluster Information](https://github.com/xplenty/xplentydoc/wiki/Get-Cluster-Information)
* [Terminate Cluster](https://github.com/xplenty/xplentydoc/wiki/Terminate-Cluster)
* [Run Job](https://github.com/xplenty/xplentydoc/wiki/Run-Job)
* [List Jobs](https://github.com/xplenty/xplentydoc/wiki/List-Jobs)
* [Get Job Information](https://github.com/xplenty/xplentydoc/wiki/Get-Job-Information)
* [Terminate Job](https://github.com/xplenty/xplentydoc/wiki/Terminate-Job)

### Collection Resources And Pagination
The response to a GET request for collection resources (e.g. /clusters) may not return all the objects in the collection, depending on how many there are. To query collection resources incrementally, use the following parameters:

* **offset** - the index of the first object to retrieve, starting from 0
* **limit** - the number of items to return (default is 20, maximum is 100)

Responses to GET requests for collection resources provide information about the total object count available and the offset/limit used for the response, so that you know how many more requests are needed to retrieve the complete list of collection resources.

Alternatively, you can use the **page** parameter, instead of **offset**, as follows:

* **page** - the index of the page to retrieve, starting from 1. A page is a list of collection items, whose length is determined by the "limit" parameter.
* **limit** - the number of items to return (default is 20, maximum is 100)

The pagination info is included in the [Link header](http://www.w3.org/Protocols/9707-link-header.html).

## Rate Limits

The Xplenty API only allows clients to make a limited number of calls in a given hour. It uses a credit allocation system to ensure fair distribution of capacity. Each user is allocated 5,000 credits per hour. This is keyed off either your login or the request IP. If you exceed this limit, you'll get a "429 Too Many Requests" response for subsequent requests.

All Xplenty API methods are rate-limited except for querying the rate limit.
You can check your rate limit status without incurring an API hit, as follows:

    GET /rate_limit_status

Every time you call the API, the current rate status will be returned in the response under the following headers:

<table>
<tr><td><b>HTTP Header</b></td><td><b>Description</b></td></tr>
<tr><td>X-RateLimit-Limit</td><td>Total credits allocated</td></tr>
<tr><td>X-RateLimit-Remaining</td><td>Total credits available</td></tr>
</table>

### Cost of API calls
Unless otherwise noted, an API call deducts 1 credit from your allocation. 

### Errors

**429 Too Many Requests (Rate Limit Exceeded)**

When a client exceeds the allocated rate limit, the Xplenty API returns a "429 Too Many Requests" response with an associated "Rate Limit Exceeded" message as the error description.

### Whitelisting
Xplenty REST API whitelisting is not supported.

### Blacklisting
We ask that you honor the rate limit. If your application abuses the rate limit your user will be blacklisted, and you will be unable to get a response from the Xplenty API.

If your user has been blacklisted and you think there has been an error, you can contact the email address on the API support page. So we can get you back online quickly, please include the following information:

1. If you are using the REST API, make a call to the /rate_limit_status from the computer which is blacklisted and include the response in your email.
2. Explain why you think your application was blacklisted.
3. Describe in detail how you have fixed the problem that you think caused you to be blacklisted.

## Terms of Service

Please refer to our [Terms of Service](http://www.xplenty.com/tos) page.

## References

[REpresentational State Transfer (REST)](http://en.wikipedia.org/wiki/Representational_State_Transfer)

[Cross-Origin Resource Sharing](http://en.wikipedia.org/wiki/Cross-Origin_Resource_Sharing)