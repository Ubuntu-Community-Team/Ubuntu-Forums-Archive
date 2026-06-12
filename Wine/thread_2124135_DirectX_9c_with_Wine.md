---
title: "DirectX 9c with Wine"
date: 2013-03-09
forum: Wine
---

### Post by Hydera5 on 2013-03-09
Hello im trying to istall DirectX 9c with wine.  When i try to install it it says "An internal system error has occured. Please refer to DXerror.log and DirectX.log in your windows folder to determine the problem.  I am trying to use a program called OBS and it needs this version of DirectX.  I was just wondering if i could get some assistance on how to install it properly.  THANKS!

The DirectX.log

03/09/13 22:41:44: DXWSetup: ***** DXWSETUP ***** 
03/09/13 22:41:44: DXWSetup: WinMain() 
03/09/13 22:41:44: DXWSetup: IsIA64(): not IA64. 
03/09/13 22:41:44: DXWSetup: Unable to get Version on target file C:\windows\system32\directx\websetup\dsetup.dll 
03/09/13 22:41:44: DXWSetup: Installed file C:\windows\system32\directx\websetup\dsetup.dll 
03/09/13 22:41:44: DXWSetup: Unable to get Version on target file C:\windows\system32\directx\websetup\dsetup32.dll 
03/09/13 22:41:44: DXWSetup: Installed file C:\windows\system32\directx\websetup\dsetup32.dll 
03/09/13 22:41:44: DXWSetup: GetDXVersion(): Unable to get RC string from registry. 
03/09/13 22:41:44: DXWSetup: DirectX Version: 4.09.00.0904.00 
03/09/13 22:41:44: DXWSetup: Setup Version: 4.09.00.0904.00 
03/09/13 22:41:44: DXWSetup: A newer version of DirectX have been installed already. 
03/09/13 22:41:55: DXWSetup: CDXWSetup::CDXWSetup() 
03/09/13 22:41:55: DXWSetup: CDXWSetup::CDXWSetup(): CoCreateInstance() failed, error = 0x80040152. 
03/09/13 22:41:55: DXWSetup: DXSError(): FormatMessage() failed, system cannot find message text for error. 
03/09/13 22:41:55: DXWSetup: CDXWSetup:downloadDXUpdate() 
03/09/13 22:41:55: DXWSetup: CDXWSetup:downloadDXUpdate(): CoCreateInstance() failed, error = 0x80040152. 
03/09/13 22:41:55: DXWSetup: DXSError(): FormatMessage() failed, system cannot find message text for error. 
03/09/13 22:41:55: DXWSetup: PreinstDlgProc(): CDXWSetup:downloadDXUpdate() failed. 
03/09/13 22:41:55: DXWSetup: WM_APP_ENDDOWNLOAD 
03/09/13 22:42:00: DXWSetup: CDXWSetup::~CDXWSetup() 
03/09/13 22:42:02: DXWSetup: CreatePropertySheet() returns -9. 
03/09/13 22:42:02: DXWSetup: Deleted file C:\windows\system32\directx\websetup\dsetup.dll. 
03/09/13 22:42:02: DXWSetup: Deleted file C:\windows\system32\directx\websetup\dsetup32.dll. 
03/09/13 22:42:05: DXWSetup: ***** DXWSETUP ***** 
03/09/13 22:42:05: DXWSetup: WinMain() 
03/09/13 22:42:05: DXWSetup: IsIA64(): not IA64. 
03/09/13 22:42:05: DXWSetup: Unable to get Version on target file C:\windows\system32\directx\websetup\dsetup.dll 
03/09/13 22:42:05: DXWSetup: Installed file C:\windows\system32\directx\websetup\dsetup.dll 
03/09/13 22:42:05: DXWSetup: Unable to get Version on target file C:\windows\system32\directx\websetup\dsetup32.dll 
03/09/13 22:42:05: DXWSetup: Installed file C:\windows\system32\directx\websetup\dsetup32.dll 
03/09/13 22:42:06: DXWSetup: GetDXVersion(): Unable to get RC string from registry. 
03/09/13 22:42:06: DXWSetup: DirectX Version: 4.09.00.0904.00 
03/09/13 22:42:06: DXWSetup: Setup Version: 4.09.00.0904.00 
03/09/13 22:42:06: DXWSetup: A newer version of DirectX have been installed already. 
03/09/13 22:42:11: DXWSetup: CDXWSetup::CDXWSetup() 
03/09/13 22:42:11: DXWSetup: CDXWSetup::CDXWSetup(): CoCreateInstance() failed, error = 0x80040152. 
03/09/13 22:42:11: DXWSetup: DXSError(): FormatMessage() failed, system cannot find message text for error. 
03/09/13 22:42:11: DXWSetup: CDXWSetup:downloadDXUpdate() 
03/09/13 22:42:11: DXWSetup: CDXWSetup:downloadDXUpdate(): CoCreateInstance() failed, error = 0x80040152. 
03/09/13 22:42:11: DXWSetup: DXSError(): FormatMessage() failed, system cannot find message text for error. 
03/09/13 22:42:11: DXWSetup: PreinstDlgProc(): CDXWSetup:downloadDXUpdate() failed. 
03/09/13 22:42:11: DXWSetup: WM_APP_ENDDOWNLOAD 
03/09/13 22:42:15: DXWSetup: CDXWSetup::~CDXWSetup() 
03/09/13 22:42:18: DXWSetup: CreatePropertySheet() returns -9. 
03/09/13 22:42:18: DXWSetup: Deleted file C:\windows\system32\directx\websetup\dsetup.dll. 
03/09/13 22:42:18: DXWSetup: Deleted file C:\windows\system32\directx\websetup\dsetup32.dll. 
03/09/13 22:49:22: DXWSetup: ***** DXWSETUP ***** 
03/09/13 22:49:22: DXWSetup: WinMain() 
03/09/13 22:49:22: DXWSetup: IsIA64(): not IA64. 
03/09/13 22:49:22: DXWSetup: Unable to get Version on target file C:\windows\system32\directx\websetup\dsetup.dll 
03/09/13 22:49:22: DXWSetup: Installed file C:\windows\system32\directx\websetup\dsetup.dll 
03/09/13 22:49:22: DXWSetup: Unable to get Version on target file C:\windows\system32\directx\websetup\dsetup32.dll 
03/09/13 22:49:22: DXWSetup: Installed file C:\windows\system32\directx\websetup\dsetup32.dll 
03/09/13 22:49:22: DXWSetup: GetDXVersion(): Unable to get RC string from registry. 
03/09/13 22:49:22: DXWSetup: DirectX Version: 4.09.00.0904.00 
03/09/13 22:49:22: DXWSetup: Setup Version: 4.09.00.0904.00 
03/09/13 22:49:22: DXWSetup: A newer version of DirectX have been installed already. 
03/09/13 22:49:28: DXWSetup: CDXWSetup::CDXWSetup() 
03/09/13 22:49:28: DXWSetup: CDXWSetup::CDXWSetup(): CoCreateInstance() failed, error = 0x80040152. 
03/09/13 22:49:28: DXWSetup: DXSError(): FormatMessage() failed, system cannot find message text for error. 
03/09/13 22:49:28: DXWSetup: CDXWSetup:downloadDXUpdate() 
03/09/13 22:49:28: DXWSetup: CDXWSetup:downloadDXUpdate(): CoCreateInstance() failed, error = 0x80040152. 
03/09/13 22:49:28: DXWSetup: DXSError(): FormatMessage() failed, system cannot find message text for error. 
03/09/13 22:49:28: DXWSetup: PreinstDlgProc(): CDXWSetup:downloadDXUpdate() failed. 
03/09/13 22:49:28: DXWSetup: WM_APP_ENDDOWNLOAD 
03/09/13 22:49:32: DXWSetup: CDXWSetup::~CDXWSetup() 
03/09/13 22:51:51: DXWSetup: CreatePropertySheet() returns -9. 
03/09/13 22:51:51: DXWSetup: Deleted file C:\windows\system32\directx\websetup\dsetup.dll. 
03/09/13 22:51:51: DXWSetup: Deleted file C:\windows\system32\directx\websetup\dsetup32.dll. 
03/09/13 23:04:04: DXWSetup: ***** DXWSETUP ***** 
03/09/13 23:04:04: DXWSetup: WinMain() 
03/09/13 23:04:04: DXWSetup: IsIA64(): not IA64. 
03/09/13 23:04:04: DXWSetup: Unable to get Version on target file C:\windows\system32\directx\websetup\dsetup.dll 
03/09/13 23:04:04: DXWSetup: Installed file C:\windows\system32\directx\websetup\dsetup.dll 
03/09/13 23:04:04: DXWSetup: Unable to get Version on target file C:\windows\system32\directx\websetup\dsetup32.dll 
03/09/13 23:04:04: DXWSetup: Installed file C:\windows\system32\directx\websetup\dsetup32.dll 
03/09/13 23:04:04: DXWSetup: GetDXVersion(): Unable to get RC string from registry. 
03/09/13 23:04:04: DXWSetup: DirectX Version: 4.09.00.0904.00 
03/09/13 23:04:04: DXWSetup: Setup Version: 4.09.00.0904.00 
03/09/13 23:04:04: DXWSetup: A newer version of DirectX have been installed already. 
03/09/13 23:04:11: DXWSetup: CDXWSetup::CDXWSetup() 
03/09/13 23:04:11: DXWSetup: CDXWSetup::CDXWSetup(): CoCreateInstance() failed, error = 0x80040152. 
03/09/13 23:04:11: DXWSetup: DXSError(): FormatMessage() failed, system cannot find message text for error. 
03/09/13 23:04:11: DXWSetup: CDXWSetup:downloadDXUpdate() 
03/09/13 23:04:11: DXWSetup: CDXWSetup:downloadDXUpdate(): CoCreateInstance() failed, error = 0x80040152. 
03/09/13 23:04:11: DXWSetup: DXSError(): FormatMessage() failed, system cannot find message text for error. 
03/09/13 23:04:11: DXWSetup: PreinstDlgProc(): CDXWSetup:downloadDXUpdate() failed. 
03/09/13 23:04:11: DXWSetup: WM_APP_ENDDOWNLOAD 
03/09/13 23:07:02: DXWSetup: CDXWSetup::~CDXWSetup() 
03/09/13 23:07:03: DXWSetup: CreatePropertySheet() returns -9. 
03/09/13 23:07:03: DXWSetup: Deleted file C:\windows\system32\directx\websetup\dsetup.dll. 
03/09/13 23:07:03: DXWSetup: Deleted file C:\windows\system32\directx\websetup\dsetup32.dll.

