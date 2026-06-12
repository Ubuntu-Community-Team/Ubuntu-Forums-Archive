---
title: "[Ubuntu 13.04] DirectX Diagnostic Tool Won't Run"
date: 2013-07-15
forum: Wine
---

### Post by JavaBeansAndOreos on 2013-07-15
Hello,

I've recently installed the latest version of DirectX (from the Microsoft website) into Wine. 

I'm very new to Wine, so I've been following [ this]("http://www.dedoimedo.com/games/wine-directx.html") tutorial. After downloading the DirectX End-User Runtimes (June 2010) redistributable version [ here]("http://www.microsoft.com/en-us/download/details.aspx?id=8109") (without the additional files prompted before download), I ran the DirectX Installer with success. In the tutorial, the user is instructed to run the DirectX Diagnostic Tool using the command:

```

wine ~/.wine/drive_c/windows/system32/dxdiag.exe

```

When I attempt this, I get the message:

```

err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"C:\\windows\\system32\\dxdiagn.dll"
err:ole:CoGetClassObject no class object {a65b8071-3bfe-4213-9a5b-491da4461ca7} could be created for context 0x1
err:dxdiag:collect_dxdiag_information IDxDiagProvider instance creation failed with 0x80070005
err:dxdiag:wWinMain DxDiag information collection failed

```

All of which is a foreign language to me. So I ran the "ls" command in the system32 directory and double-checked to make sure the dxdiag.exe file is actually in the system32 file, and it is.

The DirectX Diagnostic Tool appears critical in determining which .dll files and drivers I might be missing. The only clue I've been able to find thus far is from [ this]("http://ubuntuforums.org/showthread.php?t=1903602") thread. The user in post #7 suggests that there may be some additional files in winetricks-  namely d3dxof, devenum, dsound, dxdiag, dxdiagn - that may be missing. I'm not sure if I have those files in my winetricks (and not certain how to check) and I'm not certain if those files have anything to do with running the DirectX Diagnostic Tool.

And help is of course appreciated.

---

### Post by squiz-clifton on 2013-10-11
I noticed this issue is unresolved. I also am having a similiar problem myself. It would seem I can install the Directx9.0c re-distributable package no problems at all. But then when it comes to running Dxdiag.exe I get the following...

fixme:service:scmdatabase_autostart_services Auto-start service L"SecDrv" failed to start: 2
Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 9: reading configurations from ~/.fonts.conf is deprecated.
Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 9: reading configurations from ~/.fonts.conf is deprecated.
Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 9: reading configurations from ~/.fonts.conf is deprecated.
Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 9: reading configurations from ~/.fonts.conf is deprecated.
Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 9: reading configurations from ~/.fonts.conf is deprecated.
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"C:\\windows\\system32\\dxdiagn.dll"
err:ole:CoGetClassObject no class object {a65b8071-3bfe-4213-9a5b-491da4461ca7} could be created for context 0x1
err:dxdiag:collect_dxdiag_information IDxDiagProvider instance creation failed with 0x80070005
err:dxdiag:wWinMain DxDiag information collection failed


I hope someone reads this because it's got me scratching my head too haha.

---

### Post by Mark Phelps on 2013-10-13
The link is to the page from the WineHQ website for dxdiag:  [http://appdb.winehq.org/objectManager.php?sClass=version&iId=10562]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=10562")

---

