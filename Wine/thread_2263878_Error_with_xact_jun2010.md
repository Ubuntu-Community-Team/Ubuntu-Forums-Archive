---
title: "Error with xact_jun2010"
date: 2015-02-04
forum: Wine
---

### Post by PotatoHead007 on 2015-02-04
Hi.

I created a new 32-bit wine prefix. Then i ran this in the new prefix: ```
winetricks vcrun2012 xact_jun2010 orm=backbuffer
```
This returned this error to me:```

Executing w_do_call vcrun2012
vcrun2012 already installed, skipping
Executing w_do_call xact_jun2010
Executing load_xact_jun2010
Executing cabextract -q -d /home/MYUSER/.CubeWorld/dosdevices/c:/windows/temp/_xact_jun2010 -L -F *_xact_*x86* /home/MYUSER/.cache/winetricks/directx9/directx_Jun2010_redist.exe
Executing cabextract -q -d /home/MYUSER/.CubeWorld/dosdevices/c:/windows/temp/_xact_jun2010 -L -F *_x3daudio_*x86* /home/MYUSER/.cache/winetricks/directx9/directx_Jun2010_redist.exe
Executing cabextract -q -d /home/MYUSER/.CubeWorld/dosdevices/c:/windows/temp/_xact_jun2010 -L -F *_xaudio_*x86* /home/MYUSER/.cache/winetricks/directx9/directx_Jun2010_redist.exe
Executing cabextract -q -d /home/MYUSER/.CubeWorld/dosdevices/c:/windows/system32 -L -F xactengine*.dll /home/MYUSER/.CubeWorld/dosdevices/c:/windows/temp/_xact_jun2010/*.cab
/home/MYUSER/.CubeWorld/dosdevices/c:/windows/temp/_xact_jun2010/*.cab: No such file or directory
------------------------------------------------------
Note: command 'cabextract -q -d /home/MYUSER/.CubeWorld/dosdevices/c:/windows/system32 -L -F xactengine*.dll /home/MYUSER/.CubeWorld/dosdevices/c:/windows/temp/_xact_jun2010/*.cab' returned status 1.  Aborting.
------------------------------------------------------

```
I know xact_jun2010 is the problem, but what is the solution?

---

