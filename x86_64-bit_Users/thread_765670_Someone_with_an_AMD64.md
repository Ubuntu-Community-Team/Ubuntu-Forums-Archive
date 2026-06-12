---
title: "Someone with an AMD64 ?"
date: 2008-04-24
forum: x86 64-bit Users
---

### Post by Silent Ninja on 2008-04-24
I've currently this PC:

AMD Athlon X2 4200+ (64bits)
Asus M2N-E SLI
nVidia 8600 GTS (256mb)
2GB RAM - 800mhz
Kozumi TV Card

Has anybody with some similar hardware tried the latest Ubuntu? I've tried the beta on my laptop and sadly the wifi never came up, so I've to reinstall Billy's OS :( (I know there should be drivers.. I just was lazy, I thought it could be fixed on the final release)..

Anyway, I have no wireless on my personal computer, so.. would it be ok to remove windows and do the big jump? Does Linux support nVidia SLI with Cedega / WineX ?

I know some about linux since I work on a web-hosting company so, I might fix some thinks that went wrong on the road, but what I mean is "will it «just work», or it will not?".

---

### Post by grannyw on 2008-04-24
if you what to try-just TRY!!!
keep your windows partition and make a dual-boot with ubuntu.i'm using 64 and its pretty stable.the stability depends on your actions.it is not like in windows.here your are the master.but if u know how to work it will work.

Just dont be afraid,we have a big community,and u always get help

---

### Post by kutjara on 2008-04-24
> **Silent Ninja said:**
> I've currently this PC:

AMD Athlon X2 4200+ (64bits)
Asus M2N-E SLI
nVidia 8600 GTS (256mb)
2GB RAM - 800mhz
Kozumi TV Card

Has anybody with some similar hardware tried the latest Ubuntu? I've tried the beta on my laptop and sadly the wifi never came up, so I've to reinstall Billy's OS :( (I know there should be drivers.. I just was lazy, I thought it could be fixed on the final release)..

Anyway, I have no wireless on my personal computer, so.. would it be ok to remove windows and do the big jump? Does Linux support nVidia SLI with Cedega / WineX ?

I know some about linux since I work on a web-hosting company so, I might fix some thinks that went wrong on the road, but what I mean is "will it «just work», or it will not?".

The hardware you posted should work fine with Hardy. I've got an AMD Turion in my laptop and it runs Hardy 64 bit beautifully. You'll be prompted during the post-install process to install the latest Nvidia restricted drivers, but that's an automated process that worked fine with my Nvidia GeForce Go 6150 card.

Wireless is unlikely to work out of the box, unless you're fortunate enough to be using an Intel ProWireless card (which seem to work "out of the box" more often than other brands). Depending on what card you have, you'll have to use either the built-in bcm43 drivers (for some Broadcom cards), bm43-fwcutter (for other Broadcom cards), NDISWrapper (for still other Broadcom cards and some Atheros cards), Madwifi (for Atheros cards), or Serialmonkey (for Ralink cards). 99% of cards can be made to work using one of those solutions. The other one percent are cursed by God and should be smashed into pieces and buried in salted earth till the end of time.

---

### Post by Angus77 on 2008-04-24
I've got a Japanese Dell Inspiron 531s:
[LIST]
[*]AMD Athlon x2 3800
[*]ATI Radeon x1300
[*]2G of RAM
[*]Samsung SyncMaster 206BW 20" Widescreen monitor
[/LIST]
Works fine out of the box.  The resolution wasn't what I wanted, but still looked alright.  Fixed that by adding the restricted driver for my graphics card (just the click of a button) and voila! reboot and I had 1680x1050.

The only issue I care about is that I can't get Java to work without resorting to installing 32-bit Iceweasel.

Other than that, everything went smooth.

---

### Post by GeekGirl1 on 2008-04-24
Dual-boot with MS Windows works just fine. AMD 64 4800+ dual core, NVidia GeForce 7900 GTX 512 MB. I'm sharing my Firefox and Thunderbird profiles with MS Windows so I can easily swap between Hardy and MS Windows.

With the profile kept in Win XP, just create a profile in Linux and point to the Win XP folder.

firefox -ProfileManager
thunderbird -ProfileManager

---

### Post by old_geekster on 2008-04-24
I agree with the others.  Setup a dual boot system.  Although, you could download the LiveCD version and run Hardy Heron from it.  It will setup all of your components, so you will know what it will do for you.

---

### Post by ASULutzy on 2008-04-25
Before you try setting up a dualboot, you could always try installing Ubuntu inside a virtual machine such as virtualbox-OSE, or using Wubi, which lets you install Ubuntu inside of Windows without having to repartition or do anything else tricky.

---

### Post by mdr on 2008-04-25
I have 
AMD Athlon X2 4400+ (64bits)
Asus M2N-E SLI
nVidia 6600 GTS (256mb)
2GB RAM - 800mhz

Works fine.  Cannot say about sli - not tried it.  With nvidia drivers no reason why not.  Oh btw I dual boot for some of those pesky games.  Imho cedega is not worth it.  Dual boot or use Wine / Crossover.

---

### Post by flyinraptr on 2008-04-25
> **Silent Ninja said:**
> I've currently this PC:

AMD Athlon X2 4200+ (64bits)
Asus M2N-E SLI
nVidia 8600 GTS (256mb)
2GB RAM - 800mhz
Kozumi TV Card

Has anybody with some similar hardware tried the latest Ubuntu? I've tried the beta on my laptop and sadly the wifi never came up, so I've to reinstall Billy's OS :( (I know there should be drivers.. I just was lazy, I thought it could be fixed on the final release)..

Anyway, I have no wireless on my personal computer, so.. would it be ok to remove windows and do the big jump? Does Linux support nVidia SLI with Cedega / WineX ?

I know some about linux since I work on a web-hosting company so, I might fix some thinks that went wrong on the road, but what I mean is "will it «just work», or it will not?".

I'm running an AMD X2 64 4400+ w/ dual Nvidia 7900gt's in SLI mode ..... on 64bit Hardy with no problems.  Using the beta version of the Nvidia drivers ...173.08.

---

### Post by herdivet on 2008-04-25
FWIW I have an AMD64 3200+ and I started with 8.04 beta two weeks ago, it worked on my wireless card immediately, just had to set the encryption.  The card is an old PCI Netgear WG311 I picked up gratis for some software installation work.  It appears to be 100% compatible with 8.04.

Everyone's right, download of the 8.04 software, run it live or set up a partition to dual boot, and give it a try.  I've finally taken my 'Main' computer over (although it's dual boot) to Ubuntu with 8.04 and it's working great.

---

### Post by jim_24601 on 2008-04-28
Don't know about the TV card, but you should be OK. I still haven't been able to get the binary nvidia driver to work on my 8600GT, but I'm using a beta version because fakeraid 4/5 support is broken in the release. Graphics support seems better in the release, though. Try it and see, and let people know how you get on. I don't recommend blowing away your Windows system yet, though.

---

