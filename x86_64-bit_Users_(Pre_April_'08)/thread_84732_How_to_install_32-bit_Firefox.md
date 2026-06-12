---
title: "How to install 32-bit Firefox?"
date: 2005-10-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by lehardi on 2005-10-31
How to install 32-bit Firefox in 5.10? I need it because I can't make Flash work in 64-bit - I read FAQ. Could you give me link to any HOWTOs or give me step by step guide?
-- 
LeHardi

---

### Post by tux61 on 2005-11-01
Hi,

A solution that works on my PC :

[LIST=1]
[*]Download a 32 bits version of firefox or, better, download the .deb version (firefox_1.0.7-0ubuntu20_i386.deb)
[*]Install it : dpkg -i --force-architecture firefox_1.0.7-0ubuntu20_i386.deb
[*]Create a little script called /usr/bin/firefox32 for example :
#!/bin/sh
export GTK_PATH=/usr/lib32/gtk-2.0/
export PANGO_RC_FILE=/etc/pango32/pangorc
firefox
[/LIST]

Now you can install and use flash and realplayer 10 !  :D 
For java plugin you need also to download a 32 bits version.

---

### Post by DancingSun on 2005-11-01
[QUOTE=tux61]Hi,

A solution that works on my PC :

[LIST=1]
[*]Download a 32 bits version of firefox or, better, download the .deb version (firefox_1.0.7-0ubuntu20_i386.deb)
[*]Install it : dpkg -i --force-architecture firefox_1.0.7-0ubuntu20_i386.deb
[*]Create a little script called /usr/bin/firefox32 for example :
#!/bin/sh
export GTK_PATH=/usr/lib32/gtk-2.0/
export PANGO_RC_FILE=/etc/pango32/pangorc
firefox
[/LIST]

Now you can install and use flash and realplayer 10 !  :D 
For java plugin you need also to download a 32 bits version.[/QUOTE]
Tux61, 

Do I need to uninstall the 64-bit firefox first?  Or can they co-exist?  Same thing with Java, can I have both 64 and 32-bit versions installed?  Also, it'll be great if you can turn this into a HOW-TO so that it is documented and available for others looking to get 32-bit firefox working.

BTW, thanks for being the pioneer to try this out on Ubuntu!

---

### Post by Hallavej on 2005-11-01
[QUOTE=tux61]Hi,

A solution that works on my PC :

[LIST=1]
[*]Download a 32 bits version of firefox or, better, download the .deb version (firefox_1.0.7-0ubuntu20_i386.deb)
[*]Install it : dpkg -i --force-architecture firefox_1.0.7-0ubuntu20_i386.deb
[*]Create a little script called /usr/bin/firefox32 for example :
#!/bin/sh
export GTK_PATH=/usr/lib32/gtk-2.0/
export PANGO_RC_FILE=/etc/pango32/pangorc
firefox
[/LIST]

Now you can install and use flash and realplayer 10 !  :D 
For java plugin you need also to download a 32 bits version.[/QUOTE]

It didnt work for me. I couldnt even install the 32-bit version. (So far I only tried to install the .tar.gz and not .deb)
I got both "Gdk- and pango errors".
I'm very interested to know if anybode else got it to work.

---

### Post by RAOF on 2005-11-01
[QUOTE=tux61]Hi,

A solution that works on my PC :

[LIST=1]
[*]Download a 32 bits version of firefox or, better, download the .deb version (firefox_1.0.7-0ubuntu20_i386.deb)
[*]Install it : dpkg -i --force-architecture firefox_1.0.7-0ubuntu20_i386.deb
[*]Create a little script called /usr/bin/firefox32 for example :
#!/bin/sh
export GTK_PATH=/usr/lib32/gtk-2.0/
export PANGO_RC_FILE=/etc/pango32/pangorc
firefox
[/LIST]

Now you can install and use flash and realplayer 10 !  :D 
For java plugin you need also to download a 32 bits version.[/QUOTE]
I don't seem to have a /etc/pango32/pangorc file.  Could you post the contents of yours, and I'll see if that works.

---

### Post by tux61 on 2005-11-02
Sorry I forgot the pangorc file !!!

```

# cat /etc/pango32/pangorc

[Pango]
ModuleFiles=/etc/pango32/pango.modules
[PangoX]
AliasFiles=/etc/pango/pangox.aliases


```

For your information I was, unfortunately, unable to installed the tar.gz version of firefox (library error with libXp.so.6) but only the firefox_1.0.7-0ubuntu20_i386.deb package.
I also remove firefox version 64 and the ubuntu-desktop meta-package. 

Good luck !

---

### Post by RAOF on 2005-11-02
Awesome!  With that pangorc file, I've just got the 32bit .tar.gz of firefox 1.5 rc1 from mozilla.org running fine :)

---

### Post by Gomek on 2005-11-04
Heh...I can't get a 32 bit version of Firefox installed.  I've tried both the Firefox 1.0.7 for Linux i686 tar from the Mozilla website and the package I found at [http://packages.debian.org/unstable/web/mozilla-firefox](http://packages.debian.org/unstable/web/mozilla-firefox).  I've also tried slipping in a Ubuntu i386 CD, but that didn't work either.  >.<  What am I doing wrong?

The farthest I've gotten is with the tar file.  I install it, but when I try to boot it, I get a libXp.so.6 error.

---

### Post by activejeff on 2005-11-07
note that this also works for applications built on Firefox, including ActiveState's Komodo. I should also mention that if you want to run Komodo on Breezy, you need to use the current beta :

[http://activestate.com/Products/Komodo/beta.plex](http://activestate.com/Products/Komodo/beta.plex)

---

### Post by rhaurison on 2005-11-14
for Firefox and ALL others 32bit applications, the better solution is make chroot for 32bit because you can use apt-get to install applications.

there are a post howto: [http://ubuntuforums.org/showthread.php?t=24575&highlight=chroot+32bit]("http://ubuntuforums.org/showthread.php?t=24575&highlight=chroot+32bit")

I use firefox, opera, skype, x-lite and many other with chroot.

---

### Post by RAOF on 2005-11-14
Or, if you don't want to chroot, there is this [howto]("http://www.ubuntuforums.org/showthread.php?p=491079#post491079") now.

---

### Post by Gomek on 2005-11-28
Ugh...  Following those instructions I still get a libXp.so.6 error.  Looks like I'm gonna have to suck it up and install a whole chroot just for little ol' Firefox.

What baffles me is I could get it to work under Suse...

---

