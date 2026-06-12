---
title: "[SOLVED] Acroread plguin 64-bit firefox?"
date: 2008-01-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by macaholic on 2008-01-27
I run Swiftweasel 3.0b2, and I have gotten just about all the plugins to work under it, flash java, patched mplayer plugins, and the only one left is acroread. I currently have these acroread packages installed,
```
ii  acroread                                   8.1.1-0medibuntu3                         Adobe Reader - binary files
ii  acroread-escript                           8.1.1-0medibuntu3                         Adobe Reader - EScript plug-in
ii  acroread-plugins                           8.1.1-0medibuntu3                         Adobe Reader - extra plug-ins

``` 
Acrobat by itself runs fine w/o any glitches, but there is no firefox plugin in these packages. My question is, how would i go about installing the correct nppdf.so file so I can read pdfs easily in firefox? is this even possible w/o running a 32-bit firefox? Thx in advance.

---

### Post by macaholic on 2008-01-27
I will settle for an older version of acrobat if that is neccesary.

---

### Post by macaholic on 2008-01-27
No ideas? Is there any other in-browser reader of pdfs i'm unaware of?

---

### Post by macaholic on 2008-01-27
Well i have embedded pdfs via mozplugger, its kinda clunk, but it works.

---

### Post by sawjew on 2008-01-28
If you go to this page [here]("http://plugindoc.mozdev.org/linux-amd64.html#acroread-npwrap") it will tell you how to use nspluginwrapper with the adobe reader plugin.  I have this working with Adobe reader 8 in Ubuntu 7.10.  

The only thing is you need to uninstall the Ubuntu version of Adobe Reader and go to the Adobe web site and install the deb from there.  This is only a 32 bit package and you will need to install it using --force-architecture.  The version packaged for Ubuntu 64 bit has the firefox plugin removed.

If you have the problems with the blank page appearing on startup or the libgtkmozembed error go [here]("http://lglinux.blogspot.com/2007/10/acroread-81-on-ubuntu-gutsy-amd64.html").

It works perfectly for me.  Good luck.

PS: you can get the 32 bit adobe reader deb form [here]("http://www.adobe.com/products/acrobat/readstep2_allversions.html")

---

### Post by macaholic on 2008-01-28
I have no Acrobat folder under X11R6/lib, where is the plugin file located for Acrobat 8.1?
EDIT: Well, it is in the right spot, but it isnt showing up in my plugin list.
EDIT2: AHA it was in /opt testing it now.
EDIT3:YAY success! Thx for the help.

---

### Post by sawjew on 2008-01-28
Sorry, I am at work at the moment on Windows so I can't check for you and I can't remember where it is offhand.  One of the best ways I have found to locate installed files is using synaptic.  If you open synaptic, find acroread then right click on it and select "properties", you can then look at the list of installed files to see where they were installed to.

Just noticed your edit.  You may need to create a symlink from the the plugin to /usr/lib/mozilla/plugins and then firefox will find it.

I did this a while ago and I don't remember any major problems and it definitely works fine now.

If you can't work it out I may be able to look when I get home from work.

Good luck.

---

