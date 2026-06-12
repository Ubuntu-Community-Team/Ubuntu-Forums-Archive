---
title: "Flashplayer installing trouble"
date: 2007-02-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by eightbitstar on 2007-02-05
So I'm trying to get flashplayer onto my 64bit PC and for some reason, I can't install it! I am following instructions from this website: [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash ]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash")

I'll list my steps:

1] I first download the .tar.gz file.
2] I then right click the package and press extract here. (note, this file is on my desktop)
3] I am left with a folder containing four files.
4] I then navigate to the folder on the terminal typing in these commands:
    A) ls
    B) cd Desktop
    C) ls
    D) cd install_flash_player_9_linux
    E) ./flashplayer-installer
5] I then get this message: 

ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer.

6] I then try sudo ./flashplayer-installer and I come up with the same message!
What should I do?

(By the way, I have Ubuntu version 6.06 LTS for a 64 bit pc)

---

### Post by meng on 2007-02-05
Flash doesn't work on 64-bit architecture.

---

### Post by eightbitstar on 2007-02-05
Thank you. Now I'm switching back to windows. Good bye everyone.

---

### Post by Azakus on 2007-02-05
Uh, Flash DOES work on 64 bit
You use a program called nspluginwrapper to make the 32-bit linux Flash work on 64-bit Firefox. Very easy to do in fact.
Just follow this guide: [http://ubuntuforums.org/showthread.php?t=341727&highlight](http://ubuntuforums.org/showthread.php?t=341727&highlight)

---

### Post by meng on 2007-02-05
Didn't know that, thanks for the correction, but the OP doesn't appear to have much stomach for minor hassles by the looks of things. Hope he/she enjoys running Flash on 64-bit Windows. :D

---

