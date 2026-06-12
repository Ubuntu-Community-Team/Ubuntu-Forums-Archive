---
title: "Ubuntu on a an amd phenom"
date: 2008-06-14
forum: x86 64-bit Users
---

### Post by slymi2005 on 2008-06-14
Alright so I'm thinking about getting an hp computer with an amd phenom triple core 8400, 4gbs memory, and nvidia gefore 6150se. I have a couple of questions. First, it comes preinstalled with 64 bit vista so I was wondering if I would be able to use wubi to install ubuntu or if I should just install it in a new partition, if so would this be the 32 or 64 bit version? Second, the phenom 8400 has some bug that affects performance by 15%, what's the case with ubuntu will this be a problem? Will the three cores make everything noticeably faster? Third, will I be able to run compiz with the nvidia geforce 6150se it has 128mb of dedicated memory and it says up to 1343mb as allocated by windows vista, does this apply to ubuntu as well. Not familiar with how video cards work. I think those are all my questions for now.

---

### Post by Kilz on 2008-06-14
> **slymi2005 said:**
> Alright so I'm thinking about getting an hp computer with an amd phenom triple core 8400, 4gbs memory, and nvidia gefore 6150se. I have a couple of questions. First, it comes preinstalled with 64 bit vista so I was wondering if I would be able to use wubi to install ubuntu or if I should just install it in a new partition, if so would this be the 32 or 64 bit version? Second, the phenom 8400 has some bug that affects performance by 15%, what's the case with ubuntu will this be a problem? Will the three cores make everything noticeably faster? Third, will I be able to run compiz with the nvidia geforce 6150se it has 128mb of dedicated memory and it says up to 1343mb as allocated by windows vista, does this apply to ubuntu as well. Not familiar with how video cards work. I think those are all my questions for now.

Wubi seems to be an easy way to install. But I prefer to install and dual boot. Since you already have a 64bit operating system, why not try 64bit ubuntu. Im not sure about the card and compiz, perhaps someone else can answer that.

---

### Post by slymi2005 on 2008-06-14
It's basically the same as the 32 bit version right?

---

### Post by Kilz on 2008-06-14
> **slymi2005 said:**
> It's basically the same as the 32 bit version right?

There are slight differences. But for the most part its the same. The performance improvement of up to 30% on some applications and ability to use more ram are the big differences.

---

### Post by rt2002 on 2008-06-15
> **slymi2005 said:**
> Alright so I'm thinking about getting an hp computer with an amd phenom triple core 8400, 4gbs memory, and nvidia gefore 6150se. I have a couple of questions. First, it comes preinstalled with 64 bit vista so I was wondering if I would be able to use wubi to install ubuntu or if I should just install it in a new partition, if so would this be the 32 or 64 bit version? Second, the phenom 8400 has some bug that affects performance by 15%, what's the case with ubuntu will this be a problem? Will the three cores make everything noticeably faster? Third, will I be able to run compiz with the nvidia geforce 6150se it has 128mb of dedicated memory and it says up to 1343mb as allocated by windows vista, does this apply to ubuntu as well. Not familiar with how video cards work. I think those are all my questions for now.

Hi slymi2005... first, I think that if your system is going to come with 4GB ram (and only increase if you upgrade later) then it makes sense to use 64bit OS for memory addressing issues.  I don't know about wubi, but I have winxp and ubuntu 64 on the same drive using managed with a bootloader - works v well. About the phenom 8400, consider a system with a difference processor like a phenom 8450.  The TLB bug is not specific to windows and the patch (which causes the performance hit) is applied at the bios level.  I built my computer in January when there were no 3core processors.  I had to choose between phenom 9600 (which had the same TLB issues) and c2q6600.  don't know if it's within your budget, but if you go the next step up in the system, you might also get a better video card out of it.  Where I am, the local stores are selling geforce 7K series as the low end.

---

### Post by Arkold Thos on 2008-06-15
That is a very bad card, try to get something of 8x series or 9x, some gateway computers got that by default :O and a Phenom or a Core 2 Quad

---

### Post by slymi2005 on 2008-06-15
rt2002, regarding the tlb bug what exactly is it that it does and what will I have to do to patch it? Arkold, yeah that is what I've read but I don't intend to play any games, I just want compiz to work well. Do you think it would?

---

### Post by John.Michael.Kane on 2008-06-15
> **slymi2005 said:**
> rt2002, regarding the tlb bug what exactly is it that it does and what will I have to do to patch it? Arkold, yeah that is what I've read but I don't intend to play any games, I just want compiz to work well. Do you think it would?

The 6150 should run compiz just fine, as my previous system had a 6150, and it ran compiz without issue. however, YMMV.

Also the 6150 will not hold up to heavy gaming, as it was not built for that.

