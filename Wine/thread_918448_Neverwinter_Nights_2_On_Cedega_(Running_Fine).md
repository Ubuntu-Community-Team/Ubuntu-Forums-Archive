---
title: "Neverwinter Nights 2 On Cedega (Running Fine)"
date: 2008-09-12
forum: Wine
---

### Post by Ms_Angel_D on 2008-09-12
I just wanted to say that I was able to install and play NWN2 using cedega and it runs great on Hardy. So if anyone else is wondering I just wanted to note that it's successful for me, and may be worth trying on your own system. 

You can see my system stats in my sig. Though every system may react differently.

Angel

---

### Post by Perfect Storm on 2008-09-13
Any glitches? Does the auto-updater work? 
That's a game I'll like to play as I've been completly crazy with NWN1

---

### Post by Ms_Angel_D on 2008-09-13
I ran the update with no problems and am using the latest version. One thing I did notice is that some of the textures seem a little off I do get black areas instead of grass in some places for some reason. 

BTW I think I should note I'm using the PC/CD version and Not the PC/DVD version.

---

### Post by KhaaL on 2008-09-13
I'm also curious on performance, it's been an issue with wine/cedega before...

---

### Post by Ms_Angel_D on 2008-09-13
It's runs quite smoothly, I would even say that it's a bit faster then when I'm running the game on vista.

---

### Post by go_beep_yourself on 2008-10-14
Does this game not run native in LInux? Is it just the first Neverwinter Night that does?

---

### Post by Ms_Angel_D on 2008-10-16
> **go_beep_yourself said:**
> Does this game not run native in LInux? Is it just the first Neverwinter Night that does?

No Neverwinter Nights was developed by Bioware and Bioware made a native linux version, However Neverwinter Nights 2 was developed by Atari and well Atari wants nothing to do with linux

---

### Post by Ms_Angel_D on 2009-09-01
A bit of an update

I'm running NWN 2 with wine on my new rig
Systemax PC
CPU: AMD Athlon 64x2 4400
RAM: 3 GB DDR2 800 (PC2-6400)
Display: Nvidia Geforce 7600 GS

I installed using the 7 Disk PC/CD version
in order to get it working I had to use [winetricks]("http://wiki.winehq.org/winetricks") I installed the following with winetricks:

[LIST]
[*]DirectX9 **(not d3dx9 but the actual DirectX9)**
[*]dotnet20
[*]vcrun2005
[*]vcrun2005sp1
[/LIST]

in order to update to the latest version I ran

```
/home/angel/.wine/drive_c/windows/regedit.exe
```

and changed the value of
```
HKey_Local_Machine>Software>Obsidian>NWN2>Neverwinter>NWUpdate
```
from 0 to 1

The only issue I had was that the game only recognized a resolution of 1024x768 so I had to edit 

```
/home/angel/Neverwinter Nights 2/nwn2.ini
```

manually and put in my 1600x900 resolution.

All this info I found at [http://appdb.winehq.org](http://appdb.winehq.org)

hope this information helps other people.

---

### Post by Perfect Storm on 2009-09-01
How about the expansions to NWN2?

---

### Post by Ms_Angel_D on 2009-09-01
> **Artificial Intelligence said:**
> How about the expansions to NWN2?

I don't have them so I can't personally attest, however according to appdb they work with the latest updates.

---

### Post by Perfect Storm on 2009-09-01
> **Ms_Angel_D said:**
> I don't have them so I can't personally attest, however according to appdb they work with the latest updates.

Ok, I have the game + expansion, but I've never used them :P (simple havn't the time to do it). But I might give it a go. It's actual the first PC games for Windows I have bought for years.

---

### Post by Ms_Angel_D on 2009-09-01
> **Artificial Intelligence said:**
> Ok, I have the game + expansion, but I've never used them :P (simple havn't the time to do it). But I might give it a go. It's actual the first PC games for Windows I have bought for years.

I would like to play the expansions, but I had distaster when I pre-ordered the NWN2 dvd version and their securom. It ruined that computers drives, they stopped reading dvds and any drives I installed to the pc after words stopped reading dvds. I ended up buying the PC/CD version from amazon so I could play it on my newer computer. But then I found out that the expansions only come in dvd and carry the same "anti-piracy" crap on them so I refuse to buy them.

Good luck though I hope they work for you!

---

### Post by Ms_Angel_D on 2009-12-28
A Bit of an update, I found using the latest wine 1.1.35, I didn't need to edit the NWN.ini file to fix the resoulution, instead I just added a setting in the wine config, to run the game in a virtual desktop using my native 1600x900 resolution and it now runs in full screen on that resolution just fine.

---

### Post by vanquishedangel on 2010-09-27
> **Ms_Angel_D said:**
> A Bit of an update, I found using the latest wine 1.1.35, I didn't need to edit the NWN.ini file to fix the resoulution, instead I just added a setting in the wine config, to run the game in a virtual desktop using my native 1600x900 resolution and it now runs in full screen on that resolution just fine.

It also works great through playonlinux as well as I have it running flawlessly and updated and with the no cd hacks to, it has a visual c error after 1.2 so i udated to the newest and then used an older no cd hack and that is now gone.

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=4118](http://appdb.winehq.org/objectManager.php?sClass=application&iId=4118)

just follow the instructions here and it will run  great and you use the same wine configuration to run the expansions as well and motb works :)

---

