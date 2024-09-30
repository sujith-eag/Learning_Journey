## Simplest server

A general web server will Listen on a fixed port
On the incoming requests, run some code and return a result
	Standard headers to be sent as part of result
	Output can be text or other format - MIME 


#### Setting up the server
```
while true; do
	echo -e "HTTP/1.1 200 OK\n\n $(date)" |
		nc -l localhost 1500;
done
```
Run a infinite loop,
`echo -e "HTTP/1.1 200 OK`   pass on this line as output, 200 is a HTTP status code
`\n\n $(date)" |`  leave a two line space, take the date and pipe it to next section

`nc` is net cat which  listening for signal at `localhost 1500`
This is the line that is maintaining the server, opening port 1500, listening and whatever input comes in it will be fed to `nc`
`nc` will take data from `echo` and send to those who sent the request.  No interpretation


#### Requesting data from server
```
curl http://localhost:1500

curl -v http://localhost:1500    (using -v verbose to get more information)
```
Here curl is taking care of the background work of sending the request

Typical request will be
```
Get / HTTP/1.1
Host: localhost: 1500
User-Agent: curl/7.64.1
Accept: */*
```

### Data sent and Received
```
*  Trying ::1 ...
* TCP_NODELAY set
* Connected to localhost (::1) port 1500 (#0)
> Get / HTTP/1.1
> User-Agent: curl/7.64.1
> Accept: */*
>
< HTTP/1.1 200 OK
* no chunk, no close, no size. Assume closr to signal end
< 
  Thu Jun 17 08:14:55 IST 2024
```

`*  Trying ::1 ...`   Is trying to connect to the local server, `::1` represents local host

`> Get / HTTP/1.1`  Get is request, / is saying what is needed and protocol is defined

`> Accept: */*` indicates the MIME types the client is willing to accept, this accepts anything

`> ` The empty line indicates the end of command

`< HTTP/1.1 200 OK`  is what was in the code so will be sent back respectively.
There will be a two line gap which indicated the beginning of data





### Another web server
`python3 -m http.server`
run,  take the module HTTP and run the function Server. 
A one line server that serve file from local folder

	Returned
`Serving HTTP on 0.0.0.0 port 8000 (http://0.0.0.0:8000/) ...`
The 0.0.0.0  is the local IP address, running on port 8000 which is default for python HTTP server

While the server is running it can serve the call
`curl -v http://localhost:8000` 

in a browser, if the folder running has html file, it can be accessed in 
`localhost:8000`
or `127.0.0.1:8000` 


### `ifconfig`
Running `ifconfig` in terminal returns the IP address of the local machine.
this IP address can be accessed from another machine


Using GET/
If there was a Index.html file in that directory, by convention it would be returned
The type of file and things will be mentioned so display can happen.





Modern Application Development #12sep2024