Regarding the TLB bug, while I have read about it. I am not personally familiar with it. What I can say is that if the bug in question causes an undue amount system problems you might be best off avoiding it, and using a CPU without that particular problem.

---

### Post by stchman on 2008-06-16
> **slymi2005 said:**
> Alright so I'm thinking about getting an hp computer with an amd phenom triple core 8400, 4gbs memory, and nvidia gefore 6150se. I have a couple of questions. First, it comes preinstalled with 64 bit vista so I was wondering if I would be able to use wubi to install ubuntu or if I should just install it in a new partition, if so would this be the 32 or 64 bit version? Second, the phenom 8400 has some bug that affects performance by 15%, what's the case with ubuntu will this be a problem? Will the three cores make everything noticeably faster? Third, will I be able to run compiz with the nvidia geforce 6150se it has 128mb of dedicated memory and it says up to 1343mb as allocated by windows vista, does this apply to ubuntu as well. Not familiar with how video cards work. I think those are all my questions for now.

I recommend getting an 8600GT over the 8400.  The processor should work fine.

What are you paying for this HP?  I have an 8800GT and it works perfectly with Ubuntu.

---

### Post by John.Michael.Kane on 2008-06-16
> **stchman said:**
> I recommend getting an 8600GT over the 8400.  The processor should work fine.

What are you paying for this HP?  I have an 8800GT and it works perfectly with Ubuntu.

The OP is talking about an AMD Phenom X3 8400, not an 8400 geforce.

---

### Post by phlembob on 2008-06-16
Hi,  I also use the dual boot on my AMD 4800.  The NVidia video card --- I look for the second digit.  6600, 7600, 8600 work with Nvidia drivers of Ubuntu.  For performance, I like 6 and higher in the second identifier digit.  I have heard both good and bad things about GT and GTX cards.  Can't give you info for those.:guitar:

---

### Post by Jovec on 2008-06-17
> **John.Michael.Kane said:**
> The 6150 should run compiz just fine, as my previous system had a 6150, and it ran compiz without issue. however, YMMV.

Also the 6150 will not hold up to heavy gaming, as it was not built for that.

Regarding the TLB bug, while I have read about it. I am not personally familiar with it. What I can say is that if the bug in question causes an undue amount system problems you might be best off avoiding it, and using a CPU without that particular problem.

The TLB (Translation Lookaside Buffer) deals with the L2 and L3 caches.  In simple terms, each core has its own L2 cache and they share the L3 cache.  In very rare cases, a core will be working with some data in its L2 cache that could get placed into the L3 cache without the setting that lets other cores know it is in use.  That other core will then get the data and will not know that the first core may be modifying it, leading the a case where two cores think they have the same data but in reality they don't.  In practice, this happens extremely rarely only under a few specific programs and most users will probably never see this at all.  

There exists a bios fix (OS independent) for this that limits the use of the L2 cache and instead forces more use of the slower L3 cache. Phenoms that are affected by this use the B2 stepping and have model numbers that end in 00, 8x00 or 9x00.  The B3 stepping Phenoms do not have this bug, and their model numbers end in 50 as in 8x50 and 9x50. For safety, I believe all Bioses enable this fix when they detect a B2 stepping Phenom.  It can be disabled, but many of the larger PC manufacturers disable most of the advanced Bios options so this might not be possible if you bought a pre-built computer.

> Will the three cores make everything noticeably faster?

For most users and uses, no.  For most of the common PC tasks we do it matters very little how many cores or how fast our modern CPUs are as they are input limited and CPUs these days are "fast enough."  For most other uses a faster dual-core CPU is better than a slower tri- or quad-core.  There are select applications and uses which scale very well with more cores (even if they might be slower).

This is not to say that more than 2 cores are a waste.  Buy the highest number of cores with the fastest clock speeds you can afford, but if it comes down to more speed or more cores, more speed is better today for the typical user.

---

### Post by slymi2005 on 2008-06-20
Alright well I ended up just not getting the phenom and I went with an intel core 2 quad q6600 which also came with an invidia geforce 8500 gt, 4gb memory, 720 gb hd, and vista 64 bit. I had a question though, I popped in a live cd of ubuntu (32 bit) and I was unable to turn on the compiz effects. Does this have to do with the nvidia drivers not being installed or what? I plan to download ubuntu 64 bit and install it on another partition but I was just wondering if I would be able to get the effects to work and if there is a quick fix for the live cd that I could do just to check out how it would work. Any help would be great.

---

