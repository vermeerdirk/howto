
# Installing sqlite3 & bindings for nodejs v4.1.2 on rpi2 - raspbian jessie #

### Prerequisites: ###

Pi2 + raspbian jessie: release date 2015-09-24, kernel 4.1

	sudo apt-get update
	sudo apt-get upgrade

Nodejs v4.1.2

Login: pi

### Acquire sqlite3 ###

	sudo apt-get install sqlite3


### Install sqlite3 bindings globally for nodejs ###

I want it globally because I don't want to rebuild it everytime. Globally is usually intented for commandline stuff, so to use sqlite3 in projects, I will need link to the global path later on.
		

	npm install -g sqlite3
		#fallbacks to build, takes some time

### Sanity check

Go to a testfolder of your choice:

	cd /home/pi/Documents/Node\ Projects/
Create a testdatabase:

	sqlite3 test.db	
		create table test (data NVARCHAR(50));
		insert into test (data) values('a');
		insert into test (data) values('b');
		insert into test (data) values('c');
		select count(*) from test;
		.exit

Create a test node script:

	nano testsql.js

Make it look like this:

	console.log('require sqlite3');
	var sqlite3 = require('sqlite3').verbose();

	console.log('opening database');
	var db=new sqlite3.Database('test.db');

	console.log('executing select');

	db.get('select count(*) as count from test', 
  	function(err,row){

    	if (err) {  console.log('error');}
    	else {
    	  if (row) {
        	console.log(row.count);
      	}
    	}
  	}
	);

Make a package file: (optionally) 

	npm init
	
Link sqlite3 to it:

	npm link sqlite3

Finally:

	node testsql.js

Output:

	require sqlite3
	opening database
	executing select
	3


https://en.wikipedia.org/wiki/Victory_lap