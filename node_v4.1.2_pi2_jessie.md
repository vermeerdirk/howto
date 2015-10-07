
# Install nodejs v4.1.2 on rpi 2 - raspbian jessie #

### Prerequisites: ###

Pi2 + raspbian jessie: release date 2015-09-24, kernel 4.1

	sudo apt-get update
	sudo apt-get upgrade

Login: pi

 	
### Acquire nodejs distribution ###

Figure out latest arm build from nodejs.org server:
Browse to http://nodejs.org/dist
On october 10 2015: latest arm build: http://nodejs.org/dist/v4.1.2/

Make download folder

	cd /home/pi/Downloads
	mkdir node
	cd node

Download:

	wget http://nodejs.org/dist/v4.1.2/node-v4.1.2-linux-armv7l.tar.gz

### Unfold distribution ###

Unzip:

	tar xvzf node[tab]

Make target folder:

	sudo mkdir /opt/node

Juggle the files to target folder:

	sudo mv node[tab]/* /opt/node/

Delete download & unzip folder if you feel like it:

	cd ..
	rm node/ -R

Add node to PATH

	sudo nano /etc/profile

Edit profile so it resembles this:

    ...
	NODE_JS_HOME="/opt/node"
	PATH="$PATH:$NODE_JS_HOME/bin"
	export PATH
	...

Let's reboot.. needed? it should not hurt too much at this point.

	sudo reboot

Check versions:

	node -v
		v4.1.2
	npm -v
		2.14.4


### Does it blend? ###

Make a testfile:

	cd /home/pi/Documents
	mkdir Node\ Projects
	cd Node[tab]
	nano testnode.js

Make Testnode.js look like this:

	console.log('It blends...');

Blend it.

	node testnode.js

https://en.wikipedia.org/wiki/Ticker_tape_parade






 

 
