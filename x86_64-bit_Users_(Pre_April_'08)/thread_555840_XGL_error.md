---
title: "XGL error"
date: 2007-09-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by revchris on 2007-09-20
I was trying to install compiz-fusion (after having Beryl running on Ubuntu 32-bit I thought I'd give the CF a try) following this howto: [http://ubuntuforums.org/showthread.php?t=488385](http://ubuntuforums.org/showthread.php?t=488385)   (I also tried this [http://ubuntuforums.org/showthread.php?t=508769&highlight=ati](http://ubuntuforums.org/showthread.php?t=508769&highlight=ati) )
but when I try to start just the XGL sessions an error comes up for a about a second then the screen goes black with an X for my mouse.  Where can I find the log for that session?
I do have the newest ATI 64-bit driver, could that be the problem?  If so, how do I un-install the new one and re-install the old one?

On a side note, I did get Enlightenment (e16) running yesterday.  Its just not the same as beryl though.

---

### Post by Jouke74 on 2007-09-20
I had the same problem once or twice and to be honest I can't figure out why (I have tried). The thing that worked for me was to reinstall XGL server and it's dependencies. Sudo apt-get XGL server seems to forget these once in a while (3 files should be installed), or use synaptic.

I think the order of install steps is also important. Really start with the FGLRX drivers reboot and then XGL. FGLRX should be running correctly (which is not always true).

It's annoying.

---

### Post by revchris on 2007-09-21
What are the 3 files that need to be reloaded?

Oh and the error reads: Cannot open display

---

### Post by Jouke74 on 2007-09-22
Hmm see this one : [http://ubuntuforums.org/showthread.php?t=500416](http://ubuntuforums.org/showthread.php?t=500416)
If still causing problems, change the display to 0.

---

