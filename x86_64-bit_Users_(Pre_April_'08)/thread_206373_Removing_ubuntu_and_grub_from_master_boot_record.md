---
title: "Removing ubuntu and grub from master boot record"
date: 2006-06-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by saikiran on 2006-06-30
Hi to all.


I am facing a problem, for which i have found lots of post, but since i am non-technical i am not able to understand. so posting a new thread.

sorry, if it annoys you people.


My story is this:

I was using windows XP Pro for a long time, and i got ubuntu 5 desktop cds from my friend and i thought to install it in my PC.

What i did, is simple, worked with the live cd, for some days and one good day, i tried the install CD of ubuntu and installed it, 

I formatted my HDD Samsung (40 GB) and installed the ubuntu (Not dual booting) I thought i will work hereafter with linux instead of Windows.

I successfully installed ububtu !!! What a wonderfull Desktop it is. I got very much addicted with it.

[COLOR="Red"]But, inorder to work with practical situations, my enjoyment got vanished. I [/COLOR]have a Sify Broadband Connection (In India) and i am running a client application of them, to hookup to the internet.

[COLOR="Red"]As i said, i am not a linux master, so i dont know to connect with internet using some alternative method. Just for this reason i have to go back to windows.[/COLOR]

So what i did, i tried to boot up with the XP Pro CD and try to install it, by formatting the disk.

[COLOR="Red"]This is where i got caught. Whenever i try to boot my PC with this CD, (I have setted the 1st boot device as CDROM), i got the GRUB loader running instead of the setup CD.[/COLOR]

[COLOR="Red"]Now, out of my shear inadequate knowledge, i wiped of my HDD thru a software thinking that, it will solve my problem. 
[/COLOR]
I wipped off and once again inserted the XP CD and Reboot my PC, but still i got the GRUB loader, but with an Error 15.

Now what to do ????

[COLOR="Red"]How to resolve this problem. I had seen lots of post which tell that, we have to fix something called MBR and other things...which are very technical.
[/COLOR]
Can anyone tell me, how to get rid of this drastic situation. 

I am going out of ubuntu just for this purpose.

I want 2 things from my fellow ubuntu users:

[COLOR="DarkOrange"]1) If someone knows, how to connect to Internet using alternate way for  a cable based setup....then i will njoy what i get from ubuntu

2) If not...pls help me out in booting my PC with this XP Pro CD and re-instlling windows Operating System
[/COLOR]

Cheers
sai

---

### Post by Joeb on 2006-06-30
If you are hitting the grub boot menu instead of the Windows XP install CD then you are still booting from the hard drive and not your CD.  You may have to hit a certain function key at boot, such as F12, to bring up a boot menu to boot from something other than the hard drive.  Installing Windows XP would definately overwrite your boot record and remove grub.

However, many people do use Ubuntu (and other versions of Linux) with cable modems.  Do you know if there were/are special steps you need to take under Windows to use the cable modem?  Usually all it takes is plugging an ethernet cable from the computer to the cable modem and it works automatically.

At this point, however, it sounds like you have neither Windows or Ubuntu installed anymore.  So, one way or the other, you will need to determine why you are not able to boot from the CD (are you sure it is bootable?) before you can proceed (if you can boot from the LiveCD then your XP CD sounds like it isn't bootable).

---

