---
title: "USB 2.0 issues - ehci_hcd crappy?"
date: 2008-12-08
forum: x86 64-bit Users
---

### Post by tardeevo on 2008-12-08
My rig:
ASROCK with ATI780HD chipset, Athlon64 X2 Dual Core Processor 5200+, 4Gb ram, Kubuntu hardy 64.
All works fine except I am unable to use USB 2.0 speed and I need it badly cos I very often use an external storage HD and mc cards.
I (luckily) got another x86-32bit machine working perfectly with Hardy 32bit and here as well as windows XP on the 64 machine usb 2.0 data transfer work without a single hiccup. I tried also to install ubuntu 32 on the 64 machine but the results are the same: after a small while the data-transfer freezes and log shows lot of ```
[  407.021335] hub 6-4:1.0: cannot reset port 4 (err = -110)

``` error lines and my choices are to shut down the device OR to remove the ehci_hcd module with ```
sudo rmmod ehci_hcd
``` and after that I can now do a data transfer without any error but using usb1.0 unacceptable slow speed.
My questions are: does anybody else is experiencing this issues and had found a workaround or I am on my own? 
Does anybody knows if this is recognized as a bug and is on the way to be fixed?

---

### Post by lavinog on 2008-12-08
I am having similar issues on my 64bit machine... It is tough to troubleshoot because I cant recreate it every time.
I was thinking it was my hub, but recently I tried to transfer pictures from my camera connected to the back of my computer, and it failed half way through the transfer.

---

### Post by twade on 2008-12-09
I was also having that problem with 32 bit Hardy (so it's not just a 64 bit problem).  I think it's a new bug that's been introduced at some level.  I haven't noticed it with 64 bit Intrepid (but then again I haven't tried much).  The only solution I found was to do:
```

sudo rmmod ehci_hcd
sudo modprobe ehci_hcd

```
before connecting the usb device and attempting a transfer.

---

### Post by jhoderd on 2008-12-09
I have the same exact problem.  There are several reports about this in Launchpad, some of them dating back several months.  The Ubuntu kernel devs recommend that you disable ehci_hcd (modprobe -r ehci_hcd) until a fix is found  (I think that the Jaunty kernel suffers from the same problem, so you might have to wait for release 9.10).  The downside, of course, is that you loose high-speed USB...

---

### Post by kabaiz on 2008-12-30
Hey! There's always a solution! ...I believe! :)

It's about the 30th forum thread that I read ...my USB is getting better and better. Now, when I boot ubuntu, it recognises the disk well. If I unplug and plug again, I have about 50% chance ...at the begining it was about 15-20% and no boot time recognising :)

...maybe it would be a good idea to have a spell check here, like in gmail :) ...maybe there is, just I'm lazy to find it.

...my English is not the best :)

---

