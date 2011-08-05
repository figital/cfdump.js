#cfdump.js

I use cfdump.js to dump my Javascript objects to the browser when using node.js ....

![Screenshot](http://farm7.static.flickr.com/6132/6010277380_b92499be70.jpg "Screenshot")

Usage:

<script src="https://gist.github.com/1126635.js?file=cfdump-demo.js"></script>

https://gist.github.com/1126635

```
	// cfdump.js demo 
	
	var http = require('http');
	var dump = require('cfdump').dump;
	var port = 1337;
	var host = "localhost";
	
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
		
		response.writeHead(200, {'Content-Type': 'text/html'});
		
		response.end(body);
		
		console.log('END ------------------------------');
	
	}
	
	http.createServer(listener).listen(port, host);
	
	console.log('Server running at http://' + host + ':' + port);
```

That's about it.

NOTE: Actual function borks on plenty of objects. This is just a quick wrapper. The client-side CSS, etc is probably from 2003.