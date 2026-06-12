---
title: "srcds tons of errors."
date: 2008-05-27
forum: Wine
---

### Post by Zac_tw on 2008-05-27
I installed Wine so I could run GMOD10 (Garrysmod, a mod for Half-Life 2), as there are no Linux binaries.

I installed X and Wine, but I'm having major problems after installing steam in Wine.

This is what happens when I run steam.exe.



wine ./srcds.exe -game garrysmod
```
warn:file:wine_nt_to_unix_file_name L"USER32.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:file:wine_nt_to_unix_file_name L"USER32.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\system32\\USER32.dll" -> "/root/.wine/dosdevices/c:/windows/system32/user32.dll" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\system32\\USER32.dll" -> "/root/.wine/dosdevices/c:/windows/system32/user32.dll" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\system32\\USER32.dll" -> "/root/.wine/dosdevices/c:/windows/system32/user32.dll" required a case-insensitive search
warn:module:load_builtin_dll failed to load .so lib for builtin L"C:\\windows\\system32\\USER32.dll": /root/.wine/dosdevices/c:/windows/system32/user32.dll: invalid ELF header
warn:file:wine_nt_to_unix_file_name L"gdi32.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:file:wine_nt_to_unix_file_name L"gdi32.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:module:load_builtin_dll failed to load .so lib for builtin L"C:\\windows\\system32\\gdi32.dll": /root/.wine/dosdevices/c:/windows/system32/gdi32.dll: invalid ELF header
warn:file:wine_nt_to_unix_file_name L"advapi32.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:file:wine_nt_to_unix_file_name L"advapi32.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:file:wine_nt_to_unix_file_name L"advapi32.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:file:wine_nt_to_unix_file_name L"advapi32.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:module:load_builtin_dll failed to load .so lib for builtin L"C:\\windows\\system32\\advapi32.dll": /root/.wine/dosdevices/c:/windows/system32/advapi32.dll: invalid ELF header
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\PROG~FBU\\Valve\\HLServer\\" -> "/root/.wine/dosdevices/c:/Program Files/Valve/HLServer" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\Fonts\\vgasys.fon" -> "/root/.wine/dosdevices/c:/windows/fonts/vgasys.fon" required a case-insensitive search
warn:font:AddFontFileToList Unable to load font file "/root/.wine/dosdevices/c:/windows/fonts/vgasys.fon" err = 1
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\Fonts\\vgaoem.fon" -> "/root/.wine/dosdevices/c:/windows/fonts/vgaoem.fon" required a case-insensitive search
warn:font:AddFontFileToList Unable to load font file "/root/.wine/dosdevices/c:/windows/fonts/vgaoem.fon" err = 1
warn:font:AddFontFileToList Unable to load font file "/usr/lib/../share/wine/fonts/vgaoem.fon" err = 1
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\Fonts\\vgafix.fon" -> "/root/.wine/dosdevices/c:/windows/fonts/vgafix.fon" required a case-insensitive search
warn:font:AddFontFileToList Unable to load font file "/root/.wine/dosdevices/c:/windows/fonts/vgafix.fon" err = 1
warn:font:AddFontFileToList Unable to load font file "/usr/lib/../share/wine/fonts/vgafix.fon" err = 1
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\Fonts" -> "/root/.wine/dosdevices/c:/windows/fonts" required a case-insensitive search
warn:font:AddFontFileToList Ignoring font "/usr/lib/../share/wine/fonts//vgas1257.fon"
warn:font:AddFontFileToList Ignoring font "/usr/lib/../share/wine/fonts//vgasys.fon"
warn:font:AddFontFileToList Ignoring font "/usr/lib/../share/wine/fonts//vgas1255.fon"
warn:font:AddFontFileToList Ignoring font "/usr/lib/../share/wine/fonts//sserifeg.fon"
warn:font:AddFontFileToList Ignoring font "/usr/lib/../share/wine/fonts//smaller.fon"
warn:font:AddFontFileToList Ignoring font "/usr/lib/../share/wine/fonts//smallet.fon"
warn:font:AddFontFileToList Ignoring font "/usr/lib/../share/wine/fonts//smae1257.fon"
warn:font:AddFontFileToList Ignoring font "/usr/lib/../share/wine/fonts//smalleg.fon"
warn:font:AddFontFileToList Ignoring font "/usr/lib/../share/wine/fonts//ssee1256.fon"
warn:font:AddFontFileToList Ignoring font "/usr/lib/../share/wine/fonts//coue1255.fon"
warn:font:AddFontFileToList Ignoring font "/usr/lib/../share/wine/fonts//coue1256.fon"
warn:font:AddFontFileToList Ignoring font "/usr/lib/../share/wine/fonts//couree.fon"
warn:font:AddFontFileToList Ignoring font "/usr/lib/../share/wine/fonts//smae1255.fon"
warn:font:AddFontFileToList Ignoring font "/usr/lib/../share/wine/fonts//coue1257.fon"
warn:font:AddFontFileToList Ignoring font "/usr/lib/../share/wine/fonts//sserifee.fon"
warn:font:AddFontFileToList Ignoring font "/usr/lib/../share/wine/fonts//jvgasys.fon"
warn:font:AddFontFileToList Ignoring font "/usr/lib/../share/wine/fonts//coure.fon"
warn:font:AddFontFileToList Ignoring font "/usr/lib/../share/wine/fonts//hvgasys.fon"
warn:font:AddFontFileToList Ignoring font "/usr/lib/../share/wine/fonts//couret.fon"
warn:font:AddFontFileToList Ignoring font "/usr/lib/../share/wine/fonts//smae1256.fon"
warn:font:AddFontFileToList Ignoring font "/usr/lib/../share/wine/fonts//sserifet.fon"
warn:font:AddFontFileToList Ignoring font "/usr/lib/../share/wine/fonts//jsmalle.fon"
warn:font:AddFontFileToList Ignoring font "/usr/lib/../share/wine/fonts//ssee1257.fon"
warn:font:AddFontFileToList Ignoring font "/usr/lib/../share/wine/fonts//cvgasys.fon"
warn:font:AddFontFileToList Ignoring font "/usr/lib/../share/wine/fonts//vgasysr.fon"
warn:font:AddFontFileToList Ignoring font "/usr/lib/../share/wine/fonts//smallee.fon"
warn:font:AddFontFileToList Ignoring font "/usr/lib/../share/wine/fonts//ssee874.fon"
warn:font:AddFontFileToList Ignoring font "/usr/lib/../share/wine/fonts//courer.fon"
warn:font:AddFontFileToList Ignoring font "/usr/lib/../share/wine/fonts//sserife.fon"
warn:font:AddFontFileToList Ignoring font "/usr/lib/../share/wine/fonts//vgas874.fon"
warn:font:AddFontFileToList Ignoring font "/usr/lib/../share/wine/fonts//smalle.fon"
warn:font:AddFontFileToList Ignoring font "/usr/lib/../share/wine/fonts//vgasyst.fon"
warn:font:AddFontFileToList Ignoring font "/usr/lib/../share/wine/fonts//vgasysg.fon"
warn:font:AddFontFileToList Ignoring font "/usr/lib/../share/wine/fonts//svgasys.fon"
warn:font:AddFontFileToList Ignoring font "/usr/lib/../share/wine/fonts//vgasyse.fon"
warn:font:AddFontFileToList Ignoring font "/usr/lib/../share/wine/fonts//ssee1255.fon"
warn:font:AddFontFileToList Ignoring font "/usr/lib/../share/wine/fonts//sserifer.fon"
warn:font:AddFontFileToList Ignoring font "/usr/lib/../share/wine/fonts//vgas1256.fon"
warn:font:AddFontFileToList Ignoring font "/usr/lib/../share/wine/fonts//coureg.fon"
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\Fonts\\coure.fon" -> "/root/.wine/dosdevices/c:/windows/fonts/coure.fon" required a case-insensitive search
warn:font:AddFontFileToList Unable to load font file "/root/.wine/dosdevices/c:/windows/fonts/coure.fon" err = 1
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\Fonts\\sserife.fon" -> "/root/.wine/dosdevices/c:/windows/fonts/sserife.fon" required a case-insensitive search
warn:font:AddFontFileToList Unable to load font file "/root/.wine/dosdevices/c:/windows/fonts/sserife.fon" err = 1
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\Fonts\\serife.fon" -> "/root/.wine/dosdevices/c:/windows/fonts/serife.fon" required a case-insensitive search
warn:font:AddFontFileToList Unable to load font file "/root/.wine/dosdevices/c:/windows/fonts/serife.fon" err = 1
warn:font:AddFontFileToList Unable to load font file "/usr/lib/../share/wine/fonts/serife.fon" err = 1
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\Fonts\\smalle.fon" -> "/root/.wine/dosdevices/c:/windows/fonts/smalle.fon" required a case-insensitive search
warn:font:AddFontFileToList Unable to load font file "/root/.wine/dosdevices/c:/windows/fonts/smalle.fon" err = 1
warn:file:wine_nt_to_unix_file_name L"winex11.drv" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:file:wine_nt_to_unix_file_name L"winex11.drv" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:file:wine_nt_to_unix_file_name L"winex11.drv" not found in /root/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"winex11.drv" not found in /root/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"winex11.drv" not found in /root/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"winex11.drv" not found in /root/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"winex11.drv" not found in /root/.wine/dosdevices/c:/windows
Xlib:  extension "GLX" missing on display ":1.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
warn:file:wine_nt_to_unix_file_name L"imm32.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:file:wine_nt_to_unix_file_name L"imm32.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:file:wine_nt_to_unix_file_name L"imm32.dll" not found in /root/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"imm32.dll" not found in /root/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"imm32.dll" not found in /root/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"imm32.dll" not found in /root/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"imm32.dll" not found in /root/.wine/dosdevices/c:/windows
warn:imm:ImmAssociateContext ((nil), 0x156e00): semi-stub
warn:module:load_builtin_dll failed to load .so lib for builtin L"C:\\Program Files\\Valve\\HLServer\\orangebox\\bin\\dedicated.dll": /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox/bin/dedicated.dll: invalid ELF header
warn:module:load_builtin_dll cannot open .so lib for builtin L"dedicated.dll": /usr/lib/wine/dedicated.dll.so: cannot open shared object file: No such file or directory
warn:file:wine_nt_to_unix_file_name L"WSOCK32.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:file:wine_nt_to_unix_file_name L"WSOCK32.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\system32\\WSOCK32.dll" -> "/root/.wine/dosdevices/c:/windows/system32/wsock32.dll" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\system32\\WSOCK32.dll" -> "/root/.wine/dosdevices/c:/windows/system32/wsock32.dll" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\system32\\WSOCK32.dll" -> "/root/.wine/dosdevices/c:/windows/system32/wsock32.dll" required a case-insensitive search
warn:module:load_builtin_dll failed to load .so lib for builtin L"C:\\windows\\system32\\WSOCK32.dll": /root/.wine/dosdevices/c:/windows/system32/wsock32.dll: invalid ELF header
warn:file:wine_nt_to_unix_file_name L"ws2_32.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:file:wine_nt_to_unix_file_name L"ws2_32.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:module:load_builtin_dll failed to load .so lib for builtin L"C:\\windows\\system32\\ws2_32.dll": /root/.wine/dosdevices/c:/windows/system32/ws2_32.dll: invalid ELF header
warn:file:wine_nt_to_unix_file_name L"iphlpapi.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:file:wine_nt_to_unix_file_name L"iphlpapi.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:file:wine_nt_to_unix_file_name L"iphlpapi.dll" not found in /root/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"iphlpapi.dll" not found in /root/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"iphlpapi.dll" not found in /root/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"iphlpapi.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox/bin
warn:file:wine_nt_to_unix_file_name L"iphlpapi.dll" not found in /root/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"iphlpapi.dll" not found in /root/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"SHELL32.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:file:wine_nt_to_unix_file_name L"SHELL32.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\system32\\SHELL32.dll" -> "/root/.wine/dosdevices/c:/windows/system32/shell32.dll" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\system32\\SHELL32.dll" -> "/root/.wine/dosdevices/c:/windows/system32/shell32.dll" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\system32\\SHELL32.dll" -> "/root/.wine/dosdevices/c:/windows/system32/shell32.dll" required a case-insensitive search
warn:module:load_builtin_dll failed to load .so lib for builtin L"C:\\windows\\system32\\SHELL32.dll": /root/.wine/dosdevices/c:/windows/system32/shell32.dll: invalid ELF header
warn:file:wine_nt_to_unix_file_name L"shlwapi.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:file:wine_nt_to_unix_file_name L"shlwapi.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:module:load_builtin_dll failed to load .so lib for builtin L"C:\\windows\\system32\\shlwapi.dll": /root/.wine/dosdevices/c:/windows/system32/shlwapi.dll: invalid ELF header
warn:file:wine_nt_to_unix_file_name L"ole32.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:file:wine_nt_to_unix_file_name L"ole32.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:module:load_builtin_dll failed to load .so lib for builtin L"C:\\windows\\system32\\ole32.dll": /root/.wine/dosdevices/c:/windows/system32/ole32.dll: invalid ELF header
warn:file:wine_nt_to_unix_file_name L"rpcrt4.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:file:wine_nt_to_unix_file_name L"rpcrt4.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:module:load_builtin_dll failed to load .so lib for builtin L"C:\\windows\\system32\\rpcrt4.dll": /root/.wine/dosdevices/c:/windows/system32/rpcrt4.dll: invalid ELF header
warn:file:wine_nt_to_unix_file_name L"comctl32.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:file:wine_nt_to_unix_file_name L"comctl32.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:file:wine_nt_to_unix_file_name L"comctl32.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:file:wine_nt_to_unix_file_name L"comctl32.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:module:load_builtin_dll failed to load .so lib for builtin L"C:\\windows\\system32\\comctl32.dll": /root/.wine/dosdevices/c:/windows/system32/comctl32.dll: invalid ELF header
warn:file:wine_nt_to_unix_file_name L"vstdlib.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:file:wine_nt_to_unix_file_name L"vstdlib.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:file:wine_nt_to_unix_file_name L"vstdlib.dll" not found in /root/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"vstdlib.dll" not found in /root/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"vstdlib.dll" not found in /root/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"vstdlib.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:file:wine_nt_to_unix_file_name L"vstdlib.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:file:wine_nt_to_unix_file_name L"vstdlib.dll" not found in /root/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"vstdlib.dll" not found in /root/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"vstdlib.dll" not found in /root/.wine/dosdevices/c:/windows
warn:module:load_builtin_dll failed to load .so lib for builtin L"C:\\Program Files\\Valve\\HLServer\\orangebox\\bin\\vstdlib.dll": /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox/bin/vstdlib.dll: invalid ELF header
warn:module:load_builtin_dll cannot open .so lib for builtin L"vstdlib.dll": /usr/lib/wine/vstdlib.dll.so: cannot open shared object file: No such file or directory
warn:file:wine_nt_to_unix_file_name L"tier0.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:file:wine_nt_to_unix_file_name L"tier0.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:file:wine_nt_to_unix_file_name L"tier0.dll" not found in /root/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"tier0.dll" not found in /root/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"tier0.dll" not found in /root/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"tier0.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:file:wine_nt_to_unix_file_name L"tier0.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:file:wine_nt_to_unix_file_name L"tier0.dll" not found in /root/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"tier0.dll" not found in /root/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"tier0.dll" not found in /root/.wine/dosdevices/c:/windows
warn:module:load_builtin_dll failed to load .so lib for builtin L"C:\\Program Files\\Valve\\HLServer\\orangebox\\bin\\tier0.dll": /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox/bin/tier0.dll: invalid ELF header
warn:module:load_builtin_dll cannot open .so lib for builtin L"tier0.dll": /usr/lib/wine/tier0.dll.so: cannot open shared object file: No such file or directory
warn:file:wine_nt_to_unix_file_name L"steam_api.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:file:wine_nt_to_unix_file_name L"steam_api.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:file:wine_nt_to_unix_file_name L"steam_api.dll" not found in /root/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"steam_api.dll" not found in /root/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"steam_api.dll" not found in /root/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"steam_api.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:file:wine_nt_to_unix_file_name L"steam_api.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:file:wine_nt_to_unix_file_name L"steam_api.dll" not found in /root/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"steam_api.dll" not found in /root/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"steam_api.dll" not found in /root/.wine/dosdevices/c:/windows
warn:module:load_builtin_dll failed to load .so lib for builtin L"C:\\Program Files\\Valve\\HLServer\\orangebox\\bin\\steam_api.dll": /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox/bin/steam_api.dll: invalid ELF header
warn:module:load_builtin_dll cannot open .so lib for builtin L"steam_api.dll": /usr/lib/wine/steam_api.dll.so: cannot open shared object file: No such file or directory
warn:file:wine_nt_to_unix_file_name L"uxtheme.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:file:wine_nt_to_unix_file_name L"uxtheme.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:file:wine_nt_to_unix_file_name L"uxtheme.dll" not found in /root/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"uxtheme.dll" not found in /root/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"uxtheme.dll" not found in /root/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"uxtheme.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox/bin
warn:file:wine_nt_to_unix_file_name L"uxtheme.dll" not found in /root/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"uxtheme.dll" not found in /root/.wine/dosdevices/c:/windows
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:file:CreateFileW Unable to create file L"\\\\.\\GDPERF" (status c0000034)
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\program files\\valve\\hlserver\\orangebox" -> "/root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\program files\\valve\\hlserver\\orangebox\\bin\\" -> "/root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox/bin" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\program files\\valve\\hlserver\\orangebox\\bin\\engine.dll" -> "/root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox/bin/engine.dll" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\program files\\valve\\hlserver\\orangebox\\bin\\engine.dll" -> "/root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox/bin/engine.dll" required a case-insensitive search
warn:module:load_builtin_dll failed to load .so lib for builtin L"C:\\program files\\valve\\hlserver\\orangebox\\bin\\engine.dll": /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox/bin/engine.dll: invalid ELF header
warn:module:load_builtin_dll cannot open .so lib for builtin L"engine.dll": /usr/lib/wine/engine.dll.so: cannot open shared object file: No such file or directory
warn:file:wine_nt_to_unix_file_name L"WINMM.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox/bin
warn:file:wine_nt_to_unix_file_name L"WINMM.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\system32\\WINMM.dll" -> "/root/.wine/dosdevices/c:/windows/system32/winmm.dll" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\system32\\WINMM.dll" -> "/root/.wine/dosdevices/c:/windows/system32/winmm.dll" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\system32\\WINMM.dll" -> "/root/.wine/dosdevices/c:/windows/system32/winmm.dll" required a case-insensitive search
warn:module:load_builtin_dll failed to load .so lib for builtin L"C:\\windows\\system32\\WINMM.dll": /root/.wine/dosdevices/c:/windows/system32/winmm.dll: invalid ELF header
warn:file:wine_nt_to_unix_file_name L"WININET.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox/bin
warn:file:wine_nt_to_unix_file_name L"WININET.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\system32\\WININET.dll" -> "/root/.wine/dosdevices/c:/windows/system32/wininet.dll" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\system32\\WININET.dll" -> "/root/.wine/dosdevices/c:/windows/system32/wininet.dll" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\system32\\WININET.dll" -> "/root/.wine/dosdevices/c:/windows/system32/wininet.dll" required a case-insensitive search
warn:module:load_builtin_dll failed to load .so lib for builtin L"C:\\windows\\system32\\WININET.dll": /root/.wine/dosdevices/c:/windows/system32/wininet.dll: invalid ELF header
warn:file:wine_nt_to_unix_file_name L"mpr.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox/bin
warn:file:wine_nt_to_unix_file_name L"mpr.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:file:wine_nt_to_unix_file_name L"mpr.dll" not found in /root/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"mpr.dll" not found in /root/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"mpr.dll" not found in /root/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"mpr.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox/bin
warn:file:wine_nt_to_unix_file_name L"mpr.dll" not found in /root/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"mpr.dll" not found in /root/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\program files\\valve\\hlserver\\orangebox\\bin\\binkw32.dll" -> "/root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox/bin/binkw32.dll" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\program files\\valve\\hlserver\\orangebox\\bin\\binkw32.dll" -> "/root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox/bin/binkw32.dll" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\program files\\valve\\hlserver\\orangebox\\bin\\binkw32.dll" -> "/root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox/bin/binkw32.dll" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\program files\\valve\\hlserver\\orangebox\\bin\\binkw32.dll" -> "/root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox/bin/binkw32.dll" required a case-insensitive search
warn:module:load_builtin_dll failed to load .so lib for builtin L"C:\\program files\\valve\\hlserver\\orangebox\\bin\\binkw32.dll": /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox/bin/binkw32.dll: invalid ELF header
warn:module:load_builtin_dll cannot open .so lib for builtin L"binkw32.dll": /usr/lib/wine/binkw32.dll.so: cannot open shared object file: No such file or directory
warn:file:wine_nt_to_unix_file_name L"wineoss.drv" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:file:wine_nt_to_unix_file_name L"wineoss.drv" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:file:wine_nt_to_unix_file_name L"wineoss.drv" not found in /root/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"wineoss.drv" not found in /root/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"wineoss.drv" not found in /root/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"wineoss.drv" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox/bin
warn:file:wine_nt_to_unix_file_name L"wineoss.drv" not found in /root/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"wineoss.drv" not found in /root/.wine/dosdevices/c:/windows
warn:midi:midiOpenSeq Can't open MIDI device '/dev/sequencer' ! (No such file or directory). If your program needs this (probably not): create it ! ("man MAKEDEV" ?)
warn:mixer:OSS_MixerInit couldn't open /dev/mixer
warn:mixer:OSS_MixerInit couldn't open /dev/mixer1
warn:mixer:OSS_MixerInit couldn't open /dev/mixer2
warn:mixer:OSS_MixerInit couldn't open /dev/mixer3
warn:mixer:OSS_MixerInit couldn't open /dev/mixer4
warn:mixer:OSS_MixerInit couldn't open /dev/mixer5
warn:mixer:OSS_MixerInit no driver
warn:mmaux:OSS_AuxInit mixer device not available !
warn:winmm:MMDRV_Install Driver initialization failed
warn:file:wine_nt_to_unix_file_name L"msacm32.drv" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:file:wine_nt_to_unix_file_name L"msacm32.drv" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:file:wine_nt_to_unix_file_name L"msacm32.drv" not found in /root/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"msacm32.drv" not found in /root/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"msacm32.drv" not found in /root/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"msacm32.drv" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox/bin
warn:file:wine_nt_to_unix_file_name L"msacm32.drv" not found in /root/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"msacm32.drv" not found in /root/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"msacm32.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:file:wine_nt_to_unix_file_name L"msacm32.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:file:wine_nt_to_unix_file_name L"msacm32.dll" not found in /root/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"msacm32.dll" not found in /root/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"msacm32.dll" not found in /root/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"msacm32.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox/bin
warn:file:wine_nt_to_unix_file_name L"msacm32.dll" not found in /root/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"msacm32.dll" not found in /root/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"midimap.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:file:wine_nt_to_unix_file_name L"midimap.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:file:wine_nt_to_unix_file_name L"midimap.dll" not found in /root/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"midimap.dll" not found in /root/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"midimap.dll" not found in /root/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"midimap.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox/bin
warn:file:wine_nt_to_unix_file_name L"midimap.dll" not found in /root/.wine/dosdevices/c:/windows/system32
warn:file:wine_nt_to_unix_file_name L"midimap.dll" not found in /root/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\program files\\valve\\hlserver\\orangebox\\bin\\inputsystem.dll" -> "/root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox/bin/inputsystem.dll" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\program files\\valve\\hlserver\\orangebox\\bin\\inputsystem.dll" -> "/root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox/bin/inputsystem.dll" required a case-insensitive search
warn:module:load_builtin_dll failed to load .so lib for builtin L"C:\\program files\\valve\\hlserver\\orangebox\\bin\\inputsystem.dll": /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox/bin/inputsystem.dll: invalid ELF header
warn:module:load_builtin_dll cannot open .so lib for builtin L"inputsystem.dll": /usr/lib/wine/inputsystem.dll.so: cannot open shared object file: No such file or directory
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\program files\\valve\\hlserver\\orangebox\\bin\\materialsystem.dll" -> "/root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox/bin/materialsystem.dll" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\program files\\valve\\hlserver\\orangebox\\bin\\materialsystem.dll" -> "/root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox/bin/materialsystem.dll" required a case-insensitive search
warn:module:load_builtin_dll failed to load .so lib for builtin L"C:\\program files\\valve\\hlserver\\orangebox\\bin\\materialsystem.dll": /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox/bin/materialsystem.dll: invalid ELF header
warn:module:load_builtin_dll cannot open .so lib for builtin L"materialsystem.dll": /usr/lib/wine/materialsystem.dll.so: cannot open shared object file: No such file or directory
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\program files\\valve\\hlserver\\orangebox\\bin\\studiorender.dll" -> "/root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox/bin/studiorender.dll" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\program files\\valve\\hlserver\\orangebox\\bin\\studiorender.dll" -> "/root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox/bin/studiorender.dll" required a case-insensitive search
warn:module:load_builtin_dll failed to load .so lib for builtin L"C:\\program files\\valve\\hlserver\\orangebox\\bin\\studiorender.dll": /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox/bin/studiorender.dll: invalid ELF header
warn:module:load_builtin_dll cannot open .so lib for builtin L"studiorender.dll": /usr/lib/wine/studiorender.dll.so: cannot open shared object file: No such file or directory
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\program files\\valve\\hlserver\\orangebox\\bin\\vphysics.dll" -> "/root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox/bin/vphysics.dll" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\program files\\valve\\hlserver\\orangebox\\bin\\vphysics.dll" -> "/root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox/bin/vphysics.dll" required a case-insensitive search
warn:module:load_builtin_dll failed to load .so lib for builtin L"C:\\program files\\valve\\hlserver\\orangebox\\bin\\vphysics.dll": /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox/bin/vphysics.dll: invalid ELF header
warn:module:load_builtin_dll cannot open .so lib for builtin L"vphysics.dll": /usr/lib/wine/vphysics.dll.so: cannot open shared object file: No such file or directory
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\program files\\valve\\hlserver\\orangebox\\bin\\datacache.dll" -> "/root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox/bin/datacache.dll" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\program files\\valve\\hlserver\\orangebox\\bin\\datacache.dll" -> "/root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox/bin/datacache.dll" required a case-insensitive search
warn:module:load_builtin_dll failed to load .so lib for builtin L"C:\\program files\\valve\\hlserver\\orangebox\\bin\\datacache.dll": /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox/bin/datacache.dll: invalid ELF header
warn:module:load_builtin_dll cannot open .so lib for builtin L"datacache.dll": /usr/lib/wine/datacache.dll.so: cannot open shared object file: No such file or directory
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\program files\\valve\\hlserver\\orangebox\\bin\\vgui2.dll" -> "/root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox/bin/vgui2.dll" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\program files\\valve\\hlserver\\orangebox\\bin\\vgui2.dll" -> "/root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox/bin/vgui2.dll" required a case-insensitive search
warn:module:load_builtin_dll failed to load .so lib for builtin L"C:\\program files\\valve\\hlserver\\orangebox\\bin\\vgui2.dll": /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox/bin/vgui2.dll: invalid ELF header
warn:module:load_builtin_dll cannot open .so lib for builtin L"vgui2.dll": /usr/lib/wine/vgui2.dll.so: cannot open shared object file: No such file or directory
warn:file:wine_nt_to_unix_file_name L"OLEAUT32.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox/bin
warn:file:wine_nt_to_unix_file_name L"OLEAUT32.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\system32\\OLEAUT32.dll" -> "/root/.wine/dosdevices/c:/windows/system32/oleaut32.dll" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"OLEAUT32.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox/bin
warn:file:wine_nt_to_unix_file_name L"OLEAUT32.dll" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\system32\\OLEAUT32.dll" -> "/root/.wine/dosdevices/c:/windows/system32/oleaut32.dll" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\system32\\OLEAUT32.dll" -> "/root/.wine/dosdevices/c:/windows/system32/oleaut32.dll" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\windows\\system32\\OLEAUT32.dll" -> "/root/.wine/dosdevices/c:/windows/system32/oleaut32.dll" required a case-insensitive search
warn:module:load_builtin_dll failed to load .so lib for builtin L"C:\\windows\\system32\\OLEAUT32.dll": /root/.wine/dosdevices/c:/windows/system32/oleaut32.dll: invalid ELF header
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\program files\\valve\\hlserver\\orangebox\\bin\\shaderapiempty.dll" -> "/root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox/bin/shaderapiempty.dll" required a case-insensitive search
warn:file:wine_nt_to_unix_file_name L"\\??\\C:\\program files\\valve\\hlserver\\orangebox\\bin\\shaderapiempty.dll" -> "/root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox/bin/shaderapiempty.dll" required a case-insensitive search
warn:module:load_builtin_dll failed to load .so lib for builtin L"C:\\program files\\valve\\hlserver\\orangebox\\bin\\shaderapiempty.dll": /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox/bin/shaderapiempty.dll: invalid ELF header
warn:module:load_builtin_dll cannot open .so lib for builtin L"shaderapiempty.dll": /usr/lib/wine/shaderapiempty.dll.so: cannot open shared object file: No such file or directory
warn:debugstr:OutputDebugStringA Warning: falling back to auto detection of vproject directory.

warn:file:wine_nt_to_unix_file_name L"gameinfo.txt" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:ntdll:NtQueryFullAttributesFile L"\\??\\C:\\program files\\valve\\hlserver\\orangebox\\gameinfo.txt" not found (c0000034)
warn:file:wine_nt_to_unix_file_name L"gameinfo.txt" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer
warn:ntdll:NtQueryFullAttributesFile L"\\??\\C:\\program files\\valve\\hlserver\\gameinfo.txt" not found (c0000034)
warn:file:wine_nt_to_unix_file_name L"gameinfo.txt" not found in /root/.wine/dosdevices/c:/Program Files/Valve
warn:ntdll:NtQueryFullAttributesFile L"\\??\\C:\\program files\\valve\\gameinfo.txt" not found (c0000034)
warn:file:wine_nt_to_unix_file_name L"gameinfo.txt" not found in /root/.wine/dosdevices/c:/Program Files
warn:ntdll:NtQueryFullAttributesFile L"\\??\\C:\\program files\\gameinfo.txt" not found (c0000034)
warn:file:wine_nt_to_unix_file_name L"gameinfo.txt" not found in /root/.wine/dosdevices/c:
warn:ntdll:NtQueryFullAttributesFile L"\\??\\C:\\gameinfo.txt" not found (c0000034)
warn:file:wine_nt_to_unix_file_name L"gameinfo.txt" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:ntdll:NtQueryFullAttributesFile L"\\??\\C:\\program files\\valve\\hlserver\\orangebox\\gameinfo.txt" not found (c0000034)
warn:file:wine_nt_to_unix_file_name L"gameinfo.txt" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:ntdll:NtQueryFullAttributesFile L"\\??\\C:\\program files\\valve\\hlserver\\orangebox\\gameinfo.txt" not found (c0000034)
warn:file:wine_nt_to_unix_file_name L"gameinfo.txt" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer
warn:ntdll:NtQueryFullAttributesFile L"\\??\\C:\\program files\\valve\\hlserver\\gameinfo.txt" not found (c0000034)
warn:file:wine_nt_to_unix_file_name L"gameinfo.txt" not found in /root/.wine/dosdevices/c:/Program Files/Valve
warn:ntdll:NtQueryFullAttributesFile L"\\??\\C:\\program files\\valve\\gameinfo.txt" not found (c0000034)
warn:file:wine_nt_to_unix_file_name L"gameinfo.txt" not found in /root/.wine/dosdevices/c:/Program Files
warn:ntdll:NtQueryFullAttributesFile L"\\??\\C:\\program files\\gameinfo.txt" not found (c0000034)
warn:file:wine_nt_to_unix_file_name L"gameinfo.txt" not found in /root/.wine/dosdevices/c:
warn:ntdll:NtQueryFullAttributesFile L"\\??\\C:\\gameinfo.txt" not found (c0000034)
warn:file:wine_nt_to_unix_file_name L"gameinfo.txt" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox
warn:ntdll:NtQueryFullAttributesFile L"\\??\\C:\\program files\\valve\\hlserver\\orangebox\\gameinfo.txt" not found (c0000034)
warn:debugstr:OutputDebugStringA Unable to find gameinfo.txt. Solutions:

1. Read http://www.valve-erc.com/srcsdk/faq.html#NoGameDir
2. Run vconfig to specify which game you're working on.
3. Add -game <path> on the command line where <path> is the directory that gameinfo.txt is in.


warn:file:wine_nt_to_unix_file_name L"vconfig.exe" not found in /root/.wine/dosdevices/c:/Program Files/Valve/HLServer/orangebox/bin
warn:ntdll:NtQueryFullAttributesFile L"\\??\\C:\\Program Files\\Valve\\HLServer\\orangebox\\bin\\vconfig.exe" not found (c0000034)
warn:debugstr:OutputDebugStringA Unable to find gameinfo.txt. Solutions:

1. Read http://www.valve-erc.com/srcsdk/faq.html#NoGameDir
2. Run vconfig to specify which game you're working on.
3. Add -game <path> on the command line where <path> is the directory that gameinfo.txt is in.



```
Could someone point me in the right direction?

---

