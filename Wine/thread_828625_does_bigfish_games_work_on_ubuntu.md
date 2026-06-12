---
title: "does bigfish games work on ubuntu"
date: 2008-06-13
forum: Wine
---

### Post by timestoby on 2008-06-13
just wondering cause my partner likes to play these simple bigfish games

---

### Post by cogadh on 2008-06-13
The online games should work fine through your browser, as long as they are simply Flash games. The downloadable games won't work natively in Ubuntu (they are Windows executables), but they might work through [Wine](http://www.winehq.org/).

---

### Post by jessiwake on 2008-10-20
VirtualBox does the trick.. doodah. doodah.. :)

---

### Post by binbash on 2008-10-21
%95 of them works with wine.Just be sure the games do not contain animated cursors.If so you have to patch wine with animated mouse patch.

---

### Post by oryan_dunn on 2008-12-19
I'm trying to install this game:
[http://www.bigfishgames.com/download-games/726/mystery-case-files-huntsville/index.html](http://www.bigfishgames.com/download-games/726/mystery-case-files-huntsville/index.html)

But I keep getting this error:
[IMG]http://img380.imageshack.us/img380/553/screenshotbigfishgamessqa4.png[/IMG]

With this output:
```
$ wine mystery-case-files-huntsville_s1_l1_gF730T1L1_d382521974.exe 
fixme:advapi:CheckTokenMembership ((nil) 0x12db08 0x33ee14) stub!
fixme:advapi:CheckTokenMembership ((nil) 0x12db08 0x33ee14) stub!
fixme:advapi:CheckTokenMembership ((nil) 0x12db08 0x33ee14) stub!
fixme:advapi:CheckTokenMembership ((nil) 0x12db08 0x33ee14) stub!

```

---

### Post by oryan_dunn on 2008-12-19
This is one of those installers that connects and downloads the game within the installer.  Anyways, I turned on file debug messages and this is what it prints out:

```
warn:file:wine_nt_to_unix_file_name L"wineboot.exe" not found in /home/ryan/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"wineboot.exe" not found in /home/ryan/.wine/dosdevices/c:/windows/system32
warn:file:CreateFileW Unable to create file L"C:\\windows\\system32\\wineboot.exe" (status c0000034)
warn:file:wine_nt_to_unix_file_name L"wineboot.exe" not found in /home/ryan/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"wineboot.exe.manifest" not found in /home/ryan/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"wininit.ini" not found in /home/ryan/.wine/dosdevices/c:/windows
warn:file:CreateFileW Unable to create file L"C:\\windows\\wininit.ini" (status c0000034)
warn:file:wine_nt_to_unix_file_name L"dllcache\\" not found in /home/ryan/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"services.exe" not found in /home/ryan/.wine/dosdevices/c:/windows/system32
warn:file:CreateFileW Unable to create file L"C:\\windows\\system32\\services.exe" (status c0000034)
warn:file:wine_nt_to_unix_file_name L"services.exe" not found in /home/ryan/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"services.exe.manifest" not found in /home/ryan/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"iphlpapi.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"iphlpapi.dll" not found in /home/ryan/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"iphlpapi.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"iphlpapi.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"iphlpapi.dll" not found in /home/ryan/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"iphlpapi.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"iphlpapi.dll" not found in /home/ryan/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"winedevice.exe" not found in /home/ryan/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"winedevice.exe" not found in /home/ryan/.wine/dosdevices/c:/windows/system32
warn:file:CreateFileW Unable to create file L"C:\\windows\\system32\\winedevice.exe" (status c0000034)
warn:file:wine_nt_to_unix_file_name L"winedevice.exe" not found in /home/ryan/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"winedevice.exe.manifest" not found in /home/ryan/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"ntoskrnl.exe" not found in /home/ryan/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"ntoskrnl.exe" not found in /home/ryan/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"ntoskrnl.exe" not found in /home/ryan/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"ntoskrnl.exe" not found in /home/ryan/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"ntoskrnl.exe" not found in /home/ryan/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"ntoskrnl.exe" not found in /home/ryan/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"ntoskrnl.exe" not found in /home/ryan/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"iphlpapi.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"iphlpapi.dll" not found in /home/ryan/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"iphlpapi.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"iphlpapi.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"iphlpapi.dll" not found in /home/ryan/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"iphlpapi.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"iphlpapi.dll" not found in /home/ryan/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"USER32.dll" not found in /home/ryan/.wine/dosdevices/z:/home/ryan
warn:file:wine_nt_to_unix_file_name L"USER32.dll" not found in /home/ryan/.wine/dosdevices/z:/home/ryan
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\system32\\USER32.dll" -> "/home/ryan/.wine/dosdevices/c:/windows/system32/user32.dll" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\system32\\USER32.dll" -> "/home/ryan/.wine/dosdevices/c:/windows/system32/user32.dll" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"gdi32.dll" not found in /home/ryan/.wine/dosdevices/z:/home/ryan
warn:file:wine_nt_to_unix_file_name L"gdi32.dll" not found in /home/ryan/.wine/dosdevices/z:/home/ryan
warn:file:wine_nt_to_unix_file_name L"advapi32.dll" not found in /home/ryan/.wine/dosdevices/z:/home/ryan
warn:file:wine_nt_to_unix_file_name L"advapi32.dll" not found in /home/ryan/.wine/dosdevices/z:/home/ryan
warn:file:wine_nt_to_unix_file_name L"advapi32.dll" not found in /home/ryan/.wine/dosdevices/z:/home/ryan
warn:file:wine_nt_to_unix_file_name L"advapi32.dll" not found in /home/ryan/.wine/dosdevices/z:/home/ryan
warn:file:wine_nt_to_unix_file_name L"SHELL32.dll" not found in /home/ryan/.wine/dosdevices/z:/home/ryan
warn:file:wine_nt_to_unix_file_name L"SHELL32.dll" not found in /home/ryan/.wine/dosdevices/z:/home/ryan
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\system32\\SHELL32.dll" -> "/home/ryan/.wine/dosdevices/c:/windows/system32/shell32.dll" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\system32\\SHELL32.dll" -> "/home/ryan/.wine/dosdevices/c:/windows/system32/shell32.dll" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"shlwapi.dll" not found in /home/ryan/.wine/dosdevices/z:/home/ryan
warn:file:wine_nt_to_unix_file_name L"shlwapi.dll" not found in /home/ryan/.wine/dosdevices/z:/home/ryan
warn:file:wine_nt_to_unix_file_name L"x86_microsoft.windows.common-controls_6595b64144ccf1df_6.0.2600.2982_none_deadbeef\\comctl32.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/winsxs
warn:file:wine_nt_to_unix_file_name L"ole32.dll" not found in /home/ryan/.wine/dosdevices/z:/home/ryan
warn:file:wine_nt_to_unix_file_name L"ole32.dll" not found in /home/ryan/.wine/dosdevices/z:/home/ryan
warn:file:wine_nt_to_unix_file_name L"rpcrt4.dll" not found in /home/ryan/.wine/dosdevices/z:/home/ryan
warn:file:wine_nt_to_unix_file_name L"rpcrt4.dll" not found in /home/ryan/.wine/dosdevices/z:/home/ryan
warn:file:wine_nt_to_unix_file_name L"iphlpapi.dll" not found in /home/ryan/.wine/dosdevices/z:/home/ryan
warn:file:wine_nt_to_unix_file_name L"iphlpapi.dll" not found in /home/ryan/.wine/dosdevices/z:/home/ryan
warn:file:wine_nt_to_unix_file_name L"iphlpapi.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"iphlpapi.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"iphlpapi.dll" not found in /home/ryan/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"iphlpapi.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"iphlpapi.dll" not found in /home/ryan/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"VERSION.dll" not found in /home/ryan/.wine/dosdevices/z:/home/ryan
warn:file:wine_nt_to_unix_file_name L"VERSION.dll" not found in /home/ryan/.wine/dosdevices/z:/home/ryan
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\system32\\VERSION.dll" -> "/home/ryan/.wine/dosdevices/c:/windows/system32/version.dll" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\system32\\VERSION.dll" -> "/home/ryan/.wine/dosdevices/c:/windows/system32/version.dll" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"lz32.dll" not found in /home/ryan/.wine/dosdevices/z:/home/ryan
warn:file:wine_nt_to_unix_file_name L"lz32.dll" not found in /home/ryan/.wine/dosdevices/z:/home/ryan
warn:file:wine_nt_to_unix_file_name L"lz32.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"lz32.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"lz32.dll" not found in /home/ryan/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"lz32.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"lz32.dll" not found in /home/ryan/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\fonts\\vgasys.fon" -> "/home/ryan/.wine/dosdevices/c:/windows/Fonts/vgasys.fon" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\fonts\\vgaoem.fon" -> "/home/ryan/.wine/dosdevices/c:/windows/Fonts/vgaoem.fon" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\fonts\\vgafix.fon" -> "/home/ryan/.wine/dosdevices/c:/windows/Fonts/vgafix.fon" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\fonts" -> "/home/ryan/.wine/dosdevices/c:/windows/Fonts" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\fonts\\coure.fon" -> "/home/ryan/.wine/dosdevices/c:/windows/Fonts/coure.fon" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\fonts\\sserife.fon" -> "/home/ryan/.wine/dosdevices/c:/windows/Fonts/sserife.fon" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\fonts\\serife.fon" -> "/home/ryan/.wine/dosdevices/c:/windows/Fonts/serife.fon" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\fonts\\smalle.fon" -> "/home/ryan/.wine/dosdevices/c:/windows/Fonts/smalle.fon" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"winex11.drv" not found in /home/ryan/.wine/dosdevices/z:/home/ryan
warn:file:wine_nt_to_unix_file_name L"winex11.drv" not found in /home/ryan/.wine/dosdevices/z:/home/ryan
warn:file:wine_nt_to_unix_file_name L"winex11.drv" not found in /home/ryan/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"winex11.drv" not found in /home/ryan/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"winex11.drv" not found in /home/ryan/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"winex11.drv" not found in /home/ryan/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"winex11.drv" not found in /home/ryan/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"imm32.dll" not found in /home/ryan/.wine/dosdevices/z:/home/ryan
warn:file:wine_nt_to_unix_file_name L"imm32.dll" not found in /home/ryan/.wine/dosdevices/z:/home/ryan
warn:file:wine_nt_to_unix_file_name L"imm32.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"imm32.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"imm32.dll" not found in /home/ryan/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"imm32.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"imm32.dll" not found in /home/ryan/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"uxtheme.dll" not found in /home/ryan/.wine/dosdevices/z:/home/ryan
warn:file:wine_nt_to_unix_file_name L"uxtheme.dll" not found in /home/ryan/.wine/dosdevices/z:/home/ryan
warn:file:wine_nt_to_unix_file_name L"uxtheme.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"uxtheme.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"uxtheme.dll" not found in /home/ryan/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"uxtheme.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"uxtheme.dll" not found in /home/ryan/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"explorer.exe" not found in /home/ryan/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"explorer.exe" not found in /home/ryan/.wine/dosdevices/c:/windows/system32
warn:file:CreateFileW Unable to create file L"C:\\windows\\system32\\explorer.exe" (status c0000034)
warn:file:wine_nt_to_unix_file_name L"explorer.exe" not found in /home/ryan/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"explorer.exe.manifest" not found in /home/ryan/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"iphlpapi.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"iphlpapi.dll" not found in /home/ryan/.wine/dosdevices/z:/home/ryan
warn:file:wine_nt_to_unix_file_name L"iphlpapi.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"iphlpapi.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"iphlpapi.dll" not found in /home/ryan/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"iphlpapi.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"iphlpapi.dll" not found in /home/ryan/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\fonts\\vgasys.fon" -> "/home/ryan/.wine/dosdevices/c:/windows/Fonts/vgasys.fon" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\fonts\\vgaoem.fon" -> "/home/ryan/.wine/dosdevices/c:/windows/Fonts/vgaoem.fon" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\fonts\\vgafix.fon" -> "/home/ryan/.wine/dosdevices/c:/windows/Fonts/vgafix.fon" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\fonts" -> "/home/ryan/.wine/dosdevices/c:/windows/Fonts" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\fonts\\coure.fon" -> "/home/ryan/.wine/dosdevices/c:/windows/Fonts/coure.fon" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\fonts\\sserife.fon" -> "/home/ryan/.wine/dosdevices/c:/windows/Fonts/sserife.fon" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\fonts\\serife.fon" -> "/home/ryan/.wine/dosdevices/c:/windows/Fonts/serife.fon" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\fonts\\smalle.fon" -> "/home/ryan/.wine/dosdevices/c:/windows/Fonts/smalle.fon" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"winex11.drv" not found in /home/ryan/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"winex11.drv" not found in /home/ryan/.wine/dosdevices/z:/home/ryan
warn:file:wine_nt_to_unix_file_name L"winex11.drv" not found in /home/ryan/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"winex11.drv" not found in /home/ryan/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"winex11.drv" not found in /home/ryan/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"winex11.drv" not found in /home/ryan/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"winex11.drv" not found in /home/ryan/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"imm32.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"imm32.dll" not found in /home/ryan/.wine/dosdevices/z:/home/ryan
warn:file:wine_nt_to_unix_file_name L"imm32.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"imm32.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"imm32.dll" not found in /home/ryan/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"imm32.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"imm32.dll" not found in /home/ryan/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"(None)" not found in /home/ryan/.wine/dosdevices/z:/home/ryan
warn:file:CreateFileW Unable to create file L"(None)" (status c0000034)
warn:file:wine_nt_to_unix_file_name L"(None)" not found in /home/ryan/.wine/dosdevices/c:/windows
warn:file:CreateFileW Unable to create file L"C:\\windows\\(None)" (status c0000034)
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\temp\\nsa30c.tmp" -> "/home/ryan/.wine/dosdevices/c:/windows/temp/nsa30c.tmp" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\temp\\nsg312.tmp" -> "/home/ryan/.wine/dosdevices/c:/windows/temp/nsg312.tmp" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\temp\\nsg312.tmp" -> "/home/ryan/.wine/dosdevices/c:/windows/temp/nsg312.tmp" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"System.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/temp/nsg312.tmp
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\temp\\nsg312.tmp\\System.dll" -> "/home/ryan/.wine/dosdevices/c:/windows/temp/nsg312.tmp/System.dll" required a case-insensitive search
warn:file:CreateFileW Unable to create file L"C:\\windows\\temp\\nsg312.tmp\\System.dll" (status c0000035)
warn:file:CreateFileW Unable to create file L"C:\\windows\\temp\\nsg312.tmp\\System.dll" (status c0000035)
warn:file:CreateFileW Unable to create file L"C:\\windows\\temp\\nsg312.tmp\\System.dll" (status c0000035)
warn:file:wine_nt_to_unix_file_name L"UserInfo.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/temp/nsg312.tmp
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\temp\\nsg312.tmp\\UserInfo.dll" -> "/home/ryan/.wine/dosdevices/c:/windows/temp/nsg312.tmp/UserInfo.dll" required a case-insensitive search
warn:file:CreateFileW Unable to create file L"C:\\windows\\temp\\nsg312.tmp\\UserInfo.dll" (status c0000035)
warn:file:CreateFileW Unable to create file L"C:\\windows\\temp\\nsg312.tmp\\System.dll" (status c0000035)
warn:file:CreateFileW Unable to create file L"C:\\windows\\temp\\nsg312.tmp\\System.dll" (status c0000035)
warn:file:wine_nt_to_unix_file_name L"USER32.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/profiles/All Users/Application Data/BigFishGamesCache/Upgrade/stub
warn:file:wine_nt_to_unix_file_name L"USER32.dll" not found in /home/ryan/.wine/dosdevices/z:/home/ryan
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\system32\\USER32.dll" -> "/home/ryan/.wine/dosdevices/c:/windows/system32/user32.dll" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\system32\\USER32.dll" -> "/home/ryan/.wine/dosdevices/c:/windows/system32/user32.dll" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"gdi32.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/profiles/All Users/Application Data/BigFishGamesCache/Upgrade/stub
warn:file:wine_nt_to_unix_file_name L"gdi32.dll" not found in /home/ryan/.wine/dosdevices/z:/home/ryan
warn:file:wine_nt_to_unix_file_name L"advapi32.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/profiles/All Users/Application Data/BigFishGamesCache/Upgrade/stub
warn:file:wine_nt_to_unix_file_name L"advapi32.dll" not found in /home/ryan/.wine/dosdevices/z:/home/ryan
warn:file:wine_nt_to_unix_file_name L"advapi32.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/profiles/All Users/Application Data/BigFishGamesCache/Upgrade/stub
warn:file:wine_nt_to_unix_file_name L"advapi32.dll" not found in /home/ryan/.wine/dosdevices/z:/home/ryan
warn:file:wine_nt_to_unix_file_name L"SHELL32.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/profiles/All Users/Application Data/BigFishGamesCache/Upgrade/stub
warn:file:wine_nt_to_unix_file_name L"SHELL32.dll" not found in /home/ryan/.wine/dosdevices/z:/home/ryan
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\system32\\SHELL32.dll" -> "/home/ryan/.wine/dosdevices/c:/windows/system32/shell32.dll" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\system32\\SHELL32.dll" -> "/home/ryan/.wine/dosdevices/c:/windows/system32/shell32.dll" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"shlwapi.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/profiles/All Users/Application Data/BigFishGamesCache/Upgrade/stub
warn:file:wine_nt_to_unix_file_name L"shlwapi.dll" not found in /home/ryan/.wine/dosdevices/z:/home/ryan
warn:file:wine_nt_to_unix_file_name L"x86_microsoft.windows.common-controls_6595b64144ccf1df_6.0.2600.2982_none_deadbeef\\comctl32.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/winsxs
warn:file:wine_nt_to_unix_file_name L"ole32.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/profiles/All Users/Application Data/BigFishGamesCache/Upgrade/stub
warn:file:wine_nt_to_unix_file_name L"ole32.dll" not found in /home/ryan/.wine/dosdevices/z:/home/ryan
warn:file:wine_nt_to_unix_file_name L"rpcrt4.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/profiles/All Users/Application Data/BigFishGamesCache/Upgrade/stub
warn:file:wine_nt_to_unix_file_name L"rpcrt4.dll" not found in /home/ryan/.wine/dosdevices/z:/home/ryan
warn:file:wine_nt_to_unix_file_name L"iphlpapi.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/profiles/All Users/Application Data/BigFishGamesCache/Upgrade/stub
warn:file:wine_nt_to_unix_file_name L"iphlpapi.dll" not found in /home/ryan/.wine/dosdevices/z:/home/ryan
warn:file:wine_nt_to_unix_file_name L"iphlpapi.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"iphlpapi.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"iphlpapi.dll" not found in /home/ryan/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"iphlpapi.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"iphlpapi.dll" not found in /home/ryan/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"VERSION.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/profiles/All Users/Application Data/BigFishGamesCache/Upgrade/stub
warn:file:wine_nt_to_unix_file_name L"VERSION.dll" not found in /home/ryan/.wine/dosdevices/z:/home/ryan
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\system32\\VERSION.dll" -> "/home/ryan/.wine/dosdevices/c:/windows/system32/version.dll" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\system32\\VERSION.dll" -> "/home/ryan/.wine/dosdevices/c:/windows/system32/version.dll" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"lz32.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/profiles/All Users/Application Data/BigFishGamesCache/Upgrade/stub
warn:file:wine_nt_to_unix_file_name L"lz32.dll" not found in /home/ryan/.wine/dosdevices/z:/home/ryan
warn:file:wine_nt_to_unix_file_name L"lz32.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"lz32.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"lz32.dll" not found in /home/ryan/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"lz32.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"lz32.dll" not found in /home/ryan/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\fonts\\vgasys.fon" -> "/home/ryan/.wine/dosdevices/c:/windows/Fonts/vgasys.fon" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\fonts\\vgaoem.fon" -> "/home/ryan/.wine/dosdevices/c:/windows/Fonts/vgaoem.fon" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\fonts\\vgafix.fon" -> "/home/ryan/.wine/dosdevices/c:/windows/Fonts/vgafix.fon" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\fonts" -> "/home/ryan/.wine/dosdevices/c:/windows/Fonts" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\fonts\\coure.fon" -> "/home/ryan/.wine/dosdevices/c:/windows/Fonts/coure.fon" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\fonts\\sserife.fon" -> "/home/ryan/.wine/dosdevices/c:/windows/Fonts/sserife.fon" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\fonts\\serife.fon" -> "/home/ryan/.wine/dosdevices/c:/windows/Fonts/serife.fon" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\fonts\\smalle.fon" -> "/home/ryan/.wine/dosdevices/c:/windows/Fonts/smalle.fon" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"winex11.drv" not found in /home/ryan/.wine/dosdevices/c:/windows/profiles/All Users/Application Data/BigFishGamesCache/Upgrade/stub
warn:file:wine_nt_to_unix_file_name L"winex11.drv" not found in /home/ryan/.wine/dosdevices/z:/home/ryan
warn:file:wine_nt_to_unix_file_name L"winex11.drv" not found in /home/ryan/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"winex11.drv" not found in /home/ryan/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"winex11.drv" not found in /home/ryan/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"winex11.drv" not found in /home/ryan/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"winex11.drv" not found in /home/ryan/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"imm32.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/profiles/All Users/Application Data/BigFishGamesCache/Upgrade/stub
warn:file:wine_nt_to_unix_file_name L"imm32.dll" not found in /home/ryan/.wine/dosdevices/z:/home/ryan
warn:file:wine_nt_to_unix_file_name L"imm32.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"imm32.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"imm32.dll" not found in /home/ryan/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"imm32.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"imm32.dll" not found in /home/ryan/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"uxtheme.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/profiles/All Users/Application Data/BigFishGamesCache/Upgrade/stub
warn:file:wine_nt_to_unix_file_name L"uxtheme.dll" not found in /home/ryan/.wine/dosdevices/z:/home/ryan
warn:file:wine_nt_to_unix_file_name L"uxtheme.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"uxtheme.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"uxtheme.dll" not found in /home/ryan/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"uxtheme.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"uxtheme.dll" not found in /home/ryan/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"SHFOLDER.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/profiles/All Users/Application Data/BigFishGamesCache/Upgrade/stub
warn:file:wine_nt_to_unix_file_name L"SHFOLDER.dll" not found in /home/ryan/.wine/dosdevices/z:/home/ryan
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\system32\\SHFOLDER.dll" -> "/home/ryan/.wine/dosdevices/c:/windows/system32/shfolder.dll" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"SHFOLDER.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/profiles/All Users/Application Data/BigFishGamesCache/Upgrade/stub
warn:file:wine_nt_to_unix_file_name L"SHFOLDER.dll" not found in /home/ryan/.wine/dosdevices/z:/home/ryan
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\system32\\SHFOLDER.dll" -> "/home/ryan/.wine/dosdevices/c:/windows/system32/shfolder.dll" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"SHFOLDER.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/profiles/All Users/Application Data/BigFishGamesCache/Upgrade/stub
warn:file:wine_nt_to_unix_file_name L"SHFOLDER.dll" not found in /home/ryan/.wine/dosdevices/z:/home/ryan
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\system32\\SHFOLDER.dll" -> "/home/ryan/.wine/dosdevices/c:/windows/system32/shfolder.dll" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\system32\\SHFOLDER.dll" -> "/home/ryan/.wine/dosdevices/c:/windows/system32/shfolder.dll" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\temp\\nsy490.tmp" -> "/home/ryan/.wine/dosdevices/c:/windows/temp/nsy490.tmp" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\temp\\nsg4b2.tmp" -> "/home/ryan/.wine/dosdevices/c:/windows/temp/nsg4b2.tmp" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\temp\\nsg4b2.tmp" -> "/home/ryan/.wine/dosdevices/c:/windows/temp/nsg4b2.tmp" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"System.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/temp/nsg4b2.tmp
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\temp\\nsg4b2.tmp\\System.dll" -> "/home/ryan/.wine/dosdevices/c:/windows/temp/nsg4b2.tmp/System.dll" required a case-insensitive search
warn:file:CreateFileW Unable to create file L"C:\\windows\\temp\\nsg4b2.tmp\\System.dll" (status c0000035)
warn:file:CreateFileW Unable to create file L"C:\\windows\\temp\\nsg4b2.tmp\\System.dll" (status c0000035)
warn:file:CreateFileW Unable to create file L"C:\\windows\\temp\\nsg4b2.tmp\\System.dll" (status c0000035)
warn:file:wine_nt_to_unix_file_name L"UserInfo.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/temp/nsg4b2.tmp
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\temp\\nsg4b2.tmp\\UserInfo.dll" -> "/home/ryan/.wine/dosdevices/c:/windows/temp/nsg4b2.tmp/UserInfo.dll" required a case-insensitive search
warn:file:CreateFileW Unable to create file L"C:\\windows\\temp\\nsg4b2.tmp\\UserInfo.dll" (status c0000035)
warn:file:wine_nt_to_unix_file_name L"uac.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/temp/nsg4b2.tmp
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\temp\\nsg4b2.tmp\\uac.dll" -> "/home/ryan/.wine/dosdevices/c:/windows/temp/nsg4b2.tmp/uac.dll" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"SECUR32.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/profiles/All Users/Application Data/BigFishGamesCache/Upgrade/stub
warn:file:wine_nt_to_unix_file_name L"SECUR32.dll" not found in /home/ryan/.wine/dosdevices/z:/home/ryan
warn:file:wine_nt_to_unix_file_name L"SECUR32.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"SECUR32.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"SECUR32.dll" not found in /home/ryan/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"SECUR32.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"SECUR32.dll" not found in /home/ryan/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"netapi32.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/profiles/All Users/Application Data/BigFishGamesCache/Upgrade/stub
warn:file:wine_nt_to_unix_file_name L"netapi32.dll" not found in /home/ryan/.wine/dosdevices/z:/home/ryan
warn:file:wine_nt_to_unix_file_name L"netapi32.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"netapi32.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"netapi32.dll" not found in /home/ryan/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"netapi32.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"netapi32.dll" not found in /home/ryan/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"ws2_32.dll" not found in /home/ryan/.wine/dosdevices/c:/windows/profiles/All Users/Application Data/BigFishGamesCache/Upgrade/stub
warn:file:wine_nt_to_unix_file_name L"ws2_32.dll" not found in /home/ryan/.wine/dosdevices/z:/home/ryan
warn:file:CreateFileW Unable to create file L"C:\\windows\\temp\\nsg4b2.tmp\\System.dll" (status c0000035)
warn:file:CreateFileW Unable to create file L"C:\\windows\\temp\\nsg4b2.tmp\\System.dll" (status c0000035)
warn:file:CreateFileW Unable to create file L"C:\\windows\\temp\\nsg4b2.tmp\\System.dll" (status c0000035)
warn:file:CreateFileW Unable to create file L"C:\\windows\\temp\\nsg4b2.tmp\\System.dll" (status c0000035)
warn:file:CreateFileW Unable to create file L"C:\\windows\\temp\\nsg4b2.tmp\\System.dll" (status c0000035)
warn:file:CreateFileW Unable to create file L"C:\\windows\\temp\\nsg4b2.tmp\\System.dll" (status c0000035)
warn:file:CreateFileW Unable to create file L"C:\\windows\\temp\\nsg4b2.tmp\\System.dll" (status c0000035)
warn:file:CreateFileW Unable to create file L"C:\\windows\\temp\\nsg4b2.tmp\\System.dll" (status c0000035)
warn:file:CreateFileW Unable to create file L"C:\\windows\\temp\\nsg4b2.tmp\\System.dll" (status c0000035)
warn:file:CreateFileW Unable to create file L"C:\\windows\\temp\\nsg4b2.tmp\\System.dll" (status c0000035)
warn:file:CreateFileW Unable to create file L"C:\\windows\\temp\\nsg4b2.tmp\\System.dll" (status c0000035)
warn:file:CreateFileW Unable to create file L"C:\\windows\\temp\\nsg4b2.tmp\\System.dll" (status c0000035)
```

It looks like it's not able to create some files and cannot find some others.  The files that it is looking for, are those included with internet explorer, or some other program?

I'm trying to get this to work so my Dad can move over to linux, but he is all about these mystery case file games.

---

### Post by politick on 2009-06-22
> **jessiwake said:**
> VirtualBox does the trick.. doodah. doodah.. :)

