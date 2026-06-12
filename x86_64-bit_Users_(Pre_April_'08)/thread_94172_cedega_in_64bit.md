---
title: "cedega in 64bit"
date: 2005-11-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by shomi on 2005-11-23
hello fellows, 

i followed this guide to try and install cedega 

[http://cedegawiki.sweetleafstudios.com/wiki/Ubuntu](http://cedegawiki.sweetleafstudios.com/wiki/Ubuntu)

but i didn't install the transgaming*.deb because i didn't find it, neither did i make a chroot because my friend told me that i didn't need to...
here's my error which i have no idea what it means...
someone give a link to transgaming*.deb plz and help plz :)


shomi@ubuntu:~$ cedega

(Point2Play_gui.py:22919): Gdk-WARNING **: locale not supported by Xlib

(Point2Play_gui.py:22919): Gdk-WARNING **: cannot set locale modifiers

(Point2Play_gui.py:22919): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(Point2Play_gui.py:22919): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported
Traceback (most recent call last):
  File "/usr/lib/transgaming_cedega/Point2Play_gui.py", line 35, in ?
    import gtk.glade
ImportError: libglade-2.0.so.0: cannot open shared object file: No such file or directory

thanks

---

### Post by Drain on 2005-11-23
[QUOTE=shomi]
i followed this guide to try and install cedega 
[http://cedegawiki.sweetleafstudios.com/wiki/Ubuntu](http://cedegawiki.sweetleafstudios.com/wiki/Ubuntu)
but i didn't install the transgaming*.deb because i didn't find it, neither did i make a chroot because my friend told me that i didn't need to...[/QUOTE]

Heh. Not to be critical, but you said you did NOT follow directions and expected everything to work right?  



> 
shomi@ubuntu:~$ cedega

(Point2Play_gui.py:22919): Gdk-WARNING **: locale not supported by Xlib

(Point2Play_gui.py:22919): Gdk-WARNING **: cannot set locale modifiers

(Point2Play_gui.py:22919): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(Point2Play_gui.py:22919): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported
Traceback (most recent call last):
  File "/usr/lib/transgaming_cedega/Point2Play_gui.py", line 35, in ?
    import gtk.glade
ImportError: libglade-2.0.so.0: cannot open shared object file: No such file or directory


Is libglade2-0 installed? it contains the missing "libglade-2.0.so.0" file, and you can either get it with synaptic or through apt-get. 

Good luck with the rest of it.

---

### Post by Ribs on 2005-11-24
Which version of Cedega are you using? I'm using Cedega version 5 without issues. It takes a little forcing to work (dpkg -i --force-architecture cedega-or-whatever.deb).

I seem to recall I had issues with dpkg not setting cedga up, as it was missing some deps. Running apt-get -f install may fix this (don't remember how I did it myself now!)

---

