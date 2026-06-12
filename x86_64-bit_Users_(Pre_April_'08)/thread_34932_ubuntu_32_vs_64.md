---
title: "ubuntu 32 vs 64"
date: 2005-05-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by jzietman on 2005-05-16
i'm currently deciding on whether to install the 32-bit or 64-bit versions of ubuntu. here are my system specs:

a64 3000 s754
abit kv8-pro
512 mb ram
geforce 6800nu
74gb 10k rpm raptor sata hd
sb live! 5.1 sound card

i think that's all the important specs, if you want more, just ask. 

i know that there are a lot of people with problems getting their sb live! cards working in the 32-bit version. is there the same problem in the 64-bit version, and does anyone know a good solution? 

is 64-bit worth it in terms of smoothness, installation/compiling speed? even if i have only 512 megs of ram?

i will be playing neverwinter nights and possibly america's army on ubuntu. as far as i know, these only have 32-bit versions. can the 64-bit version run these?

is there 64-bit supoprt for java, flash, mp3, etc? even the browser plugins?

are the win codecs like wmv/wma, mp3, wav, aac, etc. even available for the 64-bit verison of ubuntu?

what's a 32-bit chroot?

thanks so much guys!

---

### Post by Sam on 2005-05-16
It a bit tricky to set up a fully functional Ubuntu 64bit... Be aware that not everything is available on 64bit, eg. Flash.

For the codec, no problem, everything is available.

But you can do a [32bit chroot environement](http://www.ubuntuforums.org/showthread.php?t=24575), which allows you to run every 32bit apps. I have an another Firefox in 32bit with Flash, and I'm switching if I need it.

I don't have any experience about gaming on 64bit, I cannot help you about this.

---

### Post by arunsub on 2005-05-17
I installed 64-bit, but I couldn't get win32codec to work with 64 bit. I couldn't install flash player for 32 bit (nor 64 bit) firefox i installed on 64 bit. i was getting an error saying flash doesn't support x86-64. I don't want to go through the hassle of installing chroot, so i went to 32 bit. There's a minute performance difference bet 32 and 64.

---

### Post by Sam on 2005-05-17
[QUOTE=arunsub]I installed 64-bit, but I couldn't get win32codec to work with 64 bit. I couldn't install flash player for 32 bit (nor 64 bit) firefox i installed on 64 bit. i was getting an error saying flash doesn't support x86-64. I don't want to go through the hassle of installing chroot, so i went to 32 bit. There's a minute performance difference bet 32 and 64.[/QUOTE]
w32codec isn't available for 64bit, however, the are alternatives (my totem and xmms plays everything but I don't remember how I did).
Flash is only available for 32bit, and with a chroot environement there isn't any problem.
There is an excellent howto for installing chroot (link above).

---

### Post by jzietman on 2005-05-17
ease-of-setup-wise, is 32 significantly easier than 64-bit if flash, java, alsa config for sb live, etc., are all figured in?

---

### Post by mrscintilla on 2005-05-18
[QUOTE=jzietman]ease-of-setup-wise, is 32 significantly easier than 64-bit if flash, java, alsa config for sb live, etc., are all figured in?[/QUOTE]

32 is infinitely better in terms of setup.  There is an automated script on this forum. You run it after you install the CD.   Everything took me less than 30 minutes or so from popping the CD in and getting a fully functioning system out.  My tip for nvidia owner is that once you install nvdia drivers, reconfigure xorg.  ask me if you need the exact command sequence.

I must say that ubuntu 32-bit beats windows by miles in terms of installation speed. 

And since I switched from 64 to 32, I have not noticed any performance difference. And everything works great!  I have sound, video, printing, everything except I have not tried my scanner yet.

The automated update is great. There is an icon that tells you when upgrades are available. I don't miss anything from windows except some seldom-played games.

Give 32 a try, don't bother with 64.  This is my adivce and I stand by it.

---

### Post by Raku on 2005-05-18
Am I understanding this right..... by using the chroot work around linked above I will be able to run both 32 and 64 bit packages at the same time?  so in theroy cedega should work too?  provided i point it to the right directories?

---

### Post by jzietman on 2005-05-19
[QUOTE=mrscintilla]32 is infinitely better in terms of setup.  There is an automated script on this forum. You run it after you install the CD.   Everything took me less than 30 minutes or so from popping the CD in and getting a fully functioning system out.  My tip for nvidia owner is that once you install nvdia drivers, reconfigure xorg.  ask me if you need the exact command sequence.[/QUOTE]

so, what's the exact command sequence?

---

### Post by BigCdaAnswer3 on 2005-05-25
dpkg-reconfigure xserver-xorg

---

### Post by gratefulfrog on 2005-05-25
[QUOTE=Raku]Am I understanding this right..... by using the chroot work around linked above I will be able to run both 32 and 64 bit packages at the same time?  so in theroy cedega should work too?  provided i point it to the right directories?[/QUOTE]

I am sorry to say that the answer to this is maybe it will and maybe it won't.  I have a 64bit system with a 32bit dchroot and after extensive efforts and suffering can tell you that:
[list]
[*]some apps only work under 32b chroot,
[*]some apps work partially under both,
[*]some apps do not work in either.
[/list] 

In particular, if you start compiling your own source downloads, you will certainly be pulling your hair out...

(One may wonder why I still have the 64 bit platform? The answer is that someone has to pull the present into the future. If we all just wait around for 64bit open software to arrive all by itself, it may never happen...)

So the final word: 
if you want a system that works easily, out of the box, go for the 32bit version of Ubuntu (forget all those sound & graphics card issues, solutions are available!).

If you're an adventurer and have time and energy to burn, 64bit is the future (or maybe get a network of PS2's and build a supercomputer...)

Good luck!

---

### Post by mthaddon on 2005-05-25
I'll second grateful frog. If you want everything working ASAP, go 32 bit. If you're willing to spend a little more time tweaking things, you can use 64 bit.

I have the 32bit chroot working and have used it very nicely to install many things. I have Quake3, UT2004, Racer, and a ZX Spectrum emulator working on the gaming front (and have installed but not played around much with Vegastrike).

I use the 32bit version of firefox with the install script for all the multi-media plugins so I can run Realplayer, Quicktime and Windows Media. Some sites are a little buggy, but overall I'm very happy with it all.

64bit is the way forward. Can you imagine everyone using 32bit 10 years from now? If you have the time and willingness to work with it, I'd definitely recommend it.

---

