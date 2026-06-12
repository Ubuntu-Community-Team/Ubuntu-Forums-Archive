---
title: "dotnet2.0"
date: 2011-10-05
forum: Wine
---

### Post by N1CKY on 2011-10-05
This is driving me absolutely crazy, Dotnet2.0 will not install using winetricks. 

Output:

```
Instaling .net 2.0 runtime.  Can take several minutes.  See http://wiki.winehq.org/MicrosoftDotNet for tips.
------------------------------------------------------
prerequisite gecko already installed, skipping
DELETE - HKLM\Software\Microsoft\Windows\CurrentVersion SubVersionNumber 0 0 1
Error: The system was unable to find the specified registry key or value
DELETE - HKLM\Software\Microsoft\Windows\CurrentVersion VersionNumber 0 0 1
Error: The system was unable to find the specified registry key or value
DELETE - HKLM\Software\Microsoft\Windows NT\CurrentVersion CSDVersion 0 0 1
The operation completed successfully
DELETE - HKLM\Software\Microsoft\Windows NT\CurrentVersion CurrentBuildNumber 0 0 1
The operation completed successfully
DELETE - HKLM\Software\Microsoft\Windows NT\CurrentVersion CurrentVersion 0 0 1
The operation completed successfully
DELETE - HKLM\System\CurrentControlSet\Control\ProductOptions ProductType 0 0 1
Error: The system was unable to find the specified registry key or value
DELETE - HKLM\System\CurrentControlSet\Control\ServiceCurrent OS 0 0 1
Error: The system was unable to find the specified registry key or value
DELETE - HKLM\System\CurrentControlSet\Control\Windows CSDVersion 0 0 1
The operation completed successfully
DELETE - HKCU\Software\Wine Version 0 0 1
Error: The system was unable to find the specified registry key or value
Setting Windows version to win2k
Executing early_wine regedit c:\winetrickstmp\set-winver.reg
Executing cp -f /home/nicky/.cache/winetricks/dotnet20/l_intl.nls /home/nicky/.wine/dosdevices/c:/windows/system32
DELETE - HKLM\Software\Microsoft\.NETFramework\policy\v2.0 (null) 0 0 1
Error: The system was unable to find the specified registry key or value
DELETE - HKLM\Software\Microsoft\.NETFramework InstallRoot 0 0 1
Error: The system was unable to find the specified registry key or value
Executing wine /home/nicky/.cache/winetricks/dotnet20/dotnetfx.exe
fixme:advapi:DecryptFileA "C:\\users\\nicky\\Temp\\IXP000.TMP\\" 00000000
fixme:advapi:LsaOpenPolicy ((null),0x33f33c,0x00000001,0x33f364) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:storage:create_storagefile Storage share mode not implemented.
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x451d7c
------------------------------------------------------
Note: command 'wine /home/nicky/.cache/winetricks/dotnet20/dotnetfx.exe' returned status 5.  Aborting.
------------------------------------------------------
------------------------------------------------------
dotnet20 failed
------------------------------------------------------

```What is happening here ? Please can someone help ?

Ubuntu 10.10 
Using latest Wine, 1.2.3 i believe.

Looking forward to a response.

Thanks in advance,

Nicky

---

### Post by ubupirate on 2011-10-05
Maybe try downloading .NET 2.0 from Microsoft website itself and install it directly with Wine and not winetricks.

[http://www.microsoft.com/download/en/details.aspx?id=19](http://www.microsoft.com/download/en/details.aspx?id=19)

---

### Post by Tweak42 on 2011-10-06
Have you tried installing using the latest Wine 1.3.x?

---

### Post by siwmper on 2011-12-04
I'm also having the same problem running Ubuntu 11.10, wine-1.3.28.

I've tried uninstalling and reinstalling wine, moving the .wine folder to force a new one to be created,  installing .Net 1.1 first, etc.

On first attempt with a clean profile I get errors like this:

```
err:module:find_forwarded_export function not found for forward 'msvcrt._vswprintf_c_l' used by L"C:\\windows\\system32\\msvcr80.dll". If you are using builtin L"msvcr80.dll", try using the native one instead.
wine: Call from 0x6832b418 to unimplemented function msvcrt.dll._set_printf_count_output, aborting
err:module:find_forwarded_export module not found for forward 'msvcr90.__clean_type_info_names_internal' used by L"C:\\windows\\system32\\msvcr80.dll"
err:module:find_forwarded_export function not found for forward 'msvcrt.wcscpy_s' used by L"C:\\windows\\system32\\msvcr80.dll". If you are using builtin L"msvcr80.dll", try using the native one instead.
```and then after that

```
fixme:storage:create_storagefile Storage share mode not implemented.
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x451d7c
------------------------------------------------------
Note: command 'wine dotnetfx.exe' returned status 5.  Aborting.
------------------------------------------------------
```I've tried installing dotnet20 both directly from downloading it from the MS website and via winetricks, and the result is the same.

Any new ideas?

---

### Post by siwmper on 2011-12-04
Fixed by updating wine to wine-1.3.34

---

### Post by AlwaysLearning on 2011-12-16
Already running wine-1.3.34 here. I started getting this error tonight when I went to play the new version of Terraria:

[INDENT]Please set registry key HKLM\Software\Microsoft\.NETFramework\InstallRoot to point to the .NET Framework install location[/INDENT]

And then I got these errors when trying to run a .NET Repair via winetricks dotnet20/dotnet30/dotnet35:

[INDENT]Note: command 'wine dotnetfx.exe' returned status 5.  Aborting.[/INDENT]

It would seem that another Steam game installed recently also added Mono 2.8 and 2.10 and has somehow broken my .NET configuration. Oh, the task ahead... :(

HTH.

---

