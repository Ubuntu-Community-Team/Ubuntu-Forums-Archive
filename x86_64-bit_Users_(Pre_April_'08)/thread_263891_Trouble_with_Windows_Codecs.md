---
title: "Trouble with Windows Codecs"
date: 2006-09-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by fatsheep on 2006-09-23
I tried this HOW TO: [http://www.ubuntuforums.org/showthread.php?t=188974](http://www.ubuntuforums.org/showthread.php?t=188974)

But I'm still getting some crap about no codecs in mplayer when I try to play a wmv file.  First off, when I got to the section where I had to make a directory here's what I got:

> fatsheep@fatsheep:~$ sudo mkdir /usr/lib/win32
mkdir: cannot create directory `/usr/lib/win32': File exists
fatsheep@fatsheep:~$ sudo cp essential-20060501/* /usr/lib/win32/


I took a look in nautilus and there is a shortcut named "win32" in /usr/lib/ pointed at /usr/lib/codecs.  Is this a problem?

Second off, do I need 32-bit mplayer for this to work?  If so how do I tell if my mplayer is 64-bit or 32-bit?  And how would I install 32-bit mplayer?

Thanks in advance,

-sheep

---

### Post by Kilz on 2006-09-23
> **fatsheep said:**
> I tried this HOW TO: [http://www.ubuntuforums.org/showthread.php?t=188974](http://www.ubuntuforums.org/showthread.php?t=188974)

But I'm still getting some crap about no codecs in mplayer when I try to play a wmv file.  First off, when I got to the section where I had to make a directory here's what I got:



I took a look in nautilus and there is a shortcut named "win32" in /usr/lib/ pointed at /usr/lib/codecs.  Is this a problem?

Second off, do I need 32-bit mplayer for this to work?  If so how do I tell if my mplayer is 64-bit or 32-bit?  And how would I install 32-bit mplayer?

Thanks in advance,

-sheep

The howto you link to gives directions on installing the 32bit mplayer, and yes you need it. This installs mplayer32 that use can use to view wmv files. right click on the file, click open with other application , click use custom command in the bottom and type in mplayer32.
But if you installed my 32bit Firefox script with mplayer plugins  you should already have the 32bit mplayer insalled as mplayer not mplayer32. This is so the plugins work.

---

### Post by fatsheep on 2006-09-23
> **Kilz said:**
> The howto you link to gives directions on installing the 32bit mplayer, and yes you need it. This installs mplayer32 that use can use to view wmv files. right click on the file, click open with other application , click use custom command in the bottom and type in mplayer32.
But if you installed my 32bit Firefox script with mplayer plugins  you should already have the 32bit mplayer insalled as mplayer not mplayer32. This is so the plugins work.

Yea you're right, now that I have reinstalled firefox32 with your script wmv playback works great in firefox and on the desktop. :razz:

---

### Post by yatt on 2006-09-24
> **fatsheep said:**
> I tried this HOW TO: [http://www.ubuntuforums.org/showthread.php?t=188974](http://www.ubuntuforums.org/showthread.php?t=188974)

But I'm still getting some crap about no codecs in mplayer when I try to play a wmv file.  First off, when I got to the section where I had to make a directory here's what I got:



I took a look in nautilus and there is a shortcut named "win32" in /usr/lib/ pointed at /usr/lib/codecs.  Is this a problem?

Second off, do I need 32-bit mplayer for this to work?  If so how do I tell if my mplayer is 64-bit or 32-bit?  And how would I install 32-bit mplayer?

Thanks in advance,

-sheep

According two the Suse forums, Some Gentooer made a 64-bit w32codec package. Might have an easy fix coming soon.

---

### Post by Kilz on 2006-09-24
> **yatt said:**
> According two the Suse forums, Some Gentooer made a 64-bit w32codec package. Might have an easy fix coming soon.

The thing is both Gentoo and SuSe are fully multiarch. They can install 32bit applications very easly. In SuSE its simply clicking on whet version of an application you want installed in yast. So it would be easy to make a 32bit codec package that would install to the 64bit version.

---

### Post by yatt on 2006-09-24
> **Kilz said:**
> The thing is both Gentoo and SuSe are fully multiarch. They can install 32bit applications very easly. In SuSE its simply clicking on whet version of an application you want installed in yast. So it would be easy to make a 32bit codec package that would install to the 64bit version.
But they package works with 64-bit MPlayer, not just the 32.

---

### Post by gurgle on 2006-09-25
is multiarch coming to ubuntu anytime soon?

---

### Post by yatt on 2006-09-25
> **gurgle said:**
> is multiarch coming to ubuntu anytime soon?

Supposed to be starting the process this release.

---

### Post by Kilz on 2006-09-25
> **yatt said:**
> But they package works with 64-bit MPlayer, not just the 32.

That I dought. 32bi9t codecs dont work with 64bit applications that I know of. Please provide a link to this if you have one.


[QUOTE=gurgle]  is multiarch coming to ubuntu anytime soon? [/quote] If by multiarch being able to open synaptic and chose between a 32bit and 64bit application. No. But 32bit applications can be installed in Dapper
If you want to learn a little bit why multiarch isnt here yet, [Read this.]("http://archives.free.net.ph/thread/20060909.143808.bde8b4cd.en.html#20060909.143808.bde8b4cd") Its my question to the developers on this issue.

[QUOTE=yatt]  Supposed to be starting the process this release.[/quote] It was suposed to. It was in the release announcement. But it looks like we are waiting on Debian. Yes I know the reason to use Ubuntu is so we dont have to wait on Debains insanly long release schedule. But it looks like Eye Candy is more important than functionality. The main reason for that is because some 64bit system users (the sheep who want it to "just work") use 32bit version and are quiet. As you know the squeeky wheel gets the grease.

---

### Post by tomdkat on 2006-09-25
"*Baaaaa*"  I'm one of the "64-bit sheep" but I try to be more vocal than not. :)

Peace...

---

### Post by Kilz on 2006-09-25
> **tomdkat said:**
> "*Baaaaa*"  I'm one of the "64-bit sheep" but I try to be more vocal than not. :)

Peace...

Its people like that who make me think about going to another distro. One that isnt aimed at newbies.

---

