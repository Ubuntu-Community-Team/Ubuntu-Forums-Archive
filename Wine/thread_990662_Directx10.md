---
title: "Directx10"
date: 2008-11-22
forum: Wine
---

### Post by kevil99 on 2008-11-22
Ive successfully installed steam using wine.

Id like to install directx10.

any help would be appreciated.

Ive had a lot of success with games lately due to wine.

I wanna play COD4:)

---

### Post by ITAndrew on 2008-11-22
Not gonna happen! Only way to have directx 10 is to run vista, there is no installer for DX10. This is not incorporated into the drivers either. 

See [http://arstechnica.com/journals/microsoft.ars/2007/2/14/7060](http://arstechnica.com/journals/microsoft.ars/2007/2/14/7060) for further reading.

---

### Post by kevil99 on 2008-11-22
kinda figured:)

im just so impressed with 8.10
as soon as i installed the drivers popped up for my 9800gtx
and after setting up wine
i installed steam with the msi as apposed to the old exe.

so i assume crysis is going to be a no go to huh?

wait cod4 is directx9

can i shoot for that?

---

### Post by ITAndrew on 2008-11-23
DX9 is partially supported and most games will work fine, although if there is an option for OpenGL you will get better performance since GL is native for linux. 

Crysis will work with DX9 as well so you still may be able to get it to work adequately but not perfectly.

---

### Post by cogadh on 2008-11-23
Check Wine's [Application Database](http://appdb.winehq.org/) for the status on what works and what doesn't, plus what you may need to do to get some things working as best as possible.

Wine does have [nearly complete](http://www.winehq.org/site/status_directx) support for DirectX 9 (saying it is "partially supported" seems unfair) and the first stages of DirectX 10 support have been added to the current unstable version of Wine. Don't expect DX10 to work fully in Wine anytime soon. It took 15 years of development for Wine to reach the status it is at today. That doesn't mean it will be another 15 years before we see DX10 working, but it will take a while.

---

### Post by ITAndrew on 2008-11-23
It will never be 100% supported. It is impossible without the original code from msft. They will be able to make it mostly compatible through the process of reverse engineering and new code implementation/work arounds but without the cooperation from msft it will be impossible to fully reproduce DX regardless of version.

---

### Post by Twitch6000 on 2008-11-23
Well I do know with wine-doors you can install direct x 9 and it is pretty much fully supported.(however there are some bugs still,but hey its wine)

For DX10 though I think three wine versions back they just started getting to work on that. So maybe around 2.0 DX10 will be fully supported?(just a guess)

---

### Post by ITAndrew on 2008-11-23
Tis true, since Microsoft released a package with the DX9c End-User Runtime you are able to install this package, using wine-doors or wine (if you download the package). They will also probably release a package for DX10 when hell freezes over or until Win 7 is released, which ever comes first.

---

### Post by cogadh on 2008-11-23
> **Twitch6000 said:**
> Well I do know with wine-doors you can install direct x 9 and it is pretty much fully supported.(however there are some bugs still,but hey its wine)

For DX10 though I think three wine versions back they just started getting to work on that. So maybe around 2.0 DX10 will be fully supported?(just a guess)

Doubtful. DX10 is really not a priority for the Wine devs. Very few games actually require it so finishing the DX9 support is still much higher on the "to do" list.

As for whether or not DX (regardless of version) will ever be supported 100%, I would say that is definitely possible, even without the support of MS. They have the major parts of DX9 90-95% completed already, without any original code from MS, there is absolutely no reason to think they can't continue that trend for the rest of DX. Like I said, it will definitely take a while to get there, considering they have to do all of it using little more than MS's piss-poor API documentation and Wine's debugging output, but it can be done.
> **ITAndrew said:**
> Tis true, since Microsoft released a package with the DX9c End-User Runtime you are able to install this package, using wine-doors or wine (if you download the package). They will also probably release a package for DX10 when hell freezes over or until Win 7 is released, which ever comes first.
Win 7 is shipping with DX11. We will never see a stand-alone installer for DX10, unless MS goes back on their word and releases one for XP.

---

### Post by kevil99 on 2008-11-23
never used wine doors.

still fairly new at linux.

anyone got a walkthru for wine doors followed with the dx9

ubuntu8.10


EVGA 780i sli
EVGA 9800gtx
Core2duo e6300 ocd from 1.86 to 3.15
Patriot ddr2 pc 8500 1066 @4g
Ultrax2 550watt
2Western digital sata300 160g

---

### Post by kevil99 on 2008-11-23
any help would be appreciated

---

### Post by ITAndrew on 2008-11-23
Download the DEB file from [http://www.wine-doors.org/wordpress/?page_id=3](http://www.wine-doors.org/wordpress/?page_id=3)

Run Wine-doors from application menu select DX9 to install.

Rather easy and straight forward.

---

