# Rerouting ports with iptables #
10/7/2015

### Set iptables prerouting ###
Reroute port 4000 to 7000:

	
	sudo iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 4000 -j REDIRECT --to-port 7000

	#see current iptables nat rules
	sudo iptables -t nat -L -n -v


### Make it stick so it will still work when rebooting ###
Installing iptables-persistent will allow you to also save current rules.

	#make persistent
	sudo apt-get install iptables-persistent
	

### Save additional changes again ###

 this works for saving changes if iptables-persistent is already installed: (v 1.0.3)

	sudo dpkg-reconfigure -y iptables-persistent


https://en.wikipedia.org/wiki/Cheerleading


----------

----------



### todo: figure out what happened since ..  ###

this doesn't work anymore as of october 2015 (probably earlier but that's when I noticed)
(version: 0.5.7) (apt-cache show iptables-persistent)
	#sudo /etc/init.d/iptables-persistent save
	#sudo /etc/init.d/iptables-persistent reload	

	
check manuals tutorials flamewars : init.d vs systemd / netfilter-persistent
	#???sudo netfilter-persistent save???

but cba atm, got a working fix



	
    
