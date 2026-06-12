---
title: "amd dualcore - one core always at 100%"
date: 2008-04-26
forum: x86 64-bit Users
---

### Post by mogliii on 2008-04-26
Hi,

I just installed Ubuntu 8.04 64bit final on my desktop.

AMD 4000+ Dualcore. 2 GB of ram, motherboard with AMD 690 chip.

I am experiencing serious mouse-lags especially using firefox.
I checked the cpu-usage with the system monitor and was pretty surprised to see, that one core was busy at 100% all the time (screen shot).

[[IMG]http://img127.imageshack.us/img127/8964/cpuhistory1xh3.th.png[/IMG]](http://img127.imageshack.us/my.php?image=cpuhistory1xh3.png)

When executing "top", it showed that evolution-data- was using all of it.
I killed that process. However the lagging of the mouse pointer continued when using firefox. 

Just opening a google-search result would cause lags.

Before I had ubuntu 7.10 for 32bit installed, but never experienced lags as this.

Oh, I used EnvyNG to install the catalyst 8.47.3. I have a Ati X1250 on board.

Has anyone else experience anything similar?

---

### Post by mogliii on 2008-04-26
update:

I just restarted and the 100%-lag of evolution-data is gone.

But Firefox is still laggy.

---

### Post by inphektion on 2008-04-26
me too but opera 64 bit running well for me... I'll wait for firefox 3.0 final to try it again...

---

### Post by smileyme on 2008-04-26
> **mogliii said:**
> update:

I just restarted and the 100%-lag of evolution-data is gone.

But Firefox is still laggy.

Rebooting didn't fix it for me. I have been using 8.04 for about 3 weeks, and this is new with the final upgrade. I just keep killing evolution-data process.

Rick :)

---

### Post by mogliii on 2008-04-27
So I'm not the only one.

Well, a bit dissapointed as it is supposed to be final, but I will wait for updates and install opera in the meantime.

---

### Post by soxs on 2008-04-27
If you do nt require evolution stuff, simply remove it from the autostartlist. System > Preferences (I think so, running a german box) > Sessions

---

### Post by Mr. Sunshine on 2008-04-27
I'm running Hardy 64 bit and I've run into the same problem while trying to install the Ati fglrx 8-4 drivers manually. Which just won't install for whatever reason I can't understand.

When following the instructions, I edited the file

/etc/default/linux-restricted-modules-common 

and changed DISABLED_MODULES="" to DISABLED_MODULES="fglrx"

When I gave up and redownloaded the fglrx drivers from the Ubuntu repos, I got a very laggy Firefox, especially when scrolling the page. I didn't check CPU usage. **Turns out I forgot to change it back.** I did, then I ticked the Ati driver again in the Hardware Drivers dialog in the System menu. My Ubuntu is back to normal.

Wish I could use the latest driver, though. The one in Ubuntu repos is crap.

---

