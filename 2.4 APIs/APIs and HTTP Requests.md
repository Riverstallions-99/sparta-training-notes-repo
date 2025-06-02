#RESTfulAPI [[RESTfulAPI]]

## API Fundamentals
What is an API?
- Application Programming Interface
- A mechanism that allows two computer programs to communicate with each other
- Provides service to access data, or request a certain action be taken

Why might DevOps Engineers need to use them?
- automate interactions with cloud services and infrastructure

RESTful services/APIs
- Representational State Transfer... Application Program Interface
- A way of implementing CRUD(Create, Read, Update, Delete)
- data represented as:
	- JSON
```JSON
{
	"customer" : {
		"ID" : 1,
		"firstname" : "becky",
		"lastname" : "white",
		"email" : "white.rebecca2012@gmail.com"
	}
}
```
	- XML
```xml
<customer>
	<ID>1</ID>
	<firstname>becky</firstname>
	<lastname>white</lastname>
	<email>white.rebecca2012@gmail.com</email>
</customer>

```
- Client-Server Architecture
- Cacheability
- Statelessness
- Layered System
- Uniform Interface

HTTP request structure
- Method is also known as the Verb.
![[Http_request_anatomy.cf4e63d8.png]]

HTTP response structure
- 
![[Http_response_anatomy.d3a140b3.png]]

Verbs
- HTTP actions:
	- POST
	- DELETE - 
	- GET - asking to retrieve a resource
	- PUT
	- PATCH

URI
http://ourservice/customer/1
http://ourservice/customer?id=1

Statelessness
- Once a response is sent, connection is no longer needed to function properly, so the connection can be severed
![[Pasted image 20250423122425.png]]

Caching
- Stores data for frequent use, to save time, saves data pulled from the server(eg images)
- Cookies stored locally with information about the user/user's machine
- 