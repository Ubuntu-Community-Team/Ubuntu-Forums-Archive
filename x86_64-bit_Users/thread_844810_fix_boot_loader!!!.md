---
title: "fix boot loader!!!"
date: 2008-06-29
forum: x86 64-bit Users
---

### Post by dogsipod on 2008-06-29
before i installed ubuntu i partitioned my harddrive such that there was a 50gig NTFS partition (i planned on putting xp on my system at some point for a few programs i can't use in wine)  at the back and every thing else was free space.  i told ubuntu to install to the freespace and it did.  then today i wanted to put xp in the NTFS space.  i followed the installer and when it asked where i wanted to install xp I pick the ntfs partition from the list.  after the install my rig will only boot into windows.  I thought it would be like fedora and all me to pick what OS i wanted to after the post screen.  What do I need to do so that grub will let me pick which OS i want to use?

---

### Post by marduk418 on 2008-06-30
I'm having a similar Problem.
It happens because Windows doesn't have a boot loader like Ubuntu, and once you install Windows, that boot loader "disappears"

Technically you should install first your Windows OS and after that install Ubuntu, but there should be a way to get a boot loader anyways (I wait for that answer as well)

---

### Post by Lonthong on 2008-06-30
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by incubii on 2008-06-30
dogsipod, please realise this is no fault of Ubuntus. It is Windows fault as it has a less then feature rish, capable boot loader and will assume its the only OS on the computer.

Its been ages since i did it but i think you can boot the Ubuntu LiveCD into repair mode and re-install the Grub boot loader which will acknowledge both Windows and Ubuntu (what you want).

---

### Post by dogsipod on 2008-06-30
i know its no fault of ubuntu.  i just was just hoping that since i created a tiny little environment for windows it would be contained there.


I got the problem fixed but I had to use some weird workarounds....I will post back here later in the day with my variation of the solutions you guys posted. Thanks for help in advance

---

