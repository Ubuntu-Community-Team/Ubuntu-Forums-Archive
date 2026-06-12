---
title: "broke x when installing xgl"
date: 2006-10-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by nidelius on 2006-10-07
When I start ubuntu I get the following message

Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view X server output to diagnose the problem?

[YES]

GDM: Xsever not found: /usr/local/bin/Xgl :0 :0 fullscreen -ac -accel xv -accel glx:pbuffer -auth /var/lib/gdm/ :0.Xauth -nolisten tcp vt7
Error: command could not be executed!
Pleas install the X server or correct GDM configuration and restart GDM.

[OK]

The X server is now disabled. Restart GDM when it is configurated correctly.

[OK]

So you have any help to provide to get this working.

Before X broke I tried to start Xgl with adding some start info in ~/.Xsession

I have tried sudo apt-get install xserver-xorg

---

### Post by xstaticxgpx on 2006-10-07
try sudo dpkg-reconfigure xserver-xorg and see if that helps your problem

---

### Post by nidelius on 2006-10-08
still getting the same message. Tried with some different configs. Anyone else have a clue or is format reinstall easier? :P

---

### Post by de4th on 2006-10-10
Try this:
[http://ubuntuforums.org/showthread.php?t=271716](http://ubuntuforums.org/showthread.php?t=271716)

:cool:

---

### Post by John.Michael.Kane on 2006-10-10
Might want to let us know what hardware this is happening on..

---

### Post by nidelius on 2006-10-14
Ok so I have been working my *** of because I'm going on a trip around the world with my girlfriend but now as it is saturday I tried the tip you came ut with. But I still get the exact same message when X tries to launch. :( I did try to configurate a .~Xsession file to log on using XGL before this happend if that can have something to do with it

---

### Post by nidelius on 2006-10-14
> **nidelius said:**
> Ok so I have been working my *** of because I'm going on a trip around the world with my girlfriend but now as it is saturday I tried the tip you came ut with. But I still get the exact same message when X tries to launch. :( I did try to configurate ~.Xsession file to log on using XGL before this happend if that can have something to do with it


I'm using A ferrari 3400 Acer laptop Radeon 9700Mobile

---

### Post by John.Michael.Kane on 2006-10-14
Being that compiz has been forked to beryl you may want to ask over at the [**beryl-forums**]("http://forum.beryl-project.org/") to see if theres a fix as alot of the old compiz based howto's don't hold up anymore.

Note heres a known working guide [**beryl-howto**]("http://ubuntuforums.org/showthread.php?t=263851&highlight=beryl") you will need 64bit beryl repo's though.

---

### Post by coder_ on 2006-10-14
I was getting that and I just didn't boot X and reset my config files for gdm, xorg, ect.  For some reason, compiz+xgl don't like Ubuntu 64bit for me, but they worked on SuSE 32 bit for me :'(  Oh well... I'll have to find another way to use up my dual core power :P

Which reminds me, I need to find out how to get xcompmgr to work with GNOME :S  It doesn't seem to work either.

---

### Post by RAOF on 2006-10-15
> **nidelius said:**
> ...
GDM: Xsever not found: /usr/local/bin/Xgl :0 :0 fullscreen -ac -accel xv -accel glx:pbuffer -auth /var/lib/gdm/ :0.Xauth -nolisten tcp vt7
Error: command could not be executed!
Pleas install the X server or correct GDM configuration and restart GDM.
...

Does the file */usr/local/bin/Xgl* actually exist?  If you installed Xgl from packages, it has almost certainly gone in */usr/bin/Xgl*.  I'd try replacing */usr/local/bin/Xgl* with */usr/bin/Xgl* in that line :)

---

