---
title: "DC Universe Online"
date: 2014-08-05
forum: Wine
---

### Post by nicholas15 on 2014-08-05
Hello Ubuntu World.
I'm a relatively nouveau to the Linux world of it all and I'm trying to get DC universe online to run through WINE. I'm having trouble in that everytime I try to install it, I get this nasty little message: 
> An internal system error has occured
Please refer to DXError.log and Directx.log in your
Windows folder to determine problem.

My DXError.log reads:
> -------------------- 
[08/05/14 20:17:46] module: DXWSetup(Jun  2 2010), file: dxwsetup.cpp, line: 65, function: CDXWSetup::CDXWSetup 
 
    Failed API:        CoCreateInstance() 
    Error:        (0x80040152) 
 
-------------------- 
[08/05/14 20:17:46] module: DXWSetup(Jun  2 2010), file: dxupdate.cpp, line: 431, function: CDXWSetup::DownloadDXUpdate 
 
    Failed API:        CoCreateInstance() 
    Error:        (0x80040152) 
 
-------------------- 
[08/05/14 20:17:46] module: DXWSetup(Jun  2 2010), file: psheets.cpp, line: 447, function: PreinstDlgProc 
 
    CDXWSetup::DownloadDXUpdate() failed. 



and my DirectX.log reads:
> 08/05/14 20:17:40: DXWSetup: ***** DXWSETUP ***** 
08/05/14 20:17:40: DXWSetup: WinMain() 
08/05/14 20:17:40: DXWSetup: IsIA64(): not IA64. 
08/05/14 20:17:41: DXWSetup: Unable to get Version on target file C:\windows\system32\directx\websetup\dsetup.dll 
08/05/14 20:17:41: DXWSetup: Installed file C:\windows\system32\directx\websetup\dsetup.dll 
08/05/14 20:17:41: DXWSetup: Unable to get Version on target file C:\windows\system32\directx\websetup\dsetup32.dll 
08/05/14 20:17:41: DXWSetup: Installed file C:\windows\system32\directx\websetup\dsetup32.dll 
08/05/14 20:17:41: DXWSetup: GetDXVersion(): Unable to get RC string from registry. 
08/05/14 20:17:41: DXWSetup: DirectX Version: 4.09.00.0904.00 
08/05/14 20:17:41: DXWSetup: Setup Version: 4.09.00.0904.00 
08/05/14 20:17:41: DXWSetup: A newer version of DirectX have been installed already. 
08/05/14 20:17:41: dsetup32: IsWow64(): not Wow64 process. 
08/05/14 20:17:46: DXWSetup: CDXWSetup::CDXWSetup() 
08/05/14 20:17:46: DXWSetup: CDXWSetup::CDXWSetup(): CoCreateInstance() failed, error = 0x80040152. 
08/05/14 20:17:46: DXWSetup: DXSError(): FormatMessage() failed, system cannot find message text for error. 
08/05/14 20:17:46: DXWSetup: CDXWSetup::DownloadDXUpdate() 
08/05/14 20:17:46: DXWSetup: CDXWSetup::DownloadDXUpdate(): CoCreateInstance() failed, error = 0x80040152. 
08/05/14 20:17:46: DXWSetup: DXSError(): FormatMessage() failed, system cannot find message text for error. 
08/05/14 20:17:46: DXWSetup: PreinstDlgProc(): CDXWSetup::DownloadDXUpdate() failed. 
08/05/14 20:17:46: DXWSetup: WM_APP_ENDDOWNLOAD

I really have no idea what I'm doing, and I have been looking online for about two days now looking for answers. Alot of general statment about winetricks and Play on Linux, but nothing that seems to work. ANY help is appreciated.

---

### Post by Mark Phelps on 2014-08-06
Here's a link to the WineHQ page for that (hope your case isn't the last one listed): [http://appdb.winehq.org/objectManager.php?sClass=application&iId=12620]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=12620")

---

### Post by nicholas15 on 2014-08-06
[INDENT]                                          I'm using PoL to install DC universe online and I've gotten through  initial setup but when ever I get to the loading screen,before I can  even log in it give me this error:> 
                           [INDENT]“There is not enough memory for this game (992MB)”[/INDENT]
     
Any help for a poor gamer?
Ubuntu 14.04
PoL 4.04
Wine 1.5.4(?)
Harddrive 80GB
Ram 512Mb                 
[/INDENT]

---

