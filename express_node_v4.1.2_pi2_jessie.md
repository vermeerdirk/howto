
# Install express (nodejs) on pi2 - raspbian jessie #

### Prerequisites: ###

Pi2 + raspbian jessie: release date 2015-09-24, kernel 4.1

	sudo apt-get update
	sudo apt-get upgrade

Nodejs v4.1.2

Login: pi

### Install express globally for nodejs ###

I want it globally because I don't want to rebuild it everytime. Globally is usually intented for commandline stuff, so to use express in projects, I will need link to the global path later on.

October 8 2015: will install express version 4.13.3

	npm install -g express
		
### Sanity check

Go to a testfolder of your choice:

	cd /home/pi/Documents/Node\ Projects/

Link express to the testfolder:

	npm link express

Create a test node script:

	nano testexpress.js

Make it look like this:

	var express = require('express');
	var app = express();
		
	app.get('/', function(req, res){
 		res.send('Hello World!');
	});

	app.listen(9999);

	console.log('Express server listening on 9999');

Finally:

	node testexpress.js

Use brower and go to:

	http://<rpi2 ipnr>:9999

Output:

	Hello World!


https://en.wikipedia.org/wiki/World
