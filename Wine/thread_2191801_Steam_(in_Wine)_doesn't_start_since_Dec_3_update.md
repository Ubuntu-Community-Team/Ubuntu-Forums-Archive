---
title: "Steam (in Wine) doesn't start since Dec 3 update"
date: 2013-12-04
forum: Wine
---

### Post by Ranko Kohime on 2013-12-04
I'm doing some sleuthing for a less than computer-literate friend of mine, and his Steam client would not start.  Judging from the timing he reported, (he's on his favorite game nearly every day, and sometimes several times throughout the day), it coincides with the Dec 3rd update.  Which I'm not sure which update it was, because I thought he was NOT in the beta, while my Windows box got the same update, and is in the beta.

He has an acer something or other with an Ivy Bridge i3, running Ubuntu 12.04.  Wine version should be the latest in the main Ubuntu repos, I don't believe he has the Wine PPA enabled.  When starting up Steam, it asks for the password, (despite the "save password" checkbox being ticked), and shows the "logging into account xxxxx" dialog, which then disappears, and spamming "ps aux" shows that the wineserver shuts down about 5 seconds later.

Please note, this is about a system that was working fine, and all of a sudden quit working in tune to this update.  Just so there's no confusion.  :)

I'm asking to see if anyone else experienced an issue with Steam on this same update, and if anyone has a possible fix.  Terminal vomit follows, of course.

