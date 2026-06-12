---
title: "ndiswrapper: doesnt detect wifi"
date: 2007-05-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by alek66 on 2007-05-05
Today a friend to my place, he owns a Acer travelmate 4100. He was able to connect to an open wifi spot, that my neighbour shares with me. But, i couldnt. The thing is that I was able to connect to it some months ago, but now I cant. There isnt any mac address filter.
My laptop is a acer aspire 1522. my wifi runs under ndiswrapper:
 > alek@DeathStar:~$ ndiswrapper -l
neti2220 : driver installed
        device (17FE:2220) present

> alek@DeathStar:~$ ndiswrapper -v
utils version: 1.9
driver filename:       /lib/modules/2.6.20-15-generic/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.38
vermagic:       2.6.20-15-generic SMP mod_unload 
alek@DeathStar:~$ 

What can I post to be more especific so that you can see if there ir any problem.

---

### Post by ronocdh on 2007-05-05
You may get more help by posting in the wireless forum, old chap.

---

### Post by alek66 on 2007-05-07
I fix it!
The wifi radio was off and I turned it on by pressing the wifi button on my laptop. The pretty odd thing is that in previous ndiswrapper versions I didnt have to press the wifi key.
try bizarre... right?

---

