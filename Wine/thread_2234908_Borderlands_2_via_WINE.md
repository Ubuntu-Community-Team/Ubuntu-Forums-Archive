---
title: "Borderlands 2 via WINE"
date: 2014-07-17
forum: Wine
---

### Post by theo5 on 2014-07-17
Hello

I see "play games on Linux" as the last frontier. After that I can uninstall windows for good. But every time a game requires steam/.NET/java_x.x/etc. it's quite difficult to get it running.
I recently tried Borderlands 2 (via DVD not steam), and I used POL and (pure) WINE.

POL was a disaster. After a hundred things that went wrong I wasn't able to run the game from the shortcut (in POL interface) - I clicked on "Run" and nothing was happening.
With Wine I made same progress. After installing BL2 - Steam - .NET4.5 (in that order), I opened a terminal using that command:

```

wine Launcher.exe 

```
but Wine was crashing, returning a huge error.

When I tried to run Borderlands2.exe (skipping the launcher), the screen went black, and after 1sec. it return with a very low resolution (something like 800x600). I could hear the sound of the game and was able to click -blindly of course- some buttons, since the only thing I was seeing was the Desktop in low res.

Could it be GPU's driver fault? "the way I installed the game" fault? or something else?

---

### Post by Mark Phelps on 2014-07-18
Here's the WineHQ web page for Borderlands 2, maybe some of the testing results will help:  [http://appdb.winehq.org/objectManager.php?sClass=application&iId=14514]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=14514")

---

### Post by theo5 on 2014-07-19
Unfortunately all those test are based on installation via Steam - not DVD.

But it gave me same ideas.
I made a new prefix @ 32 bit using 
```

WINEPREFIX='/home/username/prefix32' WINEARCH='win32' wine 'wineboot'

```
and the installed steam. Through steam I installed BL2 and try to run launcher.exe and bordelands2.exe - as usual nothing happend.

What may be the problem (in the abstract)?

---

### Post by theo5 on 2014-07-19
Ok so I tried something different. I installed via POL, Skyrim with its DLCs and it work fine (except when I exit to Desktop. In that case, screen freezes but I can tell that ubuntu is still running).
POL installed Frameworks, Steam, DirectX etc. in a specific prefix. I installed in the same prefix BL2, but when I try to run Borderlands2.exe (wine Borderlands2.exe) I get the following error in the terminal

```

err:module:import_dll Library Steamclient.dll (which is needed by L"Z:\\home\\theo\\.PlayOnLinux\\wineprefix\\Skyrim\\drive_c\\Program Files\\2K Games\\Borderlands 2\\Binaries\\Win32\\steam_api.dll") not found
err:module:import_dll Library buddha.dll (which is needed by L"Z:\\home\\theo\\.PlayOnLinux\\wineprefix\\Skyrim\\drive_c\\Program Files\\2K Games\\Borderlands 2\\Binaries\\Win32\\steam_api.dll") not found
err:module:import_dll Library steam_api.dll (which is needed by L"Z:\\home\\theo\\.PlayOnLinux\\wineprefix\\Skyrim\\drive_c\\Program Files\\2K Games\\Borderlands 2\\Binaries\\Win32\\Borderlands2.exe") not found
err:module:import_dll Library X3DAudio1_7.dll (which is needed by L"Z:\\home\\theo\\.PlayOnLinux\\wineprefix\\Skyrim\\drive_c\\Program Files\\2K Games\\Borderlands 2\\Binaries\\Win32\\Borderlands2.exe") not found
err:module:import_dll Library XAPOFX1_5.dll (which is needed by L"Z:\\home\\theo\\.PlayOnLinux\\wineprefix\\Skyrim\\drive_c\\Program Files\\2K Games\\Borderlands 2\\Binaries\\Win32\\Borderlands2.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\theo\\.PlayOnLinux\\wineprefix\\Skyrim\\drive_c\\Program Files\\2K Games\\Borderlands 2\\Binaries\\Win32\\Borderlands2.exe" failed, status c0000135


```

Obviously, it's not possible that DirectX is not installed, since Skyrim works.
I am starting to thinking that the best way to play a demanding game on linux is to install a windows partition :p:p

---

