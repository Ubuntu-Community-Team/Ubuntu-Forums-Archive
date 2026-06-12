---
title: "AMD and 8-04 incompatibilty"
date: 2008-09-04
forum: x86 64-bit Users
---

### Post by hogi on 2008-09-04
Good morning;

I am throwing this scenario out to the community to see if anyone out there is experiencing something similiar to what I am experiencing. I just built an AMD desktop system (AMD 64 bit 4000 CPU on an ASUS A8VE-XE motherboard, 4 gb of ram and a 160 gb sata hardrive.) I can install Ubuntu 7-10 or lower OS but I can not install Ubuntu 8-04 OS. Nor can I install any variant of Ubuntu that uses the 8.04 system. I can install other Linux OS just as long as they are not based on Ubuntu 8-04. I tried doing an upgrade and that process stalled during the installation. I have done on-line research and tried the various recommendations and still no luck. The system stalls during the partitioning stage, it will not build a root partition. The condition is the same whether I try to install a 32 bit system or a 64 bit system.
So just for fun I went to my "klunker box" and resurrected a 5 year E-Machine desktop with an Intel system in it. (Everything is bare minumim and ancient technology) Much to my surprise I was able to install Ubuntu 8-04 and now have a working Ubuntu 8-04 system.(I was using the same DVD to do both AMD/Intel installs) 
Is there some form of incompatibility issues between Ubuntu and AMD 64 bit technology? I have not found any information at the AMD website regarding Ubuntu.

Thanks for any and all help.

---

### Post by Kilz on 2008-09-04
Are you using the desktop CD or the alternate install cd that is better for 64bit? have you checked the media for defects, did you check the md5sum of the file you downloaded?

Buy the way, I love emachines, I have a t1120 that I use as a file sever and an upgraded t6524.  :)

---

### Post by jdguzman on 2008-09-04
I think you might be on to something.  I'm having the same problem with a different AMD 64 processor.  I started a thread here:

