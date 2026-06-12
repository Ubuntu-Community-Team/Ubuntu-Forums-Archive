---
title: "Does klik client work with Feisty 64?"
date: 2008-01-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by j0eb0b on 2008-01-10
I just tried to install the klik client on my 7.0.4 64 bit system and got the following error.  Anyone know of klik works with a 64 bit system  I thought it ought to.

j0eb0b@j0eb0b-desktop:~$ wget klik.atekon.de/client/install -O -|sh
--18:05:15--  [http://klik.atekon.de/client/install](http://klik.atekon.de/client/install)
           => `-'
Resolving klik.atekon.de... 134.169.172.48
Connecting to klik.atekon.de|134.169.172.48|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 15,397 (15K) [text/plain]

 0% [                                     ] 0             --.--K/s             test: 33: ==: unexpected operator
100%[====================================>] 15,397        49.14K/s             

18:05:16 (49.02 KB/s) - `-' saved [15397/15397]

j0eb0b@j0eb0b-desktop:~$

If this isn't an error where did klik go? I doesn't seem to work.

PS: i installed the prereqs before trying to load klk

Thanks,
Joe

---

### Post by j0eb0b on 2008-01-10
If found the answer to my question on the Klik forum.  Klik does not work on Ubuntu 64 systems.  Reportedly it might work if 32 bit compatible libraries are present. Since most of the applications it loads are 32 bit it probably wouldn't buy much anyway.  I'm not sure what I would have to enable to try it again.  

This started because i was trying to load Kleansweep.  Has anyone successfully used 
Kleansweep on an Ubuntu 64 system?

Regards,
joe

---

### Post by Kilz on 2008-01-10
[Its in the Ubuntu repositories]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=Kleansweep&searchon=names&subword=1&version=all&release=all"). I always look in the repositories to see if an application is included before looking elseware. The package site makes it easy, you might want to bookmark it.

---

### Post by j0eb0b on 2008-01-11
Thanks you, I bookmarked the site.  Looking at the developers notes, he is working with Ubuntu on integrating his file clean up tool into a future distribution.  I think I'll wait until this happens.

---

### Post by Kilz on 2008-01-11
> **j0eb0b said:**
> Thanks you, I bookmarked the site.  Looking at the developers notes, he is working with Ubuntu on integrating his file clean up tool into a future distribution.  I think I'll wait until this happens.

Up to you, but if a package is in the Ubuntu repositories, to me that says its kind of integrated. At least its been compiled by the ubuntu developers and known to work. Since its in the repositories it is available from synaptic, adept, aptitude, and apt. The site just make it easy to search.

---

