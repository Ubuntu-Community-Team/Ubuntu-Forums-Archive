---
title: "Random freezing: would like help."
date: 2008-01-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by Locuss on 2008-01-01
My computer keeps on freezing, at random intervals. Typically, it appears to be whenever the flash plugin is working in swiftweasel32, that the computer crashes. But that is not always the case. Sometimes its when I'm downloading something, or listening to music.

I've checked /var/log/messages, and dmesg, and theres no trace of any warnings, crashes, whatever. 

My platform: 

AMD Athlon X2 5200+ 90NM 
2GB DDR2 Ram
500 GB SATA drive
Ubuntu 7.10, with all updated software.

What can I do to find more information on this problem? Is this related to the recent AMD erratum?

---

### Post by megamania on 2008-01-01
> **Locuss said:**
> My computer keeps on freezing, at random intervals. Typically, it appears to be whenever the flash plugin is working in swiftweasel32, that the computer crashes. But that is not always the case. Sometimes its when I'm downloading something, or listening to music.

If you had not mentioned that it happens when the flash plugin is working, I'd say it is likely to be a hardware problem.

The last time I had a problem like yours, it was my sata hard disk cable...

---

### Post by Locuss on 2008-01-01
Thanks I'll check that in a little bit. As well, I'll be checking the power cables, they may be loose. It seems to happen mostly with the flash plugin, but again, that could be because of the demands it puts on the system(Thanks Adobe for yet another well-written software product!)

---

### Post by bigken on 2008-01-01
ramdom lockups like this are usually down to video drivers what is your video card ?

---

### Post by Locuss on 2008-01-01
My video card is an Nvidia Geforce 7300 SE. I'm using the nvidia-glx-new, at a graphics resolution of 1680x1050.

---

### Post by bigken on 2008-01-01
this what I would do to eliminate the card run sudo dpkg-reconfigure xserver-xorg
and select vesa as my video driver run the pc for a day or 2 and if the crashes still
happen if they do we can eliminate the nvidia drivers

---

### Post by Locuss on 2008-01-01
I'll try that, thanks

---

### Post by Locuss on 2008-01-03
Its been 24 hours, and no crashes. So, the vesa driver appears to only be able to handle 1024x768. I have a 22 inch lcd screen, I was wondering if there was another driver I could use, that is stable, would work on the nvidia geforce 7300 se, and has a bigger res than 1024?

---

### Post by bigken on 2008-01-03
take a look [here]("http://ubuntuforums.org/showthread.php?t=656093&highlight=Nvidia+Geforce+7300")

---

