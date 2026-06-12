---
title: "How to install gcrypt 32 compatibility libs ?"
date: 2007-08-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by interzoneuk on 2007-08-01
Hi.

I have all available 32 libs installed, except Java (i use 64 bit version).

I can run just about everything fine - doom3, flash, etc.

I am having issues running a game - paintball2 (really good fun btw) - [http://digitalpaint.planetquake.gamespy.com/](http://digitalpaint.planetquake.gamespy.com/)

It runs fine for a while then throws me out with a 

yossarianuk failed hardware check - message

Apparently it is due to not having 32 libraries of gcrypt installed.

Anyone know how to install them ?

I have the exact same issue on Kubuntu 64 as Gentoo 64 - pclinuxos 32 it works fine though on same machine.

---

### Post by chrisccoulson on 2007-08-01
What I do in situations like this is download the i386 deb, and extract the library files from /usr/lib in the package to /usr/lib32 on the system. You could try that with libgcrypt.

---

### Post by Cappy on 2007-08-01
Getlibs?
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

Just point it at the extracted binary you are running.
Maybe ```
getlibs -32 libgcrypt.so.11
``` if you can't find the binary.

---

