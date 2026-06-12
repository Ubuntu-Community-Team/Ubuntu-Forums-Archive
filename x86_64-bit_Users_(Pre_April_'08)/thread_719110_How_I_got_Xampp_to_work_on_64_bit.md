---
title: "How I got Xampp to work on 64 bit"
date: 2008-03-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by pearjam on 2008-03-08
Here's what I did to get Xampp to work on 64 bit Ubuntu Studio (Hardy)

    From Synaptic:

-Install ia32-libs

    In a terminal:

-Pull package from Apache Friends (version may change)
wget http://www.apachefriends.org/download.php?xampp-linux-1.6.6.tar.gz

-su to root, or use sudo for each of the commands below:

-Extract, w/ overwrite into /opt:
tar xvfz xampp-linux-1.6.6.tar.gz -C /opt

-Start xampp:
/opt/lampp/lampp start

-Test Xampp:
type localhost in a browser

-Start Xampp on boot:
gedit /etc/init.d/rc.local
    Below the #! /bin/sh line, type:
/opt/lampp/lampp start

-Make Xampp more secure:
/opt/lampp/lampp security
    (Follow prompts.)

That's it. Your pages go in /opt/lampp/htdocs.

If you use PHP scripts in your html & you want to keep the .html or .htm extension on your pages, you can:

-Open text editor and type:

RemoveHandler .htm. .htm
AddType application/x-httpd-php .php .htm .html

-Save the file as .htaccess (note the dot) and place in /opt/lampp/htdocs.

---

### Post by Photon on 2008-06-30
Helpful post. Thanks :)

---

### Post by tominthetrees on 2008-07-21
Thank you sir!!

---

