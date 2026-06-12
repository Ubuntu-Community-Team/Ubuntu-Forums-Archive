---
title: "Ubuntu64 And Ati ??"
date: 2005-05-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by AndreAPL on 2005-05-09
hi there. have ubuntu 5.04, and fglrx (installed following the great tutorial  :razz: )
but still have 1 problem... glxgears runs anormally slow (1400-1700fps  :roll: ) and the image of d gears run in slow motion.... what is wrong ? already tested with internalAGP and external,same issue  :???: 
any idea ?

thanks

---

### Post by DutchLau on 2005-05-09
I'm not a wiz kid, but could you at least give a few more details of what you're using? Which ATI card, what your computer specs are, etc.

Thanks  :razz: 

DutchLau

---

### Post by AndreAPL on 2005-05-10
sorry, forgot to add sign  ](*,) 

AMD K8 2.8+, DFI NF3, Ati 9800se, Ubuntu 5.0 amd64
have installed xorg-fglxr from apt-get and workin, added all codecs(in my case to /usr/lib64/win32)... can't get this work right. or i can get movie play in kaffeine and doesnt work in totem (enters and exits)  ( ) or get totem working (xine) and kaffeine doesn't start. don't get it... totem runs video for a bit and gets crazy  :neutral: 
and games run anormally...
tryed do change internal_agp yes or no (in xorg) no, same result  :?

---

### Post by DutchLau on 2005-05-10
I'm running Ubuntu i386 (i686 kernel because the 386 kernel only supports upto 900mb ram) because there is still very little multimedia support for 64 bits. I didn't notice a substantial drop in performance and everything works fine with Hoary i386. There are some guides to install ATI cards here is one of them:

[http://ubuntuforums.org/showthread.php?t=3567](http://ubuntuforums.org/showthread.php?t=3567)

Make sure you install the ATI drivers for your card (I don't have any experience with them though)

IMO (don't rant at me for this) stick with i386 hoary for the moment and wait until flash and other multimedia codecs become available for Hoary 64  :-P 

Good luck!

DutchLau

---

### Post by songochain on 2005-05-11
Did u install fglrx from ati.com or from synaptic (apt)?? I've installed fglrx from ati.com and it has increased my fps rate (800 up)

---

### Post by chryz on 2005-05-12
I installed the drivers from [www.ati.com](www.ati.com) using the ati guide at:
[http://www.ubuntuforums.org/showthread.php?t=31094&highlight=firefox+sync](http://www.ubuntuforums.org/showthread.php?t=31094&highlight=firefox+sync)

fgl_glxgears: ~500-520 fps
glxgears: ~2750 fps

This is on a laptop running Amd Athlon 64 Mobile 3000+ with Ati Radeon 9700 - your scores should be higher than mine. Run fglrxinfo and verify that it says Ati Technologies, and not Mesa or something like that.

---

