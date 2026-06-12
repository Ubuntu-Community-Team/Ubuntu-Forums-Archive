---
title: "sd trouble"
date: 2007-11-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by palletjackracer on 2007-11-24
I searched for 'sd' and 'sd card' but no one seems to have issues with this yet.  I'm running 64bit gutsy on a toshiba u205.

When I first installed gutsy I installed the 32bit version using the graphical installer.  A friend said I should check out the 64bit version because it was coming along nicely.  I also wanted to try out full hard drive encryption so this meant using the 64bit text based installer.

Everything installed just fine.  Most things work.  There are 2 things I'd like to get working.  One is the suspend functionality (it worked with the 32bit version) but I'll save this for another post.  The second is the sd card reader.  This worked in Edgy (I didn't test it in 32bit gutsy before I went to 64bit).

I'm not sure where to begin testing so if someone could walk me through I'd appreciate it.  In Edgy it would auto mount when inserted and unmounted fine when asked to do so.  Everything worked as it should.  In Gutsy, as far as I can tell, it does not auto mount and I can't seem to locate it in /dev

Thanks for any help you can give.

---

### Post by dabl on 2007-11-24
I'll assume you actually have a 64-bit CPU, with which to run the 64-bit OS.

I bought an el-cheapo SD card reader -- the brand name is "Dazzle" and I got it at Circuit City a year ago.  It is on a USB cable -- you just plug it in.  I think it cost USD $19.00.  It worked fine in Edgy, in Feisty, and now in Gutsy, so I think it's a safe bet.  :)

---

### Post by palletjackracer on 2007-11-24
The processor is an Intel Centrino Duo.  I am assuming that it is 64bit, but I'm not totally sure.  Is there a way to tell?

Ok, so I did some more research and found out that the Core Duo isn't 64bit, only the Core 2 Duo is.  I'll install the other version.

---

### Post by Jouke74 on 2007-11-26
About the SD card reader: I had the same. In Edgy it worked fine, in Fesity and later it failed to do anything. The answer to that question is that with the newer kernels (I think as of 2.6.18) they changed something with the EHCI driver (for USB). The end result is that it connects and disconnects a few times in my case, and then it is considered faulty. The real problem is that probably my usb card reader does not notice any activity of my side and puts itself into sleep state, which Ubuntu does not like. This happens in less than a minute or so, so now I connect the cardreader with SD in there only when I need it, then it seems to work. I hope it is of any help, but I am afrid it won't be...

---

