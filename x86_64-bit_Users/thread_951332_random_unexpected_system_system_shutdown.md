---
title: "random unexpected system system shutdown"
date: 2008-10-18
forum: x86 64-bit Users
---

### Post by xigen on 2008-10-18
Hello,

My system
UbuntuStudio 8.04, Amd64, 2Gig RAM,

... will randomly freeze and then reboot.

first, I checked the CPU temperature.  the logs indicate a rock-solid 40 degrees Celcius over the past week.

I checked the RAM.  No defects found.

I moved my sound card (delta66) over a slot so my GPU fan on my ATI card would have plenty of room. 

... and still ... when I am using FireFox3, with no real obvious cause - my system will freeze/re-boot.

Here is the dmesg | tail after the last failure:
ilson@wilson:~$ dmesg | tail
[   42.868977] [fglrx] interrupt source ff00002c successfully enabled
[   42.869084] [fglrx] enable ID = 0x0000000B
[   42.869171] [fglrx] Receive enable interrupt message with irqEnableMask: ff00002c
[   42.869320] [fglrx] interrupt source ff00002d successfully enabled
[   42.869425] [fglrx] enable ID = 0x0000000C
[   42.869512] [fglrx] Receive enable interrupt message with irqEnableMask: ff00002d
[   42.869661] [fglrx] interrupt source 20000400 successfully enabled
[   42.869765] [fglrx] enable ID = 0x0000000D
[   42.869852] [fglrx] Receive enable interrupt message with irqEnableMask: 20000400
[   47.969464] eth0: no IPv6 routers present
wilson@wilson:~$ 


What would you suggest I do to solve the issue?

Cheers, MW

---

### Post by purefan on 2008-10-18
I have a similar problem but perhaps I should post in a new thread to avoid thread hijacking... but still maybe this helps, in my experience a faulty flash plugin was responsible for freezing the entire operating system, I dont really remember which other did I install but it worked, if you identify your problem as happening only when you browse youtube for example, then this may be the cause...

---

### Post by xigen on 2008-10-18
I have the flashplugin - nonfree 10.0.1.218 installed.

I just reinstalled it. Hopefully this will fix everything.

.. and yes, I have been using flash quite a bit lately:
[www.seeqpod.com](www.seeqpod.com)   - music
[www.songsterr.com](www.songsterr.com) - guitar practice
elections.nytimes.com/2008/president/debates/third-presidential-debate.html
 ** really terrific flash interface to watch the debates w/ text.

---

