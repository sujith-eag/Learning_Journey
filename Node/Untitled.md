
# Simple File Server

Bridging between file server and HTTP servers.

An HTTP server that provides remote access to files. Such a server has many use cases. It enables
web applications to store and share data, or it can give a group of people access to a set of files.

When we consider files as resources over the HTTP protocol, the make,
put, and delete methods can be used to read, write, and delete files. We
will interpret the path in the request as the path to the file.

```js
var http = require("http"), fs = require("fs");
var methods = Object.create(null);

http.createServer(function(request, response) {
	function respond(code, body, type) {
		if (!type) type = "text/plain";
		
		response.writeHead(code, {"Content-Type": type});
		
		if (body && body.pipe) 
			body.pipe(response);
		else
			response.end(body);
	}

	if (request.method in methods)
		methods[request.method](urlToPath(request.url), 
			respond, request);
	else
		respond(405, "Method " + request.method 
			+ " not allowed.");
}).listen(8000);
```

This code will launch the server returning 405 errors.
The response function is passed to functions that process various meth-
ods, and works as a callback to end the request. It accepts the HTTP status
code, the body, and possibly the content type. If the passed body is a read-
only stream, it will have a pipe method that is used to pass the read stream
to the write stream. If not, it is assumed that it is either null (the body
is empty), or a string, and then it is passed directly to the end response
method.


___

GET method so that it returns a list of files when
reading the directory, and the contents of the file when reading the file.
The question to fill in is what type of Content-Type header we should
return when reading the file. Since the file can have anything, the server
can’t just return the same type for everyone.

The mime module (file content type indicators like text/plain are also
called MIME types) knows the correct type for a huge number of file
extensions.
By running the following npm command in the directory where the
server script lives, you can use require (“mime”) to query the type library.
```
npm install mime
npm http GET https://registry.npmjs.org/mime
npm http 304 https://registry.npmjs.org/mime
mime@1.2.11 node_modules/mime
```

```js
methods.GET = function(path, respond) {
fs.stat(path, function(error, stats) {
if (error && error.code == "ENOENT")
respond(404, "File not found");
else if (error)
respond(500, error.toString());
else if (stats.isDirectory())
fs.readdir(path, function(error, files) {
if (error)
respond(500, error.toString());
else
respond(200, files.join("\n"));
});
else
respond(200, fs.createReadStream(path),
require("mime").lookup(path));
});
};
```

Since disk requests take time, fs.stat works asynchronously.

The stats object returned by fs.stat tells us everything about the file. For
example, size—file size, mtime-modification date. Here we need to find
out whether it is a directory or a regular file—the isDirectory method will
tell us this.

```js
methods.DELETE = function(path, respond) {
fs.stat(path, function(error, stats) {
if (error && error.code == "ENOENT")
respond(204);
else if (error)
respond(500, error.toString());
else if (stats.isDirectory())
fs.rmdir(path, respondErrorOrNothing(respond));
else
fs.unlink(path, respondErrorOrNothing(respond));
});
};
```

ou can say that when you try to delete
a non-existent file, since the file is no longer there, the request is already
executed. The HTTP standard encourages people to make idempotent
requests—that is, those in which repeated repetitions of the same action
do not lead to different results.
```
function respondErrorOrNothing(respond) {
return function(error) {
if (error)
respond(500, error.toString());
else
respond(204);
};
}
```

When the HTTP response contains no data, you can use the status code
204 (“no content”). Since we need to provide callback functions that
either report an error or return a 204 response in different situations,
I wrote a special respondErrorOrNothing function that creates such a
callback.

This is the PUT request handler:
```
methods.PUT = function(path, respond, request) {
var outStream = fs.createWriteStream(path);
outStream.on("error", function(error) {
respond(500, error.toString());
});
outStream.on("finish", function() {
respond(200);
});
request.pipe(outStream);
};

```

Here we do not need to check the existence of the file—if it exists, we will
simply overwrite it. Again, we use pipe to transfer data from a read stream
to a write stream, in our case, from a request to a file. If the thread cannot be
created, an “error” event is created, which we report in the response. When
the data is passed successfully, pipe will close both threads, which will trigger
the “finish” event. And after that, we can report success with the code 204.

The curl command-line utility, which is publicly available on unix sys-
tems, can be used to create HTTP requests. The following fragment tests
our server. The –X option is used to specify the request method, and –d is
used to include the request body.

```
curl http://localhost:8000/file.txt
File not found
curl -X PUT -d hello http://localhost:8000/file.txt
curl http://localhost:8000/file.txt
hello
curl -X DELETE http://localhost:8000/file.txt
curl http://localhost:8000/file.txt
File not found
```

Error Handling
There are six places in the file server code where we redirect exceptions
when we don’t know how to handle errors. Since exceptions are not passed automatically to callback functions, but are passed to them as arguments,
they must be handled individually each time. This negates the advantage
of exception handling, namely, the ability to centrally handle errors.

If we need to handle all the exceptions that occur
when processing the request, so that we accurately send the response, we
need to add try/catch blocks in each callback. This is not good 

Another approach is to use promises. They catch exceptions thrown
by callback functions and pass them as errors. In Node, you can load
the promise library and use it to handle asynchronous calls. Few Node
libraries integrate promises, but they are usually quite simple to wrap. The
excellent “promise” module with NPM contains a denodeify function that
takes an asynchronous function like fs.ReadFile and converts it to a func-
tion that returns a promise.

