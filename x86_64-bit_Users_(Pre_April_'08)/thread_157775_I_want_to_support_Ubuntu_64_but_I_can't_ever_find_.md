---
title: "I want to support Ubuntu 64 but I can't ever find what I need."
date: 2006-04-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by braveerudite on 2006-04-09
I want to support Ubuntu 64 by using it but is hard to find stuff for it.  This sucks  I'm trying my best to refuse to go back to 32 Bit because I feel that if I do then Ubuntu 64 won't ever become as good or better than Ubuntu 32.  Please help me make a decision.

Should I go back to Ubuntu 32 or stay with 64?

---

### Post by John.Michael.Kane on 2006-04-09
braveerudite yes alot of programs are not natively suported yet by 64bit.However i can understand your "which one should you use question". however the best responce I can give you is to use the one that offers the things you need at this time. Speaking for myself i don't use flash or w32codec's ect so i can run 64bit clean. you have ask yourself what is it you use now ie:programs ect that you can do with out till they are suported, if you answer none then you have to use 32bit.

---

### Post by Craig Caldwell on 2006-04-10
I've been trying to stick it out with 64 bit. I can live with out flash... no wait I can't, I have to see the wrestling robot clip again... and again. Getting my logitech mx700 to work in Breezy 32 bit wasn't easy for me but i was able to copy and paste it into submission. I was able to get tseliot's script for nvidia drivers to work with the release it 64 bit, but couldn't tell what kind of difference it made because glxgears no longer worked and blender never worked for me in 64 bit. I'll stick it out with 64 for a bit but I will probably run a parallel 32 bit on another partition to get the stuff 64 is currently missing.

---

### Post by Thomas,Bakker on 2006-04-10
Im an complete newbie on Linux and i thought i need 64bits cause of my cpu.
I didnt understood the info on the d-load page right i guess cause it seems many
people whit 64bits cpu's seem to use the 32bits linux distro's.
Now i aint able to print things and also i have no succes installing my
Ati Radeon 9800 vid card.
But as you already said if we all give up on it we could just as good pull the plug out of it all together. So i think we just need to keep using it so the Dev's can improve it.
Anyway i cant wait till Dapper is out and im sticking whit 64bits.

---

### Post by rkerstetter on 2006-04-10
Stay with 64!  I will never go back after using 64 bit Linux.  I encode video and audio at more than twice the speed of a comparable 32 bit machine.  That is very significant.

---

### Post by dyrer on 2006-04-10
I agree Ubuntu 64bit will use our AMD64 processors, but it wont work well with macromedia flash and many other apps :(

---

### Post by braveerudite on 2006-04-10
[QUOTE=rkerstetter]Stay with 64!  I will never go back after using 64 bit Linux.  I encode video and audio at more than twice the speed of a comparable 32 bit machine.  That is very significant.[/QUOTE]


You encode Audio/Video with the 64 Bit version?  

If I can get the DVD/AVi (Divx) and MP3 to work on 64 bit I'll stray with Ubuntu 64.

How did you get it to work? Would you please tell me how?

---

### Post by rkerstetter on 2006-04-10
I didn't do anything special to get audio/video encoding to work.  I placed the 32 bit codecs in /usr/lib/win32.  I can then use ffmpeg to convert from say a DiVx to DVD format.  I am also talking about doing things like converting mp3 to ogg using mp32ogg.  It all works at about twice the speed of a 32 bit system.

---

### Post by slug on 2006-04-11
Stick with AMD 64 there are allways work arounds for any issue's you have.
Admittedly I don't use Flash but the things that i do use work no probs

eg:
Sun's java 1.5.06
Eclipse 3.1.2
VLC (Xvid player)
X with nvidia-glx 

If you have any problems with 64bit, just look on the forums. The support here is amazing...

If something isn't already packaged, compile if from the sources.

---

### Post by djroadrash on 2006-04-17
hi everyone;
just to mention that there is a thread that has a solution for flash and java for ubuntu 64, i have not tried it yet, just came across it. it might break some systems and some versions of firefox it seems. check it out:[http://www.ubuntuforums.org/showthread.php?t=112418]("http://www.ubuntuforums.org/showthread.php?t=112418")
i got ubuntu dapper running on an intel p4 3.0ghz prescott processor. works nice had to figure how to get sound to work but in the end it sounds better than xp pro.
Braveerudite: stick with ubuntu 64, if you have a big enough hard drive, install both 32 and 64 editons and switch when you need something that is missing, also if you can, use dapper, it works very well now and if you apt-get dist-upgrade, you will find some of the stuff will start working by itself. always remeber not to apt-get update before you dist-upgrade, and dont do it on gui. to get out of gui type Ctrl-Alt-F1, but make sure to save all files since you are going to be on comand line only. to reboot you can either stop the machine and restart with powerswitch with "sudo halt" or Ctrl-Alt-Delete should do it.
good luck choosing
djroadrash:)

---

### Post by braveerudite on 2006-04-17
> **djroadrash]hi everyone said:**
> http://www.ubuntuforums.org/showthread.php?t=112418[/URL]
i got ubuntu dapper running on an intel p4 3.0ghz prescott processor. works nice had to figure how to get sound to work but in the end it sounds better than xp pro.
Braveerudite: stick with ubuntu 64, if you have a big enough hard drive, install both 32 and 64 editons and switch when you need something that is missing, also if you can, use dapper, it works very well now and if you apt-get dist-upgrade, you will find some of the stuff will start working by itself.
djroadrash:)


Yes! 2 Days after I posted this I decided to go test my luck with Dapper Drake (Ubuntu 6.04 "AMD64 Edition")  and everything works great.  I can finally play all popular video/audio format in 64 Bit version using gstreamer 10.  Everything works perfect now.  The flash thing I haven't bother to mess with much but I will look into it more this week.  Thx for the link to the flash fix, I bookmark it to try it out later.  :)

---

