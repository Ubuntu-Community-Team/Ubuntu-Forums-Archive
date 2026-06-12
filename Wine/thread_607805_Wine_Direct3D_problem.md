---
title: "Wine Direct3D problem"
date: 2007-11-09
forum: Wine
---

### Post by evolution123 on 2007-11-09
Hi everyone!

I've been looking out for a solution for playing silkroad on linux a very long time now.
The testers on winehq.org says that you just need the latest wine version( 0.9.48 ).

Everything is ok, but when i try to start the game it says:
> Could not find any compatible Direct3D

What to do?
Maybe I need to install wined3d? but how?

---

### Post by cogadh on 2007-11-09
Wine already has a built-in implementation of Direct3D, so you shouldn't need to add anything. Did you set the OS version in Wine to Windows 98 as per the instructions on Wine's AppDB?

---

### Post by evolution123 on 2007-11-09
yes i did.
although it is set to emulate windows 98 the error appears. :(

---

### Post by cogadh on 2007-11-09
Okay, then I need a bit more info, like what video hardware do you have and have you installed the accelerated driver for it? What other settings are you using in Wine? Have you made any custom registry edits in Wine?

---

### Post by evolution123 on 2007-11-09
ati radeon 9600
ati driver installed

no special settings set

tried to install cvscedega from winecvs.linux-gamers.net, but starting cvscedega says: error: wineserver is exiting unexspectantly!

---

### Post by cogadh on 2007-11-09
Are there any Wine errors output to the terminal when you run it?

---

### Post by evolution123 on 2007-11-09
[http://phpfi.com/274962](http://phpfi.com/274962)

thats the ouput when i run the launcher.
when i click on start it says this:

> fixme:win:EnumDisplayDevicesW ((null),0,0x34f914,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
fixme:dbghelp:MiniDumpWriteDump NIY MiniDumpScanMemory
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x6e4025

([http://phpfi.com/274963](http://phpfi.com/274963))

---

### Post by cogadh on 2007-11-09
Well, you can't really do anything about the "fixme" messages, they are just developer notes, but that unhandled exception is a bit worrisome. One thing you might want to try is changing directories to the game's install directory before you run the game. Windows games generally like to be "run in" their install directory:
```
cd ~/.wine/drive_c/Program\ Files/Silkroad
wine Silkroad.exe
```

---

### Post by evolution123 on 2007-11-09
uhm....same error this time :(

but now i mentioned that this unhandled exception error appears a few seconds after i close the not compatible direct3d window. the d3d9 window appears without any error on the console.

---

### Post by cogadh on 2007-11-09
This is really odd. I think it might be the video driver, there are some anectdotal references in the AppDB page that might indicate that, but there are also many ATI users who have no issues with the game. It might also be related to this bug:
[http://bugs.winehq.org/show_bug.cgi?id=10145](http://bugs.winehq.org/show_bug.cgi?id=10145)
The bug was patched three days ago, so the next version of Wine (0.9.49, just released today!) may work better.

---

### Post by evolution123 on 2007-11-09
Hmm...thank you for your research and initiative :)
i will update wine as far as the new version is available as .deb package.
hopefully it'll work :(

---

