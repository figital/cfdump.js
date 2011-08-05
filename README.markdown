#cfdump.js

I use cfdump.js to dump my Javascript objects to the browser when using node.js ....

Usage:

https://gist.github.com/1126635

	// cfdump.js demo 
	
	var http = require('http');
	var dump = require('cfdump').dump;
	var port = 1337;
	var host = "localhost";
	var defaultMimeType = "text/html";
	
	function listener(request, response) {
		
		test = {
			port : port,
			host : host,
			listener : listener
		}	
		
		console.log('BEGIN ----------------------------');
		console.log('URI: ' + request.url);
		
		body = '<h3>Hello World</h3>';
		body += 'Dump test object:';
		body += dump(test);
		
		response.writeHead(200, {'Content-Type': defaultMimeType});
		
		response.end(body);
		
		console.log('END ------------------------------');
	
	}
	
	http.createServer(listener).listen(port, host);
	
	console.log('Server running at http://' + host + ':' + port);


That's about it.

Screenshot:

![Screenshot](http://farm7.static.flickr.com/6132/6010277380_b92499be70.jpg "Screenshot")

NOTE: actual function borks on plenty of objects. this is just a quick wrapper.