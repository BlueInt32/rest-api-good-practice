## ASP.NET Web API - Good practice

### REST
REST stands for **Re**presentational **S**tate **T**ransfer. It is an architectural style for network applications.

By nature it is :
* Simple
* Lightweight
* Stateless : the server does not persist any client related state
	-> survive server restarts
	-> no client to server binding, the request can be handled by a cluster of servers
	-> the server scales easier, by not dealing with multiple session memory management 
* Cacheable

Most of the time it relies on the HTTP protocol.

REST does not offer built-in security features, encryption, session managemeent, QoS guarantee, but those services can be added on top of HTTP.

The World Wide Web can be seen as a big RESt architecture.

Note : using HTTP cookies is not considered a good REST practice because it persists an application state on the client, whereas in good REST design, each operation carries all the information needed.

#### Simplicity
Getting a product Ref detail using a SOAP web service, we would probably have a request with a fixed URL and a body such as
	
	<?xml version="1.0"?>
	<soap:Envelope xmlns:soap="http://www.w3.org/2001/12/soap-envelope"
		soap:encodingStyle="http://www.w3.org/2001/12/soap-encoding">
		<soap:body pb="http://www.acme.com/phonebook">
			<pb:GetUserDetails>
				<pb:UserID>12345</pb:UserID>
			</pb:GetUserDetails>
		</soap:body>
	</soap:Envelope>

In a RESTful application, the query would consist only in an url
 
> http://localhost/transparency/api/productrefs/12345


The result would be sent directly in the response body, not embedded inside anything. This means you can test REST services directly using a browser (at least for GET resources) and an network connection.

The convention in REST is to provide access to resources, this leads to  designs based on *nouns* instead of *actions*.
Therefore, it is prefered to use

> /api/productrefs/12345

instead of 

> api/getproductref/12345

Rest is to SOAP what a postcard is to a letter.

#### Consistency


#### Self documentary

#### the N+1 selects issue
http://stackoverflow.com/questions/97197/what-is-the-n1-selects-issue

#### Security of REST 
http://stackoverflow.com/questions/454355/security-of-rest-authentication-schemes


#### Server response
REST is not bound to any description langage. A RESTful service can return XML, Json, CSV...


#### Guidelines
- URLS should be logical, not physical
- lists should always been paginated
- the result of the API must be well documented and stick to the documentation. Changing the API should be made in coordination with the clients.
- good design is supposed to contain hypermedia links to related resources. For example in a list of products, each product should have a link pointing to its detail URL.
- GET should never cause a state change


#### Documenting the API :
Swagger

### Bibliography 
* Learn REST : A Tutorial (a tad old)

	-> http://rest.elkstein.org/2008/02/what-is-rest.html
* Best Practices for Designing a Pragmatic RESTful API

	-> http://www.vinaysahni.com/best-practices-for-a-pragmatic-restful-api
	
	
	
	