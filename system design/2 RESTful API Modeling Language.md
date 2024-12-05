### RESTful API Modeling Language
- Writing API's before implementing it in a way to verify it from architects 
- Describes API in human readable format

Instance taken from Bank API's
#### Root
- the root of the API where we define protocol, media type, title, baseUri used
```
#%RAML 1.0
title: Open Banking API
version: v1
baseUri: http://api.openbanking.com/{version}

protocols:
	- HTTP
	- HTTPS

mediaType:
	- application/json
	- application/xml
```
#### Resources
```
/accounts:
	/{accountId}:
		/balances:
		/transactions:
			{transactionId}:
```
- resource name needs to be plural and also, it should be a noun not a verb
- resources enclosed in curly braces is an uri parameter. URI paramter (Path Param) is basically used to identify a specific resource or resources
- resource begin with '/'

#### Methods
set as per the use case
- **GET:** Fetch the information from the server
- **POST:** Create the resources on the server
- **DELETE:** Remove the resources from the server
- **PUT:** Create or update the new or existing resources on server
- **PATCH:** Modify the resources on the server

```
/accounts:
	get:
	post:
	/{accountId}:
		get:
		/balances:
			get:
		/transactions:
			{transactionId}:
				get:
```
#### Defining header and query parameters
- query parameter use to filter or sort the resources. passed in the URI as a query string in key-value form

Example Usecase:
We need to fetch all accounts for particular customers. In this case, we will be using customerId as header parameter for fetching account details for particular customers. We would have been using customerId as a query parameter but it is sensitive information so we can pass it in the header.

```
/accounts:
	get:
		headers: 
			customerId:
				required: true
				type: string
				example: "323232"
				maxLength: 20
	post:
	/{accountId}:
		get:
		/balances:
			get:
		/transactions:
			{transactionId}:
				get:
					queryParamters:
						fromTransactionDate:
							type: date-only
							example: "2021-08-01"
							required: false
						toTransactionDate:
							type: date-only
							example: "2021-08-20"
							required: false
```
#### Request and Responses






https://blogs.mulesoft.com/dev-guides/api-design/restful-api-modeling-language-101/