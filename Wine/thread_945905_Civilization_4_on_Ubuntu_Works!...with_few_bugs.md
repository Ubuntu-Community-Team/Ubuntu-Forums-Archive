---
title: "Civilization 4 on Ubuntu Works!...with few bugs"
date: 2008-10-12
forum: Wine
---

### Post by xevous on 2008-10-12
Hey

I was able to get civ 4 working on my laptop with wine and windoors. Beyond the sword expansion is working as well. I also had to copy over a few dlls and change a few options. But it works - even without patching the game to do a no cd check! 

For the record: I have an intel graphics chipset on a celreon 1.7ghz with 1.5gigs of ram. Not the greatest rig...but it works pretty good. The only bugs that I have found is the city production bar on the main map screen does not work and water animations do not work.

I will try my best to do a howto in this thread if there is a huge interest. But here is it in a nutshell:

I am running Ubuntu 8.04.01 with the latest winedoors, and wine version 1.1.5.

I installed wine and then winedoors. I used the wine website to install wine as i wanted the latest unstable (at the time?) release to see if it would work better with civ 4. 

I Ran winecfg, and added an override for msxml3 (native, builtin). Under the graphics tab, I turned off &#8220;Emulate a virtual desktop&#8221;, set vertex shaders to none, and turn on pixel shaders. As I read this in Tombuntu.com's blog on how to get it to work.

In winedoors I installed AutoHotKey 1, Fonts, Direct X 9, Wine Gecko, GDI Plus XP Library 1, MSXML 3 & Windows Installer 2. Although not all of that is required to make civ 4 work. (Possibly none...)

I then installed Civ 4.

The DLL's (Copied over to the directory where the civ 4 executable folder is) are: msxml3r.dll, msxml3.dll & d3dx9_26.dll.

Anyone else any luck with this? As all of the howto's seemed outdated. Or am I just beating a dead horse on this issue?

---

### Post by MufflonMannenDX on 2008-10-19
Hi xevous!
I'm currently having some trouble myself playing Civ 4 in Hardy. And since I'm such a sucker for Civ and play it a lot with my friends over the so called 'internets' I'd be very interested in a brief howto. So please, help me rid the shackles of oppression laid upon me by the great mega-corp Microsoft by enlightening me in the fine art of Civvin' in Linux.

Thanks a bunch (and then some) !
//Mufflon

---

### Post by jacksaff on 2008-10-20
The notes on wine appdb are pretty good. Civ4 has been running nearly flawlessly for me for a year now.
Only hassle is getting mods to load up properly.

---

### Post by boballen55 on 2008-10-31
I would be interested in a more in depth how to.  I've tried a number of different games in wine (usually they have a silver rating on the wine site so they probably don't work for most people) with very little success.  I don't know how to tweak things readily, but if I had a fairly detailed how to for some game (Civ being one I'd like to play and it has a gold rating on the wine site so most people probably can make it work) I might be able to understand how to make other games work.  In particular I've never done anything with swapping dlls.

For Civ specifically the setup.exe detects that I don't have directx and then tries to installs it, fails and forces me to quit.  You say that you used winedoors to get directx so I guess I'll try that and see if I can figure out the rest.

Any more details would be appreciated by me.  Thanks!

---

### Post by Bios Element on 2008-10-31
[http://appdb.winehq.org/appview.php?iAppId=2514](http://appdb.winehq.org/appview.php?iAppId=2514) <Tons of information on how to get Civ 4 running (at least imo) flawlessly. Never actually played it on a Win Machine so perhaps I didn't notice the bugs bug i love the game.

---

### Post by Hutongs79 on 2008-10-31
bump!!hahacheap wow power leveling (World of warcraft Power Leveling):**buy [WoW Power Leveling](http://www.igsstar.com),  cheap [world of warcraft power leveling](http://www.igsstar.com/wow-powerleveling-us/) , 1-80 level [wow Power Leveling](http://www.wowgoldweb.com),[maple story mesos](http://www.buymsmesos.com),       [wedding invitations](http://www.vponsale.com/invitations/)**

---

### Post by sea_monkey987 on 2008-11-01
i have it working also with (EDIT: WITHOUT) the noCD patch.  does that mean wine now supports safedisc 4?  i can't seem to find a clear answer to this as all the websites say you need the cracked version of civilization.exe

---

### Post by Bios Element on 2008-11-02
> **sea_monkey987 said:**
> i have it working also with the noCD patch.  does that mean wine now supports safedisc 4?  i can't seem to find a clear answer to this as all the websites say you need the cracked version of civilization.exe

Do you know what a NOCD Patch is? Didn't think so. A Safedisk is what checks for the CD...So using a NOCD patch rips Safedisk out.

---

### Post by sea_monkey987 on 2008-11-02
lol.  I meant to say WITHOUT the nocd patch.  so, my original question still stands.

---

### Post by xevous on 2008-11-03
> **sea_monkey987 said:**
> lol.  I meant to say WITHOUT the nocd patch.  so, my original question still stands.

Civ 4 and civ 4 warlords work on my ubuntu install without a no-cd patch. 

I am going to try a fresh install of wine on ubuntu soon. I will build a walk through at that time unless someone else has an updated link to a good one.

---

### Post by sea_monkey987 on 2008-11-03
a how to is unnecessary, imo.  just follow the HOWTO on appdb page on wine's website with the latest wine (i have version 1.1.7).  [http://appdb.winehq.org/appview.php?iAppId=2514](http://appdb.winehq.org/appview.php?iAppId=2514)  all you need to do is skip the part about the no-cd patch.  it works, even though the wine copy protection page says only safedisc 2 is implemented [http://wiki.winehq.org/CopyProtection](http://wiki.winehq.org/CopyProtection)

---

### Post by boballen55 on 2008-11-08
So I got Civ installed with wine after finding the dll to make it stop crashing trying to install directx.  When I click on the exe to start the game it starts loading then tells me to put in the correct cd.  I assume this is why people have had to use a nocd crack in the past but I see that it has been made to work without one.  Is anything special needed to make it work without a nocd crack or am I missing a critical dll?  I've seen many posts saying that you need up to 20 dll's and others say you only need the one to skip the directx thing and others with everything in between.  

So is there anything more anyone reading this had to do to make it work without a nocd crack after installation?  Thanks!

---

### Post by offthegrid2 on 2008-12-31
I was given the Civ4 complete DVD for xmas and have everything running using winetricks. I used winetricks to install Direct X first then the game. The only thing I had to do was copy the d3dx9_26.dll, msxml3.dll & msxml3r.dll to the game folder. Voice works and no "no cd patch" was needed.

However the only problem is the sound. Sound works but is skips and sound like s$#%. Anyone have this problem and fixed it? Thanks. I tried OSS and no sound so only ALSA works.

---

