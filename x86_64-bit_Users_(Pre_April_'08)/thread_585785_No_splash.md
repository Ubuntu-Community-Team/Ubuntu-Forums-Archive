---
title: "No splash?"
date: 2007-10-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by Origin on 2007-10-21
Loading Gutsy from livecd worked just fine, but after it was installed, when I turned on my laptop, it would go into a black screen for about ten minutes, then after hearing the hard drive scream for ten minutes, I am finally at the login screen. Previous versions of ubuntu took less than a minute to get through the initial boot-up stages, and it had a working splash. But now it doesn't, and it takes forever to load.

I thought it was a memory problem so I bought a new stick of memory (1 gig) and installed it. Now, even after 25 minutes, my laptop wouldn't get off the black screen--and the hard drive is still screaming. If I turn off the splash option on boot, it goes much faster (2 mins max) and shows me updates on what is being loaded, etc. But when I am logged onto the desktop, my wireless card doesn't work (it worked before I got the memory upgrade), my mounted windows partition disappeared, and all sorts of madness burst out.

What's the problem here? I don't understand. I can't get any networking on my ubuntu so I'm forced back onto my XP :(

I have a Compaq Presario v2565us with an AMD Turion-64 (model #32) and, after the upgrade, 1.5 gigs of ram. My wireless card is the notorious BCM4318, but it worked just fine with ndiswrapper before the memory upgrade. What's up now? :( Do I have to reinstall the whole OS, after I've spent days customizing it to my liking?

Thanks a lot. I really appreciate it.

---

### Post by picopir8 on 2007-10-22
There is a bug with the splash with the x64 version on some computers.  At the boot menu, hit "e" to edit the boot command, remove "splash" or replace it with "nosplash", hit enter to commit the change, hit "b" to boot.  It should boot just fine.

---

### Post by misfitpierce on 2007-10-22
You can do that or if that does not work you can hit CTRL ALT F1 to continue botting after a minute. Then there is a fix online about screen not coming up and it will make new startup image. 

 Friend installed 64 bit didnt get this but I did on 64 bit :( lol. Oh well got fixed now so w/e.

---

