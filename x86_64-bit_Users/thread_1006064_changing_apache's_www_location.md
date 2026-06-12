---
title: "changing apache's www location"
date: 2008-12-08
forum: x86 64-bit Users
---

### Post by stunet on 2008-12-08
hi,

i have apache installed and noticed everything has to go in /var/www/ to be seen by the web server.

I noticed that it requires root access to move things in here and just to make things easier on me(as i just installed this and will be moving several things from the old setup) is there a way I can alter the location to a folder that I can access without problems?

also regarding the same thing, where do i go to dinf the config file to enable vhost?

thanks :)

---

### Post by awam66 on 2008-12-09
Hello, 

You need to sudo gedit /etc/apache2/sites-available/default to make apache look at your web directory. mine looks like this:
NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /home/alistair/www/website/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /home/alistair/www/website/>
		Options Indexes FollowSymLinks MultiViews +Includes
		XBitHack on
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

	ScriptAlias /cgi-bin/ /home/alistair/www/website/cgi-bin/
	<Directory "/home/alistair/www/website/cgi-bin">
		AddHandler cgi-script .cgi .pl
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel debug

	CustomLog /var/log/apache2/access.log combined
	ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>


You need to replace /home/alistair/.... with your own directory.

Have a look at [http://httpd.apache.org/](http://httpd.apache.org/) for the manual.

---

### Post by stunet on 2008-12-09
got it working like i want now, thanks for the help :)

---

