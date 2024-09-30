All about taking actions, manipulating

Takes action in response to the user input
Communicates with the model, extracts the view

Originally designed fro GUI applications
Model and View are connected through the controller
State of interaction is maintained as part of overall system memory
(the present condition and what is possible and not possible)


Within the web,
Server does not and cannot maintain the state of the client, Both are in different machines.
Client is pure front-end user
So some of the analogies break down hence many variants of MVC


MVC is a good conceptual framework to understand separation of concerns but 
breaks down if applied too rigidly



# Request - Response

Clicking a link used to mean getting to a new page, that has changed with dynamic websites.  Clicking a link triggers a different behaviors and links clickable have various options.

Web is based completely on requests from user and responses from servers
Basic requests: clicking on link/URL   is HTTP GET
More complex requests like form submission is  HTTP POST

Constraints
Are there common threads that can be utilized in something new
Common Operations, essential functions can be distilled

# CRUD

Create   Read   Update  Delete
A life cycle of data models, is defined in context of Database operations

Database is optimized for various combinations of operations
	Read-heavy: lots of reading, very little writing or creating
	Write-heavy: security archive logs


# API
Application Programming Interface is a standard way to communicate with a server.
Client only needs to know API - not how the server implements the database.

CRUD is a good set of functionality for a basic API, dealing with life cycle of data
	usually considered the first level API to implement a web application




# Controllers
Actions are interactions between view and model
A set or group of actions together logically, that performs a process
Lots of controllers grouped together with complex set of capabilities forms the API

For web apps, all these interactions will happen through HTTP requests
HTTP verbs are used to convey meanings (GET, PUT, POST...)


***Rules of thumb***
Should be able to change the **View** without the **Model** ever knowing
Should be possible to change underlying storage model without views ever knowing
Controllers/Actions should generally Never talk to a database directly(No SQL query inside a controller)  only the model should interact with Database

Views and Controllers tend to be more closely inter liked than with models. 



# Routes and controllers

Web applications follow a ***Client-Server*** model and it is stateless 
> Stateless: Server does not know the present state of the client. Must be ready to respond to whatever the client requests without assuming anything about the client.
    (Even if there was a crash, form filled halfway, it should be able to recover cleanly )

Requests are sent through HTTP protocol
	Use variants of GET, POST (verbs) to convey the ***Meaning***
	Use URL (Uniform Resource Locator) structure to convey ***Context***

> Routing: mapping URLs to actions


#### Python Decorators
Adding extra functionality on top of a function
`@` -decorators before function name
It is basically a function of a function
	It takes the inner function as the argument 
	returns a function that does something before calling the inner function

### ***A basic routing in Flask***
```python
from flask import Flask
app = Flask(__name__)

@app.route("/")
def home():
	return "Hello"
```
The `"/"` within the decorator is now mapped to the function below it. 
calling / in turn calls function home()
Suppose 
	request is "GET / "
	response will be  " invoke home() and return the result "


If there is a request to " / " with a particular verb " GET " then call the function " index( ) ".
	/  with Post will not return anything, so have to be specific
```python
@app.route('/', method=['GET'])
def index():
	.....

@app.route('/create', method=['POST'])
def store():
	....
```

### CRUD like functionality
calling the function after they have already been defined.
index, store, etc are functions already defined.
The flask app creates mapping between call and functions
```python
@app.route('/', method=['GET']) (index)
@app.route('/create', method=['POST']) (store)
@app.route('/<int:user_id>', method=['GET']) (show)
@app.route('/<int:user_id>/edit', method=['POST']) (update)
@app.route('/<int:user_id>', method=['DELETE']) (destroy)
```

`'/<int:user_id>', method=['GET']) (show)`
if what follows / is an integer, then treat it as an user_id,
if the verb/method is GET, then call show() with user_id as argument




Flask is not natively MVC
Simple URL routing and has helpers to do large scale routing of common functions

But MVC is more a way of thought than a framework
Structuring the application with separation of concerns in mind where
the data models are kept separate from the data view so the communication between the two happens through Explicitly defined controllers, which prevents unnecessary modification.   So a clean design is achieved.





