---
title: "Freezing"
date: 2005-08-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by ontelo on 2005-08-13
Weird problem with Ubuntu 5.04 64 version.

I'm new to linux so I don't really understand why this is happening;

First time I tried to install ubuntu, the installation progress freezed in stage 2. I tried again and it went bit longer but still freezed. Third time the installation was successfull but after the login ubuntu freezed again.

Sounds like hardware conflict with unixbased systems. (windows xp works perfectly). 

MSI K8N Neo Platinium (nForce 3)
A64 +3000
Geforce 6800 GT
Audigy 2

Any ideas?

---

### Post by gylf on 2005-08-13
Try disabling USB 2.0 in the bios.
I had odd lock-ups using Warty w/ USB 2.0 on my MSI motherboard, so its worth a shot.

And of course, disable any other odd setting in the bios that might be causing hardware problems (turn down the AGP multiplier, don't overclock, etc), at least until you resolve the issue.

EDIT: I see this is a 64 bit machine.  My brother had similar problems (with both 64 and 32 bit Ubuntu).  Do some searchs on the forum because there are a number of people who are having this issue.

---

### Post by gylf on 2005-08-13
Here is a post that might help: [here.](http://ubuntuforums.org/showthread.php?t=35455&highlight=64)

---

### Post by ontelo on 2005-08-13
I understood that this has something to do with Video card driver? So linux doesn't fully support newest cards? Vesa-drivers seems to be only way. Well I had to try that, will be repoting back soon.

---

### Post by angro on 2005-08-14
[QUOTE=gylf]Here is a post that might help: [here.](http://ubuntuforums.org/showthread.php?t=35455&highlight=64)[/QUOTE]


Dgee tnx....   After trying Suse93, Fedora4, Solaris10, and some already deleted distros I tried Ubuntu Hoary.   **Freezed**   ](*,)  ](*,) 

Got your possible solution (X11 => vesa)  and indeed it helps.   Doesn't freeze anymore.  

 :grin:  You saved my nerves, my computer and my family life (they got malucko whenever i spoke "Linux" :wink: ).

---

### Post by ontelo on 2005-08-14
Is there any disadvantages of this method like little slowing in drawing graphics.

But anyway, how this can be applied when installation freezed at stage 2.

---

