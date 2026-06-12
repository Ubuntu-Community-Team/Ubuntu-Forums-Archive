---
title: "Ndiswrapper under Ubuntu 64"
date: 2004-11-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by latrine on 2004-11-02
How can I do it?

If I try to instal with

sudo dpkg -i ndiswrapper-utils..-i386.deb

it returns the obvious "different archittectures" i386 and AMD64 error...

So how can I do it in a 64 bit environment?

Thxs
Latz

---

### Post by Baloo on 2004-11-02
Download the source code and do it by hand? Thats what I've had to do with mono.

---

### Post by jdodson on 2004-11-02
check the .[ndiswrapper page](http://ndiswrapper.sourceforge.net/) page for more info, however according to [this thread that looks like it is from a ndis-developer](http://www.x86-64.org/lists/discuss/msg04760.html) it might not be possible.  you could however, compile ndiswrapper on your own(i did on my 32bit box) and run it that way.  though it might complain at the 32 bit windows driver.  there "might" be a 64 bit windows driver for your card, however unlikely. 

good luck.  let us know what happens

---

### Post by jdong on 2004-11-02
err, trying to wrap 32-bit drivers in a 64-bit kernel, that won't work!

---

### Post by jdodson on 2004-11-02
[QUOTE=jdong]err, trying to wrap 32-bit drivers in a 64-bit kernel, that won't work![/QUOTE]

thats what i thought, but i figured it was at least worth a shot.

---

### Post by latrine on 2004-11-03
bugger... this is the broadcom chipset in a linksys wmp11 v 2.7 802.11b that has no 64 bit driver... and linksys in Portugal when asked for a 64 bit driver for win Xp 64 bit edition replied to me to install service pack 2 :)


I have to look for another nic... no inboard nic, no wireless nic... I miss my dial-up!!!

---

### Post by jdodson on 2004-11-03
[QUOTE=latrine]and linksys in Portugal when asked for a 64 bit driver for win Xp 64 bit edition replied to me to install service pack 2 :)
[/QUOTE]

service pack 2, HA, thats classic!  seriously though i hope you find something that works well for you!

---

### Post by transgress on 2005-05-17
[http://www.ubuntulinux.org/wiki/HowtoUseNdiswrapperOnAmd64Ubuntu](http://www.ubuntulinux.org/wiki/HowtoUseNdiswrapperOnAmd64Ubuntu)  <-- that's the wiki i wrote a while back.  works like a charm to about 99% of those i spam it too on irc.

---

