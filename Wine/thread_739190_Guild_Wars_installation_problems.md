---
title: "Guild Wars installation problems"
date: 2008-03-29
forum: Wine
---

### Post by Runningflame570 on 2008-03-29
Well I've tried everything I can think of, it may just be an issue with my graphics drivers in which case theres not a ton I can do about that.

> err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support !
err:wgl:X11DRV_ChoosePixelFormat No libGL on this box - disabling OpenGL support !
err:d3d:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat
err:d3d:InitAdapters Failed to get a gl context for default adapter
err:wine_d3d:WineDirect3DCreate Direct3D8 is not available without opengl
err:seh:setup_exception stack overflow 24 bytes in thread 0037 eip b7d9848a esp 00240fe8 stack 0x241000-0x350000


Those are the errors I get when trying to install Guild Wars, this is both with the setup on disc and downloaded setup file.

Does anybody have a clue what could be causing it? Guild Wars was listed as platinum which is the only reason I even bothered trying again.

---

### Post by aphirst on 2008-03-29
It's as if WINE doesn't think OpenGL is accessible. This in itself could be a problem with Wine (did you compile it yourself and miss a flag?), your Graphics Card drivers (don't expect decent drivers from ATI, I certainly don't :P ), or the Wine Registry (the appdb.winehq.com entry on Wine clearly states that there are wine registry keys necessary to make Guild Wars run faster and more stable).

It could be that you haven't got all of the required OpenGL Libraries or Bindings (I can't give a list of them because I don't know what they are, or which ones you have :P ).

Its mainly pissing in the wind, but how many other apps have you already installed in Wine; it's possible that someithing has inadvertedly shited your wineprefix, try running
```
wineprefixcreate --prefix /home/$USER/$whatever
```
and envoking (env WINEPREFIX=/home/$USER/$whatever beforwine foo.exe) with the installer. (don't forget, of course, to run winecfg and set everything to something sensible.)

---

### Post by Runningflame570 on 2008-03-29
Actually I'm running an Nvidia card, granted one that is known to have issues (and believe me, I've experienced issues) the 7900GS. Wine was installed from their repos with synaptic, so that shouldn't be the cause of the problem.

I'll check into the other suggestions though.

EDIT: The wineprefixcreate throws up errors also..this is very odd because I had gotten Guild Wars to install before. It does create the directories correctly though.

---

### Post by Runningflame570 on 2008-03-29
So any other ideas?

---

### Post by aphirst on 2008-03-30
What errors does it throw up? That's the kind of information that allows new suggestions to materialise ;) .

If the entire thing has ground to a halt, your best bet would be to back up your Wine apps and purge wine (sudo apt-get remove wine --purge), then reinstall it.

I can run it at a decent 30+ fps on my laptop, but my friend with a desktop with a higher spec barely gets 10fps. Its an absolute cow of a program. It mught be just bad luck, but quadruple-check all your settings, and then check and reinstall again.

---

### Post by Virgilius on 2008-04-13
At the moment, I've installed and run GW already, but why is it being jerky from the menu?

---

