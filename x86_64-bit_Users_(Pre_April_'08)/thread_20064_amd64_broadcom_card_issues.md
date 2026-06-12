---
title: "amd64 broadcom card issues"
date: 2005-03-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by BigCdaAnswer3 on 2005-03-15
hey all, i have an hp zv5000 laptop w/ a broadcom 4306 wireless card. I just downloaded ndiswrapper1.1 and compiled it from source. The next thing I did was to take bcmwl5.inf off of my windows xp drivers cd. I did

sudo ndiswrapper -i bcmwl5.inf
modprobe ndiswrapper
dmesg | tail

and this gave me:

ndiswrapper version 1.1 loaded (preempt=no,smp=no)
ndiswrapper (ndiswrapper_load_driver:92): loadndiswrapper failed (65280); check system log for messages from 'loadndisdriver'

any clues? is there some 32 or 64-bit issue here that I'm now aware about?

---

### Post by blinksilver on 2005-03-15
my friend those are the 32bit drivers linuxant has the 64bit one just google ndis wrapper linuxant, don't user their wrapper, but grabe the 64bit drivers off there site

---

### Post by almahtar on 2005-11-27
Here are some mistakes I made when I was trying to get ndiswrapper up that you may have made:

1.  You need the correct .sys file in the same directory as the .inf file
2.  You must be using a 64 bit driver.

That second one had me stumped forever.  If you suspect that this could be your problem, go [here]("http://www.linuxant.com/driverloader/drivers.php"), and grab the 64 bit drivers from the top of the list.

You may try ```
cat /var/log/kernel.log | grep ndiswrapper
```
and see what you get there.  Sometimes things that make it into kernel.log don't make their way into dmesg.  That was the case for me, and why it took so long for me to figure out the 32 bit 64 bit stuff.

*edit* I just noticed that you typed "bcmwl5.inf" up there... that's definitely the 32 bit driver just like blinksilver said.

---

