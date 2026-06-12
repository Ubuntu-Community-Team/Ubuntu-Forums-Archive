---
title: "Photoshop Elements 13"
date: 2015-03-27
forum: Wine
---

### Post by ndstate on 2015-03-27
Hello,

I cannot seem to find a way to install Photoshop Elements 13 via wine (an error pops up before the install begins). I have followed some guides for older version of Photoshop Elements, but they do not work. Anyone know how to get this installed or ways I could troubleshoot the install to figure it out?

Thanks

---

### Post by ndstate on 2015-03-29
In the terminal, if I run
WINEPREFIX=~/.wine32 wine "/media/b/PSE 13/Adobe Photoshop Elements 13/Setup.exe"

I get:

```
fixme:thread:GetThreadPreferredUILanguages 56, 0x33e038, 0x33e048 0x33e03c
fixme:module:load_library unsupported flag(s) used (flags: 0x00000060)
fixme:ver:GetCurrentPackageId (0x33dd44 (nil)): stub
fixme:console:AttachConsole stub ffffffff
Starting installer...
UI mode : Full GUI.
fixme:winhttp:WinHttpDetectAutoProxyConfigUrl discovery via DHCP not supported
fixme:wuapi:update_installer_get_IsBusy 
fixme:wuapi:update_installer_get_RebootRequiredBeforeInstallation 
fixme:shell:InitNetworkAddressControl stub
fixme:ver:GetCurrentPackageId (0xace21c (nil)): stub
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
err:secur32:schan_free_handle Handle 1(0x1a17b0) is not of type 0x1
fixme:ver:GetCurrentPackageId (0x33dfb4 (nil)): stub
fixme:ver:GetCurrentPackageId (0x33de6c (nil)): stub
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ole:RemUnknown_QueryInterface No interface for iid {00000019-0000-0000-c000-000000000046}
fixme:winediag:AUDDRV_GetAudioEndpoint Winepulse is not officially supported by the wine project
fixme:winediag:AUDDRV_GetAudioEndpoint For sound related feedback and support, please visit http://ubuntuforums.org/showthread.php?t=1960599
fixme:winsock:WSAIoctl -> SIO_ADDRESS_LIST_CHANGE request: stub
fixme:winsock:WSAIoctl -> SIO_ADDRESS_LIST_CHANGE request: stub
err:secur32:schan_free_handle Handle 1(0x1a17b0) is not of type 0x1
fixme:ver:GetCurrentPackageId (0x33b71c (nil)): stub
Exiting Installer with Code: 0
b@bLenovo:~$ fixme:imm:ImmReleaseContext (0x100a2, 0x1e3f728): stub
fixme:msvcrt:__clean_type_info_names_internal (0x3e9c80) stub
fixme:msvcrt:__clean_type_info_names_internal (0x10006510) stub
```

Any ideas? Thanks

---

### Post by ndstate on 2015-04-05
Can anyone help? Thanks.

---

### Post by Mike_Walsh on 2015-04-14
Hallo, pmp6nl.

I rather think you'll find that the vast majority of Adobe's products are next to impossible to install, due to the very high proportion of 'secret' proprietary coding that they contain. Adobe and Microsoft have been in each other's back pockets for so long, that they're not about to start trying to make life easier for those non-Windows users amongst us.....

Regards,

Mike. ;)

---

