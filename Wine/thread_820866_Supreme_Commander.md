---
title: "Supreme Commander"
date: 2008-06-06
forum: Wine
---

### Post by Jimjim32 on 2008-06-06
I feel bad about continually asking for help, but in a way it's good because one day I might be the one helping everyone else.
Fresh install of Ubuntu and wine, Geforce 8600 32bit OS.
Trying to get supreme commander to run, according to the instructions on the Wine appDB, ie:

```
    *  In order to get sound:

Download this archive and extract it into windows/system32. Open a terminal, cd to system32 and do this: regsvr32 xactengine2_*.dll
You may also need to set your sample rate to 48000 in winecfg's Audio tab

    * Create the registry string HKCU/Software/Wine/Direct3D/OffscreenRenderingMode and set it to fbo

    * Make sure your Color Depth is set to 24 bits. Otherwise the game will not render fonts or 3D models correctly

    * Launch the game with wine SupremeCommander.exe

If Wine/SupCom complains about missing files make sure you're cd'ed into Supreme Commander/bin before launching.
You may also need d3dx9_31.dll. Get it from a site like dll-files.com and put it into system32
If you're still running into problems, try starting the game with the /novalidate switch

Also, if SupCom complains about insufficient video memory or crashes very early into the game,
try creating the string HKEY_CURRENT_USER\Software\Wine\Direct3D\VideoMemorySize with a value >64, e.g. 128 
```

This small section shown here has me a little stumped, particularly the "/novalidate switch"

The errors I get when trying to run the game are as follows:
```
err:module:import_dll Library X3DAudio1_1.dll (which is needed by L"C:\\Program Files\\THQ\\Gas Powered Games\\Supreme Commander\\bin\\MohoEngine.dll") not found
err:module:import_dll Library MohoEngine.dll (which is needed by L"C:\\Program Files\\THQ\\Gas Powered Games\\Supreme Commander\\bin\\SupremeCommander.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\THQ\\Gas Powered Games\\Supreme Commander\\bin\\SupremeCommander.exe" failed, status c0000135
james@james-desktop:~/.wine/drive_c/Program Files/THQ/Gas Powered Games/Supreme Commander/bin$ wine SupremeCommander.exe 
err:module:import_dll Library X3DAudio1_1.dll (which is needed by L"C:\\Program Files\\THQ\\Gas Powered Games\\Supreme Commander\\bin\\MohoEngine.dll") not found
err:module:import_dll Library MohoEngine.dll (which is needed by L"C:\\Program Files\\THQ\\Gas Powered Games\\Supreme Commander\\bin\\SupremeCommander.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\THQ\\Gas Powered Games\\Supreme Commander\\bin\\SupremeCommander.exe" failed, status c0000135
```

Thanks in advance everybody, everybody is being really great to a novice like me. To be honest, the community spirit here really heartens me, to have something so great which has evolved mostly out of human kindness (Not purely, as the developers made it for themselves).

How are you? (If anyone answers)

---

### Post by Vadi on 2008-06-06
The "cd'd" part means you need to use the terminal to start the game (with the syntax "wine <program.exe>"). Do you know how to use the terminal and cd?

As for the switch, I think they're implying you should do "wine <program.exe /novalidate".

---

### Post by Jimjim32 on 2008-06-06
Yes thanks you, I can use cd and terminal.
In fact, it's all I can do in terminal really. that and use some basic commands.
And no, that didn't seem to help either.

---

### Post by yax51 on 2010-03-14
I'm not getting any sound on supreme commander. Everything else seems to be working great. I've downloaded the .dll's as specified and placed tem in the approptiate folders, and et it still doesn't seem to work. Any ideas?

---

