---
title: "Help with Flash player in mozilla..."
date: 2005-08-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by ROUBOS on 2005-08-26
Hi, 
There is nothing mentioned in UbuntuGuide for installing flashplayer in AMD64.
Can someone tell me how to install it?

---

### Post by tseliot on 2005-08-26
It is not available for 64bit systems. If you want to use it you have to create a  32bit chroot then install firefox 32bit (in synaptic 32bit) and its flash plugin.

here's a good HOWTO about chroot:
[http://www.ubuntuforums.org/showthread.php?t=24575](http://www.ubuntuforums.org/showthread.php?t=24575)

---

### Post by Corbelius on 2005-08-26
...or install gplflash version 0.4.12 (0.4.13 crash) : [http://www.steiner-web.info/rafael/flash/](http://www.steiner-web.info/rafael/flash/)

---

### Post by rplantz on 2005-08-27
[QUOTE=Corbelius]...or install gplflash version 0.4.12 (0.4.13 crash) : [http://www.steiner-web.info/rafael/flash/](http://www.steiner-web.info/rafael/flash/)[/QUOTE]

...which caused my Firefox to freeze.

dpkg would not remove it. I managed to get my Firefox back by removing /usr/lib/mozilla/pluging/libflash-mozplugin.so

Bob

---

### Post by thelung on 2005-08-31
[QUOTE=rplantz]...which caused my Firefox to freeze.

dpkg would not remove it. I managed to get my Firefox back by removing /usr/lib/mozilla/pluging/libflash-mozplugin.so

Bob[/QUOTE]

Yeah, gplflash crashes my browser too.

---

### Post by Corbelius on 2005-08-31
[QUOTE=thelung]Yeah, gplflash crashes my browser too.[/QUOTE]

Nope with Epiphany.

---

### Post by rplantz on 2005-08-31
[QUOTE=Corbelius]Nope with Epiphany.[/QUOTE]

Yes, on the Epiphany I got from Synaptic.

On the other hand, thanks for telling me about Epiphany. It's really fast on my machine. I'm going to try it for a while.

Bob

---

