---
title: "HELP Tried installing hardware didn't work now errors all the time"
date: 2007-10-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by fatray on 2007-10-17
I get this error or something that looks just like this EVERY single time I install anything.  I believe it is totally messing things up because I can't install a lot of stuff.  It all started when I tried installing my wireless network card, but it's a no go with 64bit.  I removed it, uninstalled it, but it still gives me errors.
How to I completely remove this?:confused:

```
dpkg: error processing bcm43xx-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 bcm43xx-fwcutter

```

---

### Post by Ylang on 2007-10-17
I am pretty sure that just means that your wireless card is not supported. Do you have wireless? Anyways, I had that problem. If it is your wireless, all you have to do is install ndiswrapper. Actually, it Gutsy, this hardware is supported, so all you have to do is enable it in the restricted drivers manager.

---

### Post by Ylang on 2007-10-17
[http://ubuntuforums.org/showthread.php?t=257684&highlight=Dell+Inspiron+E1505%2F6400](http://ubuntuforums.org/showthread.php?t=257684&highlight=Dell+Inspiron+E1505%2F6400)
This is the site I used for the wireless card, it might work for you. The wireless fix is halfway down the page. If not, you might consider updating to Gutsy, it made everything much easier for me (I am  using the beta)

---

