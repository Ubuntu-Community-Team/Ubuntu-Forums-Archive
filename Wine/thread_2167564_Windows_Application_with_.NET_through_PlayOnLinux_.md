---
title: "Windows Application with .NET through PlayOnLinux (WINE?) on Ubuntu 12.04 64bit"
date: 2013-08-14
forum: Wine
---

### Post by dwashere on 2013-08-14
**What do I want to do?**

  Run this software in Ubuntu 12.04: Achieve Planner by Effexis ([http://www.effexis.com/achieve/AchievePlanner19Download.htm](http://www.effexis.com/achieve/AchievePlanner19Download.htm)).
  [B]
What have I tried so far?[/B]

  
[LIST]
[*]Installed PlayOnLinux through Software Center 
[*](Tried to install .NET.  Did not work b/c of 64bit.  Did research, then moved on to the following steps.) 
[*]Installed Wine 1.7 and 1.6 (32bit) within PlayOnLinux using "Tools/Manage Wine Versions" 
[*]Installed .NET 1.1 (required by Achieve Planner) using the "Install" window's "Install a non-listed program" option. 
[*]Installed Achieve Planner the same way. 
[*]Tried this method: [http://askubuntu.com/questions/231587/installing-dotnet-2-0-on-64-bit-machine ]("http://askubuntu.com/questions/231587/installing-dotnet-2-0-on-64-bit-machine") 
[/LIST]
  [B]
Where am I now?[/B]

  Unable to launch Achieve Planner, and unable to interpret the error messages in the log file.
Also, the other method I tried (w/o PlayOnLinux), referenced above, did not get very far, and I got these error messages:

```
   
[FONT=Courier New][SIZE=2]joshua@acer-M5640-M3640:~$ WINEARCH=win32 WINEPREFIX=~/.win32 winecfg [/SIZE][/FONT]
 [FONT=Courier New][SIZE=2]wine: created the configuration directory '/home/joshua/.win32' [/SIZE][/FONT]
 [FONT=Courier New][SIZE=2]p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory [/SIZE][/FONT]
 [FONT=Courier New][SIZE=2]p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory [/SIZE][/FONT]
 [FONT=Courier New][SIZE=2]fixme:storage:create_storagefile Storage share mode not implemented. [/SIZE][/FONT]
 [FONT=Courier New][SIZE=2]err:mscoree:LoadLibraryShim error reading registry key for installroot [/SIZE][/FONT]
 [FONT=Courier New][SIZE=2]err:mscoree:LoadLibraryShim error reading registry key for installroot [/SIZE][/FONT]
 [FONT=Courier New][SIZE=2]err:mscoree:LoadLibraryShim error reading registry key for installroot [/SIZE][/FONT]
 [FONT=Courier New][SIZE=2]err:mscoree:LoadLibraryShim error reading registry key for installroot [/SIZE][/FONT]
 [FONT=Courier New][SIZE=2]err:mscoree:LoadLibraryShim error reading registry key for installroot [/SIZE][/FONT]
 [FONT=Courier New][SIZE=2]err:mscoree:LoadLibraryShim error reading registry key for installroot [/SIZE][/FONT]
 [FONT=Courier New][SIZE=2]fixme:iphlpapi:NotifyAddrChange (Handle 0xebe8cc, overlapped 0xebe8b0): stub [/SIZE][/FONT]
 [FONT=Courier New][SIZE=2]p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory [/SIZE][/FONT]

 [FONT=Courier New][SIZE=2]wine: configuration in '/home/joshua/.win32' has been updated. [/SIZE][/FONT]
 [FONT=Courier New][SIZE=2]p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory [/SIZE][/FONT]


```

I tried to do step 2 anyway, and got this:

```
   
[FONT=Courier New][SIZE=2]joshua@acer-M5640-M3640:~$ env WINEPREFIX=~/.wine32 winetricks dotnet20 [/SIZE][/FONT]
 [FONT=Courier New][SIZE=2]Executing w_do_call dotnet20 [/SIZE][/FONT]
 [FONT=Courier New][SIZE=2]Executing load_dotnet20 [/SIZE][/FONT]
 [FONT=Courier New][SIZE=2]Executing w_do_call fontfix [/SIZE][/FONT]
 [FONT=Courier New][SIZE=2]Executing load_fontfix [/SIZE][/FONT]
 [FONT=Courier New][SIZE=2]Setting Windows version to win2k [/SIZE][/FONT]
 [FONT=Courier New][SIZE=2]Executing winetricks_early_wine regedit C:\windows\Temp\_dotnet20\set-winver.reg [/SIZE][/FONT]
 [FONT=Courier New][SIZE=2]/usr/bin/winetricks: 4376: cd: can't cd to /home/joshua/.cache/winetricks/dotnet20 [/SIZE][/FONT]
 [FONT=Courier New][SIZE=2]Executing mkdir -p /home/joshua/.cache/winetricks/dotnet20 [/SIZE][/FONT]
 [FONT=Courier New][SIZE=2]Downloading http://kegel.com/wine/l_intl.zip to /home/joshua/.cache/winetricks/dotnet20 [/SIZE][/FONT]
 [FONT=Courier New][SIZE=2]--2013-08-14 11:31:08--  http://kegel.com/wine/l_intl.zip [/SIZE][/FONT]
 [FONT=Courier New][SIZE=2]Resolving kegel.com (kegel.com)... 216.92.86.126 [/SIZE][/FONT]
 [FONT=Courier New][SIZE=2]Connecting to kegel.com (kegel.com)|216.92.86.126|:80... connected. [/SIZE][/FONT]
 [FONT=Courier New][SIZE=2]HTTP request sent, awaiting response... 200 OK [/SIZE][/FONT]
 [FONT=Courier New][SIZE=2]Length: 1103 (1.1K) [application/zip] [/SIZE][/FONT]
 [FONT=Courier New][SIZE=2]Saving to: `l_intl.zip' [/SIZE][/FONT]
 
 [FONT=Courier New][SIZE=2]100%[================================================================>] 1,103       --.-K/s   in 0s       [/SIZE][/FONT]
 
 [FONT=Courier New][SIZE=2]2013-08-14 11:31:09 (218 MB/s) - `l_intl.zip' saved [1103/1103] [/SIZE][/FONT]
 
 [FONT=Courier New][SIZE=2]Executing unzip -o -q -d /home/joshua/.wine32/dosdevices/c:/windows/syswow64 l_intl.zip [/SIZE][/FONT]
 [FONT=Courier New][SIZE=2]Executing mkdir -p /home/joshua/.cache/winetricks/dotnet20 [/SIZE][/FONT]
 [FONT=Courier New][SIZE=2]Downloading http://download.microsoft.com/download/5/6/7/567758a3-759e-473e-bf8f-52154438565a/dotnetfx.exe to /home/joshua/.cache/winetricks/dotnet20 [/SIZE][/FONT]
 [FONT=Courier New][SIZE=2]--2013-08-14 11:31:09--  http://download.microsoft.com/download/5/6/7/567758a3-759e-473e-bf8f-52154438565a/dotnetfx.exe [/SIZE][/FONT]
 [FONT=Courier New][SIZE=2]Resolving download.microsoft.com (download.microsoft.com)... 2.21.243.50, 23.62.99.17, 2.21.243.49 [/SIZE][/FONT]
 [FONT=Courier New][SIZE=2]Connecting to download.microsoft.com (download.microsoft.com)|2.21.243.50|:80... connected. [/SIZE][/FONT]
 [FONT=Courier New][SIZE=2]HTTP request sent, awaiting response... 200 OK [/SIZE][/FONT]
 [FONT=Courier New][SIZE=2]Length: 23510720 (22M) [application/octet-stream] [/SIZE][/FONT]
 [FONT=Courier New][SIZE=2]Saving to: `dotnetfx.exe' [/SIZE][/FONT]
 
 [FONT=Courier New][SIZE=2]100%[================================================================>] 23,510,720   505K/s   in 1m 51s   [/SIZE][/FONT]
 
 [FONT=Courier New][SIZE=2]2013-08-14 11:33:00 (207 KB/s) - `dotnetfx.exe' saved [23510720/23510720] [/SIZE][/FONT]
 
 [FONT=Courier New][SIZE=2]Executing wine dotnetfx.exe [/SIZE][/FONT]
 [FONT=Courier New][SIZE=2]fixme:advapi:DecryptFileA "C:\\users\\joshua\\Temp\\IXP000.TMP\\" 00000000 [/SIZE][/FONT]
 [FONT=Courier New][SIZE=2]p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory [/SIZE][/FONT]
 [FONT=Courier New][SIZE=2]p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory [/SIZE][/FONT]
 [FONT=Courier New][SIZE=2]fixme:advapi:LsaOpenPolicy ((null),0x33f31c,0x00000001,0x33f344) stub [/SIZE][/FONT]
 [FONT=Courier New][SIZE=2]fixme:advapi:LsaClose (0xcafe) stub [/SIZE][/FONT]
 [FONT=Courier New][SIZE=2]------------------------------------------------------ [/SIZE][/FONT]
 [FONT=Courier New][SIZE=2]Note: command 'wine dotnetfx.exe' returned status 26.  Aborting. [/SIZE][/FONT]
 [FONT=Courier New][SIZE=2]------------------------------------------------------ [/SIZE][/FONT]


```

  **Background Info**

  
[LIST]
[*]Ubuntu 12.04 64bit 
[*]Acer Desktop M3640 | Intel® Core™2 Quad CPU Q6600 @ 2.40GHz x 4 | ATI Radeon HD 3650 | 3GB RAM 
[*]Thread on Ask Ubuntu: [http://askubuntu.com/questions/332107/windows-application-with-net-through-playonlinux-on-ubuntu-12-04-64bit-beginn](http://askubuntu.com/questions/332107/windows-application-with-net-through-playonlinux-on-ubuntu-12-04-64bit-beginn) 
[/LIST]
      

I am completely stuck, not being able to interpret the error messages I keep getting (either in Terminal or in Debugging mode of PlayOnLinux).  It might be something simple regarding 64bit vs. 32bit, but it's just way above my head right now.

Any ideas?

---

### Post by GwL3eNC on 2013-08-14
Hi,

i have also constalntly problems in understanding the messages. It say's that the file [FONT=Courier New][SIZE=2]gnome-keyring-pkcs11.so[/SIZE][/FONT]
could not found. Or? It should be in [FONT=Courier New][SIZE=2]/usr/lib/i386-linux-gnu/pkcs11[/SIZE][/FONT], have you looked there?

A Ubuntu package search [http://packages.ubuntu.com/](http://packages.ubuntu.com/) shows that the file is locate in a package  [libp11-kit-gnome-keyring]("http://packages.ubuntu.com/raring/libp11-kit-gnome-keyring") [TABLE]
[TR]
[TD="class: file"][/TD]
[TD]                   

[/TD]
[/TR]
[/TABLE]

---

