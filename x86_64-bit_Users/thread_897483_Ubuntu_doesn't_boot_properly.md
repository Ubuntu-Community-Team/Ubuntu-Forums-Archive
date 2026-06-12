---
title: "Ubuntu doesn't boot properly"
date: 2008-08-22
forum: x86 64-bit Users
---

### Post by psie on 2008-08-22
Hey,
I am running a Ubuntu Hardy with a 2.6.24-19-generic kernel, the hard drive is encrypted with LUKS. I have been running the system for quite a long time without any problems. Yesterday, I switched my laptop off and while this it froze! I mean the hard drive was still doing something but after 10 minutes I manually disconnected the power to switch it off. 
Today, I was switching it on and after entering my LUKS password for my hard drive it stopped (the hard drive is still "doing" something) while "starting early crypto disks..."! It didn't continue for more than one hour so I pushed strg+alt+del then the boot process continued slowly until "Starting ACPI services...", here again the process didn't continue. Now I could switch to an other tty form where I could log in as a user, again everything works very slowly!
I checked my /boot folder and I didn't get any output with "ls". It appears that there is noting in there what doesn't make any sense as i could enter grub when I was booting last time, and I know that there are files in that folder.

MY QUESTION: What can I do to get my system back to work? Is my hard disk broken?

Thanks in advance for every hint ;)

---

### Post by NTBao on 2008-08-22
Not saying I can help, but I think you need to be more specific with

> the hard drive was still doing **something** 

---

### Post by livestockPimp on 2008-08-22
if you can get to a shell can you use TOP or anything to see what is using your disk activity?

I am not familiar with the LUKS encryption but can you put the password in, boot of a CD and see if your drive is accessible and not broken?

---

### Post by psie on 2008-08-22
> **NTBao said:**
> Not saying I can help, but I think you need to be more specific with

I mean that the light which indicates that there is disk activity is constantly on

---

### Post by psie on 2008-08-22
> **livestockPimp said:**
> if you can get to a shell can you use TOP or anything to see what is using your disk activity?

I am not familiar with the LUKS encryption but can you put the password in, boot of a CD and see if your drive is accessible and not broken?

Well I thought about this, but I am using 3G to connect the Internet and so it is a bit complicated as if I am going to boot from CD I need some "mods" to be loaded to access my encrypted drive. These mods can just be loaded with Internet connection, and as already mentioned I use 3G with a pcmcia card to connect. But I need internet connection to install some "drivers" for the pcmcia card to connect the internet!

But is there any tool to check the hard drive while it is still mounted?

---

### Post by livestockPimp on 2008-08-22
you can use hdparm to test disk i/o speeds, or maybe run fsck on it and see if there are any errors.

you should be able to find some tools on using these.

from memory it is:

hdparm -T /dev/sda1
(check this from the man page) to run speed tests
and
fsck /dev/sda1
this will check the drive for consistancy, ect. there are more thorogh tests you can perform with this tool.

---

### Post by psie on 2008-08-22
Thanks for this! I'll try it! I just booted with live CD and have troubles mounting or first decrypting the disk... but this is now getting too off-topic...

---

### Post by psie on 2008-08-22
Now I can assess my problem a bit more accurate. It is that I am not able to mount my /boot and /home partition automatically. But I am able to do this from a Live-CD meaning that hdd and partitions are ok.

I really need some advice on this thx.

---

### Post by linux_tech on 2008-08-22
Do you get an error from grub or does grub no longer appear at startup?

---

