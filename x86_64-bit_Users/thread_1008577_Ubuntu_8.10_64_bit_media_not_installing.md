---
title: "Ubuntu 8.10 64 bit media not installing"
date: 2008-12-11
forum: x86 64-bit Users
---

### Post by jaime256 on 2008-12-11
I was wondering if anyone else is having a problem installing Ubuntu 8.10 64 bit? I have tried the amd 64 bit which you are routed to for all 64 bit versions and the alternate cd starts but then just stops. Sometimes I can get to the install screen and that's it. I tried different media, dvd-r, cd-r, cdr with lightscribe support or the ones you can write to I guess it is. I thought it was the hard drive and cd rom, but I have checked all that and it's fine. I have even burned the iso at different speeds, but still the same thing. I have even downloaded different isos and still the same. I got windows xp installed on it fine. I did manage to install one 64 bit version before on one of the hard drives, but the same can't be replicated again no matter what. I have two drives I'm using, both are working. I'm just wondering if anyone else is having problems with the 64 bit downloads? I've never had any problems before but I know the hardware is working fine. Just odd but now I'm almost certain it's not on my side. The alternate cd is now stuck at select and install software and it only got to 2%. I have been using the computer even though it's new so I know the hardware is fine.

System is:
Zotac nForce 630i-ITX micro itx
intel celeron 430 and the box does say it supports 64 bit, if I swap the hard drives i can use the other 64 bit system I managed to install.
2GB Ocz ram

---

### Post by jaime256 on 2008-12-12
Okay so far no matter which Ubuntu 8.10 64bit version I use, they all get stuck and won't finish installing. So here are a couple of other things I've done...

1. Updated the cd-rom bios even though I know this has nothing to do with this. I figured since I'm updating, I might as well.

2. Updated the bios on the motherboard, again to a new one. The older bios had the cpu dual core deactivated, the new one activated this, but my cpu is a single core. I disabled this and then the cd started going again, but eventually got stuck. I did get further in with this though. Hence the reason I had narrowed my problem to two items, either the cpu or the iso from canonical. I thought the cpu may be having problems with the 64 bit version of well, anything. I got windows xp working on it which is what I'm using to update this posting so the machine is working. And yes I know this is not a 64 bit version.

3. I got one of the alternate cd's, started the install and it stalled, I then restarted and did the recover and got a bit further, but then you have to manually set partitions and what not which I did, but it kept stalling on that select and install software.

4. I have decided to download a different distro and see what happens. I'll test that and if that works, I'll just keep using that. I don't know if this helps anyone, but I've done all the testing I can take for now. It's been two days and nothing, but I want to dual boot the desktop so I'll keep trying a few other things.

---

### Post by angryfirelord on 2008-12-12
Seems you did a lot of the testing already, so here's what I would suggest:

-When it get stuck on installing the packages, press Alt+F4. This will display the dpkg output and will allow you to see what package is getting stuck.
-Check for kernel issues. Boot with the -v option and see if it's throwing up any errors. You can also play around with some settings such as noacpi and noapic.
-Try another distro (as you said). If it boots properly, then it's probably something with Ubuntu.

---

### Post by jaime256 on 2008-12-13
Thanks for the info afl, I did download opensuse and I'm getting the same thing. It's just getting stuck. This is the same issue I had when I tried installing the 64 bit versions of the earlier Ubuntu and other distro versions. This was on a whole different system. So I will try your suggestion and see if I can find anything else. But now I'm sure it's on the iso side and not hardware. I guess this is something that's not fixed yet.

---

### Post by Arup on 2008-12-13
What program are you using to burn the ISO? If its Windows based, try ImgBurn, also select the lowest possible speed allowed by your disc.

---

### Post by Nemesis1278 on 2008-12-13
Ubuntu installed just fine for me.  I am although a ubuntu noob. But I do know that linux distros can be frustrating to work with.  Try running the Live CD option or Desktop option and see if that runs.

---

