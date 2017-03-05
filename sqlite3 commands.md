# Do stuff in sqlite3

### Create empty database ###

	sqlite3 mynewdatabasefile.db

### Create table ###

	create table test (data NVARCHAR(50));
		
		insert into test (data) values('b');
		insert into test (data) values('c');
		select count(*) from test;
		.exit


	CREATE TABLE dailylog(
		logid INTEGER PRIMARY KEY, 
		name  TEXT, 
		date TEXT, 
		value REAL,
		volume INTEGER
		);



	 insert into dailylog(name, date, value, volume) values ('UMI', '2015-09-30 18:00:00.000', 34.48, 0);


### Datatypes ###
Only datatypes in sqlite:

	INTEGER, REAL, TEXT

Datetime format:

	TEXT: "YYYY-MM-DD HH:MM:SS.SSS"



### Insert data ###
Example 1

	insert into test (data) values('a');


Example 2

	insert into dailylog(
		name, 
		date, 
		open, 
		close, 
		volume,
		low,
		high)
		values(
	
		'SOL', 
		'2015-10-9 17:30:00.000',
		
		170456,

		);


### Scripting ###

 sqlite3 my.db < script.sql


### Useful commands ###

List all tables

	.tables
	.schema

Show 'columnnames'/headers in resultset in commandline:

	.headers on

Leave sqlite command shell when stuck (invalid command/syntax): 

	Ctrl + D