### Post by John.Michael.Kane on 2008-06-20
> **slymi2005 said:**
> Alright well I ended up just not getting the phenom and I went with an intel core 2 quad q6600 which also came with an invidia geforce 8500 gt, 4gb memory, 720 gb hd, and vista 64 bit. I had a question though, I popped in a live cd of ubuntu (32 bit) and I was unable to turn on the compiz effects. Does this have to do with the nvidia drivers not being installed or what? I plan to download ubuntu 64 bit and install it on another partition but I was just wondering if I would be able to get the effects to work and if there is a quick fix for the live cd that I could do just to check out how it would work. Any help would be great.

Yes, you have to installed the nvidia driver from the repo, as for testing the nvidia driver under a live environment I am not sure this can be.

You are best bet is doing a direct install, if all other hardware is working without issue.

---

### Post by slymi2005 on 2008-06-21
Alright so I installed ubuntu 64 bit and after logging in it said something about the video card drivers and I had to use it in 800x600 mode and vesa or something and I just looked for my card in a list (nvidia 8500 gt 512mb) and I just kept going and when I logged in it told me I had to download a driver in order to enable compiz and so I did and it told me to restart and so i did but after choosing ubuntu in the boot menu I got a black screen and was unable to do anything. I think I recall having this problem before when I installed xubuntu and I had to start in recovery mode and change something with the display. If anyone has any idea what I am talking about or has any suggestions I would appreciate them. I was so happy I got it installed and then this, such a bummer.

---

### Post by sitarammani on 2008-07-01
> **slymi2005 said:**
> Alright so I installed ubuntu 64 bit and after logging in it said something about the video card drivers and I had to use it in 800x600 mode and vesa or something and I just looked for my card in a list (nvidia 8500 gt 512mb) and I just kept going and when I logged in it told me I had to download a driver in order to enable compiz and so I did and it told me to restart and so i did but after choosing ubuntu in the boot menu I got a black screen and was unable to do anything. I think I recall having this problem before when I installed xubuntu and I had to start in recovery mode and change something with the display. If anyone has any idea what I am talking about or has any suggestions I would appreciate them. I was so happy I got it installed and then this, such a bummer.
On 64Bit
Try Knoppix 5.1.x. It does a good job detecting the hardware.
So also Wolvix Hunter.
Both these are good running on CD.

Open Suse 11 installed without any fuss on my Harddisk (AMD Phenom 8450 ATI Radeon 250g SATA HDD.)

Hope this information helps you.

sitaram mani

---

### Post by sitarammani on 2008-07-01
> **slymi2005 said:**
> Alright so I installed ubuntu 64 bit .....................nd then this, such a bummer.



...

---

### Post by sitarammani on 2008-07-01
> **slymi2005 said:**
> Alright so I installed ubuntu 64 bit .....................nd then this, such a bummer.



I tried direct install of ubuntu64, running on CD, WUBI....looked for help....still waiting for help.

Probably the next version of ubuntu should install fine on my machine.

---

### Post by slymi2005 on 2008-07-02
It's depressing though to try another distro when ubuntu is touted as having the best support community. If this is the best then it really scares me to try another distro because I'll have a worse time trying to find help when I run into trouble.

---

### Post by goforlinux on 2008-07-02
UBuntu seems to work fine on my 64 bit AMD dual boot with XP and WIN 2000 server

---

### Post by Ghone on 2008-07-05
> **slymi2005 said:**
> Alright so I installed ubuntu 64 bit and after logging in it said something about the video card drivers and I had to use it in 800x600 mode and vesa or something and I just looked for my card in a list (nvidia 8500 gt 512mb) and I just kept going and when I logged in it told me I had to download a driver in order to enable compiz and so I did and it told me to restart and so i did but after choosing ubuntu in the boot menu I got a black screen and was unable to do anything. I think I recall having this problem before when I installed xubuntu and I had to start in recovery mode and change something with the display. If anyone has any idea what I am talking about or has any suggestions I would appreciate them. I was so happy I got it installed and then this, such a bummer.

I really don't know much about this sort of thing but I know what worked for me getting my nVidia 8500GT to work on Ubuntu 8.04 AMD64 (with a Phenom 9500 which should have the TLB bug.)  The drivers in the repository don't work quite right giving me no GLX and the newest driver from the nVidia web site threw me into low resolution.

EnvyNG worked perfectly.  Older versions of envy were a bit problematic and maybe EnvyNG is too, but for me it worked automatically and with no hassle it all.  Try it and see if it fixes everything for you.  It's a good enough solution that it's now in the repositories so you can apt-get install envyng.

---

### Post by AFarris01 on 2008-08-05
i believe what you were thinking of for fixing the display issue was reconfiguring the Xorg config file... try restarting in recovery mode, and when you hit the terminal, i think you run this:

sudo dpkg reconfigure xorg

then press alt+enter? to continue booting into a GUI
i dont remember exactly, because its been a while but go ahead and give it a try anyway... and if it doesnt work, then ill do some hardcore searching and come back with better info :)   hopefully this will do it for you though...
Andrew

---

