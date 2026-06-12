---
title: "Gaim 2.0 ppc .deb"
date: 2006-05-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by cloudaj on 2006-05-01
Just because it took me more than a few minutes to track down...

[http://mighmos.org/packages.php](http://mighmos.org/packages.php)

you'll probably want to remove gaim before installing this as it in all likelihood will complain of a conflict (just use sudo apt-get remove gaim, and im almost positive that won't kill your settings but proceed at your own risk).  And I'm not sure if its just due to the goofy way I tried to install, but I had to install the first .deb in the archive, then the third, then the second, again, YMMV.  This may already be old news, I tried to search the forums and didnt see anything, so my apologies if it is, just thought I'd throw this out there in case any other mac owners were looking for it :)

---

### Post by maneesh on 2006-05-01
When I try to install Gaim 2.0 B3 on my dapper ... 
My package installer cribs by saying -
Error: dependency is not satisfiable : libdbus-1-1
I tried finding libdbus-1-1, but I coudnt .... I dont know what to do now.

---

### Post by cloudaj on 2006-05-01
this may be what you're looking for: [ftp://rpmfind.net/linux/MandrakeCooker/cooker/ppc/media/main/libdbus-glib-1_2-0.61-2mdk.ppc.rpm](ftp://rpmfind.net/linux/MandrakeCooker/cooker/ppc/media/main/libdbus-glib-1_2-0.61-2mdk.ppc.rpm)

from the site: [http://rpmfind.net/linux/rpm2html/search.php?query=libdbus-glib-1.so.2](http://rpmfind.net/linux/rpm2html/search.php?query=libdbus-glib-1.so.2)

im not really sure why your getting that dependency error though, I installed gaim from a basically fresh dapper install and it went through without a hitch.

---

