---
title: "Using Bittorrent in Vista 32/Ubuntu 64"
date: 2008-08-02
forum: x86 64-bit Users
---

### Post by dystorteddream on 2008-08-02
So I've been using Deluge Bittorrent client here in Hardy 64. Everything's going great, so i switch on over to Vista to use my AVerMedia card to play some GCN (see my other thread). Now... I saved the torrent and used the same torrent to open with Utorrent, to the same file location (external HDD). It works great, hash checks go well, they pick off from the same place... but a few hours after doing this (started today) and switching back and forth between the OS's... all of a sudden i get the notorious BSOD in Vista. Twice. Now the dump manager doesn't give me much information. It's not a memory error, doesn't even tell me the program that it was having the problem with (thanks Bill... really helps) But it happened twice, and I noticed it was with Utorrent running.

Alrighty... now i would just LOOOVE to chalk this up and MS being ubertarded, but I don't think it is. I don't know if it has anything to do with the two architecture types, since someone thought it was brilliant to send a 64 bit system with a 32 bit OS pre-installed. I don't know if it has to do with the fact that two different OS's are using different protocols in downloading the same file to the same location. 

Who knows. I thought i'd be all neat and keep downloading, no matter which OS I was using, but nope... I just get the BSOD and it makes me love Linux even more.

Any thoughts will be greatly appreciated, and i will send 64 imaginary virgins to smother you in olive oil and feed you grapes. Or i'll finish this guinness and be happy with my current lot in life. :)

---

### Post by BGFG on 2008-08-02
Have you tried googling the BS code? i got the BS on a brand new dell64 system 
Kernel_data_Inpage something or other. Never got a proper answer but it turned out to be resources. I just had to kill vista's unnecessary processes and the BS never appeared again. 
In your case though, utorrent uses barely any memory... 
Vista is ntfs and well i'm guessing your hardy is ext3 but BS from 2 diff filesystems writing to the same drive ? seems outlandish....

---

### Post by dystorteddream on 2008-08-02
> **BGFG said:**
> Have you tried googling the BS code? i got the BS on a brand new dell64 system 
Kernel_data_Inpage something or other. Never got a proper answer but it turned out to be resources. I just had to kill vista's unnecessary processes and the BS never appeared again. 
In your case though, utorrent uses barely any memory... 
Vista is ntfs and well i'm guessing your hardy is ext3 but BS from 2 diff filesystems writing to the same drive ? seems outlandish....
My external HD is NTFS. I had it on a previous WIN XP system, and kept all of my files on it. Never changed the File System, since i bring it everywhere and use it on multiple machines, 3 on a regular basis.

---

### Post by BGFG on 2008-08-02
I have an internal ntfs media dump drive also. Works fine.. But slower than my ext3 ones. Not that i'd want you to get a blue screen again, but if it does happen, take a look at the error code. May give you some great insight.
As for vista, have you ever been in the vista services manager ? a little work in here could free up some resources.

---

### Post by dystorteddream on 2008-08-02
> **BGFG said:**
> I have an internal ntfs media dump drive also. Works fine.. But slower than my ext3 ones. Not that i'd want you to get a blue screen again, but if it does happen, take a look at the error code. May give you some great insight.
As for vista, have you ever been in the vista services manager ? a little work in here could free up some resources.
My resources never to have seemed to be a problem. Not lagging, not doing anything extensive. Utorrent was running in the background, and i was just web browsing through our lovely Ubuntu Forums. I've got 4 Gig's of RAM, which is more than enough for using a bittorrent app and firefox. Nothing else going on, never had the problem before until I decided to use the seperate torrent clients for the same torrent on the External HDD.

---

### Post by BGFG on 2008-08-02
Drivers ? Updates ? check these:

[http://thevistaforums.com/index.php?showtopic=37276](http://thevistaforums.com/index.php?showtopic=37276)

[http://forums.windrivers.com/showthread.php?t=57063](http://forums.windrivers.com/showthread.php?t=57063)

---

