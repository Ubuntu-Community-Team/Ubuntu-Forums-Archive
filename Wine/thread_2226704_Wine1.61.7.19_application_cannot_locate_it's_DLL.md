---
title: "Wine1.6/1.7.19 application cannot locate it's DLL"
date: 2014-05-28
forum: Wine
---

### Post by Juan_Laporte on 2014-05-28
I am running Ubuntu 14.04 LTS (trusty) 32-bit w/ wine1.6. I am trying to run SimCity 2013 which I know works perfectly fine with any Windows machine. When I run the exe it returns:

> Error Code: [4000] SimCity could not find the EA WebKit DLL. SimCity will now exit.

The dll is named "eawebkit.dll"
I tried using winetricks and add the dll and select every option available to no avail.
The file is in the correct folder in order to run just as another machine running Win 7 does. My thoughts are, there is some configuration file possibly needing altered. I think the program is looking outside the .wine/drive_c parameters.

Any thoughts? Tricks? Bag of bones?? :shock:

Below is the process output:
```
fixme:hnetcfg:fw_profile_get_ExceptionsNotAllowed 0x146dd8, 0x32fd2c
fixme:hnetcfg:fw_app_get_Enabled 0x146df0, 0x32fd34
fixme:hnetcfg:fw_app_put_ProcessImageFileName 0x146e38, L"C:\\Games\\SimCity 2013 Offline\\SimCity\\SimCity.exe"
fixme:hnetcfg:fw_app_put_Name 0x146e38, L"SimCity"
fixme:hnetcfg:fw_apps_Add 0x146df0, 0x146e38
fixme:thread:SetThreadIdealProcessor (0xb4): stub
fixme:thread:SetThreadIdealProcessor (0xbc): stub
fixme:system:SetProcessDPIAware stub!
fixme:xinput:XInputGetState (0 0x32f410)
fixme:ole:RemUnknown_QueryInterface No interface for iid {00000019-0000-0000-c000-000000000046}
fixme:win:EnumDisplayDevicesW ((null),0,0x32ee68,0x00000000), stub!
fixme:thread:SetThreadIdealProcessor (0x1d8): stub
err:ole:CoInitializeEx Attempt to change threading model of this apartment from apartment threaded to multi-threaded
fixme:winediag:AUDDRV_GetAudioEndpoint Winepulse is not officially supported by the wine project
fixme:winediag:AUDDRV_GetAudioEndpoint For sound related feedback and support, please visit http://ubuntuforums.org/showthread.php?t=1960599
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:debug_d3dformat Unrecognized 0x36314644 (as fourcc: DF16) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x36314644) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x34324644 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x34324644) in the format lookup table
```

---

### Post by Juan_Laporte on 2014-05-29
To tough of a question for everyone???

---

### Post by Juan_Laporte on 2014-06-26
[Solved] installed using wine 1.5.21 with play on linux and it worked

---

### Post by fricigrillbufe on 2014-07-03
Hi,

Which windows version have you chosen in Wine configuration? (XP/Vista/7/8...)

Thanks!

---

### Post by Juan_Laporte on 2014-08-19
> **fricigrillbufe said:**
> Hi,

Which windows version have you chosen in Wine configuration? (XP/Vista/7/8...)

Thanks!

I choose WinXP

---

### Post by mastablasta on 2014-08-21
how about if you put the required dll in simcity folder?

most games and such first look local and only when they can't find it in windows, windows/system folder. they are known to bring all libraries with them as they can not know if they are installed or not.

in Linux this is checked and package manager downloads them and puts them where they have to be. which ha sit's own issues, but anyway... in windows programs bring them along so you can have duplicate or triplicates or more of certain library in different folders across the disk.

---

