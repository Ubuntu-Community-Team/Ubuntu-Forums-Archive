---
title: "I want a simple answer please"
date: 2007-01-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by paul cooke on 2007-01-21
OK,

having panicked at the thought of Vista being forced on consumers in February when it is released to the OEMs... I decided to get new boxes to basically future proof myself (and avoid the Vista EULA).

(I was forced to buy one, my daughter "killed" the laptop by spilling a can of cola over it and we had to get a new box for her to do her coursework on (she has to use visual studio .NET for her  assignments))

Having discovered what a bargain I got for her, I got myself one as well, but I went up a step and got AMD64x2 3800+ with a gig of RAM instead (she's got a basic Sempron 3000+ with 512 Meg RAM).

We both want Ubuntu/Kubuntu on these boxes as our main OS (preserving XP for games (in my case) and coursework for her). However, I've never had an AMD64 box before, or SATA and I'm frightened of killing a box while attempting to install the amd64 version of Ubuntu/Kubuntu. (all I got with these boxes was a couple of blank DVDs to burn the restore disks onto (first thing I did for both), so I haven't got proper XP install disks at all)

I've heard some horror stories about Linux and SATA and want to know if it is idiot proof now to install Edgy Eft on an AMD64 box with only SATA drive(s) without having to wipe XP off first and partition from scratch.

I'm currently downloading the desktop and the alternate versions of both Ubuntu and Kubuntu AMD64 torrents. Which should I use to install from, the desktop or the alternate? And will I have any problems partitioning? The boxes currently have the disks set up as C: & D: for her machine and C:, D: & E: for mine. They appear to be single disks according to the box specs, but I'm not sure where to check this using the Live desktop distro to find out.

So, is there a proper WIKI page dedicated to this issue?

---

### Post by Garyu on 2007-01-21
I used to have a machine with AMD-64 and IDE drives. No problems there with anything I tried.

Now I have a similar setup as you do: AMD-64x2, 1gig RAM, SATA-drive. No problems. I have installed Ubuntu64 and Ubuntu-i386, both 6.10, and everything has been working just fine. I have never tried Kubuntu on this machine though, but that shouldn't be a problem. 

As I understand, the main problem with SATA is if you want to make a software-RAID out of it, which is quite possible but requires a lot of work. I've never tried this since I only got one harddrive, but from what I have heard this is what is causing most people problems.

The main thing you need to do (as always BEFORE buying anything) is check the linux hardware compatibility guide/list so you know that your hardware is actually supported. With that reservation, things should work just fine.

---

### Post by Sef on 2007-01-21
It would best to use the 32 Ubuntu for now.  Not all of the apps are 64 bit, e.g., flash.

---

### Post by paul cooke on 2007-01-21
> **Garyu said:**
> I used to have a machine with AMD-64 and IDE drives. No problems there with anything I tried.

Now I have a similar setup as you do: AMD-64x2, 1gig RAM, SATA-drive. No problems. I have installed Ubuntu64 and Ubuntu-i386, both 6.10, and everything has been working just fine. I have never tried Kubuntu on this machine though, but that shouldn't be a problem.

thanks for the reassurance :) does nvidia 3D work on AMD64? It's not desperately essential, but would be nice. I couldn't find any desktop boxes with Intel graphics on them... it appears those graphics chips are pretty rare in the shops... OEMs appear to go for the cheap nvidia and ati setups.

---

### Post by paul cooke on 2007-01-21
> **Sef said:**
> It would best to use the 32 Ubuntu for now.  Not all of the apps are 64 bit, e.g., flash.

would that take advantage of the dual cores?

---

### Post by Garyu on 2007-01-21
Oh right, as Sef is saying: if you are only downloading 64-bit versions... You will have some difficulties with many things...

I got World of Warcraft running under Wine no problems on the 64-bit version. But to get flash in Firefox... You need to meddle with running 32-bit applications in a 64-bit environment, which is not impossible but not something you would recommend to anyone. So unless you know what you're doing, do like I do, install Ubuntu-64 on one partition and Ubuntu-i386 on another. Then find out what you can't do on Ubuntu-64, and decide if you need those things enough to bother with the 64-bit version or if you want to run the i386 version all together. The performance boost on 64-bit version is negligible in most cases.

---

### Post by Garyu on 2007-01-21
> **paul cooke said:**
> thanks for the reassurance :) does nvidia 3D work on AMD64? It's not desperately essential, but would be nice. I couldn't find any desktop boxes with Intel graphics on them... it appears those graphics chips are pretty rare in the shops... OEMs appear to go for the cheap nvidia and ati setups.

