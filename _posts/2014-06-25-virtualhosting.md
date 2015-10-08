#Two on One 
##How to host Two Websites on One Server.

-------
####My Setup
Apache 2 on an Ubuntu Server hosted on <http://www.digitalocean.com>.
Domains Registrar  <http://www.united-domains.de>

-----

####My Solution
I was trying to set up multiple websites on one server.
The keyword here is **virtual host** for apache.
There are a lot of different ways in which you can make this happen.
I decided that i would redirect the traffic to the appropriate website based on what people put into their url bars in their browsers.
The two urls i was working with were <http://www.anzumana.com> and <http://www.theprojectcast.com>.
To make the magic happen i had to create a **cname record** with my domain registrar. For me this was united domains.
In that cname record i put the static ip address of my webserver. 
If i don't do this and use the default redirect that [united domains](http://www.united-domains.de) offers the server is not able to differentiate between the traffic for <http://www.anzumana.com> and <http://www.theprojectcast.com>
On my server i had to create a virtual host
This [digial ocean tutorial](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-12-04-lts) should help you to do so.

Files:

	/etc/apache2/sites-available
	/var/www/yourwebsites_public_folder
	
To check how your sites are enabled check this folder

	/etc/apache2/sites-enabled
	
helpful Commands 

	sudo apache2ctl -S // shows currently enabled sites
	sudo a2ensite mywebsite_config_file_name
	sudo a2dissite mywebsite_config_file_name
	sudo service apache2 restart // restart or reload for changes to be applied !

The following links helped me a lot:
[digial ocean tutorial](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-12-04-lts)
[stackexchange post](http://unix.stackexchange.com/questions/106326/apache-virtual-host-pointing-to-wrong-documentroot/106396#106396"stackexchange")
[apache doc example](http://httpd.apache.org/docs/2.2/vhosts/examples.html "apache2")


