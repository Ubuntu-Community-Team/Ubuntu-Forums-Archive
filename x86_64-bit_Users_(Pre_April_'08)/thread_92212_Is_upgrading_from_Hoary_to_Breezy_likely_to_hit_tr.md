---
title: "Is upgrading from Hoary to Breezy likely to hit trouble?"
date: 2005-11-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by casper_2095 on 2005-11-19
Yes, yes, of course you can't answer this for me, just sounding out the general mood. The initial upgrade reports when breezy became official sounded like an entirely mixed bag so I've waited for some dust to settle.

AMD64 (Asus a8v) workstation with
  raid1/mdadm
  generic kernel
  lm-sensors/fancontrol
  wireless (ra0)
  samba
  postfix+cyrus
  etc... (they're the main needs).  

Do I just point the repositories at breezy and see what happens?  [Never mind I'll go hunt for the how-to-upgrade instructions]

But does anyone think I'll hit major issues venturing into the breeze?

---

### Post by MaX on 2005-11-19
My upgrade somehow didn't work quite aswell as my reinstall but it could be since many confs didn't get installed since I had been fiddling with them.

Breezy works great here. I have run it on a A8VX motherboard btw.

---

### Post by casper_2095 on 2005-11-19
So did you "upgrade" and something wasn't right which invoked a "reinstall"?
Doesn't sound too promising. :(

---

### Post by GuyveR800 on 2005-11-20
Just make sure you got the 'ubuntu-desktop' package installed. Change 'hoary' to 'breezy' in /etc/apt/sources.list and do 'apt-get update' + 'apt-get dist-upgrade'.

No probs upgrading here.

---

### Post by Drain on 2005-11-20
I waited a while to upgrade my AMD64 Hoary server to a Breezy setup, and then just did what other people have - changed the /etc/apt/sources.list and ran the proper apt-get commands, and rebooted into Breezy. It was smooth as smooth can be. 

Which honestly shocked me a little - I re-installed Breezy from CD on my x86 box, because I ran into problems with the apt-get process there (I later found the answer to my issues in the forum, but that's another story). 

I guess the best answer to your question " Is upgrading from Hoary to Breezy likely to hit trouble?" is "yes, be prepared, but no, it should be simple" ;-) YMMV.

---

### Post by casper_2095 on 2005-11-21
Thanks guys. I've confidence now, but, yeah, still holding off until I have a chunk of time up my sleeve just in case any issues appear.  I've no compelling requirement other than to keep current - which was my whole rationalisation for ubuntu over vanilla debian (stable) - doh!  Hopefullly I'll return and bump this thread to report success/failure.

---

### Post by adeh on 2005-11-21
I am writing from a newly upgraded breezy box.

The key was mentioned in another post, but I want to make it more clear:

apt-get install ubuntu-base ubuntu-desktop

I did the normal upgrade stuff without that step and I ended up with a working system that was a little off, not to mention no changes to the desktop enviroment.

But after those two packages installed themselves, its perfect.

Enjoy,
Adeh

---

### Post by casper_2095 on 2005-11-24
Cheers Adeh.  On the issue of "ubuntu-desktop"...

After Synaptic has used its "smart" interdependancy checking it sets ubuntu-desktop to "REMOVE COMPLETELY".  Yet many are saying that they had a bit of an issue which turned out to be not installing exactly that.

Should I override synaptic's decision to remove ubuntu-desktop v0.43, and insist that it does indeed upgrade to v0.80?

What other 'smart' things does it decide?

---

### Post by chajuram on 2005-11-24
Hi,

I upgraded to breezy about a month back. To be honest I expected an easier upgrade, ubuntu has raised my expectations. 

Anyway, I had to spend about two days fixing the programs that started giving me problems. 

First of all, I had to reinstall some programs that came from outside the ubuntu repositories. Since there is a new kernel, anything that uses kernel headers/source will have to be reinstalled. 

I was reading another post where someone said that it might be a good idea to upgrade after a year. I think it is a personal choice, one thing you could upgrade is the OpenOffice to OpenOffice2. If you don't care too much about the latest changes, and just want a working system, then it might be a good idea to stick to your current version. If on the other hand there is a bug that is bugging you and you know it has been fixed, you might think of the upgrade.

I also miss gdesklets, they are still there but don't work perfectly. 

Chajuram.

---

### Post by skylark on 2005-11-24
B4 u upgrade, be aware of potential issues if you are running lvm on software
raid...: [http://ubuntuforums.org/showthread.php?t=94203](http://ubuntuforums.org/showthread.php?t=94203)
(although it may only affect xfs partitions).

If this is your config, I suggest a backup of crucial data just in case.

After upgrading I also ran into common problems like the macromedia flash-plugin sound not working in 32-bit chrooted firefox, and a few other problems with sound in general. I've worked around most of my issues now, but when dapper comes out I think I'll do a re-install from scratch.

---

### Post by skylark on 2005-11-24
[QUOTE=adeh]
apt-get install ubuntu-base ubuntu-desktop
But after those two packages installed themselves, its perfect.
[/QUOTE]

No wonder I was having issues. I just did this then and it installed an extra 33MB of stuff. I'm annoyed that a dist-upgrade doesnt work out that this stuff is needed given my old config. hmm.. I wish Id known about this earlier. Thanks adeh!

---

