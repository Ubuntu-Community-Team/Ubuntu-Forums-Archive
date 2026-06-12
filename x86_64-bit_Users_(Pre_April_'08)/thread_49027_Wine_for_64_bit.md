---
title: "Wine for 64 bit?"
date: 2005-07-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by Flac on 2005-07-14
Alright, im pretty new to linux in general, but im starting to get the hang of it.. I tried to install wine(i've heard it doesnt have great support, but i figured i'd see what it could and couldnt do myself)

 When i run the wine installer, i get this message

> Running configure...

configure: creating cache config.cache
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking whether make sets $(MAKE)... yes
checking for gcc... gcc -m32
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

Configure failed, aborting install.

I have the latest build-essentials installed, i can config/make other things, but this fails, My friend who got me into linux in the first place, said he had no clue, so i was thinking maybe it was a 64 bit thing?(i know we kind of have the short end of the stick when it comes to support right now)

 Is there a way i can do this? Am i just stupid and doing something wrong?

Any help would be appriciated :)

---Flac

---

### Post by filterban on 2005-07-14
I recall reading in this forum that the only way to get Wine working on 64bit is with a 32bit chroot.

Which, yes, is ugly.

Any other ideas?

---

### Post by Tamir on 2005-07-15
I belive you should install:
apt-get install libc6-dev

Tell us how it goes.

---

### Post by Flac on 2005-07-15
hmm, its already installed/up-to-date say's apt-get. Guess im just outa luck, oh well.

---

### Post by FluffyElmo on 2005-07-15
Onother option might be Qemu? It supports amd64 as a host architecture. Essentially an open source version of VirtualPC it will let you install a copy of Windows into your Ubuntu desktop. 

[http://fabrice.bellard.free.fr/qemu/](http://fabrice.bellard.free.fr/qemu/) 

There are pros and cons vs WINE, but if you just want to run office apps it may be less hassle than WINE in a chroot.

---

### Post by Tamir on 2005-07-15
Or you can wait some days, and I will try to work on it (a deb).
Keep updated : [http://ubuntuforums.org/showthread.php?t=48905](http://ubuntuforums.org/showthread.php?t=48905)

---

### Post by obx-jdt on 2005-07-15
just wondering.....What do you plan to do with wine? I installed it on Ubuntu 32bit. But I have no use for it myself. I use to use Mandrake, and wine worked great for browsing Win. partions, but it's not so swell on Ubuntu. You might want to try [Sourceforge](http://sourceforge.net/) for the latest version. 
Let us know how it works.

---

### Post by Flac on 2005-07-16
[QUOTE=obx-jdt]just wondering.....What do you plan to do with wine? I installed it on Ubuntu 32bit. But I have no use for it myself. I use to use Mandrake, and wine worked great for browsing Win. partions, but it's not so swell on Ubuntu. You might want to try [Sourceforge](http://sourceforge.net/) for the latest version. 
Let us know how it works.[/QUOTE]

 I was going to try to install some low-graphic games, I dont know much about wines functionality, but i heard it did alright for basic things. I would get cedega, but 1) I cant afford it(im po') and 2) from what i've seen it wouldnt run any better then wine does on 64 bit?

 Most of what i do on my linux partition is experimentation, mainly just trying to get the feel for things and learn my way around.

---

### Post by Tamir on 2005-07-17
I have the solution, do :
./configure CC=gcc

It should work

---

### Post by FluffyElmo on 2005-07-18
Thanks, Tamir...I'll have to try that! Just a quick notes from posts above...

For 'low-graphic' games you might want to try dosbox ([http://dosbox.sourceforge.net/news.php?show_news=1](http://dosbox.sourceforge.net/news.php?show_news=1) ), it's in the repositories and plays a lot of old games perfectly on my system. Games needing DirectX do need Wine though.

If you like old adventure games you might also like SCUMMVM ([http://www.scummvm.org/downloads.php](http://www.scummvm.org/downloads.php)), it and 'Beneath A Steel Sky' are both in the repositories.

---

