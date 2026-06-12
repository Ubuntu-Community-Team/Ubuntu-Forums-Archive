---
title: "AMD 64 Users Experiences"
date: 2004-10-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by Baloo on 2004-10-12
My new A64 board is due to turn up next week and I'm interested in A64 Ubuntu users experiences. Any problems so far? Any tips on installation?

---

### Post by ubuntu-geek on 2004-10-12
You might check this out, it may have some insight to any issues or tweaks when installing.

[http://www.ubuntulinux.org/support/documentation/howto/installation-amd64](http://www.ubuntulinux.org/support/documentation/howto/installation-amd64)

---

### Post by tambooki on 2004-10-14
I've been running Ubuntu on my Athlon64 for a couple of weeks now, and it's been a sweet ride. My only "complaint" at first was the lack of nvidia drivers for the amd64 flavor, remedied at the time doing it by hand. However, I just discovered today that the drivers are now available on amd64, so I'm happier than ever. The only thing to watch out for is there are fewer repositories you can look to for 64-bit binaries. I mainly feel this in regards to multimedia stuff. I don't believe there's a 64-bit version of the "marillat" repository referenced when discussing getting win32codecs and such. Of course, one can also install a 32-bit chroot, as I did the other day. I followed the Debian 64 howto, although of course I adapted it to install an ubuntu 32-bit chroot instead of debian. (If anybody knows of some repositories or easier way to do this, please post!)  I came to ubuntu from gentoo, and haven't looked back (thankfully, I don't think I need to worry about distro-religious wars starting on this forum  :wink: )

---

### Post by Baloo on 2004-10-14
I have a Radeon 9800 pro coming so 3d stuff is out of the question for me (hurry up ATI!) but I too would be interested in more 64 bit repositories.

---

### Post by goatboy on 2004-10-14
I've been running amd64 ubuntu since the preview first came out. It's the first amd64 distro that's actually been stable for me. I tried FC2 and debian-amd64 before, and both were crashing all the time. My only complaint is how much of multiverse is unbuilt. Mostly things like transcode and mplayer.

Also, while the base system has been 100% stable a few apps just don't work. transcode and xmame just crash on startup here.

[quote=tambooki]The only thing to watch out for is there are fewer repositories you can look to for 64-bit binaries. I mainly feel this in regards to multimedia stuff. I don't believe there's a 64-bit version of the "marillat" repository referenced when discussing getting win32codecs and such.[/quote]
Multiverse! It contains most of debian non-free, marillat, and a few other things (mythtv!). Large portions of it are still unbuilt, but for what's there you can get by adding "multiverse" to /etc/apt/sources.list, like so:
```
deb http&#58;//archive.ubuntu.com/ubuntu/ warty main restricted universe multiverse
```

Of course, 32bit w32codecs won't work with a 64bit mplayer. Not that mplayer is built in multiverse yet, anyway.

---

### Post by latrine on 2004-10-22
Please post your specs...

1- I Can't start a gnome session because it freezes... Can only use it at command line...
2- SUDO *****-* doesn't work... just doesn't... it does nothing and I keep the keyboard input on the screen... just pressing enter takes me to the next line... 
3- My network card isnt' detected... at least during instalation... and tha leaves without apt-get internet updates.
4- awfulll experience...

Will install windows XP 64 Bits free edition and see what happens... 

AMD Atlhon 3200+
Abit k8v pro ( via chipset 754)
geforce 4400 (agp - &gt; waiting for a 660 gt agp with a nice price tag)
512 mb Ram
SATA 150 120 GB seagate
IDE IBM 15 Gb totaly devoted to alternative OS (where I installed Ubunto 4.1)

Have fun... I haven't given up... I have just postponed.. maybe on ubunto 5

Latrine

---

### Post by jdong on 2004-10-24
Asus K8V Deluxe
Athlon64 3000+ ClawHammer
512MB RAM


Warty 4.10 release for amd64, k8-optimized kernel


Overall positive experience, system working on first boot! The Setting Hardware Clock process gives weird error, but causes no problems. Sudo works, GNOME works, installing Nvidia through APT works.


Same complaints as with any 64-bit Linux distro (Suse, Gentoo, Debian-AMD64, Fedora), that is lack of packages and compatibility issues. Ubuntu is significantly better than the other mentioned distro in this field, but still packages like WINE are missing, which drives me NUTS! lol


I installed i386 Ubuntu. I feel no performance difference between 64-bit and 32-bit (like any other of my 64-bit Linux experiences!), so I'm extremely happy with Warty i386. Until I find a convincing reason, I'm staying with a 32bit Ubuntu.

---

