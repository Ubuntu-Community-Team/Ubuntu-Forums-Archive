---
title: "Network Booting?"
date: 2006-02-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by Jagged on 2006-02-24
I can't seem to find whether this was addressed yet here. I'd like to find out how to install using the network I have. I am mass installing Ubuntu and the cd's are kind of annoying.

---

### Post by ssam on 2006-02-24
would the oem installer help you? i think that lets you install on one machine and clone the install.

also have a look at [https://wiki.ubuntu.com/Installation](https://wiki.ubuntu.com/Installation)

---

### Post by Jagged on 2006-02-24
[QUOTE=ssam]would the oem installer help you? i think that lets you install on one machine and clone the install.

also have a look at [https://wiki.ubuntu.com/Installation](https://wiki.ubuntu.com/Installation)[/QUOTE]
I considered that, but I am using g3 Imacs...so it's a real pain to take out hard drives!

---

### Post by ssam on 2006-02-24
do you have a network share large enough to host a drive image?

you could mount the share from a live cd and dd /dev/hda to the share on the installed machine, and the opisite on the others.

for three machine it might just be quicker to burn three copys of the live cd and do the installs at the same time. there are very few questions on the default install. (the expert install can cause problems, so i dont recommend it)

---

### Post by Jagged on 2006-02-24
I have a server I can put it on. I'm just not familiar with network booting a mac.

---

### Post by Jagged on 2006-02-24
I am installing on tray loading Imacs if it helps any

---

### Post by Jagged on 2006-02-24
Also, do you mount network drives pretty much the same way as physical drives... just give linux the path?

---

### Post by jdp on 2006-02-24
I'm not positive on how to setup the boot server, but to get the Macs to boot from the network you can either enter the commands in Open Firmware, or use the Option boot menu where it should probe the network for a boot server.

---

### Post by Jagged on 2006-02-25
Thanks...I'll see what I can do with that.

---

### Post by ninotob on 2006-02-28
Have I got a deal for you!  ;-)  Here's how I did a netinstall of ubuntu on a g3 ibook:

[http://www.ubuntuforums.org/showthread.php?p=311246#post311246](http://www.ubuntuforums.org/showthread.php?p=311246#post311246)

---

