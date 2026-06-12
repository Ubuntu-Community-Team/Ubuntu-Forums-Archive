---
title: "[SOLVED] Deleting SUSE linux"
date: 2008-04-03
forum: openSUSE and SUSE Linux Enterprise
---

### Post by Orian.au on 2008-04-03
I have installed Ubuntu on my laptop, after it I have installed SUSE. So now to boot Ubuntu I need to choose Ubuntu in suse grub and then again to choose Ubuntu in ubuntu grub. So how can I delete suse leaving ubuntu?

---

### Post by ubuntu27 on 2008-04-03
You can eliminate Suse or any other Operating System by deleting the partition in which it resides. 

To do that, you can use a partition editor such as gparted or qtparted. Seelect the partition where Suse is located, and delete. :)

You can get a Gparted LiveCD here: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

You can also use Ubuntu's Desktop CD.


After you eliminated the partition, you will have to fix the GRUB to only show Ubuntu. (search in the forums)

---

### Post by cprofitt on 2008-04-03
Making the assumption you only have one grub installed all you have to do is go to the /boot/grub/menu.lst and edit out the entry for openSUSE.while booted in to Ubuntu.

---

### Post by Medieval_Creations on 2008-04-03
Depending on how you have your partitions setup, when you delete your Suse partition you may get a Grub error on the next reboot.  The reason for that would be that after installing Suse, Grub will be looking for the /boot/grub/menu.lst on a partition that no longer has any data on it.  You don't have to do a fresh install, but will have to setup Grub again.

EDIT:  You could also boot into Ubuntu and re-setup Grub from there, rather than a boot CD and then use Gparted or what ever program you like to delete Suse and use that space for something else.

Here's a post on how to restore it:
[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

and Supergrub is another good choice to fix it.
[http://supergrub.forjamari.linex.org/?section=download](http://supergrub.forjamari.linex.org/?section=download)

---

### Post by Orian.au on 2008-04-04
thank you. have fixed the problem with supergrub.

---

### Post by Medieval_Creations on 2008-04-04
No Worries.  Glad I could help. :guitar:

---

### Post by ubuntu27 on 2008-04-04
Good job Orian.au :)

Don't forget to[ mark this thread as SOLVED.]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

