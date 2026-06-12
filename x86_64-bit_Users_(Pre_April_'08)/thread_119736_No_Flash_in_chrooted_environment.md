---
title: "No Flash in chrooted environment"
date: 2006-01-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by andrewsawyer on 2006-01-20
I have installed Firefox in a chrooted 32bit environment (when I click Help >> About in firefox, it tells me it is the i686 version.  However, every time I go to a site with Flash, I get a message saying it needs to be installed.  I click ok, agree with the terms and conditions, watch the progress bar reach 100%, and click finish when it is done.  It then refreshes the page, and again tells me I need to install Flash.  I've even tried loading firefox32 as sudo, but still no luck - and yes I've tried closing, rebooting and all that.

Can anyone shed some light on this?  I am more than happy to post any configuration files/screenshots that may be needed.

Many thanks,

Andy

---

### Post by awi on 2006-01-29
Try typing on the URL bar:

```
about:plugins
```

That gives you a list of plugins, look for Shockwave... 

I suggest, you go to Macromedia, download the flash version and just copy the two files necessary:

```
/usr/local/firefox32/plugins/flashplayer.xpt
/usr/local/firefox32/plugins/libflashplayer.so
```

adjusting to your firefox32 installation, of course.

---