Personally I would never use anything else than nvidia. I got nForce chips on my motherboards and GeForce chips on my graphics cards. And as I said, I've never encountered any hardware issues on my computers. You need to install the nvidia graphics driver separately though. I usually install Automatix ([www.getautomatix.com](www.getautomatix.com)) to do this for me, but you could probably do it with EasyUbuntu, Synaptic or apt-get as well.

---

### Post by paul cooke on 2007-01-21
OK then... Looks like I'll start downloading the 32 bit versions then... cheers. I suspect the boxes are only running XP MCE in 32 bit as well...

---

### Post by Kilz on 2007-01-21
> **paul cooke said:**
> OK then... Looks like I'll start downloading the 32 bit versions then... cheers. I suspect the boxes are only running XP MCE in 32 bit as well...

Dont let installing 32bit applications scare you away from using 64bit Ubuntu. There are a lot of howto's , scripts, and applications designed to install 32bit firefox, flash and java. If you can cut and paste you can have it installed in under a half hour , less time if you use a application/script like simple64. Installing 32bit applications is not hard and there are only a handful that you may need.

---

### Post by Garyu on 2007-01-21
> **Kilz said:**
> Installing 32bit applications is not hard and there are only a handful that you may need.

Really? I was messing with this in Dapper and thought it was really difficult so I finally gave up and just started using the 32-bit. There was really not any good howto's around though, that I could find.

---

### Post by Kilz on 2007-01-21
> **Garyu said:**
> Really? I was messing with this in Dapper and thought it was really difficult so I finally gave up and just started using the 32-bit. There was really not any good howto's around though, that I could find.

You must not have looked real hard. [There is a sticky ]("http://www.ubuntuforums.org/showthread.php?t=191205") that has links for howto's to the few common 32bit applications that are needed. If you are specificly looking for help installing 32bit Firefox and plugins, I wrote the howto and script most people used for Dapper. But there are numerous posts, a search, or even looking at the top 2 pages in this forum should give you all the help you need.

---

### Post by Garyu on 2007-01-21
ah, well, I was looking at it the weeks immidiately after Dapper was released. At that time at least the thread you are pointing to did not exist. Anyways, it is very nice to see that there are some things available in this area now. Maybe I will start using my 64-bit edition a bit more often. Thank you for the link. :)

---

### Post by Kilz on 2007-01-21
> **Garyu said:**
> ah, well, I was looking at it the weeks immidiately after Dapper was released. At that time at least the thread you are pointing to did not exist. Anyways, it is very nice to see that there are some things available in this area now. Maybe I will start using my 64-bit edition a bit more often. Thank you for the link. :)

[Dapper was released June 1 2006 ]("https://wiki.ubuntu.com/DapperReleaseSchedule") [The sticky was started on June 7, 2006]("http://www.ubuntuforums.org/showthread.php?t=191205"). While it has changed over time. The 64bit section has always been available to help people on the subject of installing 32bit software into Dapper at least. I wrote the 32bit Firefox howto on June 23rd 2006. I remember linking to it a lot back then.
What surprises me is that some people still think that 32bit applications cant be installed , or that its to hard. That may have been the case right after Dapper, but it is not the case any more. It seems some things never go away. Just like "Is 64bit ready yet" posts. :D

---

### Post by Garyu on 2007-01-21
> **Kilz said:**
> What surprises me is that some people still think that 32bit applications cant be installed , or that its to hard. That may have been the case right after Dapper, but it is not the case any more. It seems some things never go away. Just like "Is 64bit ready yet" posts. :D

Well, maybe we shouldn't hi-jack this thread... But I have to comment and say that I followed the link you provided and tried some things out. What I found was broken links, and the links that worked gave me packages that wouldn't install ("Broken pipe"?). I did not try your particular howto though, if that makes you feel better. ;) But I will stick to the i386 version at least for now. 64-bit sounds great, but to make everything work like you expect with i386 versions is just too much hassle. Also, I experience crashes a lot more often in the 64-bit environment. Especially annoying: the gnome panels will freeze (very often) so I have to Ctrl-Alt-Backspace every now and then. Stability is always more important than performance. And as I said before, the performance boost is negligible in most cases.

I still check back to the 64-bit now and then though. I am hoping to make the switch when enough stuff is working. Like Feisty + 1 or something. :)

---

