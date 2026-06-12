---
title: "Hey guys i have a question about installing the new ubuntu."
date: 2008-04-26
forum: x86 64-bit Users
---

### Post by Samurai123 on 2008-04-26
Ok so i am completely new to this, so sorry for sounding dumb. 

But basically what happened was i did everything the ubuntu site told me to do, I burned the ISO to a disk and used winMd5sum. then i put the disk into my computer, everything seemed to be going ok when i booted up the live CD. 

Then i tried installing this program into the computer, so it went through the steps ok. but i think it messed up in the partitioning part, while it was installing at like 25% so i clicked ok. 

well i didnt no what to do, so i just restarted. the computer automatically popped the disked out, so i later tried to do the live CD again which didnt work this time. It brings me to some kind of shell i guess. 

But here is the weird thing, i think the partition happened without me actually installing ubuntu...In this rare time i was actually able to get into my windows XP(long story but my XP is totally messed up) and i looked at the C drive, it said i only had 11 GB. when it should be 200 something. 11 was the amount i wanted in the partition when i clicked ok for the ubuntu installation.

I no this is long read, but i really need your guys help.

---

### Post by esdaniel on 2008-04-26
If you've resized your XP partition to 11GB it will render using XP very difficult, I find 20GB a good size for XP with gaming only.

You can resize the XP partition by booting into the LiveCD though I prefer  rescue images out there such as: [SystemRescueCD]("http://www.sysresccd.org/Main_Page") - check the download page at this site for instructions, also you will need to familiarise yourself with partition management and how to make/delete/re-size etc..  

Right now all you need to do is re-size XP partition i.e. increase it (and create a new partition (blank) for Ubuntu if you're going to install it later).  It's likely you might have created a partition to install Ubuntu to - just delete that for now so that you're able to increase the XP partition to something sensible such as 50GB if you use it for more than gaming.

Once you've got the partion problem rectified then decide if you want to testdrive Ubuntu or install it.  Test drive will mean just booting from the live CD and not installing but running the LiveCD version.  If you then are happy with the LiveCD you can install, however note you should create a partition either in advance using the XP tools, the systemrescue tools or via the partition manager that is provided as part of the install process.

By default the Ubuntu installer does recognise an existing Windows partition when installing it's own boot loader, Grub, so you should be able to boot into both without further modifications after install via the Grub loader - if however you have borked your XP partition this will not be the case and you'll need to either get a techie to help you resolve that or ask us here for the steps to undertake - if you're not au fait with this I recommend stating that straight away so we can give you sufficient help.

---

