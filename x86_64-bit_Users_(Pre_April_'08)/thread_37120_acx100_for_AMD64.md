---
title: "acx100 for AMD64"
date: 2005-05-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by copperhead on 2005-05-25
I bought a Compaq R3000Z laptop, and tried out the 64bit live cd with Ubuntu.  Everything seemed to work fine except for the wireless card... it's broadcom, so I expected it.

I had a D-Link DWL-650+ card, and I know that it uses the ACX100 drivers ([http://acx100.sourceforge.net/)](http://acx100.sourceforge.net/)), and the wiki on this site said that "it just works".  However, when I installed the AMD64 version of Ubuntu, the card didn't work.

It seems to detect it in the Device Manager, but there are no acx100 drivers to be found on the install.  Should I just install the 32-bit version and try from there, or is there a quick fix to my dilema?

---

### Post by stevenyu on 2005-05-26
if you want to use the ndiswrapper, you will need to use the 32bit Intel version of ubuntu

---

### Post by copperhead on 2005-05-26
[QUOTE=stevenyu]if you want to use the ndiswrapper, you will need to use the 32bit Intel version of ubuntu[/QUOTE]
My understanding is that I shouldn't need to use ndiswrapper, since there are native drivers for the chipset.

---

### Post by stevenyu on 2005-05-26
[QUOTE=copperhead]My understanding is that I shouldn't need to use ndiswrapper, since there are native drivers for the chipset.[/QUOTE]

You can give it a try, however I never got ACX100 driver to work under WEP, it will only work with no encryption on the wifi channel :neutral:

---

### Post by copperhead on 2005-05-26
[QUOTE=stevenyu]You can give it a try, however I never got ACX100 driver to work under WEP, it will only work with no encryption on the wifi channel :neutral:[/QUOTE]

Ok... consider me a newbie.  Where do I look to get the acx100 driver?  Should it already be here?  Do I need to install a special package?

I'm not using WEP, so that's not a concern.

---

### Post by stevenyu on 2005-05-26
the acx100 driver is already included in the kernel module

---

### Post by ::DoGG:: on 2005-05-27
Try this:
[http://cmb.phys.cwru.edu/kisner/linux/compaq-r3000/](http://cmb.phys.cwru.edu/kisner/linux/compaq-r3000/)
great installation description on presario r3000, i used that, also check out the mailing list (You will find a link above) about linux on Presario on R3000.
P.S. I got R3004US but can`t help, no Broadcom chipset in mine machine :D

---

