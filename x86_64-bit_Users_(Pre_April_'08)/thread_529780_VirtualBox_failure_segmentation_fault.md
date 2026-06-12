---
title: "VirtualBox failure segmentation fault"
date: 2007-08-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by kthardin on 2007-08-19
Okay I've got a strange one here.

I used Automatix to install Virtual Box.  No problems there, and it worked great.  I installed XP, did all my updates, etc, etc.

I was attempting to find out if I could install and play the game Overlord without having to actually run a dual boot scenerio.  This turned out to be harder than I thought as the DRM management on the disk, SecuRom knew I was running VirtualBox and refused to let Overlord run...all manner of workarounds on this failed.

Still, I figured this would be a useful tool for other purposes.  However, when I booted up this morning, VirtualBox refuses to run.

From the command line I get:

Segmentation fault (core dumped)

Deinstalling and reinstalling the program did nothing.  It is straight out broken.  VMware for some reason will not play any sounds from its virtual machine, so I quickly abandoned that.  What I saw of VirutalBox I liked, but it is straight out broken now, and I have no idea where to begin to try to fix it.

As far as Overlord goes, has anyone got any games of this type to work on a virtual machine?  I note that none of the workarounds mentioned on places like GameCopyWorld worked in regards to this one specifically.  I own both the game and the copy of XP legitimately, so I ask that no one complain about me violating copyrights as far as this goes.

Any ideas?

---

### Post by armware on 2007-08-20
i'm also having the same virtualbox error, which is how i found your thread. sorry, i can't help you there.

i'm not at all familiar with the game you mentioned, but have you tried running it in wine?

---

### Post by armware on 2007-08-20
ok, i was able to boot my vm anyways

in a terminal, run 
VBoxSDL --list

to list all the available virtual machines. get the name of the one you want, then type:
VBoxSDL -vm [NAME]

no fancy gui, but it works. hopefully until a fix gets around.

---

### Post by kthardin on 2007-08-20
Unfortunately, I won't be able to do that.  As part of my attempt at fixing it, I purged all files relating to the virtual machine.

---