### Post by DeMus on 2008-12-13
> **jaime256 said:**
> I was wondering if anyone else is having a problem installing Ubuntu 8.10 64 bit? I have tried the amd 64 bit which you are routed to for all 64 bit versions and the alternate cd starts but then just stops. Sometimes I can get to the install screen and that's it. I tried different media, dvd-r, cd-r, cdr with lightscribe support or the ones you can write to I guess it is. I thought it was the hard drive and cd rom, but I have checked all that and it's fine. I have even burned the iso at different speeds, but still the same thing. I have even downloaded different isos and still the same. I got windows xp installed on it fine. I did manage to install one 64 bit version before on one of the hard drives, but the same can't be replicated again no matter what. I have two drives I'm using, both are working. I'm just wondering if anyone else is having problems with the 64 bit downloads? I've never had any problems before but I know the hardware is working fine. Just odd but now I'm almost certain it's not on my side. The alternate cd is now stuck at select and install software and it only got to 2%. I have been using the computer even though it's new so I know the hardware is fine.

System is:
Zotac nForce 630i-ITX micro itx
intel celeron 430 and the box does say it supports 64 bit, if I swap the hard drives i can use the other 64 bit system I managed to install.
2GB Ocz ram

Are you absolutely sure your system can handle a 64-bit OS? When I read your story it seems to me that you can not install a 64-bit OS at all. Try the 32 bit and let us know if that goes well.

---

### Post by jaime256 on 2008-12-13
Well, the box the cpu came in does say it supports 64 bit. I got a retail boxed cpu. In any case, I have tried burning at different speeds and also burned the newly downloaded image on a different computer as well. I like to do a clean install just to make sure the iso's work.

Here is a picture of where the system halted. This was the alternate cd. I went back and put the other HD I installed the 64 bit system on, but now it doesn't seem to be working at all. I'll take a picture of that later. I had the same problems on an AMD system a while back, this is an Intel system. If I remember correctly the i386 isos install fine, but I'll check later. I just want to use the 64 bit since the system can go up to 4 gigs, but also to just test it anyway.

I just turned on the computer with the 64 bit hard drive and now it works again...ahhh...I'll post the picture if it starts acting up again on this drive. I'll downgrade the bios and see if it will let me install it. I used the lower bios to install the system on this other HD. This is the first time they had two different bios, one I guess for the board I have and now a new version of the board. Go figure. I'm using a removable drive cage which is why I can change the hard drives quicker.

I use starburn on windows or the ubuntu burning programs, usually ubuntu. Thanks for the link arup, here's the one I use on windows.
[http://www.rocketdivision.com/starburn.html](http://www.rocketdivision.com/starburn.html)

My laptop has the i386 on it and the other computer has the amd 64 bit which was also a pain to install with 8.04. I even tried this old on on the new hardware, but still having similar install issues with the 64 bit. I did find out that once you get one installed, the upgrades work fine, but installation part is the part that still does this.

---

### Post by r m h on 2008-12-13
I installed Ubuntu 8.10 x86_64 just fine using the ISO image from the official Ubuntu DL site.

I burned the ISO to optical within ubuntu (actually mythbuntu 8.10).

---

### Post by jaime256 on 2008-12-19
Update: I finally downgraded the bios to make sure this was not the problem. Unfortunately I'm still getting the same problem so then I thought...why don't I try the other cd rom, just to see if that works...

It seems my cdrom is having issues but I can't tell because when I put in a cd with pictures under windows, I can see them fine. But now I can at least check the media where before the previous cdrom wasn't even letting me do this. Both are having problems on the first cdrom, the i386 and 64bit. I can get further down with the new cdrom, but the OS is still getting stuck later on.

I decided that instead of deleting the ubuntu partition with xp, I used Gparted to make sure everything was gone. At least I got the xp to use the full HD so I can start the Ubuntu and try once again. If you do this, ubuntu sees the whole drive and partitions it. There is just no option to continue from where it left off if you got through the installation half way. If you don't do this, ubuntu wants to partition the first partition where xp in my example is, and not use the second partition it first created. A pain really. I should also note that on this last time I used Gparted, it messed up my partition when I tried to expand it so the whole drive would be ntfs. Now I only see one hundredd from the two fifty drive under xp.

So....I'm wiping the whole drive and starting over. So the HD has been wiped and I'm now trying to get the 64 bit installed on the whole drive to keep things simple.

Okay, good news. After changing the physical cdrom I have been able to check most of the media cds I have burned the 64 bit isos on. I have found most of them regardless of the maker of the media have found an error in one file. I had one with no errors and used this for the install. Everything has installed fine without errors and I went up to the update and found that there are 202 updates! I did make sure to use the whole drive so it got wiped out of anything that was in there just to be sure. Did the bios have anything to do with this problem? I don't think so, but at least I narrowed things down and it never hurts to check even if it takes two weeks! I just had to be sure.

---

