---
title: "System freezes too often"
date: 2008-04-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by bedege on 2008-04-07
Hello

I've just installed a fresh new Ubuntu 7.10 distro on my neighbor's machine : Dell desktop computer with an AMD64 CPU. I've also installed the Nvidia drivers, Automatix and the codecs to read DVD, plus the Flash plugin from Adobe (r115)

The system hangs from time to time (every 15 minutes or so). It's a complete system freeze, with no Ctrl-Alt-Backspace escape. Only the on/off button helps ! Sometimes, that happens when surfing the net (possibly with some Flash content), sometimes doing no surfing at all but simply being connected.

I've had a look to the logs in /var/log and found nothing really stunning that could explain  this behavior.

Any clue or hint ? Where should I look next to have a fully working system. It's hard to convince one's neighbor about Linux when the PC crashes too often !

---

### Post by Jouke74 on 2008-04-07
And it worked fine under Windows, or were crashes the reason for installing Ubuntu? The first major concern you should always have with random crashes fully stopping the system is memory problems. If you start Ubuntu there is an option in Grub to do a memtest (pressing Esc while it counts down, or shown straight in the boot menu). Let this program run for a few hours, until it has at least 7 passes. If any errors show up than that is the reason. If it crashes here, memeory is also the reason(!)

If the computer has a hard crash it cannot write anything to the logs anymore. Hence, you won't find it there.

If memory is no problem then start installing a clean Ubuntu. Test this for a couple of days, and then add software slowly until you have found the offender. 
(Likely Nvidia drivers, Automatix, Flash).

---

### Post by bedege on 2008-04-08
Thanks for the advice. Again, it is my neighbor's PC, so I do not know it very well. Apparently, he never had any issue while running Windows XP ;-( but a mem test does not hurt.

OTOH, it is a clean and recent install of Ubuntu 7.10 (200+ packages to upgrade after install !). Maybe Automatix or Nvidia, flash are not that reliable on AMD64 ?

---

### Post by Jouke74 on 2008-04-08
"Maybe Automatix or Nvidia, flash are not that reliable on AMD64?" Could be anything. Generally they are ok, not particularly unreliable, but with installs things more often go wrong.

---

### Post by davepimp00 on 2008-04-08
When if freezes are you by chance running myspace on firefox??

---

### Post by njparton on 2008-04-08
Remove compiz and set metacity to be the default gnome window manager.  That cured a lot of ills for me including lock ups, long boot times and long times from login to a working desktop.

---

### Post by bedege on 2008-04-08
> **davepimp00 said:**
> When if freezes are you by chance running myspace on firefox??

When the system freezes, sometimes I am running Firefox (possibly with Flash animations running), but not always. It is not that deterministic, unfortunately !

---

### Post by bigtony on 2008-04-08
I also have 7.10 running on a new Dell Inspiron with an AMD Athlon 64 X2 (5000+) that kept hard locking.

I fixed the problem by going to System - Preferences - Power Management - The "On AC Power" tab, and slide both of the rulers to never put the computer or display to sleep. That has completely resolved my problems. 

To me, this makes since because Dell has been marketing it's desktops as energy efficient and my computer seems to adjust it's fan speed on it's own. (I love the way my new Dell "revs" it's fans when it first power on).  I guess Dell's intergrated power controller doesn't like Ubuntu's power management.

I hope this helps you too.

---

### Post by Kilz on 2008-04-08
IMHO its probably the nvidia drivers or a memory (bad ram) problem. 
Linux tends to allocate  more memory, that may be a reason xp doesn't show the issue. 
Another question, is the installed Ubuntu 64bit or 32bit? You say amd64, but are you referring to the software or the hardware. The reason I ask is you say you are using the r115 release of flash. This is quite buggy, but I have never heard of it causing a complete system freeze.
Lastly, Automatix is [a known culprit for system instability. ]("http://mjg59.livejournal.com/77440.html") At one time (Breezy Badger) Automatix was a necessary evil. But nowadays a user can easily install most of what Automatix installs. A side benefit is that when you do it yourself you gain knowledge about how to do things.

---

### Post by bedege on 2008-04-08
> **bigtony said:**
> I also have 7.10 running on a new Dell Inspiron with an AMD Athlon 64 X2 (5000+) that kept hard locking.

I fixed the problem by going to System - Preferences - Power Management - The "On AC Power" tab, and slide both of the rulers to never put the computer or display to sleep. That has completely resolved my problems. 


Was this Power management issue locking your computer while you were away from it and the system inactive, ie shifting to a low consumption mode or sleep, or could that happen while you were actually in front of it and doing real stuff ? For me, the latter case is true: the system freezes while using it !

---

### Post by bedege on 2008-04-08
> **Kilz said:**
> 
Another question, is the installed Ubuntu 64bit or 32bit? You say amd64, but are you referring to the software or the hardware. The reason I ask is you say you are using the r115 release of flash. This is quite buggy, but I have never heard of it causing a complete system freeze.
Lastly, Automatix is [a known culprit for system instability. ]("http://mjg59.livejournal.com/77440.html") At one time (Breezy Badger) Automatix was a necessary evil. But nowadays a user can easily install most of what Automatix installs. A side benefit is that when you do it yourself you gain knowledge about how to do things.

The Ubuntu I installed is 64bit, 7.10 desktop edition. The Flash release I'm using is the latest from Adobe's web site. It might be buggy, but OTOH I've read post/blogs for 64bits Ubuntu users were actually advising this version.... Where can I get an older flash release ?

I've also discovered that Automatix can also cause misbehaviors. I plan not to use when I'll upgrade to 8.04 Hardy !

---

### Post by Kilz on 2008-04-08
> **bedege said:**
> The Ubuntu I installed is 64bit, 7.10 desktop edition. The Flash release I'm using is the latest from Adobe's web site. It might be buggy, but OTOH I've read post/blogs for 64bits Ubuntu users were actually advising this version.... Where can I get an older flash release ?

I've also discovered that Automatix can also cause misbehaviors. I plan not to use when I'll upgrade to 8.04 Hardy !

You can get the older one in the flash sticky post. But I don't think that is your problem. I have been dealing with flash issues a long time. I have never heard of flash freezing everything. I would suggest looking at the video drivers.

---

### Post by bigtony on 2008-04-09
> **bedege said:**
> Was this Power management issue locking your computer while you were away from it and the system inactive, ie shifting to a low consumption mode or sleep, or could that happen while you were actually in front of it and doing real stuff ? For me, the latter case is true: the system freezes while using it !

My system would go to sleep and lock up even while I was using it.

---

### Post by bedege on 2008-04-29
Hello

Just to let you know that I solved this issue last week-end by fresh installing Hardy 64 bits. The system is now stable and runs smoothly. I've taken advandtage of your comments in:
- not using Automatix. Libdvdcss2 is installed directly from medibuntu
- disabling power management
- not using Nvidia restricted drivers but coping with open source drivers
- disabling compiz or fancy eye-candy effects

And everything is now fixed, as far as my neighbor told me !

Thanks for your help

---