I had no luck with VMWare player and XP.
Can you give out more details?

---

### Post by deesto on 2009-08-03
> **politick said:**
> I had no luck with VMWare player and XP.
Can you give out more details?VirtualBox is another virtualization software that, like VMWare, lets you install multiple operating systems within a single host.  But if you have already tried this with VMWare, I'm not sure that VirtualBox would get you any better results.  It also seems a bit excessive to recommend an entire, separate OS running on the host just to play Flash-based games.

This seems like a common problem for all wine users and BigFishGames games.  There is a bug report to wine and a possible fix patch [1] but this may not work on all systems.

[1] [http://bugs.winehq.org/show_bug.cgi?id=15755](http://bugs.winehq.org/show_bug.cgi?id=15755)

---

### Post by saam1 on 2009-08-03
You know most of game does not have animated cursor so we need patch wine......

---

### Post by made_of_spoons on 2011-05-26
They don't work on my computer. Well, by now I've tried only one, to be honest. But I love those Hidden Object games and I MUST get them working. But how?
My problem is, that when I go to C drive and press on the .exe file, nothing happens. ._. What do I do?

EDIT: Okay, just downloaded Fishdom H2O and it seems to be half working. I can hear the music but the screen is just white. Do I need to change something in the ''configure wine'' thing?

---

