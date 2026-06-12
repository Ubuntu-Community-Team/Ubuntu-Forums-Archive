---
title: "Thinking of going completely Feisty 64...advice needed"
date: 2007-08-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by philinux on 2007-08-09
Local pc builder is offering this spec base unit. Thinking of buying one to replace my ageing 
pentium  3 in Autumn. 
£270 for:

                                          ASUS M2N-MX or M2M4-SLi
                ATHLON 64 DUAL CORE 4600+
                       2GB (2x1GB) DDR2 800 MEMORY
                       250GB SATA300 HARD DISK
                                  16X DVD±ReWriter/RAM
                              INT. GeForce 6100 graphics
                                       5.1 SOUND & LAN
                               
Already running Feisty on my old machine. Have the 64 bit iso ready to go. I've seen some comments regarding Asus m2n-mx. So the big question what do I need to prepared for? Is it a good spec for Feisty64?

Any advice gratefully received.

---

### Post by nowhere.elysium on 2007-08-09
Should  be fine, dude. Personally, I'd sort out a better graphics card, though, because onboard ones aren't all that, but that's about all I'd change...
Just be prepared for some of your programs to return the error 'Wrong architecture: i386' when trying to install. It can be gotten around, but only if you're persistent.
dpkg -i --force-architecture should do it.

---

### Post by nss0000 on 2007-08-09
The ASUS-m2n mobos have ETHport, sound-chip & LM_Sensor issues for DAPPERx64. Make sure those are fixed in v_7.04.

---

### Post by Kilz on 2007-08-09
> **nowhere.elysium said:**
> Should  be fine, dude. Personally, I'd sort out a better graphics card, though, because onboard ones aren't all that, but that's about all I'd change...
Just be prepared for some of your programs to return the error 'Wrong architecture: i386' when trying to install. It can be gotten around, but only if you're persistent.
dpkg -i --force-architecture should do it.

Let me clarify the above. If you go on the internet and download i386 deb files you may have to force them in.

---

### Post by butcher99 on 2007-08-09
check on the threads with crashes on loading and installing.    Took me a long time to get it sorted and still not done.    you need to edit the boot line and add noapic nolapic nosplash to get it to boot or some people do.
 
more than a few posts about it.
jim

---

### Post by philinux on 2007-08-09
Thanks for replies so far,

Anythoughts on the ASUS M2M4-SLi mobo?

---

### Post by John.Michael.Kane on 2007-08-09
> **philinux said:**
> Thanks for replies so far,

Anythoughts on the ASUS M2M4-SLi mobo?

I would avoid it. Unless you can.
1) Find a forum member/etc who has that board, and install ubuntu on it with out issue.
2) Run a live Cd on the setup at the shop that is ordering the board for you. "Before you lay out cash"
3) Find out if the issues listed in posts above have been resolved. 

If it was me. I would look at other models that they offer that fit's your need/want, and post them here so that you can get help finding one that is supported.

---

### Post by stmiller on 2007-08-09
> **SD-Plissken said:**
> I would avoid it. Unless you can.


Yeah I've read comments that ASUS boards are not what they used to be. MSI is a good brand, I think.

That internal graphics card is good (Nvidia) for basic 3D, and will run UT2004/Quake 3 ok. But not fantastic. You can always try it now, and upgrade later (put in own video card).

---