```
fixme:exec:SHELL_execute flags ignored: 0x00000100
fixme:exec:SHELL_execute flags ignored: 0x00004100
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
[2013-12-03 23:39:28] Startup - updater built Dec  3 2013 18:35:30
fixme:advapi:EventRegister {47a9201e-73b0-42ce-9821-7e134361bc6f}, 0x3f005c90, 0x3f03ab30, 0x3f03ab28
fixme:advapi:EventRegister {58a9201e-73b0-42ce-9821-7e134361bc70}, 0x3f005c90, 0x3f03ab68, 0x3f03ab60
fixme:advapi:EventRegister {3fa9201e-73b0-43fe-9821-7e145359bc6f}, 0x3f005c90, 0x3f03aaf8, 0x3f03aaf0
fixme:advapi:EventRegister {1432afee-73b0-42ce-9821-7e134361b433}, 0x3f005c90, 0x3f03aba0, 0x3f03ab98
fixme:advapi:EventRegister {4372afee-73b0-42ce-9821-7e134361b519}, 0x3f005c90, 0x3f03abd8, 0x3f03abd0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
Looks like steam didn't shutdown cleanly, scheduling immediate update check
[2013-12-03 23:39:29] Checking for update on startup
[2013-12-03 23:39:29] Checking for available updates...
fixme:winhttp:WinHttpDetectAutoProxyConfigUrl discovery via DHCP not supported
[2013-12-03 23:39:29] Download skipped: /client/steam_client_win32 version 1386125885, installed version 1386125885
[2013-12-03 23:39:29] Nothing to do
[2013-12-03 23:39:29] Verifying installation...
[2013-12-03 23:39:29] Performing checksum verification of executable files
[2013-12-03 23:39:29] Verification complete
fixme:advapi:EventRegister {47a9201e-73b0-42ce-9821-7e134361bc6f}, 0x3f005c90, 0x3f03ab30, 0x3f03ab28
fixme:advapi:EventRegister {58a9201e-73b0-42ce-9821-7e134361bc70}, 0x3f005c90, 0x3f03ab68, 0x3f03ab60
fixme:advapi:EventRegister {3fa9201e-73b0-43fe-9821-7e145359bc6f}, 0x3f005c90, 0x3f03aaf8, 0x3f03aaf0
fixme:advapi:EventRegister {1432afee-73b0-42ce-9821-7e134361b433}, 0x3f005c90, 0x3f03aba0, 0x3f03ab98
fixme:advapi:EventRegister {4372afee-73b0-42ce-9821-7e134361b519}, 0x3f005c90, 0x3f03abd8, 0x3f03abd0
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gno
me-keyring-pkcs11.so: cannot open shared object file: No such file or directory
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
fixme:ole:RemUnknown_QueryInterface No interface for iid {00000019-0000-0000-c000-000000000046}
[1203/233930:ERROR:resource_bundle.cc(417)] Failed to load C:\Program Files (x86)\Steam\bin\chrome.pak
Some features may not be available.
fixme:iphlpapi:NotifyAddrChange (Handle 0x5b4d4c8, overlapped 0x58f75f0): stub
fixme:winsock:WSALookupServiceBeginW (0x5b4d5c8 0x00000ff0 0x5b4d610) Stub!
[1203/233930:ERROR:network_change_notifier_win.cc(126)] WSALookupServiceBegin failed with: 8
fixme:winediag:AUDDRV_GetAudioEndpoint Winepulse is not officially supported by the wine project
fixme:winediag:AUDDRV_GetAudioEndpoint For sound related feedback and support, please visit http://ubuntuforums.org/showt
hread.php?t=1960599
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:win:RegisterDeviceNotificationA (hwnd=0x100b4, filter=0x8ffe4ec,flags=0x00000000) returns a fake device notificatio
n handle!
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub
err:ole:CoGetClassObject class {77f10cf0-3db5-4966-b520-b7c54fd35ed6} not registered
err:ole:CoGetClassObject no class object {77f10cf0-3db5-4966-b520-b7c54fd35ed6} could be created for context 0x1
fixme:wbemprox:wbem_locator_ConnectServer unsupported flags
fixme:wbemprox:client_security_SetBlanket 0x7c3ff280, 0x1fc880, 10, 0, (null), 3, 3, (nil), 0x00000000
fixme:wbemprox:client_security_Release 0x7c3ff280
err:wbemprox:wql_error syntax error, unexpected TK_NOT
fixme:wbemprox:wbem_locator_ConnectServer unsupported flags
fixme:wbemprox:client_security_SetBlanket 0x7c3ff280, 0x1fc8a8, 10, 0, (null), 3, 3, (nil), 0x00000000
fixme:wbemprox:client_security_Release 0x7c3ff280
fixme:mountmgr:harddisk_ioctl The DISK_PARTITION_INFO and DISK_DETECTION_INFO structures will not be filled
fixme:wbemprox:enum_class_object_Next timeout not supported
fixme:wbemprox:enum_class_object_Next timeout not supported
fixme:wbemprox:enum_class_object_Next timeout not supported
fixme:wbemprox:enum_class_object_Next timeout not supported
err:ole:CoGetClassObject class {dff32fea-3331-48da-a272-ccfc238695be} not registered
err:ole:CoGetClassObject class {dff32fea-3331-48da-a272-ccfc238695be} not registered
err:ole:create_server class {dff32fea-3331-48da-a272-ccfc238695be} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {dff32fea-3331-48da-a272-ccfc238695be} could be created for context 0x17
fixme:advapi:EventRegister {47a9201e-73b0-42ce-9821-7e134361bc6f}, 0x3f005c90, 0x3f03ab30, 0x3f03ab28
fixme:advapi:EventRegister {58a9201e-73b0-42ce-9821-7e134361bc70}, 0x3f005c90, 0x3f03ab68, 0x3f03ab60
fixme:advapi:EventRegister {3fa9201e-73b0-43fe-9821-7e145359bc6f}, 0x3f005c90, 0x3f03aaf8, 0x3f03aaf0
fixme:advapi:EventRegister {1432afee-73b0-42ce-9821-7e134361b433}, 0x3f005c90, 0x3f03aba0, 0x3f03ab98
fixme:advapi:EventRegister {4372afee-73b0-42ce-9821-7e134361b519}, 0x3f005c90, 0x3f03abd8, 0x3f03abd0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:dbghelp:elf_search_auxv can't find symbol in module
fixme:dbghelp:elf_search_auxv can't find symbol in module
fixme:dbghelp:elf_search_auxv can't find symbol in module
fixme:dbghelp:elf_search_auxv can't find symbol in module
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub

```

---