The DXerror.log

-------------------- 
[03/09/13 22:41:55] module: DXWSetup(Mar 30 2011), file: dxwsetup.cpp, line: 72, function: CDXWSetup::CDXWSetup 
 
    Failed API:        CoCreateInstance() 
    Error:        (0x80040152) 
 
-------------------- 
[03/09/13 22:41:55] module: DXWSetup(Mar 30 2011), file: dxupdate.cpp, line: 431, function: CDXWSetup:downloadDXUpdate 
 
    Failed API:        CoCreateInstance() 
    Error:        (0x80040152) 
 
-------------------- 
[03/09/13 22:41:55] module: DXWSetup(Mar 30 2011), file: psheets.cpp, line: 680, function: PreinstDlgProc 
 
    CDXWSetup:downloadDXUpdate() failed. 
 
-------------------- 
[03/09/13 22:42:11] module: DXWSetup(Mar 30 2011), file: dxwsetup.cpp, line: 72, function: CDXWSetup::CDXWSetup 
 
    Failed API:        CoCreateInstance() 
    Error:        (0x80040152) 
 
-------------------- 
[03/09/13 22:42:11] module: DXWSetup(Mar 30 2011), file: dxupdate.cpp, line: 431, function: CDXWSetup:downloadDXUpdate 
 
    Failed API:        CoCreateInstance() 
    Error:        (0x80040152) 
 
