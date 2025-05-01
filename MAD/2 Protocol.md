```
TCP  Transfer Control protocol
BGP  Border gateway protocol
UDP  
IP   Internet protocol
SMTP 
HTTP Hypertext transfer protocol
```


Protocols are Agreeing on how to talk to each other and how they communicate

Server expects "requests"
	Nature of requests 
	Nature of client
	Type of results client can deal with

Client expects "responses"
	Ask server for something
	convey what you can accept
	read result and process


Primarily text based:
Requests specified as "GET", "POST", "PUT" etc
	Headers used to convey acceptable response types, languages, encoding
	Which host to connect to (if multiple hosts on single server)
Response headers
	convey message type, data
	cache information
	status code: 404 not found


### Use cases
GET:  simple requests, search queries etc
POST: sending more complex form of data, large text blocks, file uploads
PUT/DELETE/...  various other exist as standard part of HTTP protocol

These are extensively used in Web 2.0 and form the basis of most APIs like REST, CRUD


## Performance of a Website
**Latency**
The amount of time it takes to get response.
Even with speed of light, for a to and fro between data center 200 km away, 
its only 50 requests/second

**Response size**
Response = 1 kb of text(headers, HTML, CSS, JS)
If server has 100 Mbps connection also,  its about 10,000 requests/second

**Memory**
Multiple parallel requests: multiple processes

**Storage**
**Retrieval**




#12sep2024 