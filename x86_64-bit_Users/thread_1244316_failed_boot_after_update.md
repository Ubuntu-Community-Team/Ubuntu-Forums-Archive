---
title: "failed boot after update"
date: 2009-08-19
forum: x86 64-bit Users
---

### Post by notquitestr8t on 2009-08-19
I installed ubuntu 9.0.4amd64. All went well. I moved several files from an old windows hardrive that I need to keep and then removed that hardrive from the computer. The last thing I did was run updates after a failed Vuze install. When I rebooted, all I get is a blinking cursor in the corner of the screen. I believe the update tried to install a new kernal. Anyway, I am dead in the water right now. I have a live CD and can mount the drive but I'm not sure what is wrong and how to fix it. I don't want to start all over cause it took me forever to move all the data off of the old windows drive. Lastly, I have an intel quad processor and 8GB of RAM. I don't see a version for x386-64 so I'm assuming the amd-64 is supposed to work. Any help would be appreciated. I am a newbie so please be explicit in your answers/recommendations.
Thanks!!!

---

### Post by philinux on 2009-08-19
> **notquitestr8t said:**
> I installed ubuntu 9.0.4amd64. All went well. I moved several files from an old windows hardrive that I need to keep and then removed that hardrive from the computer. The last thing I did was run updates after a failed Vuze install. When I rebooted, all I get is a blinking cursor in the corner of the screen. I believe the update tried to install a new kernal. Anyway, I am dead in the water right now. I have a live CD and can mount the drive but I'm not sure what is wrong and how to fix it. I don't want to start all over cause it took me forever to move all the data off of the old windows drive. Lastly, I have an intel quad processor and 8GB of RAM. I don't see a version for x386-64 so I'm assuming the amd-64 is supposed to work. Any help would be appreciated. I am a newbie so please be explicit in your answers/recommendations.
Thanks!!!

Reboot and when you see grub press the esc key. Use the down arrow key and choose the recovery boot line. See where you get with that

---

### Post by realzippy on 2009-08-19
..if you replug your old windows HD,does it work?
It could be that you have to edit your /boot/grub/menu.list.
There is a SuperGrubDisc,you can boot from it and it fixes your grub easily..

---

### Post by realzippy on 2009-08-19
"See where you get with that"

somewhere in nowhere...
He pointed out that he is a beginner....

---

### Post by notquitestr8t on 2009-08-19
Tried hitting escape during reboot but I don't even get a grub menu. I also replaced the windows drive without luck. I guess I'll try the supergrub disk. I'm getting nervous, I'll try putting ONLY the windows drive in and see if I can boot. If not perhaps I've hosed my bios?

---

### Post by notquitestr8t on 2009-08-19
Whew! Supergrub disk fixed it. Thank you everyone!!!!!!

---

### Post by philinux on 2009-08-19
> **realzippy said:**
> "See where you get with that"

somewhere in nowhere...
He pointed out that he is a beginner....

Everyone needs to know the recovery mode. Also now you are not in nowhere as it now has a menu instead of just dropping you to the command line. ;)

---

### Post by realzippy on 2009-08-19
> **philinux said:**
> Everyone needs to know the recovery mode. Also now you are not in nowhere as it now has a menu instead of just dropping you to the command line. ;)

...have not been there for a while ;-),
just thought it was no good place to start anyone's ubuntu experience..
SuperGrubDisc is kind of "press repair" and go...

---

### Post by philinux on 2009-08-19
Try it it's really very smart now.

I had to use supergrub once or twice. The first time was very tricky to say the least. Dual boot on two hard drives.

---

