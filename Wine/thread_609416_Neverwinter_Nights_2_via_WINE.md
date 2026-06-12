---
title: "Neverwinter Nights 2 via WINE"
date: 2007-11-10
forum: Wine
---

### Post by Maelgwyn on 2007-11-10
I think this may have been covered, but I can't see any resolved versions, so here's my two cents!

I've successfully installed NWN2 from CD via WINE, but now when I try to load it, I get this:

```
nik@user-desktop:~$ wine "C:\Program Files\Atari\Neverwinter Nights 2\NWN2Launcher.exe"
fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias -720, std (d/m/y): 18/03/2007, dlt (d/m/y): 30/09/2007
fixme:winmm:MMDRV_Exit Closing while ll-driver open
fixme:winmm:MMDRV_Exit Closing while ll-driver open
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Atari\\Neverwinter Nights 2\\nwn2.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Atari\\Neverwinter Nights 2\\nwn2.exe" failed, status c0000135
nik@user-desktop:~$ 
```

Any ideas on how to fix this?

---

### Post by Vadi on 2007-11-10
I'm not sure how legal this is, so please ready any licensing info on this. But there's a site where you can practically get every .dll from, including this one apparently:

[http://www.dll-files.com/dllindex/dll-files.shtml?msvcr80](http://www.dll-files.com/dllindex/dll-files.shtml?msvcr80)

---

### Post by Maelgwyn on 2007-11-11
Sweet thanks!

That helped a lot, however now NWN2 cannot load a 'security module'...
```

nik@user-desktop:~$ fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias -720, std (d/m/y): 18/03/2007, dlt (d/m/y): 30/09/2007
fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias -720, std (d/m/y): 18/03/2007, dlt (d/m/y): 30/09/2007
fixme:ntdll:NtQueryInformationProcess (0xffffffff,info_class=34,0x13857e0,0x00000004,0x13857dc) Unknown information class
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0x13857e0): Stub!
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x1383d38,0x00000000), stub!
```

---

### Post by Vadi on 2007-11-11
Oh I have no idea. Try posting it on appdb.

---

### Post by KhaaL on 2007-11-11
let us know if you get it working, I feel so left out with no port of nwn2 to linux...

---

### Post by Ferrat on 2007-11-11
Make sure that 
msvcr80
msvcp80
msvcm80
are matching version numbers (not the same nr, just matching), pref. find them in a bundle or excract them all from the same place 

get a no-cd exe since wine can't handle the cd protection

---

### Post by Mr_HeNtAi on 2007-11-30
> **Maelgwyn said:**
> Sweet thanks!

That helped a lot, however now NWN2 cannot load a 'security module'...


I'm having a similar issue with F.E.A.R Combat.

```

ALSA lib conf.c:3949:(snd_config_expand) Unknown parameters 0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:0
fixme:ntdll:NtQueryObject Unsupported information class 3
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0xee664c): Stub!

```

The same cannot load a 'security module' msg. I'd love to know if there is a fix for this issue.

---

### Post by cogadh on 2007-11-30
F.E.A.R. doesn't work in Wine:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=5159](http://appdb.winehq.org/objectManager.php?sClass=version&iId=5159)

NWN2 has inconsistent performance in Wine, depending on the version of the game and Wine:
[http://appdb.winehq.org/appview.php?iAppId=4118](http://appdb.winehq.org/appview.php?iAppId=4118)

---

### Post by Mr_HeNtAi on 2007-11-30
> **cogadh said:**
> F.E.A.R. doesn't work in Wine:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=5159](http://appdb.winehq.org/objectManager.php?sClass=version&iId=5159)


Not, yet anyways.

---

### Post by cogadh on 2007-11-30
> **Mr_HeNtAi said:**
> Not, yet anyways.
Truer words have never been spoken. :D

---

### Post by KhaaL on 2007-12-10
Oh, regarding that "security module", try setting the windows version to vista or windows server 2003 and using a no-cd patch.

---

### Post by WaySensei on 2008-01-11
I have the same problem with my NWN2. I have installed in with wine but cannot run the game because "A required security module cannot be activated." I would like to try applying a no-cd patch, but am not sure how to do this. I have downloaded a no cd .exe and have no idea what to do with it.

---

### Post by KhaaL on 2008-01-11
Make sure the No-cd exe file is of the same version as the game. what you do with it is simply replacing the original .exe with it, since it won't have copy protection.

---

### Post by Yeeha on 2010-06-23
just ran into problem when playing storm of zephyr expansion, ore trading window doesnt seem to work. When i click on << or < it doesnt put ore into selling box and all buttons >> and > too become pressed. Any ideas how to fix it? :(

---

