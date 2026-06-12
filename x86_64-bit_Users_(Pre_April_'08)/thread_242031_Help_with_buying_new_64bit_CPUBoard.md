---
title: "Help with buying new 64bit CPU/Board"
date: 2006-08-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by lithium on 2006-08-23
Hi there, I'm planning to upgrade my aging Athlon XP 2200 to something more up to date ;) 

The main problem now is that I'm not really into hardware ATM so it would be nice If you could post your hardware (If you have have a recent CPU/RAM/Mainboard) and also write how well it works with Linux or where the Problems are.

A few notes:
- Doesn't have to be the *very* recent things on the market but don't want to loose to much money, so I'm looking for technology that is established for some month and has now a payable price wile still "high end".
- Compatibility with Linux (nice would be unpatched Dapper or current Edgy) is most important. I don't need to run any version of Windows on this.
- I would like a 64bit CPU... I know this is still problematic and even if I have to use the 32bit mode, I think this ist more future-proof. Right?
- AMD or Intel? What do you buy these days? I was always more the AMD buyer but I heard from a few that Intel gives you more for your money these days?
- Another thing is the board/chipset: I want something where I can be sure it won't make to much trouble with linux, so the chipset should be well supported. No integrated graphics or LAN/WLAN.

Sorry if this posting doesn't really fit to this forum but well, it's me trying to get a foot into the 64 bit computing world, so I hope it will be ok and a few of you (the more the better) will comment. Thanks in Advance!

---

### Post by hitekhal on 2006-08-23
just bought this last week:

after 2 ecs mobos crapped out within 2yrs of use i went with:

Gigabyte GA-M55SLI-S4 NVIDIA® nForce™ 4 SLI
Socket AM2 ATX Motherboard ($95 us at Frys)

AMD Athlon™ 64 X2 Dual-Core Processor 4200+ ($183 at Frys)

OCZ DDR2 2GB (2x1GB) PC2-6400 800MHz Dual Channel Kit - OCZ2P8002GK ($200 at Frys with $50 rebate)

note about DDR2 memory, unless you install at least 2 sticks (pair) of identical memory (same manufacturer advised) then the DDR2 function will not be enabled. will still work as DDR.

it is a PCIE mobo so you will need PCIE vid card i chose:

3d Fuzion 7300GS 256Mb PCI-Express Graphics card ($100 at Frys)

you can save about $80 if you do some shopping searches and buy above online, but i needed something asap and Frys is just down the road from me. of course you can go with some less expensive components as well you have choices with the cpu, memory, vid card.
 
linux installed smooth and runs great!

i am running Ubuntu Dapper and/or Fedora core 5 with no problems, I have a WD 200 gb sata hdd  plus two ide hdd , 2 dvd rw's (old memorex, newer pioneer), old hauppauge wintv card, epson allinone printer scanner (ok, the scanner i haven't got to work under Ubuntu yet but i just haven't had time to sort it out) got network printing over the home wifi working.

so far i am very happy, now if i could just get wine going, say goodby windows XP!

btw i have tried XP64 and imho Ubuntu is better.

enjoy!

---

### Post by lithium on 2006-08-23
Thanks for your reply hitekhal. Can you say something about the performance specific to the dual core feature? I've seen a few benachmark tests where those cpus performed really bad on unopimized software. Is it really worth it?

---

### Post by hitekhal on 2006-08-23
not sure what you mean by 'unoptimized' software but read this review:

[http://www.legitreviews.com/article/373/1/](http://www.legitreviews.com/article/373/1/)

---

### Post by hitekhal on 2006-08-23
not sure what you mean by 'unoptimized' software but read this review:

[http://www.legitreviews.com/article/373/1/](http://www.legitreviews.com/article/373/1/)

---

### Post by TripleE on 2006-08-23
My hardware is working great.  I documented my experience if you want to see what I did:
[http://geocities.com/eric1548/](http://geocities.com/eric1548/)
**Hardware:**

  Asus A8S-X motherboard
 AMD Athlon 64 3000+ Processor (Venice) Socket 939
 Corsair TWINX1024-3200C2PT 1GB DDR400 (2x 512mb match pair) 2.5-3-3-6
 BFG GeForce 7300 GS PCI Express 256MB - Now a XFX 7900 GT
 1x 300gb IDE hard drive
 1x 250gb IDE hard drive
 2x 80gb SATA hard drives (Raid0)

---

### Post by Cynical on 2006-08-24
Lately intel has been outperforming amd.

My setup:

Gigabyte GA-965P-DS3 motherboard
Intel Core 2 Duo E6300 processor
1GB Corsair DDR2-675 XMS2-5400 Xtreme Performance memory
128MB MSI Geforce 6600GT 
320GB Seagate SATAII drive 

Dapper has been snappier than my old setup with an opteron 165. A word of advice though, buy a motherboard with an nvidia (ati has some coming out soon) chipset. Intel decided to remove support for ide and force motherboard manufacturers to add the jmicron controller to make up for it. Theres a bug in the linux kernel atm that prevents you from reading cds (meaning you wont even be able to install). This will be fixed by the time Ubuntu 6.10 arrives, so it really depends on when you want to upgrade.

I decided to make a list of the parts I would buy that would be affordable, mid-high end, and most of all linux compatible (will work with ubuntu out of the box)

[http://secure.newegg.com/NewVersion/wishlist/PublicWishDetail.asp?WishListNumber=3855466](http://secure.newegg.com/NewVersion/wishlist/PublicWishDetail.asp?WishListNumber=3855466)

---

### Post by kuja on 2006-08-24
I've seen the benchmarks on the new Intel Core2 processors and it looks like they've one-uped AMD for now.

However, my system still runs smooth as silk, and does its job well.

My hardware:
Asus A8N-SLI Premium, heatpipe cooler is a very nice plus.
Athlon 64 FX-60 (running at 2.8GHz)
OCZ Platinum DDR400 dual channel (2x 512mb) (running at 2-2-2-5-1t @ DDR433, if I remember right)
eVGA 7600GT KO 256MB PCI-E
2 x 250GB SATA HDD (software RAID 0)

---

### Post by thoffland on 2006-08-24
Here's another one for you to look at: 

Gigabyte K8N Ultra 9 nForce 4
Bios F8
AMD64 4400+ X2 (socket 939)
2gigs Corsair Ram (2/1)
XFX 7800GT
2x WD Raptor 36g
1 Maxtor 120g slave/storage

The only problem I had was that I wouldn't let me install ubuntu to a RAID 0 config, but windows wouldn't either. There might be soemthing about my Mobo, or it's just me... probably me. 

Ubuntu runs very well on it and it's really... really.... really fast. It does a complete re-boot faster than my Win2K machine powers up.

Good luck!

---

### Post by kuja on 2006-08-24
> **thoffland said:**
> The only problem I had was that I wouldn't let me install ubuntu to a RAID 0 config, but windows wouldn't either. There might be soemthing about my Mobo, or it's just me... probably me. 

Ubuntu runs very well on it and it's really... really.... really fast. It does a complete re-boot faster than my Win2K machine powers up.

Good luck!

Try taking a look at this document: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by lithium on 2006-08-24
Thanks @ all!

---

