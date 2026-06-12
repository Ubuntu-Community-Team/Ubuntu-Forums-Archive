---
title: "OpenOffice2 won't start on Ubuntu 5.10 64bits"
date: 2006-02-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by HellSpawn on 2006-02-24
Hi...

   I've been useing Ubuntu 5.10 64 bits since it came out. I got a new Nvidia Card and installed the latest drivers from the Nvidia Web site, and now I can't start any OpenOffice module I only get this:

> 
igor@ubuntu:~$oowriter2

(process:28663): Gdk-WARNING **: locale not supported by Xlib

(process:28663): Gdk-WARNING **: cannot set locale modifiers

(soffice.bin.real:28663): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(soffice.bin.real:28663): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported


....etc...etc...

[COLOR="Red"]/usr/lib/openoffice2/program/soffice: line 224: 28663 Segmentation fault      "$sd_prog/$sd_binary" "$@"
[/COLOR]


I read, here and there, that it's a problem with OpenGL 32bits working in 64bits and oo.org useing it, there are some work arounds for som distros but I haven't get any of them working in Ubuntu.

Any ideas??
Thanks for your attention...
I have a strace output if anyone is interested... I don't quite know how to use it...

---

### Post by HellSpawn on 2006-02-27
I finally founf someone with the same problem, I just reinstalled OO.org and now it works ok again...

Thanks anyway

---

### Post by oxpack on 2006-02-27
I have had luck with it but there are some shortcomings I have noticed. My OpenOffice 2.0 shows 1.9.129. I finally left Debian Sarge to ubuntu just because OpenOffice actually loaded on the distribution and runs. So far I have noticed that in Draw the gluepoints dont quite work and that the help system is missing the icons. But for the most part it works.

---

