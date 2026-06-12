---
title: "installing epson scanner"
date: 2008-08-31
forum: x86 64-bit Users
---

### Post by bregale on 2008-08-31
hi all i have spent quite a few hours now trying to to get my epson 
perfection 3170 scanner to work with hardy, not had any luck yet i have got xsane, it sees i have a epson scanner but still wont work i have read that some scanners are not supported, but surely there is a way round it any ideas welcome
     
  thanks:lolflag:

---

### Post by cariboo on 2008-08-31
According to the sane database there is good support for your scanner, you need DFSG non-free iscan-plugin-gt-9400, The only one I could find was this one:

[http://gentoo.netnitco.net/distfiles/iscan-plugin-gt-9400-1.0.0-1.c2.i386.rpm](http://gentoo.netnitco.net/distfiles/iscan-plugin-gt-9400-1.0.0-1.c2.i386.rpm)

As you can see it is an .rpm file so you will have to convert it to a .deb. To do the converison you will have to install alien, which is available in the repositories. To do the conversion, in a terminal type:

```
sudo alien -d iscan-plugin-gt-9400-1.0.0-1.c2.i386.rpm
```

Jim

---

### Post by bregale on 2008-08-31
thanks very much i will try that .

---

### Post by David1000 on 2008-09-05
I have exactly the same problem so I thought I will tag onto this thread.

I have an AMD 64 bit computer so should the i386 file work?  I tried converting the file with Alien and got a few error messages including:

"  dpkg-gencontrol: error: current host architecture 'amd64' does not appear in package's architecture list (i386)  "

Everything I've looked at appears to require a 32 bit system.

---

### Post by Crafty Kisses on 2008-09-05
Good tutorials and what not here.

For scanners you can look through this list > [http://www.sane-project.org/sane-mfgs.html](http://www.sane-project.org/sane-mfgs.html)



[http://www.linuxfoundation.org/en/OpenPrinting/Database/SuggestedPrinters](http://www.linuxfoundation.org/en/OpenPrinting/Database/SuggestedPrinters)

[http://www.linuxfoundation.org/en/OpenPrinting/Database/LinuxSupportByPrinterVendors](http://www.linuxfoundation.org/en/OpenPrinting/Database/LinuxSupportByPrinterVendors)

---

### Post by Indyviews on 2009-01-17
Hello, I have the same problem...I have download the DFSG non-free iscan-plugin-gt-9400 onto desktop and have extracted the files (also in a folder on desktop) and have also placed them in: filesystem.usr.lib. 

When I use sudo alien -d iscan-plugin-gt-9400-1.0.0-1.c2.i386.rpm in Terminal...I get:File "iscan-plugin-gt-9400-1.0.0-1.c2.i386.rpm" not found.  I believe I am close to getting my scanner to work and this may be the one item I need.

I am a newbie at this and my question is: Where do I put these files so they may be found?

I am on Ubuntu 8.10, use a 32bit system, have an Ebson Perfection 3170 scanner, and have Alien installed. Can someone help me?

---

### Post by stormtrooprdave on 2009-01-18
I had problems with an Epson Sx200 all in one and could not get scanning to work.  It is now working thanks to a post by Kaho in [this thread]("http://ubuntuforums.org/showthread.php?t=932547&page=2") (sorry don't know how to link to a specific post)

Hope this works for your model or gives some ideas

---

### Post by waster on 2009-03-23
commiserations to those unfortunate people like me who have an epson scanner.

there are no 64 bit libraries for linux. email epson to complain about lack of openness and lack of drivers.

there is a way of running i386 libs on a 64 bit platform - a new package appeared in jaunty to do this (it automatically fetched the 386 libs somehow) but i cannot remember the name of the package. this is probably our best hope.

---

