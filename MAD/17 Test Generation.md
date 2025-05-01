
Systematic way to generate these tests

### API based testing

abstraction for system design
Standard representation for APIs
Open API, swagger etc

Swagger inspector, on giving api end point and requirements provides 

#### Use cases
Import API definition from standard like OpenAPI
General tests for specific endpoints, scenarios
Record API traffic
Inject possible problem cases based on known techniques
Data validation tests


Abstract tests
Semi verbal description: make a request to "/" endpoint, ensure that result contains text "hello"

Executable test
```
def test_hello(client):
	"""Verify home page."""

	rv = client.get('/')
	assert b'Hello' in rv.data
```


Model based testing

Authenticate user before showing information

Scenarios: 
user already logged in - page shown
user not yet logged in - redirect to login page
forgot password - after resetting, come back to desired page

Model:
Possible states (logged in, password reset, ...)
Possible transitions
generate tests for the possible transitions

This is another way of generating automatic test cases for based on this model based testing


Models and abstract tests
Abstract tests apply to generic models
create model for system under test
Drive "executable" tests by combining abstract test information with model



(G)UI testing
User interface : visual outputs


### Browser automation
Some test s cannot be directly run programmatically
browser is rewuired, just requests are not sufficient

Request generation: python requests library, capybara(ruby)

Direct browser automation: selenium framework - actually instantiates a browser


### Security testing

Generate invalid inputs to test app behaviour
Try to crash server - overload, injection etc
Black box or white box approaches 
Fuzzing or fuzz testing:
	generate large number of random / semi random inputs