-------------------- 
[03/09/13 22:42:11] module: DXWSetup(Mar 30 2011), file: psheets.cpp, line: 680, function: PreinstDlgProc 
 
    CDXWSetup:downloadDXUpdate() failed. 
 
-------------------- 
[03/09/13 22:49:28] module: DXWSetup(Mar 30 2011), file: dxwsetup.cpp, line: 72, function: CDXWSetup::CDXWSetup 
 
    Failed API:        CoCreateInstance() 
    Error:        (0x80040152) 
 
-------------------- 
[03/09/13 22:49:28] module: DXWSetup(Mar 30 2011), file: dxupdate.cpp, line: 431, function: CDXWSetup:downloadDXUpdate 
 
    Failed API:        CoCreateInstance() 
    Error:        (0x80040152) 
 
-------------------- 
[03/09/13 22:49:28] module: DXWSetup(Mar 30 2011), file: psheets.cpp, line: 680, function: PreinstDlgProc 
 
    CDXWSetup:downloadDXUpdate() failed. 
 
-------------------- 
[03/09/13 23:04:11] module: DXWSetup(Mar 30 2011), file: dxwsetup.cpp, line: 72, function: CDXWSetup::CDXWSetup 
 
    Failed API:        CoCreateInstance() 
    Error:        (0x80040152) 
 
