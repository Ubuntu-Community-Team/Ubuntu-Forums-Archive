---
title: "A Couple AMD64 Ubuntu Problems..."
date: 2005-05-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by drews_blunted on 2005-05-18
Hey, i have been running ubuntu for some time now, and recently upgraded to ubuntu x86-64. I have had a couple problems and im hoping someone here can help me out. 

First i wanted to get zsnes working or some snes emulator to play some of my old favorites. I tryed the zsnes package for (hoary i386) I force installed it. But now i get this error: error while loading shared libraries: libSDL-1.2.so.0: cannot open shared object file: No such file or directory

Im not sure if there is a zsnes amd64 package or if there is a way to run zsnes 32 bit in 64 bit ubuntu.

My second problem is with Azureus and can be summed up in this post i made:
[http://ubuntuforums.org/showthread.php?t=34708](http://ubuntuforums.org/showthread.php?t=34708)

My third Problem is that i have been unsucessful in installing unrar.
I did the simple sudo apt-get install unrar, but file-roller still does not work!
If read baout problems with unrar in 64 bit linux but i was wounding if anyone figured a way to get it working out?

Thanks for your time and sorry about my lack of writing skills.

---

### Post by zxc on 2005-05-18
[QUOTE=drews_blunted]Hey, i have been running ubuntu for some time now, and recently upgraded to ubuntu x86-64. I have had a couple problems and im hoping someone here can help me out. 

First i wanted to get zsnes working or some snes emulator to play some of my old favorites. I tryed the zsnes package for (hoary i386) I force installed it. But now i get this error: error while loading shared libraries: libSDL-1.2.so.0: cannot open shared object file: No such file or directory

Im not sure if there is a zsnes amd64 package or if there is a way to run zsnes 32 bit in 64 bit ubuntu.

My second problem is with Azureus and can be summed up in this post i made:
[http://ubuntuforums.org/showthread.php?t=34708](http://ubuntuforums.org/showthread.php?t=34708)

My third Problem is that i have been unsucessful in installing unrar.
I did the simple sudo apt-get install unrar, but file-roller still does not work!
If read baout problems with unrar in 64 bit linux but i was wounding if anyone figured a way to get it working out?

Thanks for your time and sorry about my lack of writing skills.[/QUOTE]
 [http://ubuntuforums.org/showthread.php?t=34548](http://ubuntuforums.org/showthread.php?t=34548)

That's how I open .rars...works fine for me, but I couldn't get unrar to work for me either :/

---

### Post by FluffyElmo on 2005-05-19
I've had good luck with *unrar-nonfree*. Just enable the multiverse repository in Synaptic and you should be able to install it.

---

### Post by drews_blunted on 2005-05-19
Ahh, thank you very much i got my unrar working great and it even works in file-roller!

:)

Now if i could just get azureus and zsnes to work i would have a great system!

---

### Post by FluffyElmo on 2005-05-20
I haven't tried ZSNES but if it isn't in the repositories, you'll either have to find a repository that has it or build from source. There are instructions on the ZSNES forums for building from source, you'll have to install development tools first.

A Google search turns up this as a repository that has an amd64 version of ZSNES, but note that it seems to build against Debian testing so there may be dependency problems. 

[http://ftp.tiscali.nl/debian-pure64/dists/testing/non-free/](http://ftp.tiscali.nl/debian-pure64/dists/testing/non-free/)

Good Luck!

---

### Post by Sam on 2005-05-20
I've successfully installed zsnes on an AMD64, by using a [32bit chroot](http://ubuntuforums.org/showthread.php?t=24575).

---

### Post by drews_blunted on 2005-05-21
[QUOTE=Sam]I've successfully installed zsnes on an AMD64, by using a [32bit chroot](http://ubuntuforums.org/showthread.php?t=24575).[/QUOTE]
 Thanks this seems to work for zsnes. My only issue now with 64 bit linux, is that azureus still does not work. what is the easyest and fullproof way to install azureus on amd64 ubuntu?

---

