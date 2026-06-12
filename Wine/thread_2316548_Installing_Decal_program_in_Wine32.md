---
title: "Installing Decal program in Wine32"
date: 2016-03-09
forum: Wine
---

### Post by Jhall1108 on 2016-03-09
Hey, Im running Asheron's Call 1 in a 32bit Winearch and im trying to  install an addon for the game called Decal. Im in Ubuntu 15.10 and running Wine 1.8. I have  installed dotnet20 and vcrun2012 in winetricks. 

```
$ WINEARCH=win32 WINEPREFIX=/home/jeremy/.wine32 wine '/home/(my username)/Downloads/setup.exe' 
fixme:service:scmdatabase_autostart_services Auto-start service L"clr_optimization_v2.0.50727_32" failed to start: 1053
fixme:urlmon:InternetBindInfo_GetBindString not supported string type 20
fixme:urlmon:InternetBindInfo_GetBindString not supported string type 17
fixme:urlmon:InternetBindInfo_GetBindString not supported string type 16
fixme:urlmon:DownloadBSC_OnProgress Unsupported status 25
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:msvcrt:__clean_type_info_names_internal (0x63f085fc) stub
```

Any help would be appreciated.

---