-------------------- 
[03/09/13 23:04:11] module: DXWSetup(Mar 30 2011), file: dxupdate.cpp, line: 431, function: CDXWSetup:downloadDXUpdate 
 
    Failed API:        CoCreateInstance() 
    Error:        (0x80040152) 
 
-------------------- 
[03/09/13 23:04:11] module: DXWSetup(Mar 30 2011), file: psheets.cpp, line: 680, function: PreinstDlgProc 
 
    CDXWSetup:downloadDXUpdate() failed.

---

### Post by 3rdalbum on 2013-03-10
Wine already comes with its own implementation of Direct X. You can't use the official Microsoft one on Wine because there is no Windows kernel.

---

### Post by MikeCyber on 2013-03-10
Personally I've installed DX that came with Wolfenstein CD and works perfectly. But try winetricks and make sure to select only the right DX. Last time I've looked it showed lots of antique DX versions....

---

### Post by Hydera5 on 2013-03-10
> **3rdalbum said:**
> Wine already comes with its own implementation of Direct X. You can't use the official Microsoft one on Wine because there is no Windows kernel.

When i try to run my program (OBS) it says i need a DirectX update for the program to work.

---

### Post by Shadowstripe on 2013-03-10
have you tried installing it with winetricks ?
winetricks d3dx9

---

### Post by Hydera5 on 2013-03-10
> **Shadowstripe said:**
> have you tried installing it with winetricks ?
winetricks d3dx9

So it looks like i got it installed with wine tricks but now another problem arises... when trying to install my program it says "Due to extensive use of DirectX10 features, the program requires Windows Vista SP2 or higher."  How do i go about getting the SP2 on here...

---

### Post by Shadowstripe on 2013-03-10
I don't remember where off the top of my head maybe its in winecfg but you can set what version of windows wine reports itself as

have you checked the app db to see if the program is listed and has comments/instructions on how to get it working under wine ?

[http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by Mark Phelps on 2013-03-11
> **Hydera5 said:**
> How do i go about getting the SP2 on here...

Sorry ... basically you don't. Wine is not an emulation of Windows, so you can't install Windows Updates or Service Packs.

---

