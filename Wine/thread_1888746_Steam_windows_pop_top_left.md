---
title: "Steam windows pop top left"
date: 2011-11-30
forum: Wine
---

### Post by Ghouli on 2011-11-30
So yeah. I did a clean install with Ubuntu 11.10 64-bit and been experiencing funky behavior with Steam menus in current Unity. As I click on any menu, it appears on the top left corner of my screen. This also happens with update new as I start it up, and with Settings, Friends, etc windows as I open them. This is Unity related, as it doesn't happen with Xfce4 or Gnome3. It's really damn frustrating, and I haven't been able to find any fix. Could you guys help me? :confused:

Edit: and yeah, if anyone knows how to get rid of that white background on Steam icon in indicator area, I would appreciate that also. Had that same problem on 64-bit Ubuntu 11.04, but not on 32-bit version of Ubuntu 11.04. Weird.

---

### Post by ergo-proxy on 2011-11-30
Check emulate desktop option in winecfg under graphics tab.

---

### Post by Ghouli on 2011-11-30
Umm you emulate virtual desktop? I suppose it kinda works, but isn't what I'm after. The problem is with Unity, as with default Unity desktop it throws those windows on top left corner, and this behavior doesn't occur while using Gnome3 or Xfce4.

---

### Post by ergo-proxy on 2011-11-30
Make sure you installed all addons using winetricks (check winehq), I had the same problem for a while but then it was fixed by itself. You can try using the latest wine version.

---

### Post by Ghouli on 2011-11-30
I have tried this with several Wine versions (most recent one directly from their ppa and older via PlayOnLinux), with no effect on the matter.

---

### Post by Ghouli on 2011-12-07
So no-one else is having this problem? :confused: Would be nice if someone could at least point me in the right direction, I'm totally puzzled here. I'm one of those handful of people who actually like Unity, and I wouldn't want to switch it for another window manager just because of Steam issues. It's usable as it is, but this behavior is very frustrating.

---

### Post by Ghouli on 2011-12-07
Did sum testing, and switching Nvidia drivers to Nouveau didn't help, nor did different driver versions. Unity 2D didn't suffer from this problem, but something ain't right there either, see attachment..

Örr. This is driving me nuts.

---

### Post by P-I H on 2011-12-08
I have the same behaviour with an ATI card (6850) and I am using Wine 1.3.32.

I am using Wine to play Civ V and I am satisfied as long as it plays OK.

---

### Post by dakira on 2011-12-20
This is a Unity problem and every wine-window suffers from this. When I open submenus in Wine-apps (like drop-down-menus) they don't open in place, but in the top-left. I haven't found a solution, yet either.

---

### Post by DemonSharkKisame on 2011-12-21
So this is a somewhat well-known problem with Wine and Unity, then? I had it, it annoyed me to the point that I switched to using KDE as my default desktop. GNOME Shell also doesn't suffer from this issue, for some reason, only Unity.

---

### Post by uh20 on 2011-12-23
this never really annoyed me, but i get this too, i will search around for ways to fix this while keeping unity

and just a side note: i do not agree with ubuntu using pulse audio or unity, nuff said

---

