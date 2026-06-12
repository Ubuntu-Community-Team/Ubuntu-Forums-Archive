---
title: "wine video problem"
date: 2007-12-24
forum: Wine
---

### Post by faraz_k86 on 2007-12-24
i used wine for the first time and installed age of empires 2 on it.


when i run the game i get the following error:

> could not initialize video. make sure ur video card is compatible with direct draw



but i have been playing this game on windows on this laptop.

---

### Post by cogadh on 2007-12-24
What video hardware do you have on your laptop and have you installed the 3D accelerated drivers for it yet?

---

### Post by faraz_k86 on 2007-12-24
it is some intel chip, its my laptop.


how do i find the exact model? is there any terminal command?

---

### Post by cogadh on 2007-12-24
I don't think it will matter. The Linux driver for the Intel chipsets is not the greatest and it will likely not work for this game with Wine. The driver that comes with Ubuntu by default is the only available driver for it, unfortunately.

---

### Post by faraz_k86 on 2007-12-24
so if i cant even play a game as old as age of empires then that means i cant play any game????


there has got to be a solution

---

### Post by cogadh on 2007-12-24
No, you could probably play some Linux native games, but Wine is a different animal entirely. It is basically taking DirectX output and converting it to OpenGL output. If your card can't do the OpenGL functions that Wine is calling for (because of the lackluster Intel driver), then the game won't run.

It might help to get the terminal output that Wine produces when you run the game, it could have some useful information that might point to a potential solution.

---

### Post by faraz_k86 on 2007-12-24
wine does not produce any terminal output.

how do i get it to do that?

---

### Post by cogadh on 2007-12-24
If you run it from the terminal, it will always produce some output. Open a terminal and run the game like this:
```
cd .wine/drive_c/Program\ Files/<game directory>
wine <game executable>.exe
```

---

### Post by faraz_k86 on 2007-12-24
i dont know why but when i run the game from terminal as you said. then it works perfectly??   why is that.   after entering the commands it started working. but only from the terminal.

this is the output:

> fixme:system:SystemParametersInfoW Unimplemented action: 110 (SPI_GETSHOWIMEUI)
fixme:win:EnumDisplayDevicesW ((null),0,0x34da10,0x00000000), stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:system:SystemParametersInfoW Unimplemented action: 111 (SPI_SETSHOWIMEUI)
err:dplay:DP_IF_InitializeConnection Unable to load service provider {36e95ee0-8577-11cf-960c-0080c7534e82}
err:dplay:DirectPlayCreate Failed to Initialize SP: DPERR_UNAVAILABLE
err:dplay:DP_IF_InitializeConnection Unable to load service provider {685bc400-9d2c-11cf-a9cd-00aa006886e3}
err:dplay:DirectPlayCreate Failed to Initialize SP: DPERR_UNAVAILABLE
err:dplay:DP_IF_InitializeConnection Unable to load service provider {44eaa760-cb68-11cf-9c4e-00a0c905425e}
err:dplay:DirectPlayCreate Failed to Initialize SP: DPERR_UNAVAILABLE
err:dplay:DP_IF_InitializeConnection Unable to load service provider {0f1d6860-88d9-11cf-9c4e-00a0c905425e}
err:dplay:DirectPlayCreate Failed to Initialize SP: DPERR_UNAVAILABLE


---

### Post by faraz_k86 on 2007-12-24
bump.


any ideas?

---

### Post by cogadh on 2007-12-25
Windows applications like to be run in the directory where they are installed. The fact that you changed directories to the game's install directory and then ran the game allows it to run the way it would have in Windows. Generally speaking, that is the way you should always run applications with Wine.

As for the errors you are still getting, they all refer to DirectPlay, the networking component of DirectX. It looks like it was unable to create a network connection for online multiplay. You might be able to fix that by copying a dplay.dll file from a Windows machine (or Google it, you might be able to download it) and placing it in the .wine/drive_c/windows/system32 directory, then applying a DLL override in winecfg for it.

---

