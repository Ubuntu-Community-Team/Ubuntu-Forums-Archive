---
title: "Issue with wine1.6-rc2 and GLIBC"
date: 2013-06-19
forum: Wine
---

### Post by Roguebantha on 2013-06-19
Here's the story:
Originally, I installed wine normally, as wine 1.4, the stable package. I found though, that I was having several issues with running it:
> 
wine: failed to initialize: /opt/McAfee/runtime/2.0/lib/libc.so.6: version `GLIBC_2.9' not found (required by /usr/lib/i386-linux-gnu/wine/ntdll.dll.so)

I then, after reading several more articles on the issue, attempted to compile the newest version of wine, wine 1.6-rc2. This is what I normally do (I'm not using the computer I normally use), on the other hand, it was complaining about me not having X installed. After looking online, I found that this was a common issue with AMD64. and by using:
configure --enable-wine64

I was able to compile and install wine with little issue. On the other hand, I could not access winecfg and the executable "wine" was not on the system. wine64 was though, and that appeared to be wine, just the 64 bit version. I tried running a program (the Spotify Installer actually), but it didn't work at all. I ran it, and it just exitted, no errors, no nothing. Today, I had an upgrade for wine in my automatic software updates, which I took. Now it's giving me the GLIBC error again. I do have libc6 installed, and I saw some sort of libc6amd64 dev library for the AMD 64 that looked promising but to install it, I would have to uninstall gcc and g++ among several other applications and this doesn't seem to be much of an option for me, nor does it make sense that I would have to uninstall my biggest compiler to use the compiled version of wine ><.

I have:
Release 12.04 (precise) 64-bit
Kernel Linux 3.5.0-34-generic
Intel® Core™2 Duo CPU E8400 @ 3.00GHz × 2
3.8 GB of RAM
libc6 version 2.15-0ubuntu10.4

Any help would be greatly appreciated!

---

### Post by KARNVORbeefRAGE on 2013-07-08
Do you have q4wine installed as a graphical frontend?  This may help access WINE cfg, plus I had an issue similar to this but after installing wine 1.6-rc2 I had to go back and install wine 1.4 (I also have AMD64 but this was a problem on Arch Linux not running programs).
Is that McAfee running?  Try disabling it during the install if that is the case.
Sorry if I am not much help, I just wanted to make sure you got a reply.  Post results and good luck.

---

