---
title: "How to: install .net framework 2.0 in ubuntu using wine"
date: 2008-10-10
forum: Wine
---

### Post by G_man on 2008-10-10
1- set Windows 2000 as your default app in wine config.

2- In teminal enter these lines one by one:
```
wget http://kegel.com/wine/winetricks
```
```
sh winetricks corefonts dotnet20
```
```
sh winetricks fakeie6
```


*- If you got an error about c://windows/ does not exist try to mount your drives
(This is general to all app. if you installed fake windows file in another drive)

This is for shark so that he does not ask me again every time he installs it :)

---

### Post by YokoZar on 2008-10-10
Would you mind pointing me to a downloadable app that needs this?  I want to test if the new Mono 2 can work as a replacement.

---

### Post by tc101 on 2008-10-11
You could try SQL Server Express

[http://www.microsoft.com/express/2005/sql/download/](http://www.microsoft.com/express/2005/sql/download/)

And please tell me if it works, because I may be using it soon.

---

### Post by Oceanwatcher on 2008-10-11
I tried RSS Bandit.

.net 2.0 installed fine.
RSS Bandit installed fine.

Tried starting RSS Bandit. It got as far as teh splash screen saying it was going to load the main GUI. Splash went away and nothing more happened.

Suspect it has to do with RSS Bandit using an embedded IE. My guess only. Would love to see it work. Or find a way to run RSS Bandit on Mono..

---

### Post by qwertymn on 2008-10-12
> I tried RSS Bandit.

.net 2.0 installed fine.
RSS Bandit installed fine.

Tried starting RSS Bandit. It got as far as teh splash screen saying it was going to load the main GUI. Splash went away and nothing more happened.

Suspect it has to do with RSS Bandit using an embedded IE. My guess only. Would love to see it work. Or find a way to run RSS Bandit on Mono..

I tried that Rss Bandit app. It also seems to suffer from bug 

[http://bugs.winehq.org/show_bug.cgi?id=13462](http://bugs.winehq.org/show_bug.cgi?id=13462)

as many other .net 2.0 applications do

I f you want to get it running you could try the two patches
[http://www.winehq.org/pipermail/wine-patches/attachments/20080928/93d2b9ce/attachment.txt](http://www.winehq.org/pipermail/wine-patches/attachments/20080928/93d2b9ce/attachment.txt)

and 

[http://bugs.winehq.org/attachment.cgi?id=16397](http://bugs.winehq.org/attachment.cgi?id=16397)

applied on top of each other. Then the app starts for me, but it seems to have some menu-issues, and i'm not sure if it's usable, don't know really how the app works

---

### Post by tom2oo8 on 2009-02-09
> fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
err:ole:CoInitializeEx Attempt to change threading model of this apartment from apartment threaded to multi-threaded
err:ole:CoUninitialize Mismatched CoUninitialize
fixme:msi:msi_unimplemented_action_stub MsiUnpublishAssemblies -> 2 ignored L"MsiAssembly" table values
err:rpc:I_RpcGetBuffer no binding
err:rpc:I_RpcGetBuffer no binding
err:rpc:I_RpcGetBuffer no binding
fixme:msi:msi_unimplemented_action_stub DeleteServices -> 4 ignored L"ServiceControl" table values
fixme:msi:msi_unimplemented_action_stub RemoveRegistryValues -> 4 ignored L"RemoveRegistry" table values
fixme:msi:msi_unimplemented_action_stub RemoveDuplicateFiles -> 7 ignored L"DuplicateFile" table values
fixme:msi:msi_unimplemented_action_stub RemoveFolders -> 16 ignored L"CreateFolder" table values
err:msi:msi_cabextract FDICopy failed
err:msi:ACTION_InstallFiles Failed to extract cabinet: L"#_13017_URTM_STD_ENU_X86_IXP.MSM"
err:msi:ITERATE_Actions Execution halted, action L"InstallFinalize" returned 1627
Note: command 'wine /home/tom/.winetrickscache/dotnet20/dotnetfx.exe' returned status 91.  Aborting.
tom@tom-desktop:~$ fixme:imm:ImmDisableIME (-1): stub
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
fixme:richedit:ME_HandleMessage EM_SETMARGINS: stub
fixme:richedit:ME_HandleMessage EM_SETMARGINS: stub
err:ole:CoUninitialize Mismatched CoUninitialize
err:ole:CoUninitialize Mismatched CoUninitialize


I get this when i try to istall :S? Anyone got any ideas on how to fix this?


Oh wait.. ill try again as i think its beciuase i didnt set win 2k as my default :P --- edit: ok that didnt help either.. same error

---

### Post by cardpogi on 2009-03-18
Im getting this same error I'm on the Linux4one, coming from Hardy, anyone have an idea on how to solve this please? I'm trying to install MS-Office and need the .Net Framework

---

### Post by NetFreeDiver on 2009-04-28
Hi,

I applied both steps and I have difficulty with permission. If I pur sudo infront it gives an error that .wine is not owned by the user (root), which is true :)
I gave permission of writing and reading on .wine (including folders beneath) for everyone. Still didn't work.

Would you please sugest me what to do.

Thanks in advence,

Net_Free_Diver

---

### Post by asdfoo on 2009-04-29
> **NetFreeDiver said:**
> Hi,

I applied both steps and I have difficulty with permission. If I pur sudo infront it gives an error that .wine is not owned by the user (root), which is true :)
I gave permission of writing and reading on .wine (including folders beneath) for everyone. Still didn't work.

Would you please sugest me what to do.

Thanks in advence,

Net_Free_Diver

try with a clean prefix.. don't use sudo.

mv ~/.wine ~/.wine-old
sh winetricks dotnet20

---

### Post by caryb on 2009-07-30
Thanks for that I now have Citrix xencentre 5.5 working:) last thing needed to dewindowfy my life!


Cary

---

### Post by dunk on 2009-08-14
Hi, I've tried installing .net 2.0 and I get the following error message, can anyone shed any light??

> Executing cabextract -q --directory=/home/dpratchett/.wine/drive_c/winetrickstmp /home/dpratchett/.winetrickscache/arial32.exe
winetricks: 2178: cabextract: not found
Note: command 'cabextract -q --directory=/home/dpratchett/.wine/drive_c/winetrickstmp /home/dpratchett/.winetrickscache/arial32.exe' returned status 127.  Aborting.
dpratchett@dpratchett-ubuntu:~$ sh winetricks corefonts dotnet20
Cannot find cabextract.  Please install it (e.g. 'sudo apt-get install cabextract' or 'sudo yum install cabextract').
Executing cabextract -q --directory=/home/dpratchett/.wine/drive_c/winetrickstmp /home/dpratchett/.winetrickscache/arial32.exe
winetricks: 2178: cabextract: not found
Note: command 'cabextract -q --directory=/home/dpratchett/.wine/drive_c/winetrickstmp /home/dpratchett/.winetrickscache/arial32.exe' returned status 127.  Aborting.


Cheers
Dunk

---

### Post by NightMKoder on 2009-08-14
sudo apt-get install cabextract

---

### Post by X1R1 on 2009-12-01
Imn going to install this along with solarwinds IP address tracker and see if it works out, I will come back with results.

thanks for sharing :D

---

### Post by rfrey74 on 2010-03-06
Tried this, but it complains that I do not have Microsoft Installer 3.0 installed.  Any suggestion on that?

---

### Post by JosueAquino on 2010-04-07
WOw ya me instale El framwrok 2.0 gracias, aki desde la comunidad ubuntu el  salvador.

___________
Wow i have installed the framework 2.0 thanks, from here the communitty Ubuntu El Salvador!!:guitar::guitar::guitar::guitar::lolflag::lolflag::lolflag:

---

### Post by GiuseppeP on 2010-07-10
I have this error @ sh winetricks corefonts dotnet20
```

Executing /usr/bin/cabextract -q --directory=/home/utente/.wine/dosdevices/c:/winetrickstmp /home/utente/.winetrickscache/arial32.exe
/home/utente/.wine/dosdevices/c:/winetrickstmp/FONTINST.EXE: Permission denied
/home/utente/.wine/dosdevices/c:/winetrickstmp/fontinst.inf: Permission denied
/home/utente/.wine/dosdevices/c:/winetrickstmp/Ariali.TTF: Permission denied
/home/utente/.wine/dosdevices/c:/winetrickstmp/Arialbd.TTF: Permission denied
/home/utente/.wine/dosdevices/c:/winetrickstmp/Arialbi.TTF: Permission denied
/home/utente/.wine/dosdevices/c:/winetrickstmp/Arial.TTF: Permission denied

```

and @ sh winetricks fakeie6winetricks
```

utente@LidiaPC:~$ sh winetricks fakeie6winetricks: 4081: cannot create /home/utente/.wine/dosdevices/c:/winetrickstmp/fakeie6.reg: Permission denied
winetricks: 4081: cannot create /home/utente/.wine/dosdevices/c:/winetrickstmp/fakeie6.reg: Permission denied
winetricks: 4081: cannot create /home/utente/.wine/dosdevices/c:/winetrickstmp/fakeie6.reg: Permission denied
winetricks: 4081: cannot create /home/utente/.wine/dosdevices/c:/winetrickstmp/fakeie6.reg: Permission denied
winetricks: 4081: cannot create /home/utente/.wine/dosdevices/c:/winetrickstmp/fakeie6.reg: Permission denied
winetricks: 4081: cannot create /home/utente/.wine/dosdevices/c:/winetrickstmp/fakeie6.reg: Permission denied
winetricks: 4081: cannot create /home/utente/.wine/dosdevices/c:/winetrickstmp/fakeie6.reg: Permission denied
Executing early_wine regedit c:\winetrickstmp
                                             akeie6.reg
regedit: File not found "c:\winetrickstmp\fakeie6.reg" (2)
------------------------------------------------------
Note: command 'early_wine regedit c:\winetrickstmp
                                                  akeie6.reg' returned status 1.  Aborting.
------------------------------------------------------

```

---

### Post by psychok7 on 2010-08-19
will i be able to install Windows C# developed applications if a install .net?

---

### Post by tunist on 2010-12-01
i've been attempting to get philips vlounge to install via wine..
and it requires dotnet2.0.
i got wine to install dotnet2.0 without any glitches using the supplied command line texts..

however, the vlounge installer is still producing an error msg about needing dotnet to be installed..

does anyone have any idea why this might be?
thanks

---

### Post by dwdarkstar on 2011-01-19
hello, i have Wine 1.0.1 running on Ubuntu 9.10 and i'm having trouble with the last step in this guide, the output is given below.  my ultimate goal is the instillation/operation of software to control a Quakko Programmable Bench-top Power Supply.  

```
Install of dotnet20 done
winetricks done.

farstar@go-bot-lab:~$ sh winetricks fakeie6

fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\windows\\Microsoft.NET\\Framework\\v2.0.50727\\mscorsvw.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\Microsoft.NET\\Framework\\v2.0.50727\\mscorsvw.exe" failed, status c0000135
Unknown arg fakeie6
Usage: winetricks [options] package [package] ...
This script can help you prepare your system for Windows applications
that mistakenly assume all users' systems have all the needed
redistributable runtime libraries or fonts.
Some options require the Linux 'cabextract' program.

Options:
 -q         quiet.  You must have already agreed to the EULAs.
 -v         verbose
 -V         display Version
Packages:
 7zip          7-zip file archiver
 adobeair      Adobe AIR runtime
 amstream      MS amstream.dll
 art2kmin      MS Access 2007 runtime

```


pressing on with the P/S software instillation despite the fakeie trouble yields the following after installing the USB driver:

```
farstar@go-bot-lab:~/Desktop$ wine USB_CP2102_XP_2000.exe 
fixme:advapi:LookupAccountNameW (null) L"farstar" (nil) 0x33f864 (nil) 0x33f868 0x33f85c - stub
fixme:advapi:LookupAccountNameW (null) L"farstar" 0x134e78 0x33f864 0x130db8 0x33f868 0x33f85c - stub
fixme:msi:ControlEvent_HandleControlEvent unhandled control event L"Reinstall" arg(L"ALL")
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:advapi:CheckTokenMembership ((nil) 0x1901e8 0x7ed194e0) stub!
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:crypt:CertAddEncodedCTLToStore (0x19f430, 00000001, 0x19f530, 9225, 00000004, 0x7ed19290): stub
err:msi:ITERATE_Actions Execution halted, action L"InstallFinalize" returned 1603
err:msi:ITERATE_Actions Execution halted, action L"ExecuteAction" returned 1603

```

installing the actual software program yields:

```
farstar@go-bot-lab:~/Desktop$ wine DPS_Setup.exe 
fixme:shell:IPersistFile_fnGetCurFile (0x169e88)
fixme:shell:IPersistFile_fnGetCurFile (0x16a710)
fixme:shell:IPersistFile_fnGetCurFile (0x16a710)
fixme:shell:IPersistFile_fnGetCurFile (0x16ad28)
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub

```

finally, attempting to run the power supply control program from terminal results in:

```
farstar@go-bot-lab:~/.wine/drive_c/Program Files/DPS/DPS 32V5A Software$ wine CAPDPScontrol.exe 
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\windows\\Microsoft.NET\\Framework\\v2.0.50727\\mscorwks.dll") not found

```

Along with this error box: **C:\windows\Microsoft.NET\Framework\v2.0.50727\mscorwks.dll could not be loaded**

any ideas...?  thanxs!

---

### Post by KrisDouglas on 2011-02-11
I have a question, someone above managed to get xenserver working properly. When I run it, first the installer tells me that .net 2.0 is not installed (even though it is, through winetricks)

I then moved the files from another windows XP pc and it crashes 

```
2011-02-11 16:23:09,605 ERROR XenAdmin.Core.NamedPipes+Pipe [Named pipe thread] - Error in named pipe thread.
System.ComponentModel.Win32Exception: ConnectNamedPipe failed ---> System.ComponentModel.Win32Exception: Invalid handle
   --- End of inner exception stack trace ---
   at XenAdmin.Core.NamedPipes.Pipe.BackgroundPipeThread()
```

I have tried registering the libs that xencentre uses, without avail. I was just wondering if anyone had any tips?

---

