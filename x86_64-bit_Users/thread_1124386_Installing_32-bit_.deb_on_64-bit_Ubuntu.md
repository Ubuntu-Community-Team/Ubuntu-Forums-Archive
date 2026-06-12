---
title: "Installing 32-bit .deb on 64-bit Ubuntu?"
date: 2009-04-13
forum: x86 64-bit Users
---

### Post by Lazy-buntu on 2009-04-13
I'm looking to install mklivecd ([http://mklivecd.sourceforge.net/](http://mklivecd.sourceforge.net/)), but it looks like all they offer is a .deb for i386.

Is it possible to use that .deb on 64-bit jaunty install? I installed getlibs ([http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)) and tried ```
getlibs -i mklivecd_0.01-1_i386.deb
``` Of course I went to the correct directory.

It says > Installing libraries...

And that's all.

I'm a newbie when it comes to x86. I just installed 9.04 beta 64-bit yesterday, and everything went fine. So is it possible to use 32-bit .debs on a 64-bit OS?

---

### Post by Chemical Imbalance on 2009-04-13
sudo dpkg --force-architecture -i <filename>.deb

---

### Post by Lazy-buntu on 2009-04-13
> **Chemical Imbalance said:**
> sudo dpkg --force-architecture -i <filename>.deb

Any hazards involved with this?

---

### Post by MysticGold04 on 2009-04-13
Yes that's the way to do it, but also check this thread because if it requires certain 32-bit libraries, you will need to install those also because the 32-bit programs cannot use 64-bit libraries. 

If the libraries installed okay, I'd say go for it. I have avast running just fine on my 64bit install of 8.10. 


[http://ubuntuforums.org/showthread.php?t=1065805&highlight=avast+64+bit](http://ubuntuforums.org/showthread.php?t=1065805&highlight=avast+64+bit)

---

### Post by Lazy-buntu on 2009-04-13
This is the output of that command:

```
re -i mklivecd_0.01-1_i386.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package mklivecd.
(Reading database ... 121437 files and directories currently installed.)
Unpacking mklivecd (from mklivecd_0.01-1_i386.deb) ...
dpkg: dependency problems prevent configuration of mklivecd:
 mklivecd depends on debootstrap; however:
  Package debootstrap is not installed.
 mklivecd depends on mkinitrd-cd; however:
  Package mkinitrd-cd is not installed.
 mklivecd depends on shellutils (>= 2.0.11); however:
  Package shellutils is not installed.
 mklivecd depends on cloop-src; however:
  Package cloop-src is not installed.
 mklivecd depends on cloop-utils; however:
  Package cloop-utils is not installed.
 mklivecd depends on fileutils (>= 4.1); however:
  Package fileutils is not installed.
dpkg: error processing mklivecd (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Errors were encountered while processing:
 mklivecd
```

So I did:

```
sudo getlibs -i mklivecd_0.01-1_i386.deb
```

Result: > Installing libraries ...


Do I have to create my own application launcher? And is there anyway to confirm that it is installed properly?

---

### Post by Lazy-buntu on 2009-04-13
Now that I'm looking at the errors, do I need to manually install those dependencies as 32 bit debs?

---

### Post by MysticGold04 on 2009-04-13
I believe you do...

---

### Post by Lazy-buntu on 2009-04-13
Well that's bad :mad:

I'll probably just ditch it. It's not really urgent to have that installed, so I'd rather not clutter up a clean install.

Thanks for the help :popcorn:

---

### Post by MysticGold04 on 2009-04-13
If you dont want to install those libraries, check for an alternative application that will allow you to do the same thing... you might be able to find one.  I assume you are trying to make your own LiveCD?

---

### Post by Lazy-buntu on 2009-04-13
> **MysticGold04 said:**
> If you dont want to install those libraries, check for an alternative application that will allow you to do the same thing... you might be able to find one.  I assume you are trying to make your own LiveCD?

Not so much make my own LiveCD as make a back up of my freshly installed system. I used it on PCLOS Gnome 2008 to back up my install, so if I screwed it up some how I could install it and it would have my network settings, apps, printer, etc. all set up and ready to go.

---

### Post by Clancy_s on 2009-04-14
Or you could try getlibs, which apparently will sort out the 32 bits libraries needed for you, I've never needed it but the guns often recommend it.

[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

### Post by Yellow Pasque on 2009-04-15
When you use getlibs -i on a .deb, it just extracts the libs and puts them in /usr/lib32. getlibs doesn't install the other parts of the .deb

You don't need 32-bit versions of programs, only **libraries**. Try installing the packages it's asking for.

---

