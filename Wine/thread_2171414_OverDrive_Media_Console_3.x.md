---
title: "OverDrive Media Console 3.x"
date: 2013-08-30
forum: Wine
---

### Post by temporos on 2013-08-30
There's a new version of Overdrive Media Console (OMC) out which does not require Adobe Digital Editions to check out e-books from the library. Users of the old OMC are being forced to upgrade in order to continue borrowing books from the public library.

The new version of OMC (3.x) does not install in Wine like the previous version (2.x) did. The only mention I've found of a successful install was from the [WineHQ]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=14894&iTestingId=80042") site.

[quote=WineHQ]
Needed to do the following to get the installer to work:

[LIST=1]
[*]Create a 32-bit Wine Prefix: ```
WINEPREFIX='/home//.wine-32' WINEARCH='win32' wine 'wineboot'
```
[*]Install WMP9: ```
WINEPREFIX='/home//.wine-32' winetricks wmp9
```
[*]Run the installer in our 32-bit Wineprefix (note, I previously had Z: mapped to my linux root in Wine Config): ```
WINEPREFIX='/home//.wine-32' wine msiexec /i "Z:\home\\Downloads\ODMediaConsoleSetup.msi"
```
[/LIST]
[/quote]

Is this talking about putting those WINEPREFIX lines into a bash file? What's he doing, exactly? Also, how can I find my linux root directory in the Wine config utility? "/root" doesn't show up in the list. Do I need to do everything under sudo?

---

### Post by temporos on 2013-11-24
... Anyone?

---

### Post by ElsieMariah on 2014-04-20
I just got Overdrive media console to install, it was a pain because it now has an msi ending. 

I tried a lot of things that didn't work but I think this is the path that did

If you don't already have the most recent version of windows media player on your system install it with winetricks from terminal with the following code

[FONT=courier new]winetricks wmp10
[/FONT]
If you don't have winetricks you can install it using the instructions on this website, [https://code.google.com/p/winetricks/wiki/Installing](https://code.google.com/p/winetricks/wiki/Installing)

Now load the msi file with the following code in terminal
[FONT=courier new]
[/FONT][FONT=courier new]wine msiexec /i [file path]/ODMediaConsoleSetup.msi[/FONT]

Hopefully that works for you.

---

### Post by cmcanulty on 2014-11-06
I get a pile of errors with those commands it seems to not like 64 bit which is odd as most win computers have been 64bit for years
```

cmcanulty@ubuntu1:~$ winetricks wmp10
------------------------------------------------------
You are using a 64-bit WINEPREFIX. If you encounter problems, please retest in a clean 32-bit WINEPREFIX before reporting a bug.
------------------------------------------------------
Executing w_do_call wmp10
Executing load_wmp10
------------------------------------------------------
Installer doesn't support 64-bit architecture. Use a 32-bit WINEPREFIX instead.
------------------------------------------------------
cmcanulty@ubuntu1:~$ WINEPREFIX='/home//.wine-32' WINEARCH='win32' wine 'wineboot'
wine: '/home/' is not owned by you, refusing to create a configuration directory there
cmcanulty@ubuntu1:~$ sudo WINEPREFIX='/home//.wine-32' WINEARCH='win32' wine 'wineboot'
[sudo] password for cmcanulty: 
wine: created the configuration directory '/home//.wine-32'
fixme:storage:create_storagefile Storage share mode not implemented.
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
fixme:storage:create_storagefile Storage share mode not implemented.
fixme:iphlpapi:NotifyAddrChange (Handle 0x10ee890, overlapped 0x10ee89c): stub
wine: configuration in '/home//.wine-32' has been updated.
cmcanulty@ubuntu1:~$ WINEPREFIX='/home//.wine-32' winetricks wmp9
------------------------------------------------------
wine cmd.exe /c echo '%ProgramFiles%' returned empty string
------------------------------------------------------
cmcanulty@ubuntu1:~$ WINEPREFIX='/home//.wine-32' wine msiexec /i "Z:\home\\Downloads\ODMediaConsoleSetup.msi"
wine: /home//.wine-32 is not owned by you
cmcanulty@ubuntu1:~$ sudo WINEPREFIX='/home//.wine-32' wine msiexec /i "Z:\home\\Downloads\ODMediaConsoleSetup.msi"
cmcanulty@ubuntu1:~$ winetricks wmp10
------------------------------------------------------
You are using a 64-bit WINEPREFIX. If you encounter problems, please retest in a clean 32-bit WINEPREFIX before reporting a bug.
------------------------------------------------------
Executing w_do_call wmp10
Executing load_wmp10
------------------------------------------------------
Installer doesn't support 64-bit architecture. Use a 32-bit WINEPREFIX instead.
------------------------------------------------------
cmcanulty@ubuntu1:~$ wine msiexec /i [file path]/ODMediaConsoleSetup.msi
err:service:service_send_start_message service L"BackupStack" failed to start
fixme:service:scmdatabase_autostart_services Auto-start service L"BackupStack" failed to start: 1053
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:process:SetProcessDEPPolicy (3): stub
fixme:ver:GetCurrentPackageId (0x11ae9c8 (nil)): stub
cmcanulty@ubuntu1:~$ fixme:advapi:LsaOpenPolicy ((null),0xe9df90,0x00000800,0xe9df60) stub
fixme:advapi:LsaLookupNames (0xcafe,0x00000001,0xe9df6c,0xe9df5c,0xe9df64) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:winsock:convert_proto_w2u unhandled Windows socket protocol 4
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER: unimplemented TransmitFile
fixme:ntdll:NtQuerySection (0x124,0,0xe9de68,0x00000010,(nil)) stub!
fixme:process:WTSGetActiveConsoleSessionId stub
fixme:process:WTSGetActiveConsoleSessionId stub
fixme:wtsapi:WTSEnumerateSessionsW Stub (nil) 0x00000000 0x00000001 0xe9e030 0xe9e044
fixme:wtsapi:WTSFreeMemory Stub (nil)
fixme:process:WTSGetActiveConsoleSessionId stub
fixme:process:WTSGetActiveConsoleSessionId stub
fixme:wtsapi:WTSEnumerateSessionsW Stub (nil) 0x00000000 0x00000001 0xe9e6e0 0xe9e6f4
fixme:wtsapi:WTSFreeMemory Stub (nil)
fixme:ole:RemUnknown_QueryInterface No interface for iid {00000019-0000-0000-c000-000000000046}
err:ole:CoReleaseMarshalData IMarshal::ReleaseMarshalData failed with error 0x8001011d

```

---

