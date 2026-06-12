---
title: "Update failure."
date: 2007-04-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by Tuxaby on 2007-04-13
Every time I try to install updates they fail and I get the response MD5mismatch.   And when I try to open the update manager I get a blank panel.  Help!  Lee

---

### Post by xopher on 2007-04-13
Try changing to a different mirror. Preferably a mirror near you. Run a ```
sudo apt-get clean
```, this shouldn't make a difference, but you never know - alway good to start clean.. And try different programs, eg. apt-get, aptitude, synaptic, update-manager.

And your internet connection is working as it should right? No corruption going on?

---

### Post by Tuxaby on 2007-04-13
This is a fresh install from disc of 6.06 LTS upgraded via the web to 6.1.   Then the only thing I have done so far is try just about every HowTo out there to get my Broadcom BCM4318 wireless to work.  No success there.   
Ran the code and tried Update manager and Synaptec.  Same results.  Aptitude is installed according to Synaptec.  How do  I access it so I can try it? and  how do   change Mirors?

---

### Post by Tuxaby on 2007-04-25
Finally found the problem with my update problems.   Turns out this affected all my computers on all operating systems.  Turns out that my Netgear WGR614v7 router was the cause.  After searching Netgears forum, I found Info that pointed to its SPI firewall.  Turned it off as recommended , having a software firewall on all systems for protection, and all download problems have cleared.   Hope this helps .  Thanks to all for your help.  Thanks, Lee

---

