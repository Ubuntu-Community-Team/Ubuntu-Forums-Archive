---
title: "[Ubuntu 11.04] Wine does not recognize mounted .iso's as cd-roms"
date: 2011-09-03
forum: Wine
---

### Post by CFet on 2011-09-03
Greetings!

So here is my issue. I can successfully complete installations with .iso of both neverwinter nights and diablo II in wine. I am using AcetoneISO to mount the .iso's to virtual drives. Correct me if I'm wrong but I believe acetone is just a front end for mount -o loop, which, I have also tried. 

Once installed, I can execute the launch file in wine with the game appropriate flash screens. With both games follows a prompt "Please insert disc into cd-rom". 

But... I still have the "play disc" iso mounted! Suddenly, wine cannot detect I have the data in a cd-rom location? Configured in winecfg as a CD-ROM type, with the path leading to the virtual drive. 

I am using Ubuntu 11.04 with GNOME3. All physical discs seem to auto-mount by ubuntu to /media/NAMEOFDISK.

Is there someone out there who can help me diagnose this problem? I would much like to enjoy these games in wine rather than resort to my vista/virtual box solution for playing these old classics of mine :(

Best regards,
Chris

---

### Post by CFet on 2011-09-05
Anyone able to assist with this? I'm stumped :S

---

### Post by disabledaccount on 2011-09-05
First try nocd patch for those games - this is often the only solution.

---

### Post by CFet on 2011-09-05
> **tomazzi said:**
> First try nocd patch for those games - this is often the only solution.

Thanks for the suggestion but I tried that tomazzi. I can't believe that the only solution to a rudimentary "can't find cd problem" is a nocd patch. Wine should be perfectly capable of detected a mounted .iso as an inserted cd-rom. I just don't have the expertise to properly diagnose the issue :(

---

### Post by 4Orbs on 2011-09-05
I don't know if this will help. I play Diablo2 + the LOD expansion, and it will only work in wine after installing the LOD_112a.exe patch from Blizzard. Maybe there is a 112 patch for Diablo2 alone (no expansion pack).

Also, in order to get sound working during gameplay, it was necessary to install a modified version of wine 1.2 which adds the option to use pulseaudio sound output. To get this wine mod add the c-korn ppa to your sources list. In the terminal paste:
```
sudo add-apt-repository ppa:c-korn/ppa
```
Then open synaptic and refresh the sources, then install or upgrade to wine ver 1.2

---

### Post by disabledaccount on 2011-09-06
> **4Orbs said:**
> I don't know if this will help. I play Diablo2 + the LOD expansion, and it will only work in wine after installing the LOD_112a.exe patch from Blizzard. Maybe there is a 112 patch for Diablo2 alone (no expansion pack).


Also, in order to get sound working during gameplay, it was necessary to install a modified version of wine 1.2 which adds the option to use pulseaudio sound output.

Yes, patch 1.12+ removes checking for PLAY disc in diablo, but to have it working all movies from play disc must be moved to HDD (this is official nocd patch).
Maybe I should explain it earlier: it's not that wine can't see mounted iso - this is problem with copy-protected CDs - thats why nocd patch is needed.

I would say that the best wine as of today is 1.3.23/24, but Diablo2 LOD, MedianXL, etc works just perfectly even with the latest 1.3.27

---

