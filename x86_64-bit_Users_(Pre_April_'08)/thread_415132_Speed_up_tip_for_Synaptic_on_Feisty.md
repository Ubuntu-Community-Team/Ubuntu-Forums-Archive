---
title: "Speed up tip for Synaptic on Feisty"
date: 2007-04-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2007-04-20
I just discovered something while playing with my new installation of Feisty. If you go into System > Administration > Software Sources you can change the mirror to download from. I set it to mirrors.cat.pdx.edu, because I am a student there and it is right in my backyard. But then I had only about 1500 packages. When I went back into Software Sources I noticed that you can also specify http or ftp. It was set to http so I changed it to ftp. After reloading I had more packages available than before -- 21,115. More important, using the Ubuntu server for the United States (the default for my installation because of the locale I specified during setup) the download rate was around 20K/s. Now I get 4-500K/s. You'll have to play with the different choices to see which one gives you the best bandwidth, but one of them will probably be faster than the default.

This tip doesn't work on Edgy because Software Sources only gives you two choices. However, I think you can do the same thing on earlier versions by manually editing /etc/apt/sources.list (as root).

---

### Post by ronocdh on 2007-04-20
> **John Jason Jordan said:**
> I just discovered something while playing with my new installation of Feisty. If you go into System > Administration > Software Sources you can change the mirror to download from. I set it to mirrors.cat.pdx.edu, because I am a student there and it is right in my backyard. But then I had only about 1500 packages. When I went back into Software Sources I noticed that you can also specify http or ftp. It was set to http so I changed it to ftp. After reloading I had more packages available than before -- 21,115. More important, using the Ubuntu server for the United States (the default for my installation because of the locale I specified during setup) the download rate was around 20K/s. Now I get 4-500K/s. You'll have to play with the different choices to see which one gives you the best bandwidth, but one of them will probably be faster than the default.

This tip doesn't work on Edgy because Software Sources only gives you two choices. However, I think you can do the same thing on earlier versions by manually editing /etc/apt/sources.list (as root).
Sick! Thank you! This is a wonderful time to know, as servers have been getting hammered by DL requests. =) Thanks again, 3J.

---

### Post by Drunner611 on 2007-04-20
How did you check to see how many packages are available to you?

NVM - i see it.

LMAO, i did "find best server" and it sent to Tawain from the US.  Somehow those are faster than the ones next to me.

---

### Post by octoberdan on 2007-04-20
> **John Jason Jordan said:**
> I just discovered something while playing with my new installation of Feisty. If you go into System > Administration > Software Sources you can change the mirror to download from. I set it to mirrors.cat.pdx.edu, because I am a student there and it is right in my backyard. But then I had only about 1500 packages. When I went back into Software Sources I noticed that you can also specify http or ftp. It was set to http so I changed it to ftp. After reloading I had more packages available than before -- 21,115. More important, using the Ubuntu server for the United States (the default for my installation because of the locale I specified during setup) the download rate was around 20K/s. Now I get 4-500K/s. You'll have to play with the different choices to see which one gives you the best bandwidth, but one of them will probably be faster than the default.

This tip doesn't work on Edgy because Software Sources only gives you two choices. However, I think you can do the same thing on earlier versions by manually editing /etc/apt/sources.list (as root).

Debian's apt-spy utility does this automatically. It tests the speed of each mirror then rewrites sources.list with the best mirrors. I just apt-cache searched and discovered that we have an apt-spy! Haven't checked it out yet though.

daniel@ubernix:~$ apt-cache show apt-spy 
Package: apt-spy
Priority: optional
Section: universe/admin
Installed-Size: 180
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Stephen Stafford <bagpuss@debian.org>
Architecture: i386
Version: 3.1-14.1
Depends: libc6 (>= 2.5-0ubuntu1), libcurl3 (>= 7.15.5-1)
Filename: pool/universe/a/apt-spy/apt-spy_3.1-14.1_i386.deb
Size: 28844
MD5sum: c53b95319512ffc239079c6e27fbfd8e
SHA1: fee6fad0ef79cfd55dd29e8b294bdfd41fc19abc
SHA256: 3bd138e7833cf973d2cd8a757d5fab67783a4b0511e15f8b52ee7c025650cddd
Description: writes a sources.list file based on bandwidth tests
 Parses a list of mirrors and tests each of the mirrors for bandwidth.
 Writes a /etc/apt/sources.list file based on the responses it gets.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

---

### Post by Spr0k3t on 2007-04-20
Interesing, I'll have to keep my eye open on this one.

---

### Post by Medieval_Creations on 2007-04-20
Definately kool... I plan on checking it out when I get home.
:)

---

### Post by timothywcrane on 2007-10-19
As I read through this thread I saw plenty of opportunity for quick post, but found it redundant to post to every one. I can´t wait to try the apt spy. In fact I won´t.

MS wants $60 to tell me how to get THEIR virus addicted (like America is to Oil) swiss cheese corporate code to educate itself in finding out that I do have a hard drive. I thought that´s what I paid over $100.00 for. How stupid do they think I am, oh right, that´s why they have me call them so they can ask me for $60.......NO More!

I&#314;l admit it, I´m lazy, but not stupid. 

I got an idea.


Added Linux cd, 
pushed install, 
played some Doom, 
played with the cuby thing, 
listened to some Beatles,
and watched a movie...
 
met a few cool cats in the forums.
told grandma about it,
The whole family can play along.


Get it. It really works.

Think Linux has what it takes to be a viable desktop?

Congratulations, I congratulate you all. I think we have made it, and beyond.

:lolflag:

---

