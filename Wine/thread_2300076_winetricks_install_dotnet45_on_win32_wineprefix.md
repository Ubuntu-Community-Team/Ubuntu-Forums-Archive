---
title: "winetricks install dotnet45 on win32 wineprefix"
date: 2015-10-23
forum: Wine
---

### Post by cybermecano on 2015-10-23
Hi,

I would like to run a microsoft program named ConPADE on my ubuntu 14.04 LTS (64-bits) and for that I need to first install .NET framework 4.5 so this is the steps I've done for that purpose :

1- I created a clean 32-bit wineprefix
```
export WINEARCH=win32 && WINEPREFIX=/home/ahmed/.newWine32 winecfg
```
2- I tried to install dotnet45 on that newly created wineprefix
```
WINEPREFIX='/home/ahmed/.newWine32' bash winetricks dotnet45 corefont
```
it seemed like it started to download dotnet35 instead of dotnet45 !!
```
Executing w_do_call dotnet45
Executing load_dotnet45
Executing w_do_call remove_mono
Executing load_remove_mono
fixme:storage:create_storagefile Storage share mode not implemented.
DELETE - HKLM\Software\Microsoft\NET Framework Setup\NDP\v4 (null) 0 0 1
Error: The system was unable to find the specified registry key or value
Executing rm -f /home/ahmed/.newWine32/dosdevices/c:/windows/system32/mscoree.dll
Executing w_do_call dotnet35
Executing load_dotnet35
------------------------------------------------------
dotnet35 does not yet fully work or install on wine.  Caveat emptor.
------------------------------------------------------
------------------------------------------------------
Checksum for /home/ahmed/.cache/winetricks/dotnet35/dotnetfx35.exe did not match, retrying download
------------------------------------------------------
Downloading http://download.microsoft.com/download/6/0/f/60fc5854-3cb8-4892-b6db-bd4f42510f28/dotnetfx35.exe to /home/ahmed/.cache/winetricks/dotnet35
--2015-10-23 14:58:34--  http://download.microsoft.com/download/6/0/f/60fc5854-3cb8-4892-b6db-bd4f42510f28/dotnetfx35.exe
Resolving download.microsoft.com (download.microsoft.com)... 2.22.26.7, 2001:668:108:8882::e59, 2001:668:108:888c::e59
Connecting to download.microsoft.com (download.microsoft.com)|2.22.26.7|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 206692864 (197M) [application/octet-stream]
Saving to: ‘dotnetfx35.exe’

 0% [                                                                                                   ] 289,790      139KB/s   
```

should I let it do ?

Thanks.

---

### Post by cybermecano on 2015-10-23
Hi,

Indeed, I let it do the job and it turns out that versions 2.0, 2.0sp1, 3.0, 3.0sp1, 3.5, 3.5sp1, 4.0 should be set up prior to the installation of .NET 4.5.

Cheers.

---