[http://ubuntuforums.org/showthread.php?t=909900](http://ubuntuforums.org/showthread.php?t=909900)

I have not recieved a response though.

Regards,

JD

---

### Post by blindmellojelly on 2008-09-04
For what it's worth to you, I have almost the exact same machine and I've had no problem getting it up and running - however, when I first downloaded the DVD installer it did come up with a bad md5 every single time. I tried getting it from the local server about half a dozen times and every time it was broken. Finally I got a copy from Russia and it came up just fine.

Might want to check that if you haven't. The first broken disc (before I started checking them) did try to install but failed in random spots.

---

### Post by kjb34 on 2008-09-04
I have an Asus 8V-X with an Athlon 64 4600+ and I had the same problem getting 8.04 working. I even started a thread about it [http://ubuntuforums.org/showthread.php?t=899997&page=2]("http://ubuntuforums.org/showthread.php?t=899997&page=2").
Hope that helps. Anyway I don't think AMD64 and Ubuntu are incompatible but I think there's a problem with Asus and SATA hard drives

---

### Post by ianellis on 2008-09-05
Your data on the cd might be corrupt, try re-downloading it again

---

### Post by Jouke74 on 2008-09-05
This may sound crazy but there are even more reports about 4GB and AMD combo (Dutch forums). I heard of people installing it with 2 Gb and add the next 2 Gb afterwards.. Are you using an Nvidia card, because many people report problems with that as well.

Alternative approach: If you can install Gutsy then you can do a distro update as well. But there will be no guarantees it works then... (I guess)

Btw. I am running AMD 4200+ S939, 2 Gb Corsair, A8N SLI Premium and Raedon 1600 and all is working fine after a clean install with the AMD64 alternate CD.

---

### Post by Liviu-Theodor on 2008-09-05
Maybe you are trying to install the 32 bit variant of Ubuntu? Maybe you should install the 64 bit variant, because of the amount of RAM and the 64 bit processor. There are some errors on many OS-s when installing a 32 bit OS, with more then 3 GB of RAM.

---

### Post by xTheAvatarx on 2008-09-05
At this point im willing to try anything. I'm going to try installing the latest version 8.04 with less ram ( i have 4GB) and see if that installs properly. 

I have an ECS mobo, an ati video card, and an amd processor. I've been having really bad issues with install 8.04, so i don't think it's just ASUS motherboards.

---

### Post by Liviu-Theodor on 2008-09-05
> **xTheAvatarx said:**
> At this point im willing to try anything. I'm going to try installing the latest version 8.04 with less ram ( i have 4GB) and see if that installs properly. 

I have an ECS mobo, an ati video card, and an amd processor. I've been having really bad issues with install 8.04, so i don't think it's just ASUS motherboards.

Not long before, I stumbled upon a thread, on which ECS motherboards were describes as "not so good" or "very poor". I avoided them myself, because of who distribute them in my area (I don't like the shop). Sorry, it could be a problem with the motherboard itself. I use mainly AMD processors at home, while Intel at work. Motherboard used are from Gigabyte, ASUS, Foxconn (and some others, but these are the main).

---

### Post by xTheAvatarx on 2008-09-05
Quite possible, but unlikely. I have been running OpenSuse for over a year and it's been working fine. I decided to try ubuntu because i heard it was a little more efficient and streamlined , plus i wanted to try something new.

Ubuntu 7.10 installed just fine on my machine. But, the machine crashes randomly. I've never had that problem before.

I'm starting to think the ram probably isn't the issue. I mean why would the previous distro install fine (albeit with a few problems after installation) with 4GB's of ram, but next version doesn't? 

Does anyone know when the next version of ubuntu is coming out?

---

### Post by philinux on 2008-09-05
[http://ubuntuforums.org/forumdisplay.php?f=346](http://ubuntuforums.org/forumdisplay.php?f=346)

Scroll down for the release schedule.

---

### Post by Lenry on 2008-09-05
I have a core2duo 2.4 ghz processor in my aluminum I-mac and I tried to load the 64 bit version of ubuntu that I downloaded today. 9/5/2008.

I get a message that it needs to 64 bit os to work. And I can't load it.

What's up with that?

---

### Post by hogi on 2008-09-05
Thanks for the input guys.

Thinking it was my download and burning process I ordered a dvd from Ship IT. I have also tried a dvd from a magazine called "Linux Identity". The issue was a dedicated Ubuntu magazine. Still have the same problem so I ruled out a bad dvd.

I have tried the 32 bit and the 64 bit install--no good.

I have taken the system back to 1 gb of ram, then 2 gb of ram---no good.

The only success I have had is when I successfully installed Ubuntu 8.04 on the Intel system. This is why I think there is an incompability issue with the AMD hardware.

---

### Post by Lexicon101 on 2008-09-06
have you tried the dist-upgrade method? I see no reason it wouldn't work, everything worked fine on my system. (AMD 64 x2 4000+, 4 gigs of (multi-brand) ram, NVIDIA geforce 8600 gts, some creative sound card, and such.. I threw it lots of curves, and no chokes for me..)
I'm even running 8.10 right now, with few problems, mostly pertaining to USB stuff.. It works better, in my estimation, the only killer of the deal is.. usb HD + usb crashes = SUCK!

(It has something to do with my webcam, because when I boot without the cam plugged in, everything works fine for hours, but as soon as it's plugged in (whether at boot or during a session) usb stuff = crash.)

---

### Post by Liviu-Theodor on 2008-09-08
> **xTheAvatarx said:**
> Quite possible, but unlikely. I have been running OpenSuse for over a year and it's been working fine. I decided to try ubuntu because i heard it was a little more efficient and streamlined , plus i wanted to try something new.

Ubuntu 7.10 installed just fine on my machine. But, the machine crashes randomly. I've never had that problem before.

I'm starting to think the ram probably isn't the issue. I mean why would the previous distro install fine (albeit with a few problems after installation) with 4GB's of ram, but next version doesn't? 

Does anyone know when the next version of ubuntu is coming out?

One problem could be the use of the 32 bit version of ubuntu with 4 GB (but maybe you tried the 64 bit variant). The next version is scheduled for october (Intreprid Ibex, 8.10).

---

### Post by Liviu-Theodor on 2008-09-08
> **hogi said:**
> 
The only success I have had is when I successfully installed Ubuntu 8.04 on the Intel system. This is why I think there is an incompability issue with the AMD hardware.

I don't think ubuntu does not run on AMD hardware. In fact, I am sure it runs on such hardware, as I installed it on several such computers and worked just fine (I have installed also on Intel hardware, though). But, for sure, it has some minor glitches on both platforms (but no so big so one could not use it).

---

### Post by xTheAvatarx on 2008-09-08
> **Lexicon101 said:**
> have you tried the dist-upgrade method? I see no reason it wouldn't work, everything worked fine on my system. (AMD 64 x2 4000+, 4 gigs of (multi-brand) ram, NVIDIA geforce 8600 gts, some creative sound card, and such.. I threw it lots of curves, and no chokes for me..)
I'm even running 8.10 right now, with few problems, mostly pertaining to USB stuff.. It works better, in my estimation, the only killer of the deal is.. usb HD + usb crashes = SUCK!

(It has something to do with my webcam, because when I boot without the cam plugged in, everything works fine for hours, but as soon as it's plugged in (whether at boot or during a session) usb stuff = crash.)

The auto update feature hangs when i try to use it in 7.10. So I've abandoned that tactic.  Not sure why that happens either. Whenever i try to upgrade anything in my 7.10 version of ubuntu the auto updating program crashes/hangs.

I think i might try my chances with 8.10 and see how that goes.

---

### Post by StormPCs on 2008-09-14
I am running 64 bit Hardy on an AMD Phenom 9850 quad core (AM2+), 4GB DDR-2 800 and an nVidia 8600GTS on a Shuttle SFF.  It is rock solid.  There are no AMD compatibility problems.  If you use an ECS motherboard you are asking for trouble no matter what OS you run.

Get a decent motherboard and verify that your media integrity is good and you will have little trouble, 32 or 64 bit.

---

### Post by gragib on 2008-09-15
FWIW, I was having the same problem installing the 32-bit version. I have a 5000+BE on a GA-M69GM-S2H with 4GB RAM. Installation from CD always failed in unpredictable manners, and I thought it was a bad burn. That was my last blank CD, so I burnt the image to a DVD, and that worked fine.

The CD works fine with my Q6600 on a GA-P35C-DS3R with 6GB RAM, though I installed the 64-bits version on it later. It was just a test.

---

### Post by pony-tail on 2008-09-16
To my knowledge there is no AMD specific incompatibility issues with Ubuntu 8.04 - I have 8 AMD systems  3 are nForce 4 939 Dual core the rest are AM2 2 are Phenoms the other 3 are Athlon X2 All run 8.04.1 without any problems or issues except one - it is a Phenom 9850 on an Asus M3N-VM mobo with 2gig ram . it instals but has random lock-ups . random reboots , drops to a black screen in Firefox from time to time and just generally does weird things works fine with windows and strangely enough is now running OK with SuSe - So there can be distro specific issues with some motherboards . 
I think your board may have a piece of hardware that has an issue with the current kernel .

---

### Post by tuxxy on 2008-09-16
I cant see it, you could try a different motherboard in there and see if anything changes.

Heres a link to the [64-bit user group]("http://ubuntuforums.org/group.php?groupid=258") if you need any more information

---

### Post by pony-tail on 2008-09-16
> I cant see it, you could try a different motherboard in there and see if anything changes.
I have tried a different Mobo and It did make a difference (I fitted the components to a Gigabyte 780g mobo and all was well ! I tried an X2 5000+ on the Asus board - unstable . I did many mix and match combinations and the issue remained with that board , I even went back to the retailer and tried another M3N-vM board and it had the same issues - I am not overly concerned about it I was just letting the OP know that although there is not usually issues they crop up from time to time . The Asus M3N-VM is built on a fairly recent chipset (nVidia GF8200 ) and may not have full Linux support yet . If my recollections are correct the board the OP has is a VIA chipset and they have had issues with various kernel over the years .

---

### Post by tuxxy on 2008-09-16
Yes if there is an issue then it will most likely be down to how new that board is maybe you could check the hardware wiki for known comaptible boards for a replacement

---

### Post by KibaSilvernusWolfe on 2008-10-12
I am having this: "This kernel requires an x86-64 CPU, but only detected an i1586 CPU.  Unable to boot - please use a kernel appropriate for your CPU"

I have an **AMD X2 Dual core 6400+** with 2 gig ram.  Shouldn't this system be able to handle The **ubuntu-8.04.1-desktop-amd64.iso** from ubuntu's site?  Or am I misunderstanding that this "64 bit processor on the box"  isn't REALLY a 64 bit processor or just requires the other install. (Grinning with a bit of confusion)

Thanks,
Kiba

---

### Post by nordrasor on 2008-10-12
I'm running an AMD Athlon 3600+ 64 X2 Dual core processor. 4GB RAM. Asus M2N SLI Motherboard. I've installed Hardy Heron 64bit twice without any issues.

---

