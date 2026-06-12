---
title: "Problems running httpd"
date: 2008-10-16
forum: x86 64-bit Users
---

### Post by vikramsharma on 2008-10-16
I have installed apache and am planning to run a webserver on my linux box, I have the content of webpage ready and placed in the right directory.  The problem I am having is that [http://localhost](http://localhost) gives nothing except the version of Apache I have installed (I hecked that using the serverspy extension of Firefox) but [http://localhost/index.html](http://localhost/index.html) works.  Ideally speaking [http://localhost](http://localhost) should work.  I am also uploading the httpd.conf file for refrence purposes (filename: httpd.conf.doc).  Thanks in advance guys.

PS: I tried uploading the file in txt format but it exceeded the size limits,it was 35 kb in size and only 192.5 kb of txt attachments are allowed.

---

### Post by penguinpi.com on 2008-10-16
I think I know what the problem might be. Honestly I didn't look at your doc put try this first.

edit /etc/apache2/sites-available/default

see if the Document Root is /var/www/apache2-default or something like that.

and change in to /var/www

also change anything else that contains apache2-default to the real path of your files.

the restart apache

Hope this Helps!

---

### Post by vikramsharma on 2008-10-18
> **penguinpi.com said:**
> I think I know what the problem might be. Honestly I didn't look at your doc put try this first.

edit /etc/apache2/sites-available/default

see if the Document Root is /var/www/apache2-default or something like that.

and change in to /var/www

also change anything else that contains apache2-default to the real path of your files.

the restart apache

Hope this Helps!

Thanks I checked for a diectory named sites-available in /etc/httpd but there wasn't any.  I am trying to migrate the website from one server to the other.  The website is running without any problems in the old server but is giving problems on the new server.  I tried looking for /etc/apache2/sites-available or even /etc/httpd/sites-available but could not find the directory on both the server.  Thanks anyways for your effort.

---

