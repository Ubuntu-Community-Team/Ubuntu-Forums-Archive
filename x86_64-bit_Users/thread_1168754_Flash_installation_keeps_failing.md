---
title: "Flash installation keeps failing"
date: 2009-05-24
forum: x86 64-bit Users
---

### Post by spookztar on 2009-05-24
(ver. 8.04, 64 LTS)

Hello,

New user, great to be here...

I have a flash-issue, searching the forums gave nothing.

All of a sudden, I got "your flashplayer is outdated or javascript is off" on youtube. JS is on, so that isn't it. But installing the latest flash doesn't remedy anything.

1) I tried this (at the bottom) : [http://www.ubuntugeek.com/how-to-install-adobe-flash-player-10-in-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/how-to-install-adobe-flash-player-10-in-ubuntu-804-hardy-heron.html)

2) I tried putting the latest flash [http://labs.adobe.com/technologies/flashplayer10/](http://labs.adobe.com/technologies/flashplayer10/)  in:   home>.mozilla>plugins

3) - and also placed it (as root): /usr/lib/firefox-addons/plugins/

- restarting firefox every time.

Nothing, same message from YT.

Suggestions?

---

### Post by SuperSonic4 on 2009-05-24
Stupid question but did you extract the tarball from Adobe to ~/.mozilla/plugins

---

### Post by spookztar on 2009-05-24
@Supersonic4: That has GOT to be the record for speedy replies, thx!

I extracted the file and dumped it manually at the two locations mentioned.

---

### Post by Yellow Pasque on 2009-05-25
After you ran that script and it didn't work, did you remove all the stuff it installed?

---

### Post by spookztar on 2009-05-25
Temüjin

Thanx foir responding.

Yes, I did.

I Just removed everything and re-installed the flash available from the repo. Now it works  about 50% of the time. I Always get audio, but half the time I only get video after I refresh the browser (sometimes that doesn't even help)

How long can I expect it to take until the latest flash shows up in an LTS installs' repo?

---

### Post by pixel :-) on 2009-05-25
are you sure it was the 64bit plugin and not the 32bit?

This is the 64bit. It works (almost always) on Firefox, Konqueror can't recognize it.
[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz)

and of course you have to unistall anything else.

---

### Post by spookztar on 2009-05-30
Works now with file from Pixels link. The first file I tried was also a 64 bit (it was in the filename), but it was named differently from this one.

Thanx for the responses.

---

