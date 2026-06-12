---
title: "Black Ops 2 won't start on a PlayOnLinux Steam Installation"
date: 2012-11-13
forum: Wine
---

### Post by PyGuy on 2012-11-13
Hey everyone. I just got Black Ops 2 on Steam (as with a lot of people), but when I try to launch it, it closes itself without opening any windows :/

Here's what the terminal spat out at me when I executed the command "wine t6sp.exe" (Black Ops 2 Single Player)
```
fixme:service:scmdatabase_autostart_services Auto-start service L"dxregsvc" failed to start: 2
err:module:import_dll Library d3d11.dll (which is needed by L"Z:\\home\\andrew\\.PlayOnLinux\\wineprefix\\Steam\\drive_c\\Program Files\\Steam\\steamapps\\common\\Call of Duty Black Ops II\\t6sp.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\andrew\\.PlayOnLinux\\wineprefix\\Steam\\drive_c\\Program Files\\Steam\\steamapps\\common\\Call of Duty Black Ops II\\t6sp.exe" failed, status c0000135
```

OS: Ubuntu 12.04 64-bit
Processor: Intel Core i5-2400 @ 3.10Ghz (4 CPUs) ~3.1Ghz
Graphics: Nvidia GeForce GTX 560 (4GB VRAM)
Memory: 8GB DDR3 1333MHz RAM
Wine Version: 1.5.4
Winecfg Windows Version: Windows 7

Any help would be appreciated on finding a solution based on what the terminal is saying.

---

### Post by chaosportal on 2012-11-14
I'm getting the same result. My google searching just leads me here to your post ! HAHA

It's a new game, I expect someone will have a solution soon.

---

### Post by iemesis on 2012-11-14
Well it's asking for d3d11.dll witch is needed for directx 11 to work  witch has not been made to work with wine, yet, enough to play dx11  games at least. And Black Ops 2 cannot be launched with dx9 that's why  it cannot be played on xp. Since it would have probably taken no effort  to make the game run on both dx11 and dx9 and since graphics aren't that  much better than older versions of the engine they should not bothered  to make it dx11 in the first place. No you cannot play it on wine.

---

### Post by TheRealRilo on 2013-03-29
Use WineTriks to install DX11

---

### Post by TheRealRilo on 2013-04-12
Is there anyone who got BO2 working (Steam version) in Ubuntu 12.04 LTS?

---

