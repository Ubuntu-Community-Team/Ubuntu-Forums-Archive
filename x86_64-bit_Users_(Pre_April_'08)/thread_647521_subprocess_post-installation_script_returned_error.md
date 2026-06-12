---
title: "subprocess post-installation script returned error exit status"
date: 2007-12-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by Victormd on 2007-12-22
(I posted this under another section but I think it was the wrong place so here goes another try)...

I was running some configuration scripts and updates (don't remember at which point this started so can't say what I installed that caused this) and now, every time I install something I get the following message.

E: linux-image-2.6.22-14-generic: subprocess post-installation script returned error exit status 3

I tried searching for a related post but found only with errors 1 and 2 that seem to be related to RAID configuration and I don't have RAID setup on my machine...

The funny thing is that, even though I get this error, the software seems to be working fine. However, I do have to restart now every time I install anything.
I'm running

Ubuntu amd64

Any thoughts?

---

### Post by WileyCoyote on 2007-12-23
I have the identical problem.

Also using AMD64.

There seems to be some link to clamav, since the two items that "sudo apt-get --fix-broken install" can't resolve are

[I]Errors were encountered while processing:
 linux-image-2.6.22-14-generic
 clamav-base[/I]

Removing ClamAV doesn't seem to make a difference to any of this.

The relevant errors when you try and use the -fix-broken install appear to be:

[I]Setting up linux-image-2.6.22-14-generic (2.6.22-14.47) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
Failed to create initrd image.[/I]


Elsewhere I saw the advice to someone else with this problem to:

*sudo chmod 755 /usr/sbin/mkinitramfs*

Which I did, but it also makes no difference.

---

### Post by WileyCoyote on 2007-12-23
The fix appears to be the following:

*sudo apt-get install util-linux*

Reboot, and presto.  Problem begone.

Pain is the @ss finding the answer to this one, and I still have no clue WHY it happened to me in the first place.


EDIT - 

one thing I just noticed.  I recall trying to use the whereis command recently on this system and being REALLY puzzled I didn't have it.  But checking on what's actually IN util-linux, for one thing I notice it includes whereis, which incidentally DOES now exist on my system and work.

My conclusion is that something must have gone wrong during my initial install of this system, keeping some essential files off my system.  This stuff must have not been necessary for most everyday activity, but boom, when I got a kernel update (this is definitely the first kernel update I've had on this system) something in THAT didn't run because essential stuff was missing.  I mean MOST of what's in util-linux must have been present on my system, but obviously not everything.

---

### Post by blade8562 on 2007-12-25
If you have /boot in its own partition and you haven't given it enough space (say less than 25 mb) you will get this message due to the lack of space. Resize the partition and all will be well.

---

### Post by Victormd on 2007-12-27
My /boot is on the same partition as Ubuntu = 6Gb + 1Gb swap... I'm trying out WileyCoyote's solution right now by installing Alien-arena... not sure this is the best way to test it but if at the end I don't see any errors, I think I'm good...

---

### Post by Victormd on 2007-12-27
Nope... same problem.
I think I'm just going to change to 32bit version...
I've read somewhere (hopefully I read it right) that Ubuntu running on AMD64 takes longer to boot + has less support. Furthermore, if I need to install 32bit software using wine, how does that work? Oh well... I'll get to it and see what happens! At least this error should go away!!!

--------------------------

Installed 32bit version and came running back to AMD64! Much better!!!
Even though I did read it right that 32bit is better in most instances for the common user, 64bit runs much smoother (as an OS)... of course there are downsides, but worth the trouble...

---

### Post by biddy on 2008-01-09
Hi Thanks for the sudo apt-get install util-linux
 command, i was getting nowhere until I read your post, i was getting the error below

[B]E: linux-image-2.6.22-14-generic: subprocess post-installation script returned error exit status 2

[/B]the util-linux install did the trick for me, now i can update without any errors.
cheers fellow ubuntu user, big bag of popcorn for you my friend.

:popcorn:
:guitar:
:KS

---

### Post by El-Al on 2008-02-15
yup! identical problem here on AMD 64bit. I took the same advice and just installed util-linux which requires that I uninstall linux32 (which is required for building Haiku on an older version of gcc I believe).

Anyhow, I'm gonna reboot right now, I'm fully expecting the problem to go away, I'll be back if it doesn't :D

---

### Post by El-Al on 2008-02-15
> **El-Al said:**
> yup! identical problem here on AMD 64bit. I took the same advice and just installed util-linux which requires that I uninstall linux32 (which is required for building Haiku on an older version of gcc I believe).

Anyhow, I'm gonna reboot right now, I'm fully expecting the problem to go away, I'll be back if it doesn't :D

Problem solved, thanks for supplying a solution to this.:)

I wonder if I reinstall linux32 the problem will return?

---

