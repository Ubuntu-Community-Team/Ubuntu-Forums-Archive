---
title: "Freeze after login"
date: 2006-03-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by naadir on 2006-03-28
Hi,

My pc freezes as soon as i enter my user name and password. its the first time i installed linux. The same happens when i boot up using the preview cd. I have a amd 64 3000 and windows xp running on my first partition. Is it maybe the way i coould have installed it? Is there any easy steps i can take to install ubuntu on a pc that has another operating system on it?

---

### Post by jimi.vicious on 2006-03-28
What do you mean by freeze? Are you still able to move the mouse pointer?

Just an idea, but check that the date and time are set correctly on your machine.

I had a problem with Ubuntu hanging like this on an old laptop. It turned out that the date was set to something ridiculous, which confuses Gnome and prevents it from starting.

Just a thought.

---

### Post by naadir on 2006-03-28
It just freezes. The mouse doesn't even move. Will check the date of my pc l8r.

---

### Post by naadir on 2006-03-29
Checked the date out... don't know what the problem is. I left it for like 10 minutes hoping that it would recover but nothing happens... Maybe i should try the normal pc version instead of the 64bit version...

---

### Post by andi on 2006-03-29
i had the same issues. it was the powernowd daemon which wanted to throttle down the cpu and caused the entire system to freeze.

you could try to do a "ctrl+alt+F1" to get to the first console. after the login type "sudo /etc/init.d/powernowd stop" and type in your password. after that type "Alt+F7" to get to the GDM-Login and try to login.

if that helps you can remove the daemon permanently from all runlevels "rm -rf /etc/rc*.d/*powernowd".

---

### Post by naadir on 2006-03-29
Thanks,
Will try and do that and see if it works. :D

---

### Post by naadir on 2006-03-30
I tried that out. I had to log on as root coz it didn't allow me to run the command so i started linux in that other mode(like a safe mode kinda thing)... but when i ran it gave ane error saying that the file doesn't exist and if i had mounted the /sys/ directory and some other stuff that i cant remember. Oh and it gives an error when ubuntu loads saying that it couldn't synchronize the clock to something.ubuntu.org... dont know the specifics.

I'm guessing that i didn't install linux correctly... i installed it on a seperate partition on my drive. the first partition holds windows xp. when i created the partition for linux it created 2 partitions, one for swap and one that displays this - "/". I assume i did everything correctly?
is there in dummy help for installing linux? maybe i should install the normal pc version and not the 64 bit one. Oh could it be my graphics card? I have a ATI X550...

The pain of having to deal with open source software ](*,)

---

### Post by lopzided on 2006-03-31
i am having the same problem.  when i get to the login screen, everything freezes...i cannot use the mouse or the keyboard.  occasionally, i have a few seconds where i can type my user name and password, but as soon as gnome gets past the splash screen, i get the desktop and it freezes again.  the only thing that gets loaded is the taskbar and the top menu bar (minus the system tray and the clock).

i have tried formatting/repartitioning/reinstalling, but the same problem occurs.  right now i am reinstalling using ext2 instead of ext3, as was suggested in the #ubuntu channel on freenode.  if that doesn't work, i will check my system clock (although i'm almost positive it's right), and post back my results.

also, as a side note, my installation worked perfectly fine, until i moved yesterday...when i set my computer back up, that is when the problem began.  i am still able to boot up from a livecd (i used knoppix), and even mount the drive, but it appears that the drive is being mounted as read only.

**EDIT** : i just realized that this is in the amd64 user area...i am not using an amd, it's a p4 2gig...however, the problem i'm having is the same

**EDIT** : reinstalling using ext2 did not solve this problem.

---

### Post by saphire_2001 on 2006-03-31
For your intstallation question:
You should have at least 3 partitions.  1 for windows (recommended to be first) 2 One obviously needs to be mounted at / 3 1 you need a swap partition.  Question number 1 You do have a swap partition right? Question 2 how much memory do you have in your machine?
Question 3 What kind of video card do you have?  I had a similar issue with some of the old S3 cards and some of the older Radeon Cards.  If it's an nVIDIA card you shouldn't have an issue of that type.  Also in your /etc/X11/xorg.conf try changing the video card driver to vesa

---

