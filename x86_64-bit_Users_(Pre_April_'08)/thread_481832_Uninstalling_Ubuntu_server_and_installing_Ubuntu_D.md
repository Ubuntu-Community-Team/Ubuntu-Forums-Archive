---
title: "Uninstalling Ubuntu server and installing Ubuntu Desktop"
date: 2007-06-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by birenv on 2007-06-22
Hey guys,
I've never really used Linux. I just installed Ubuntu Server 7.04 on a separate partition on my workstation.
Then read on the forums that the Ubuntu server doesn't come with GUI, I tried installing the desktop with

sudo apt-get install ubuntu-desktop

with the ubuntu 7.04 32 bit disc and 64 bit disc in the drive but it didn't install anything, it couldn't find the package.

So finally, i've decided to install Ubuntu desktop instead of server, so here's the question.

What would be the best way to uninstall Ubuntu server and install Ubuntu Desktop, without the grub loader wreaking havoc with my system :)?

In case, your wondering why i would install the server version, I tried installing the regular 64 bit version of it on my system, but everytime i selected start or install ubuntu from the CD menu, it would just goto a black screen and do nothing. I'm downloading the 64bit desktop disc, just in case, my disc was faulty.

The specs of my system are 
Intel S5000xvn Motherboard
Dual Xeon 2345
4 gigs of RAM 
and 2x500 gb SATA2 with XP 64 installed on the primary one.


so.... HELP!:)

---

### Post by birenv on 2007-06-22
btw totally open to just installing GUI for the server... my machine is just being used as a workstation

---

### Post by bapoumba on 2007-06-23
Moved the thread to the -64 bits section.

---

### Post by Cappy on 2007-06-23
1) You can just re-install over your current ubuntu, it will work fine - just use the manual partitioning and select your current partition(s) and be sure to select quick format.

2) You are getting a black screen because you need to use boot parameter
```
nosplash
```

---

### Post by birenv on 2007-06-23
Thanks!.... will try that now

---

### Post by Cappy on 2007-06-23
There may not be a "quick" format, it may just be a "format" checkbox. Don't be worried if you don't see a "quick format". It forces you to format your "/" partition anyway.

---

### Post by birenv on 2007-06-24
so i edited the boot parameter ... and added nosplash it, its still doing the same thing
when i was installing it used to do the same thing, but i used to press F4 and select a resolution like 800x600 or 1024x768 and that fixed that. 
no clue what to try... not going to try and install nvidia drivers this time, last time i did that i pretty much had to reinstall ubuntu.

starting to think i should try some other version of linux like fedora core... what would you guys recommend??? just want a version of linux that works without me spending hours on it.... thanks again guys!!! :) really appreciate the help.

---

