***REpresentational State Transfer*** - REST
	(Roy fielding, PhD thesis)

REST take into account the limitations of the web and provides guidelines or constraints
REST is a Software Architectural Style, not a set of rules.

The best way to understand REST is to understand the Constraints it imposes on the architecture.

#### Constraint 1: Client-Server
	Server: Stores data, Provides data on demand, May perform computation
	Network: Connects client to server, can be local
	Client: End user, Request data, Might not be human also

#### Constraint 2: Stateless
	Server cannot assume state of client
		Which page is looked at, is the data sent properly
		Is a request coming from an already logged in user
	Client cannot assume the state of the server
		Did the server reboot, is this the same server, how long has it been running

#### Constraint 3: Layered System
	(Load balancer - proxy frontend,  Authentication server,  Pool of backend)

#### Constraint 4: Cachebility
	Response directly from proxy cache without going to backend servers every time	
		
#### Constraint 5: Uniform Interface
	Client and Server interact in a uniform and predictable manner (same request same response)
	server exposes "resources" and standardized way of interacting with it.
	Hypertext / media used to convey the available resources and functionality -
	can be discovered by client through hypertext information from server

#### Constraint 6: Code on Demand
	Server can extend client functionality with Javascript




***REST means,***
state information between client and server explicitly transferred with every communication.

***Sequence***
Client accesses a Resource Identifier from server
	URI is a superset of URL, meaning URI is not all webpages, but other resource
	Typically starts from home page of application
	No initial state is assumed
Resource operation specified as part of access
	if HTTP, then GET, POST etc
	Not fundamentally tied to protocol
Server responds with new Resource identifier
	New state of system; new links to follow etc

State of interaction transferred back and forth


***HTTP***
One possible protocol to carry REST messages
use the HTTP verbs to indicate actions
standardized some types of functionality

GET: Retrieve representation of target resource's state
POST: Enclose data in request target resource "processes" it
PUT: Create a target resource with data enclosed
DELETE: Delete the target resource


***Idempotent operations***
Repeated application of the operation is not a problem 
	GET is safe as it is read only
	PUT will create the same resource, if it exists may give error
	DELETE can delete only once using same ID, wont change data
POST may not be Idempotent
	Adding comment to blog - repeat will cause multiple copies


REST != CRUD    but they work well together
CRUD refers to the basic database operations and 
REST is about the whole architecture of the web application

***Data Encoding***
Mostly HTML files are common to get from a web server, but REST is more about machine readable code which might not be seen by a human for state information.
For this HTML might not be the best way to do it,
HTML: for simple response
XML: Structured data response
JSON: Simpler form of structured data in text based format

***JSON***
JavaScript Object Notation
Serializes complex data structures like dictionaries and arrays.

***API Data transfer format***
Input to API is mostly in: text or HTML
Outputs will be some complex data types like - JSON, XML, YAML etc

These will be different from the internal server representation
Also different from final view presentation

YAML - Yet Another Markup Language (used for documentation and Configuration, metadata)

#  REST API's Examples
Wikipedia API's using curl
Testing some other API's


