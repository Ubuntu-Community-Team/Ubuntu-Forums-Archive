---
title: "Considering 64-bit"
date: 2006-07-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by ATAQ on 2006-07-01
Hi, I currently run Ubuntu 5.04 32-bit, 
I was thinking about running 64-bit 6.06.
Not sure though. I mainly use my computer for internet, music, video, games (Native & Cedega)
Can anybody tell me if 64-bit would be a good solution for what I am using it for.
Thanks,

---

### Post by Kilz on 2006-07-01
[QUOTE=ATAQ]Hi, I currently run Ubuntu 5.04 32-bit, 
I was thinking about running 64-bit 6.06.
Not sure though. I mainly use my computer for internet, music, video, games (Native & Cedega)
Can anybody tell me if 64-bit would be a good solution for what I am using it for.
Thanks,[/QUOTE]
I dont think you will have a lot of problems if you want to try 64 bit. [There is a sticky with links to work arounds for all the common problems]("http://www.ubuntuforums.org/showthread.php?t=191205"). As for video and music you can play almost all file formats, except wma and wmv without any work arounds. You can use Cedega by installing the small package with
sudo dpkg --force-architecture -i <filename> 
It works for me without problems.

---

### Post by zonerr on 2006-07-01
The only problem right now with 64 bit is that a lot of programs runs 32 bit only. There are work arounds but thatcan also entail loading up 32 bit gcc libraries to run Wine. In time it will all be 64 but untill then I boot three OS's one being a 32 bit Linux so I can run some programs not yet in the 64bit cue.

---

### Post by Kilz on 2006-07-01
[QUOTE=zonerr]The only problem right now with 64 bit is that a lot of programs runs 32 bit only. There are work arounds but thatcan also entail loading up 32 bit gcc libraries to run Wine. In time it will all be 64 but untill then I boot three OS's one being a 32 bit Linux so I can run some programs not yet in the 64bit cue.[/QUOTE]
What programs are those that you cant install in 64bit? If its wine, there is one lib package that needs to be copied in.[ Is should take all of about 5-10 minutes to setup.]("http://www.ubuntuforums.org/showthread.php?t=185557")

---

### Post by ATAQ on 2006-07-02
Nice one, I'll try out 64-bit. Thanks lads ;)

---

### Post by Lil_Eagle on 2006-07-03
I have to agree that the 64-bit version works well.  I have managed to fix most of the shortcomings (thanks to kilz).  It doesn't seem much faster than the 32-bit version for the day to day use, but if you do some number crunching, you'll notice a difference.  Especially if you do video editing or rip a lot of music.   I sometimes (frequently actually) recode music that I have downloaded to a lower bitrate so I can fit more songs on my mp3 player.  That is a task that is faster on the 64-bit than the 32.

I have noticed that some of the applications don't work the same.  Firefox is one of them.  The solution is simply to install the 32-bit version of any program that doesn't have full functionality in 64 bit.  You can have the best of both worlds, but there are configuration issues that must be dealt with.

A multiarch distro is in the works, but it may be a year or two before it actully becomes reality on the desktop.  Hopefully, as more people start demanding a fully working 64-bit version, everything will be made to work effortlessly.  Debian is supposed to have a multiarch realease of etch, which is supposed to  be released by the end of the year, but honestly I don't see it happening.  Perhaps Edgy+1 will be multiarch, however don't hold your breath.

---

### Post by Kilz on 2006-07-03
[QUOTE=Lil_Eagle]A multiarch distro is in the works, but it may be a year or two before it actully becomes reality on the desktop.  Hopefully, as more people start demanding a fully working 64-bit version, everything will be made to work effortlessly.  Debian is supposed to have a multiarch realease of etch, which is supposed to  be released by the end of the year, but honestly I don't see it happening.  Perhaps Edgy+1 will be multiarch, however don't hold your breath.[/QUOTE]
Believe me, I wont hold my breath. I plan on being very vocal in requests for 64bit development. As should all users of the 64bit OS.

---

