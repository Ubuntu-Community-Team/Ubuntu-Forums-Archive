---
title: "Printer won't work..CUPS is installed"
date: 2005-07-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by tachum on 2005-07-21
HI,

I have installed Kubuntu (and now Ubuntu) on AMD 64. Two things don't work; Flash (enough said) and the printer. Now I have XP, Mandrake LE 64 bit and Suse 9.3 64 bit all working on this machine, and the Lexmark E210 works fine on all the others. 

During boot up it says that CUPS is installed, but when you go to print, it says it ain't. A print job will get the printer 'whirring', but that's it. I thought it might be firewalled on port 631, but that's fine, too. Stumped at the moment. 

Thoughts???

Update: Thanks for the quick response. I will look at that in a minute. The problem seems to be that the printer is locked in 'paused' mode, as per the status output:

Paused: Unable to open parallel port device file "/dev/lp0": Permission denied

Does that help????

---

### Post by az on 2005-07-21
Flash:  Enable the universe repository and install flashplayer-nonfree.  Flas does not ship with Ubuntu because it is proprietary.  Nuff said.  Look on the wiki about RestrictedFormats (wiki.ubuntu.com/RestrictedFormats)

Lexmark:  I think it uses the gimprint driver?  I do not think it is installed by default?  Look in synaptic...

---

### Post by tachum on 2005-07-21
Update: Thanks for the quick response. I will look at that in a minute. The problem seems to be that the printer is locked in 'paused' mode, as per the status output:

Paused: Unable to open parallel port device file "/dev/lp0": Permission denied

Does that help????

---

