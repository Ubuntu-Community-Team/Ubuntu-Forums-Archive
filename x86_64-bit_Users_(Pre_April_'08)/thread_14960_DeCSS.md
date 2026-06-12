---
title: "DeCSS?"
date: 2005-02-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by Reb on 2005-02-11
Title says it all... does Ubuntu have any means of playing DVDs?

---

### Post by wallijonn on 2005-02-11
go to the FAQ/HOWTO SECTION  - you have MPlayer... just do a sub search for DVD.

---

### Post by Sleeper Service on 2005-02-11
If you get the libdvdcss2 package installed, you ought to be able to play DVDs using any media player you've got installed.  Totem, Xine, etc.

Here's a quote from an [Ubuntu Multimedia HOWTO](http://www.oldskoolphreak.com/tfiles/hack/ubuntu.txt):

> Playing DVDs
------------
The Ubuntu Wiki discusses restricted formats [4], which include CSS and
DVD playback.  To add DVD playback capability to Ubuntu, use your favorite
text editor and add the following line to your /etc/apt/sources.list file.

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main

Then sync your package index and grab the infamous DeCSS.

$ sudo apt-get update
$ sudo apt-get install libdvdcss2

Hope that helps, but shout if you need any more help...

---

### Post by Reb on 2005-02-15
On AMD64... I should have mentioned that. The FAQ didn't explain it. Maybe I'w slow.

---

### Post by GeBo on 2005-02-15
On this same forum (Topic: Some missing software on Ubuntu AMD64) I've read the following: 

You can get libdvdcss2 by running ```
/usr/share/doc/libdvdread3/examples/install-css.sh
```
However,  later on I read about an extra option to /etc/apt/sources.list. (Sorry, I can't find the url at this moment...) If you add 
```
deb http://cyberspace.ucla.edu/marillat/ unstable main
```
to your sources list, and use the following key 
```
gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 1F41B907
```
This will give you Marillat's AMD64 packages.

Success!

---

