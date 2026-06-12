---
title: "I installed DCOP98 and DotNet stuff and broke WINE"
date: 2008-06-05
forum: Wine
---

### Post by ProbablyX on 2008-06-05
Hello,

I have the latest version of wine and I've been using STEAM with it which have been working fine. However I got this script called "winetricks.sh" and I used it for installing .NET 2, DCOP 98, GDI+, Visual Studio 2008 in order to try Windows Live Messenger.

The problem is that I think this did more harm than good as it seems I cant use neither WL or Steam now...

I'm using Kubuntu amd64.

As I've only been using Steam (and the mozilla-ie-emulation stuff) I think removing all what wine is and installing it again might be the best idea... However if I need to remove WINE, I want to back up Steam (and it's games) before doing this, so Valve won't come hunting me for downloading Half-Life two times the same day :)

Is there any neat way to save Steam etc and remove all the damage this script made (like adding gdi, and libraries, and changing my wine units to '/media' and stuff which wasn't there before)? Or make a COMPLETE whipe out of wine so I can get things like they were before again?

Thanks!

---

### Post by cogadh on 2008-06-05
Valve won't care if you download it again, AFAIK, there is no limit to the number of times you can download it. I've downloaded all of my Steam applications multiple times and it has never been an issue.

However, if you want to save you existing stuff, just copy the Steam install directory someplace safe, then delete the .wine directory, recreate the .wine directory (run winecfg), reinstall Steam, copy the old Steam install directory back from its safe place, then delete the clientregistry.blob file. When you restart Steam, it will briefly update itself, then everything will still be there. There is no need to uninstall/reinstall Wine and that wouldn't really correct the issue anyway, since uninstalling Wine does not remove the .wine directory, which is where all the stuff you installed resides.

---

