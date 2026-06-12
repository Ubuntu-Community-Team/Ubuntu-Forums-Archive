---
title: "Sun xVM VirtualBox Guest Addition Problem"
date: 2008-05-23
forum: x86 64-bit Users
---

### Post by kamale on 2008-05-23
Ok recently i've just installed this Sun xVM VirtualBox program. It works great so far but i can't seem to get my ubuntu drives to be connected to it. I already set the shared folder i want in the settings.

According to online guides, they just say click devices and click Install Guest Additions, which does not work for me. Nothing comes out. Does any1 know or have any experience with this program?

I'm running windows XP on the VirtualBox.

---

### Post by kamale on 2008-05-23
No one???

---

### Post by briandu on 2008-05-25
I am playing with VB on Ubuntu and have had a lot of problems - in fact VB on 8.04 is broken.

Also you cannot run in Win 32 bit VB a 64 bit Ubuntu - just so you know.

cheers.

---

### Post by inphektion on 2008-05-25
huh?  I have 64 bit ubuntu host running 32bit vista guest just fine with VB.  I typically run it in full screen mode on one face of my spinning compiz cube but even the seamless mode works.

---

### Post by aaron.d on 2008-05-26
> I am playing with VB on Ubuntu and have had a lot of problems - in fact VB on 8.04 is broken.

Also you cannot run in Win 32 bit VB a 64 bit Ubuntu - just so you know.

cheers.


This info is either incorrect, or mis-worded.

I am currently using U8.04 with default kernel, I have installed, direct from the repos, the Virtualbox OSE packages (including kernel module). This is the easiest way to get vbox running but does carry with it SOME restrictions.
However, with this installation I have been able to install win2003 32bit, no problems.

A couple things to note:

1) The repos arent 100% up to date with the virtualbox release versions, repos are still on a 1.5.x (or something of that nature) vs. 1.6 current.

2) permissions can cause issues. Check the obvious if it doesnt seem to work at all --> you must be in vboxusers group (and restart your session)

For the OP, can you elaborate on what you mean by:

"i can't seem to get my ubuntu drives to be connected to it."

Do you mean a shared folder from host OS (ubuntu) to guest (xp) doesnt work? what directory on the host are you trying to share?

---

### Post by pixel :-) on 2008-05-26
try the virtualization forum[http://ubuntuforums.org/forumdisplay.php?f=308]("http://ubuntuforums.org/forumdisplay.php?f=308")

---

### Post by unicorn_2003_1 on 2008-05-26
I got my VirtualBox copy directly from its official site, the normal copy, not the OSE one, as there's a kernel module not compiled in, in the Ubuntu repository yet, whichc made it more difficult to install.

Click the install the guest additions, and iso file should be automatically inserted into your Windows XP's CD driver, just click there and install. Actually the ISO file itself is at /usr/share/virtual/VBoxGuestAdditions.iso

You need to enable the shared folder feature when the virtual machine is turned off, and then get into Windows, ->my neighborhood->entire network->vboxshare(spelling maybe wrong, but you get it), mount the shared folder you see to a driver in Windows (Z: for default).

---

