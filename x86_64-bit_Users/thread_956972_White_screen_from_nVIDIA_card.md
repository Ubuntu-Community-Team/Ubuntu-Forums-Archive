---
title: "White screen from nVIDIA card"
date: 2008-10-23
forum: x86 64-bit Users
---

### Post by JHSheridan11 on 2008-10-23
Hello all,
First let me describe my system: Kubuntu Hardy Heron 8.04, nVIDIA GeForce 7600GT, Two Acer X193w Monitors. 

Here's my story:
I've had my dual monitors set up for about a year now, but I decided to start over with a fresh copy of Kubuntu for various reasons. After the install, I do all of the updates needed. Then I try to get my dual monitors working. What always happens is I install the graphics card(I've tried using the Kubuntu Hardware Drivers thing, apt-get nvidia-glx-new, and envyNG). Then I use the old method from this thread [http://ubuntuforums.org/showthread.php?p=1773584](http://ubuntuforums.org/showthread.php?p=1773584) . That gets everything good to go but the resolution, which I simply fix with nvidia-settings. Everything works perfectly for around five minutes, then I'll go to apply a change(from changing icons, to setting desktop wallpaper), and the screen goes white. I've searched for people with similar problems but cannot seem to find anyone with this exact problem. 

Anyone have any clue? Any help is greatly appreciated. Just ask if you need to know anymore info

THANKS!

---

### Post by JHSheridan11 on 2008-10-27
Bump...Anyone?

---

### Post by xen-uno on 2008-10-27
Are you using the latest NVidia drivers? (from the NVidia site ... not repositories). It may help (along with the thread you pointed to).

---

### Post by skorchx7 on 2009-01-05
im having the same problem. i was using dual monitors for a few days. while working with the compiz effects panel one of the monitors abruptly shut off for no reason. thought it was because the drivers were somewhat unstable. decided to revert back to the single display. and heres where it went wrong...inside envyNG i uninstalled all the nvidia drivers it had installed for me. and i think it didnt modify the xorg.conf file the right way and left me with a blank white screen everytime i log into KDE.




-hp dv9000 running ubunti 8.10 intrepid
-nvidia gforce go 7600

---

### Post by IQRules on 2009-01-05
You can solve this easily by install envyNG software first. Then go to GUI, click and run envy, reboot. Make sure lsmod | grep nvidia, driver nvidia is loaded.

---

