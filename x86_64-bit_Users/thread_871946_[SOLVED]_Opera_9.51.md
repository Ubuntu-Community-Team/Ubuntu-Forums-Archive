---
title: "[SOLVED] Opera 9.51"
date: 2008-07-27
forum: x86 64-bit Users
---

### Post by coolbrook on 2008-07-27
Does anyone know how to uninstall Opera 9.50 beta 2 so that 9.51 can be installed.  An upgrade does not work.  I tried removing from terminal and Synaptic but Opera still shows up in the Applications menu.  When I try to install the new .deb, 'About Opera' still shows Opera 9.50 beta 2 (Synaptic says that 9.51 is installed.)

---

### Post by thewolf32 on 2008-07-27
Have you tried the "completly remove" option in Synaptic?

---

### Post by coolbrook on 2008-07-27
Already tried it.  The only result is that I have no Opera option in Synaptic.  The Opera beta's still installed.

---

### Post by nikgare on 2008-07-27
Are you sure that it isn't just a case of Opera reporting the wrong version number?

---

### Post by coolbrook on 2008-07-27
Of that I'm not certain, but I do know that it won't remove from the system. (for example if I just wanted to uninstall without installing a new version.)

---

### Post by nikgare on 2008-07-27
How did you install the beta on your system? Presumably not via dpkg or synaptic?
Maybe it's in a folder in your home folder and you just need to remove it/uninstall it

---

### Post by vanden12 on 2008-07-27
have you tryed...

sudo apt-get remove Opera....

and to remove the configuration

sudo apt-get remove --purge opera

---

### Post by Sef on 2008-07-27
> have you tryed...

sudo apt-get remove Opera....

and to remove the configuration

sudo apt-get remove --purge opera

All that is needed to do is the latter command.

---

### Post by coolbrook on 2008-07-29
> **vanden12 said:**
> 

sudo apt-get **remove --**purge opera

Thanks.  I bolded what I omitted.  I ran this command and this is what terminal tells me...

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package opera is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

..but I can very easily still run the old Opera beta from the Applications menu. :confused:

---

### Post by drken on 2008-08-03
Thanks for the info!  I tried Opera 9.51 and did not like it at all, and wanted to remove it but didn't have a clue.  I tried the Add/Remove under Applications, but no dice.  I just installed Ubuntu 8.04 this week on a new laptop I purchased just for this purpose (my other machines are all WinXP) and am tring my hardest to learn linux.  I am very favorably impressed with Ubuntu 8.04 (tried RedHat and earlier Ubuntu distributions in the past and hated them) but this is super!  In the 5 days I've been using this system exclusively, removing Opera was the only sore spot I've encountered thus far.

---

### Post by TenPlus1 on 2008-08-03
Hmm, bit strange that removing opera using synaptic doesnt seem to work for you properly...  How about deleting the .opera directory in your home folder then re-installing the latest version 9.52 ?

---

