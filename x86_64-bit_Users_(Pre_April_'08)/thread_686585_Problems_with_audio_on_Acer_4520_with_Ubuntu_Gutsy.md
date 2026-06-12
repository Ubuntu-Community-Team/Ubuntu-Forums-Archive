---
title: "Problems with audio on Acer 4520 with Ubuntu Gutsy 64 bit"
date: 2008-02-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by mittaldeepak01 on 2008-02-03
Hello All, 

I have almost everything working on my Acer 4520 (AMD 64 bit) running Ubuntu Gutsy 64 bit except sound card and microphone. 

Does somebody have any tips on getting this working. I don't know if it has something to do with kernel - my kernel version is 2.6.20-15-generic

Any help/pointers?

Best Regards,

-Deepak

---

### Post by mittaldeepak01 on 2008-02-04
Hi got this working on my machine finally. 

Here are the steps that I did : 

- Added the following line in /etc/modprobe.d/alsa-base : 
   options snd-hda-intel model=acer
- Added the following line to /etc/modules
   snd-hda-intel
- compiled alsa-driver from source (when doing this step, it is important to run "configure step" using "./configure --with-cards=hda-intel".
- compiled alsa-lib from source
- compiled alsa-utils from source

And rebooted the machine :)

Regards,

-Deepak

---

### Post by airputihdingin on 2008-02-20
how to save alsa-base?

---

