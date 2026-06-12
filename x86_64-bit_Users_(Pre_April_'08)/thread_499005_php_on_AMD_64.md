---
title: "php on AMD 64"
date: 2007-07-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by echofire on 2007-07-12
There is a bug in php 5.2.1 (see [http://bugs.php.net/bug.php?id=40543](http://bugs.php.net/bug.php?id=40543)) which breaks my application running on Fiesty 64 bit and an AMD 64.  How should I best upgrade to the current php 5.3.1 ?  I have downloaded the 5.3.1 source and been through ./configure, make, make install but phpinfo() is still reporting use of 5.2.1.  Or should I use the Gutsy repository, and if so how ?  Thanks.

---

### Post by Red Badger on 2007-07-12
Have you changed which php module is loading in httpd.conf?

---

### Post by echofire on 2007-07-12
Good point, and no.  /etc/apache2/mods-enabled/php5.load is I guess the equivalent part of httpd.conf, and this points to /usr/lib/apache2/modules/libphp5.so which has a date of May 2007 so is well before I compiled the later version.  BUT I can't find another version of libphp5.so anywhere.  Maybe the compile failed ? though I didn't see an error message.  Do you know where I should expect to find it ?  Thx.

---

### Post by Red Badger on 2007-07-13
Hi Echofire

Yes, /usr/lib/apache2/modules/libphp5.so is the right location.
Which suggests libphp5.so is corrupted.
I found this post from someone with a missing libphp5.so file that seems to be connected with mysql. They supply a link to an article that solves the problem.

[http://www.linuxquestions.org/questions/showthread.php?t=446404](http://www.linuxquestions.org/questions/showthread.php?t=446404)

Hope this might be of help.

---

