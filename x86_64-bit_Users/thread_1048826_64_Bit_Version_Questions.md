---
title: "64 Bit Version Questions"
date: 2009-01-23
forum: x86 64-bit Users
---

### Post by ddeile on 2009-01-23
Hi,

I plan on installing (dual booting on a two drive system) the 64 bit version of Ubuntu in the next few days.  I want to use the 64 bit version to take advantage of the higher memory allowance. 

I'll be using this for development.  I'll be installing the following software

PHP (w/ memcached, eaccelerator, and other php extensions)
Apache
Python
Mysql

I know that the above should work without issue, but what about these:

Aptana
Songbird
Flash
Adobe Air

---

### Post by rv65 on 2009-01-23
Adobe air is a 32 bit app but it does work. It's not a browser plugin so it doesn't have to be 64 bit. Adobe however, may consider a 32 bit Adobe Air. Right now there are no plans to release a 64 bit adobe air. Flash does have a 64 bit version though if you install ubuntu-restricted-extras make sure you remove nspluginwrapper which removes the flash player.

[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz)

Download this file and extract it. All you have to do is copy it to your /usr/lib/mozilla/plugins and you're good to go.

---

### Post by rv65 on 2009-01-24
Songbird does work on 64 bit linux. I went to their website and I downloaded one for x86_64 which is the 64 bit version. Their website does tell you but some really nice person made a 64 bit .deb of it. 

Aptana does work on 64 bit as an eclipse plugin. The Adobe Flash program does work in 64 bit Linux under wine. Well at least CS3 works. No word on CS4. Wine can be downloaded for amd64. 

[www.winehq.com](www.winehq.com) is where you get wine. [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb) This teaches you how to add it for 64 bit ubuntu. Add the repo link and the key in order for it to work. 

Make sure you follow the instructions 

[http://labs.adobe.com/technologies/flashplayer10/faq.html](http://labs.adobe.com/technologies/flashplayer10/faq.html) 
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

[http://www.mediafire.com/?nimn2yyhfjy](http://www.mediafire.com/?nimn2yyhfjy)

Copy and install and you should be good to go. Hope this helps.

---

### Post by jespdj on 2009-01-24
Note that 32-bit software also runs on a 64-bit system. So if you really cannot find a 64-bit native version of the software you need, you can still run the 32-bit version. You might need to use [getlibs](http://ubuntuforums.org/showthread.php?t=474790) to install the 32-bit libraries that a specific program needs.

---

### Post by Kilz on 2009-01-24
I know the flash content is listed in the stickies.

---

### Post by ddeile on 2009-01-24
Thanks for the info everyone.  Very helpful.:D

---

