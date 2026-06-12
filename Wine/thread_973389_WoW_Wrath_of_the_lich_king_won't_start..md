---
title: "WoW Wrath of the lich king won't start."
date: 2008-11-06
forum: Wine
---

### Post by Rammatamago on 2008-11-06
Hi, I've been trying to get World of Warcraft Wrath of the lich king working for the past few days and I keep running into problems. When I opened wow to start each patch the screen was black other than the buttons and login/password area. Then from patch 3.0.1 to 3.0.2 the screen turned completely black. The final 3.0.2 patch completely broke it to where it doesn't open at all.

Regular WoW works just fine, I even tried copying my config.wtf folder, but that did nothing.

I'm running Ubuntu 8.0.4 Hardy with a AMD Athlon 64 X2 processor, and an ATI 3850HD graphics card.

Here's what the terminal prints when I run wow.
```
BLAH@BLAHBLAH:~$ wine .wine/drive_c/Program\ Files/Wrath\ of\ the\ Lich\ King\ Beta/Wow.exe 
fixme:ntoskrnl:KeInitializeSpinLock 0x4577a4
err:module:attach_process_dlls "opengl32.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\BLAH\\.wine\\drive_c\\Program Files\\Wrath of the Lich King Beta\\Wow.exe" failed, status c0000005
```

Any help would be greatly appreciated!

---

### Post by Rammatamago on 2008-11-08
I managed to get the game patched fully but now I can't enter the world at all. When trying to enter the world the loading bar will get to full, and then the game crashes giving me a fatal error.

The gist of the error is...
!("CGMinimapFrame::Initialize(): can't get render target for minimap")

I searched google, these forums, and any place I could think of with no luck. I did find a post saying that disabling the minimap completely solves the problem, but the .exe I found to disable it was not updated to the latest patch. Also addons to disable the minimap don't work because the game loads the map before the addons it seems.

Any help or a point in the right direction would be great, thanks!

---

### Post by ajackson on 2008-11-08
What version of wine are you using?

---

### Post by Rammatamago on 2008-11-08
Wine 1.1.7.

---

### Post by Manice on 2008-11-12
I still have to launch wow with the -opengl command. Might work for you too.  

```
wine .wine/drive_c/Program\ Files/Wrath\ of\ the\ Lich\ King\ Beta/Wow.exe -opengl
```

---