### Post by cubic2 on 2013-12-04
This is due to bug [COLOR=#000000]http://bugs.winehq.org/show_bug.cgi?id=35030.
Fixed in Git Commit [/COLOR]http://source.winehq.org/git/wine.git/commit/fd65b0a1c3f5f981cc110ca9e6a0edb6323e1296.
It's not only you ;)

---

### Post by K0Yama on 2013-12-04
Hello!

I'm sorry, I'm pretty noob with Ubuntu. I just wanted to relax with a game for couple of hours after work, but now I've spent those couple of hours trying to get my Steam work again. 
Could you guide me through with how to apply that patch you linked?

Thank you in advance.

---

### Post by cubic2 on 2013-12-05
You'll need to build wine from the source. This "patch" is a commit to the master branch of wine's git repository. This means, that it's already "applied" to the source available in git. You need to clone the git repo, build it and install it. The following links should help:
[http://wiki.winehq.org/GitWine](http://wiki.winehq.org/GitWine)
[http://ubuntuforums.org/showthread.php?t=1034649](http://ubuntuforums.org/showthread.php?t=1034649)

If you are not familiar with that process, it could take some more hours =/ Or you can wait for the next development release 1.7.8(?) and get it from wine ppa.

---

### Post by K0Yama on 2013-12-05
Thank you for the links, cubic2. 
I'll look into it the next time I have a day off. For now I'll just give up trying to play my steam games.

---

### Post by cubic2 on 2013-12-05
[COLOR=#ff0000]EDIT: wine 1.7.8 has been released and fixes steam problems now.[/COLOR]

Today I found time to build a **32-bit(requires a 32-bit prefix![~/.wine])** version from Git and created a .deb package for you. You can download it from my server [COLOR=#ff0000][link removed - see edit][/COLOR]

First just remove your old wine binaries (your prefix will not be removed of course):
```
$ sudo apt-get remove wine1.7
``` or ```
$ sudo apt-get remove wine
```
depending what version you were running before.

And install this package:
```
$ sudo dpkg -i wine_1.7.7-custom-1_i386.deb
```

You'll maybe need to set it to Windows 7 again. That's it. Just tested - steam is running again.
I advice you to switch back to the official version when 1.7.8 is released.

Have fun gaming ;)

---

### Post by K0Yama on 2013-12-06
Oh. Wow. Thanks! 
I'm in your debt!

---

### Post by MattBro on 2013-12-16
Is wine 1.7.8 working consistently with steam?  It sure isn't for me.  Once steam crashes once or twice that's it.  It starts hanging on authentication again.  It seems like you need a pristine 32 bit prefix as well, to get it to work again.  It's extremely annoying.

I don't think their fix really is fixing it.
My log is showing this error:
[1216/030949:ERROR:resource_bundle.cc(417)] Failed to load C:\Program Files\Steam\bin\chrome.pak
Some features may not be available.

then a bunch of fixme problems, finally followed by this:
fixme:wbemprox:wbem_locator_ConnectServer unsupported flags
fixme:wbemprox:client_security_SetBlanket 0x7c43c304, 0x7bed200, 10, 0, (null), 3, 3, (nil), 0x00000000
fixme:wbemprox:client_security_Release 0x7c43c304
err:wbemprox:wql_error syntax error, unexpected TK_NOT
fixme:wbemprox:wbem_locator_ConnectServer unsupported flags
fixme:wbemprox:client_security_SetBlanket 0x7c43c304, 0x7bed228, 10, 0, (null), 3, 3, (nil), 0x00000000
fixme:wbemprox:client_security_Release 0x7c43c304

It just hangs thereafter, with a few more fixme messages.

---

### Post by dannyboy79 on 2014-02-11
> **cubic2 said:**
> [COLOR=#ff0000]EDIT: wine 1.7.8 has been released and fixes steam problems now.[/COLOR]

Today I found time to build a **32-bit(requires a 32-bit prefix![~/.wine])** version from Git and created a .deb package for you. You can download it from my server [COLOR=#ff0000][link removed - see edit][/COLOR]

First just remove your old wine binaries (your prefix will not be removed of course):
```
$ sudo apt-get remove wine1.7
``` or ```
$ sudo apt-get remove wine
```
depending what version you were running before.

And install this package:
```
$ sudo dpkg -i wine_1.7.7-custom-1_i386.deb
```

You'll maybe need to set it to Windows 7 again. That's it. Just tested - steam is running again.
I advice you to switch back to the official version when 1.7.8 is released.

Have fun gaming ;)I'm running Wine 1.7.12-0ubuntu1~saucy1 and I can NOT log into steam. I enter the code steam emails me and hit enter (after I choose a unique name) and it just crashes out and steam never starts. I am only trying to get steam to work in wine because I just bought Outlast through steam and I shouldn't have cause I have a windows 7 dual boot so I can just install outlast in that BUT I was trying to get Wine to work for the very first time. I've never used Wine EVER before. :)

---

