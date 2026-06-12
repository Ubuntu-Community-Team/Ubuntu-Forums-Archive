---
title: "Squirrelmail 1.4.8 problem"
date: 2007-03-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by vickistan on 2007-03-27
I recently moved to Ubuntu after using Slackware for years. In my old system, I simply untarred squirrelmail in /var/www/htdocs/squirrelmail and configured from there. Worked fine. Now I am trying to acquaint myself with Ubuntu's way. I did an apt-get install of squirrelmail and configured it. I am now getting this error:

Error opening ../config/default_pref
Could not create initial preference file!
../data/ should be writable by user www-data

I found a previous post which suggested chowning the data directory to be owned by www-data. I did this, but it is still not working. I get exactly the same error. For clarity, the perms and ownership on /var/lib/squirrelmail/data are drwx-wx--- 2 www-data www-data.

Can someone give me a hint?

vickistan

---

### Post by Kilz on 2007-03-27
> **vickistan said:**
> I recently moved to Ubuntu after using Slackware for years. In my old system, I simply untarred squirrelmail in /var/www/htdocs/squirrelmail and configured from there. Worked fine. Now I am trying to acquaint myself with Ubuntu's way. I did an apt-get install of squirrelmail and configured it. I am now getting this error:

Error opening ../config/default_pref
Could not create initial preference file!
../data/ should be writable by user www-data

I found a previous post which suggested chowning the data directory to be owned by www-data. I did this, but it is still not working. I get exactly the same error. For clarity, the perms and ownership on /var/lib/squirrelmail/data are drwx-wx--- 2 www-data www-data.

Can someone give me a hint?

vickistan


Did you also change the permission/owners of the config diectory and the default_pref file?

---

### Post by vickistan on 2007-03-27
Actually am not seeing a config directory (I have the old ones from the tarball that I used to use, but not one that got installed with apt-get install squirrelmail. Where should it be located by default? Thanks.

Vickistan

---

### Post by vickistan on 2007-03-27
Replying to myself.....I see it now. It is a sym link to /etc/squirrelmail. I have chowned /etc/squirrelmail/default_pref to www-data:www-data. I have also chowned /etc/squirrelmail to www-data:www-data. I am still getting the same error.

Vickistan

---

### Post by vickistan on 2007-03-28
OK, perhaps if I just asked about the stuff that I don't understand, I could stumble upon the answer. First, the error

Error opening ../config/default_pref
Could not create initial preference file!
../data/ should be writable by user www-data

seems to indicate that the config directory is one level up from something (..). But the config directory is a sym link to /etc/squirrelmail located in /usr/share/squirrelmail/

vickistan@oncearound:~$ ls -l /usr/share/squirrelmail/config
lrwxrwxrwx 1 root root 17 Mar 22 10:02 /usr/share/squirrelmail/config -> /etc/squirrelmail

and here's /etc/squirrelmail's contents

vickistan@oncearound:~$ ls -l /etc/squirrelmail
total 60
-rw-r--r--     1  www-data www-data  1118 Aug 29  2006 apache.conf
lrwxrwxrwx 1 root     root        32 Mar 22 10:02 conf.pl -> /usr/sbin/squirrelmail-configure
-rw-r--r--     1  www-data www-data  7124 Mar 22 10:19 config.php
-rw-r--r--     1  www-data www-data 23637 Mar  6 17:08 config_default.php
-rw-r--r--     1  www-data www-data   191 Mar  6 17:08 config_local.php
-rw-rw-rw-  1 www-data www-data    48 Jul 27  2003 default_pref
-rw-r--r--     1 www-data www-data  6589 Feb  3  2006 filters_setup.php
-rw-r--r--     1 www-data www-data   492 Feb  3  2006 index.php
-rw-r--r--     1 www-data www-data  1901 Aug 29  2006 sqspell_config.php

and the data directory is 

/var/lib/squirrelmail/data and is absolutely empty.

drwx-wx--- 2 www-data www-data 4096 Aug 29  2006 data

So am I wrong in assuming that the data and the config directories are intended to be in the same location?

Vickistan

---

### Post by Kilz on 2007-03-28
Do you absolutely need to install this from a tarball? If not delete the folders.  [Make sure that the universe and multiverse repose are enabled]("http://www.monkeyblog.org/ubuntu/installing/#enabling_extra_repositories"). Search for [squirrelmail in synaptic.]("http://www.monkeyblog.org/ubuntu/installing/#installing_with_synaptic")  :)

---

### Post by vickistan on 2007-03-28
I am NOT using a tarball now. I still have the old directories but they are specifically located so that they do not interfere. I am trying to use the ubuntu packaged version of squirrelmail. I am not sure why it doesn't work. Can you post a ls -l of your squirrelmail-related directories for comparison?

Vickistan

---

### Post by Kilz on 2007-03-28
> **vickistan said:**
> I am NOT using a tarball now. I still have the old directories but they are specifically located so that they do not interfere. I am trying to use the ubuntu packaged version of squirrelmail. I am not sure why it doesn't work. Can you post a ls -l of your squirrelmail-related directories for comparison?

Vickistan

I dont have squirrelmail installed. I was just looking at your errors and trying to see what it was telling you. The package should work.

---

### Post by vickistan on 2007-03-28
Got it! The default location for the data directory apparently is ../data. I changed this relative path to an absolute one (using sudo /usr/sbin/squirrelmail-configure), and it works. I still have problems with the way I am specifying my folders apparently, but it is a step in the right direction.

Thanks for your willingness to help.

Vicki

---

### Post by Kilz on 2007-03-28
> **vickistan said:**
> Got it! The default location for the data directory apparently is ../data. I changed this relative path to an absolute one (using sudo /usr/sbin/squirrelmail-configure), and it works. I still have problems with the way I am specifying my folders apparently, but it is a step in the right direction.

Thanks for your willingness to help.

Vicki

Helping is the best part of Ubuntu.  :)

---

