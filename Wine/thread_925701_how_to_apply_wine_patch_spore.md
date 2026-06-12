---
title: "how to apply wine patch? spore"
date: 2008-09-20
forum: Wine
---

### Post by Frontierbacon on 2008-09-20
hello

im trying to get the game "spore" to run properly in wine, anyway the questions/problems i have shouldent be related to the game itself, its a wine thing i believe.

i have ubuntu 7.10 with wine-1.0 ( installed from the synaptic)
here is the wine appdb entry for spore : [http://appdb.winehq.org/objectManager.php?sClass=version&iId=12614](http://appdb.winehq.org/objectManager.php?sClass=version&iId=12614)

in the comments section theres a link posted to a patch for wine 1.1.4 ( [http://bugs.winehq.org/attachment.cgi?id=15516](http://bugs.winehq.org/attachment.cgi?id=15516) ) that should make the game run fine.

so heres the problems.
im relatively new to linux and have no idea how to apply this patch?
and secoundly, if the patch is meant to go on wine 1.1.4 how do i get that? the latest version i can get from synaptic is 1.0.. and if i look at deb package archive ( [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html) ) the highest there is for ubuntu 7.10 is wine 1.0 ... 1.1.4 is only for ubuntu 8.04 . i tried downloaing the 1.1.4 deb package anyway but i cannot install it.. theres several dependencies which is not satisfied (libldap-2.4-2 etc)

so i guess it comes down to this.

1 : can this patch just the same be applied to wine 1.0. or does it only work in 1.1.4? and if so, can i get 1.1.4 without upgrading to ubuntu 8.04?
2 : how do i finally apply the patch?

and remember keep it simple, as said im new to linux :P

any help appreciated

---

### Post by Bios Element on 2008-09-20
Upgrade to Wine 1.1.5 and you shouldn't need the patch for Spore to run well.

---

### Post by aoanla on 2008-09-21
> **Frontierbacon said:**
> 
so i guess it comes down to this.

1 : can this patch just the same be applied to wine 1.0. or does it only work in 1.1.4?


Probably only 1.1.4 - patches may work against other releases of the software, depending upon how much of the code in the area they patch has changed.
In any case, 1.1.0 has other issues with running Spore that seem to be addressed in 1.1.4 itself.

>  and if so, can i get 1.1.4 without upgrading to ubuntu 8.04?
2 : how do i finally apply the patch?

and remember keep it simple, as said im new to linux :P

any help appreciated

You can only patch against source code, which you'd need to compile yourself. There's another thread with someone wanting to know how to compile wine if you're brave enough to try this (there's not a compiled release of 1.1.4 for Ubuntu 7.10, as the Wine developers only really have the time to support the most recent releases of any Linux distribution).

As Bios Element notes, though, the easiest approach would be to upgrade to 8.04 and then get 1.1.5, which includes the patch in question.

---

### Post by bobandiara on 2008-10-27
Ummm... right, but what about  version 1.1.7?

Does it include this patch?

---

### Post by Indubitableness on 2008-12-03
I had 1.1.9 and i was still getting a lot of rendering issues with Spore. I just uninstalled (purged) wine with aptitude and i got the patch and the source, and i'm fixing to try patching it. I'm looking for the instructions on how to patch and compile it from the command line.

 Of course, if 1.1.9 includes this patch already, then that means it would be silly for me to apply it, and that i purged my wine for no good reason, and i'll probably get the same errors anyway.

 So i'm going to try and apply it anyway, but i need to know how to do this from the command line.

 Anyone got any links?

---

