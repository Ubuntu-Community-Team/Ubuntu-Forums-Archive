---
title: "The Binding of Isaac on WINE"
date: 2011-09-28
forum: Wine
---

### Post by Kimos on 2011-09-28
I grabbed a copy of The Binding of Isaac on Steam. The game seems to be Flash based so I thought I had a pretty good chance of getting it running.

[http://store.steampowered.com/app/113200/](http://store.steampowered.com/app/113200/)

Installed it through Steam on WINE no problem. When I launch it, it just hangs. I get a transparent Window on screen but nothing else. I don't even know what to try next to troubleshoot it.

Here is the extremely verbose output from wine with all warnings, if anyone has any insight.

```
kevin@zim:~/source/cliftonstudios.ca$ WINEDEBUG=warn+all wine /home/kevin/.local/share/wineprefixes/steam/drive_c/Program\ Files/Steam/steamapps/common/the\ binding\ of\ isaac/Binding_of_Isaac.exe
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows" not found (c0000035)
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows\\system32" not found (c0000035)
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows" not found (c0000035)
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows\\system32" not found (c0000035)
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows\\system32\\wineboot.exe.manifest" not found (c0000034)
warn:ntdll:NtPowerInformation semi-stub: ProcessorInformation
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows\\wininit.ini" not found (c0000034)
warn:file:CreateFileW Unable to create file L"C:\\windows\\wininit.ini" (status c0000034)
warn:profile:PROFILE_Open profile file L"C:\\windows\\wininit.ini" not found
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows\\system32\\dllcache\\" not found (c0000034)
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows" not found (c0000035)
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows\\system32" not found (c0000035)
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows\\system32\\winemenubuilder.exe.manifest" not found (c0000034)
warn:module:load_builtin_dll failed to load .so lib for builtin L"C:\\windows\\system32\\oleaut32.dll": /home/kevin/.wine/dosdevices/c:/windows/system32/OLEAUT32.DLL: invalid ELF header
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows" not found (c0000035)
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows\\system32" not found (c0000035)
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows\\system32\\services.exe.manifest" not found (c0000034)
warn:font:AddFontToList Unable to load font "/home/kevin/.wine/dosdevices/c:/windows/Fonts/vgasys.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/home/kevin/.wine/dosdevices/c:/windows/Fonts/vga850.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/usr/bin/../share/wine/fonts/vga850.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/home/kevin/.wine/dosdevices/c:/windows/Fonts/vgafix.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/usr/bin/../share/wine/fonts/vgafix.fon"/(nil) err = 1
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smae1255.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smae1257.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//ssee1257.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//hvgasys.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//jsmalle.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coure.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smallet.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coue1256.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smallee.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgas874.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//couree.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//ssee1256.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smae1256.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserife.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coue1257.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasysr.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserifee.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasyse.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coue1255.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserifet.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgas1255.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smalleg.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgas1256.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//ssee874.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasys.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasyst.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasysg.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//courer.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgas1257.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//jvgasys.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//cvgasys.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserifeg.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//ssee1255.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smaller.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smalle.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//couret.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//svgasys.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserifer.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coureg.fon"/(nil)
warn:font:AddFontToList Unable to load font "/home/kevin/.wine/dosdevices/c:/windows/Fonts/coure.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/home/kevin/.wine/dosdevices/c:/windows/Fonts/sserife.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/home/kevin/.wine/dosdevices/c:/windows/Fonts/serife.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/usr/bin/../share/wine/fonts/serife.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/home/kevin/.wine/dosdevices/c:/windows/Fonts/smalle.fon"/(nil) err = 1
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program.exe" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common.exe" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Mobile" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Mobile.exe" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Mobile" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Mobile Device" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Mobile Device.exe" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Mobile Device" not found (c0000034)
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows" not found (c0000035)
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows\\system32" not found (c0000035)
warn:actctx:parse_assembly_elem unknown element L"trustInfo"
warn:actctx:parse_file_elem asmv2:hash (undocumented) not supported
warn:actctx:parse_file_elem asmv2:hash (undocumented) not supported
warn:actctx:parse_file_elem asmv2:hash (undocumented) not supported
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Mobile Device Support\\ADVAPI32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\ADVAPI32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Mobile Device Support\\ADVAPI32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\ADVAPI32.dll" not found (c0000034)
warn:module:load_builtin_dll failed to load .so lib for builtin L"C:\\windows\\winsxs\\x86_Microsoft.VC80.CRT_1fc8b3b9a1e18e3b_8.0.50727.6195_x-ww_44262b86\\MSVCP80.dll": /home/kevin/.wine/dosdevices/c:/windows/winsxs/x86_Microsoft.VC80.CRT_1fc8b3b9a1e18e3b_8.0.50727.6195_x-ww_44262b86/msvcp80.dll: invalid ELF header
warn:module:load_builtin_dll failed to load .so lib for builtin L"C:\\windows\\winsxs\\x86_Microsoft.VC80.CRT_1fc8b3b9a1e18e3b_8.0.50727.6195_x-ww_44262b86\\MSVCR80.dll": /home/kevin/.wine/dosdevices/c:/windows/winsxs/x86_Microsoft.VC80.CRT_1fc8b3b9a1e18e3b_8.0.50727.6195_x-ww_44262b86/msvcr80.dll: invalid ELF header
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Mobile Device Support\\msvcrt.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\msvcrt.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Mobile Device Support\\msvcrt.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\msvcrt.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Mobile Device Support\\SHLWAPI.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\SHLWAPI.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Mobile Device Support\\user32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\user32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Mobile Device Support\\gdi32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\gdi32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Mobile Device Support\\version.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\version.dll" not found (c0000034)
warn:msvcrt:msvcrt_init_console :Console handle Initialisation FAILED!
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Mobile Device Support\\MSCoree.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\MSCoree.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Mobile Device Support\\PGORT80.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\PGORT80.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\PGORT80.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system\\PGORT80.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\PGORT80.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\PGORT80.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\PGORT80.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\QuickTime\\QTSystem\\PGORT80.dll" not found (c0000034)
warn:keyboard:X11DRV_KEYBOARD_DetectLayout 6 keysyms per keycode not supported, set to 4
warn:keyboard:X11DRV_KEYBOARD_DetectLayout Using closest match (United States keyboard layout (phantom key version)) for scan/virtual codes mapping.
warn:keyboard:X11DRV_InitKeyboard vkey 0008 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 010D is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0124 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0126 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0121 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0125 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0127 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0123 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0128 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0122 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 012D is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 012E is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 00A4 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 01A5 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 01B3 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 01B3 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 012C is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 01B4 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0003 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard No more vkeys available!
warn:class:CLASS_RegisterClass Win extra bytes 44 is > 40
warn:font:AddFontToList Unable to load font "/home/kevin/.wine/dosdevices/c:/windows/Fonts/vgasys.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/home/kevin/.wine/dosdevices/c:/windows/Fonts/vga850.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/usr/bin/../share/wine/fonts/vga850.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/home/kevin/.wine/dosdevices/c:/windows/Fonts/vgafix.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/usr/bin/../share/wine/fonts/vgafix.fon"/(nil) err = 1
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smae1255.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smae1257.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//ssee1257.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//hvgasys.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//jsmalle.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coure.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smallet.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coue1256.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smallee.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgas874.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//couree.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//ssee1256.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smae1256.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserife.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coue1257.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasysr.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserifee.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasyse.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coue1255.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserifet.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgas1255.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smalleg.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgas1256.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//ssee874.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasys.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasyst.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasysg.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//courer.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgas1257.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//jvgasys.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//cvgasys.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserifeg.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//ssee1255.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smaller.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smalle.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//couret.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//svgasys.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserifer.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coureg.fon"/(nil)
warn:font:AddFontToList Unable to load font "/home/kevin/.wine/dosdevices/c:/windows/Fonts/coure.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/home/kevin/.wine/dosdevices/c:/windows/Fonts/sserife.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/home/kevin/.wine/dosdevices/c:/windows/Fonts/serife.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/usr/bin/../share/wine/fonts/serife.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/home/kevin/.wine/dosdevices/c:/windows/Fonts/smalle.fon"/(nil) err = 1
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows" not found (c0000035)
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows\\system32" not found (c0000035)
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows\\system32\\explorer.exe.manifest" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Mobile Device Support\\winex11.drv" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\winex11.drv" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Mobile Device Support\\imm32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\imm32.dll" not found (c0000034)
warn:keyboard:X11DRV_KEYBOARD_DetectLayout 6 keysyms per keycode not supported, set to 4
warn:keyboard:X11DRV_KEYBOARD_DetectLayout Using closest match (United States keyboard layout (phantom key version)) for scan/virtual codes mapping.
warn:keyboard:X11DRV_InitKeyboard vkey 0008 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 010D is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0124 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0126 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0121 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0125 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0127 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0123 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0128 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0122 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 012D is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 012E is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 00A4 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 01A5 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 01B3 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 01B3 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 012C is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 01B4 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0003 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard No more vkeys available!
warn:class:CLASS_RegisterClass Win extra bytes 44 is > 40
warn:debugstr:OutputDebugStringA "YSLoader checking for parameters in environment variable \"AppleMobileDeviceService.exe.ysLoaderConfig\"\n"
warn:font:AddFontToList Unable to load font "/home/kevin/.wine/dosdevices/c:/windows/Fonts/vgasys.fon"/(nil) err = 1
warn:debugstr:OutputDebugStringA "YSLoader checking for parameters in environment variable \"com.apple.global.ysLoaderConfig\"\n"
warn:font:AddFontToList Unable to load font "/home/kevin/.wine/dosdevices/c:/windows/Fonts/vga850.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/usr/bin/../share/wine/fonts/vga850.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/home/kevin/.wine/dosdevices/c:/windows/Fonts/vgafix.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/usr/bin/../share/wine/fonts/vgafix.fon"/(nil) err = 1
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Mobile Device Support\\ASL.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Mobile Device Support\\ASL.dll" not found (c0000034)
warn:module:load_builtin_dll failed to load .so lib for builtin L"C:\\Program Files\\Common Files\\Apple\\Apple Application Support\\ASL.dll": /home/kevin/.wine/dosdevices/c:/Program Files/Common Files/Apple/Apple Application Support/ASL.dll: invalid ELF header
warn:module:load_builtin_dll cannot open .so lib for builtin L"ASL.dll": /usr/bin/../lib/wine/asl.dll.so: cannot open shared object file: No such file or directory
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smae1255.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smae1257.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//ssee1257.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//hvgasys.fon"/(nil)
warn:module:alloc_module disabling no-exec because of L"ASL.dll"
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//jsmalle.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coure.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smallet.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coue1256.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smallee.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgas874.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//couree.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//ssee1256.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smae1256.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserife.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coue1257.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasysr.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserifee.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasyse.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coue1255.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserifet.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgas1255.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smalleg.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgas1256.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//ssee874.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasys.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasyst.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasysg.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//courer.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgas1257.fon"/(nil)
warn:actctx:parse_file_elem asmv2:hash (undocumented) not supported
warn:actctx:parse_file_elem asmv2:hash (undocumented) not supported
warn:actctx:parse_file_elem asmv2:hash (undocumented) not supported
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//jvgasys.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//cvgasys.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserifeg.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//ssee1255.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smaller.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smalle.fon"/(nil)
warn:debugstr:OutputDebugStringA "ASL checking for logging parameters in environment variable \"AppleMobileDeviceService.exe.log\"\n"
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//couret.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//svgasys.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserifer.fon"/(nil)
warn:debugstr:OutputDebugStringA "ASL checking for logging parameters in environment variable \"asl.log\"\n"
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coureg.fon"/(nil)
warn:font:AddFontToList Unable to load font "/home/kevin/.wine/dosdevices/c:/windows/Fonts/coure.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/home/kevin/.wine/dosdevices/c:/windows/Fonts/sserife.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/home/kevin/.wine/dosdevices/c:/windows/Fonts/serife.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/usr/bin/../share/wine/fonts/serife.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/home/kevin/.wine/dosdevices/c:/windows/Fonts/smalle.fon"/(nil) err = 1
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows" not found (c0000035)
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows\\profiles" not found (c0000035)
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows\\profiles\\kevin" not found (c0000035)
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows\\profiles\\kevin\\Application Data" not found (c0000035)
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows\\profiles\\kevin\\Application Data\\Apple Computer" not found (c0000035)
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows\\profiles\\kevin\\Application Data\\Apple Computer\\Logs" not found (c0000035)
warn:debugstr:OutputDebugStringA "ASL logging to file \"C:\\windows\\profiles\\kevin\\Application Data\\Apple Computer\\Logs\\asl.190316_28Sep11.log\"\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] \n\t=====================================\n\t AppleMobileDeviceService.exe begins\n\t=====================================\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] parent process: 14 \"services.exe\"\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] main thread 18\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] command line: \"C:\\Program Files\\Common Files\\Apple\\Mobile Device Support\\AppleMobileDeviceService.exe\"\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] WINEDEBUG=warn+all\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] ORBIT_SOCKETDIR=/tmp/orbit-kevin\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] SSH_AGENT_PID=1481\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] TERM=xterm\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] SHELL=/bin/bash\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] XDG_SESSION_COOKIE=2bc2d852416564a302a8c7f14b512a6d-1316992340.955173-784345667\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] WINDOWID=62981268\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] GNOME_KEYRING_CONTROL=/tmp/keyring-FFgpsE\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] GTK_MODULES=canberra-gtk-module\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] USER=kevin\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] LS_COLORS=rs=0:di=01;34:ln=01;36:hl=44;37:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.zip=01;31:*.z=01;3"...
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] SSH_AUTH_SOCK=/tmp/keyring-FFgpsE/ssh\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] DEFAULTS_PATH=/usr/share/gconf/gnome.default.path\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] SESSION_MANAGER=local/zim:@/tmp/.ICE-unix/1390,unix/zim:/tmp/.ICE-unix/1390\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] USERNAME=kevin\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] XDG_CONFIG_DIRS=/etc/xdg/xdg-gnome:/etc/xdg\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] DESKTOP_SESSION=gnome\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] EDITOR=/usr/bin/vi\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] GDM_KEYBOARD_LAYOUT=us\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] LANG=en_CA.utf8\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] MANDATORY_PATH=/usr/share/gconf/gnome.mandatory.path\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] GDM_LANG=en_CA.utf8\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] GDMSESSION=gnome\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] SPEECHD_PORT=7560\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] SHLVL=1\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] GNOME_DESKTOP_SESSION_ID=this-is-deprecated\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] LOGNAME=kevin\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] XDG_DATA_DIRS=/usr/share/gnome:/usr/local/share/:/usr/share/\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-X6mVtmbwIt,guid=d9fb0eccce9c330b1b0ccfef4e7fb5a3\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] LESSOPEN=| /usr/bin/lesspipe %s\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] DISPLAY=:0.0\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] LESSCLOSE=/usr/bin/lesspipe %s %s\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] XAUTHORITY=/var/run/gdm/auth-for-kevin-RJ5qEl/database\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] COLORTERM=gnome-terminal\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] _=/usr/bin/wine\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] WINELOADERNOEXEC=1\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] APPDATA=C:\\windows\\profiles\\kevin\\Application Data\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] asl.log=Destination=file\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] CLASSPATH=.;;C:\\Program Files\\QuickTime\\QTSystem\\QTJava.zip\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] CommonProgramFiles=C:\\Program Files\\Common Files\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] LOCALAPPDATA=C:\\windows\\profiles\\kevin\\Local Settings\\Application Data\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] NUMBER_OF_PROCESSORS=4\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] OS=Windows_NT\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] PATHEXT=.COM;.EXE;.BAT;.CMD;.VBS;.VBE;.JS;.JSE;.WSF;.WSH\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] PROCESSOR_ARCHITECTURE=x86\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] PROCESSOR_IDENTIFIER=x86 Family 6 Model 30 Stepping 5, GenuineIntel\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] PROCESSOR_LEVEL=6\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] PROCESSOR_REVISION=1e05\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] ProgramFiles=C:\\Program Files\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] QTJAVA=C:\\Program Files\\QuickTime\\QTSystem\\QTJava.zip\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] SystemDrive=c:\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] SYSTEMROOT=C:\\windows\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] winsysdir=C:\\windows\\system32\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] ComSpec=C:\\windows\\system32\\cmd.exe\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] PATH=C:\\windows\\system32;C:\\windows;C:\\Program Files\\QuickTime\\QTSystem\\\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] TEMP=C:\\windows\\profiles\\kevin\\Temp\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] TMP=C:\\windows\\profiles\\kevin\\Temp\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] windir=C:\\windows\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] ALLUSERSPROFILE=C:\\windows\\profiles\\All Users\n"
warn:module:load_builtin_dll failed to load .so lib for builtin L"C:\\Program Files\\Common Files\\Apple\\Mobile Device Support\\AppleMobileDeviceService_main.dll": /home/kevin/.wine/dosdevices/c:/Program Files/Common Files/Apple/Mobile Device Support/AppleMobileDeviceService_main.dll: invalid ELF header
warn:module:load_builtin_dll cannot open .so lib for builtin L"AppleMobileDeviceService_main.dll": /usr/bin/../lib/wine/applemobiledeviceservice_main.dll.so: cannot open shared object file: No such file or directory
warn:actctx:parse_assembly_elem unknown element L"trustInfo"
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Mobile Device Support\\WSOCK32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Apple Application Support\\WSOCK32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\WSOCK32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Mobile Device Support\\ws2_32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Apple Application Support\\ws2_32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\ws2_32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Mobile Device Support\\iphlpapi.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Apple Application Support\\iphlpapi.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\iphlpapi.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Mobile Device Support\\iphlpapi.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Apple Application Support\\iphlpapi.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\iphlpapi.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Mobile Device Support\\SETUPAPI.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Apple Application Support\\SETUPAPI.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\SETUPAPI.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Mobile Device Support\\SETUPAPI.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Apple Application Support\\SETUPAPI.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\SETUPAPI.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Mobile Device Support\\winspool.drv" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Apple Application Support\\winspool.drv" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\winspool.drv" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Mobile Device Support\\winspool.drv" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Apple Application Support\\winspool.drv" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\winspool.drv" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Mobile Device Support\\rpcrt4.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Apple Application Support\\rpcrt4.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\rpcrt4.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Mobile Device Support\\WTSAPI32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Apple Application Support\\WTSAPI32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\WTSAPI32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Mobile Device Support\\WTSAPI32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Apple Application Support\\WTSAPI32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\WTSAPI32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Mobile Device Support\\USERENV.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Apple Application Support\\USERENV.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\USERENV.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Mobile Device Support\\CoreFoundation.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Mobile Device Support\\CoreFoundation.dll" not found (c0000034)
warn:module:load_builtin_dll failed to load .so lib for builtin L"C:\\Program Files\\Common Files\\Apple\\Apple Application Support\\CoreFoundation.dll": /home/kevin/.wine/dosdevices/c:/Program Files/Common Files/Apple/Apple Application Support/CoreFoundation.dll: invalid ELF header
warn:module:load_builtin_dll cannot open .so lib for builtin L"CoreFoundation.dll": /usr/bin/../lib/wine/corefoundation.dll.so: cannot open shared object file: No such file or directory
warn:actctx:parse_file_elem asmv2:hash (undocumented) not supported
warn:actctx:parse_file_elem asmv2:hash (undocumented) not supported
warn:actctx:parse_file_elem asmv2:hash (undocumented) not supported
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Mobile Device Support\\SHELL32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Apple Application Support\\SHELL32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\SHELL32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Mobile Device Support\\comctl32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Apple Application Support\\comctl32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\comctl32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Mobile Device Support\\comctl32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Apple Application Support\\comctl32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\comctl32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Mobile Device Support\\pthreadVC2.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Mobile Device Support\\pthreadVC2.dll" not found (c0000034)
warn:module:load_builtin_dll failed to load .so lib for builtin L"C:\\Program Files\\Common Files\\Apple\\Apple Application Support\\pthreadVC2.dll": /home/kevin/.wine/dosdevices/c:/Program Files/Common Files/Apple/Apple Application Support/pthreadVC2.dll: invalid ELF header
warn:module:load_builtin_dll cannot open .so lib for builtin L"pthreadVC2.dll": /usr/bin/../lib/wine/pthreadvc2.dll.so: cannot open shared object file: No such file or directory
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Mobile Device Support\\objc.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Mobile Device Support\\objc.dll" not found (c0000034)
warn:module:load_builtin_dll failed to load .so lib for builtin L"C:\\Program Files\\Common Files\\Apple\\Apple Application Support\\objc.dll": /home/kevin/.wine/dosdevices/c:/Program Files/Common Files/Apple/Apple Application Support/objc.dll: invalid ELF header
warn:module:load_builtin_dll cannot open .so lib for builtin L"objc.dll": /usr/bin/../lib/wine/objc.dll.so: cannot open shared object file: No such file or directory
warn:module:alloc_module disabling no-exec because of L"objc.dll"
warn:actctx:parse_file_elem asmv2:hash (undocumented) not supported
warn:actctx:parse_file_elem asmv2:hash (undocumented) not supported
warn:actctx:parse_file_elem asmv2:hash (undocumented) not supported
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Mobile Device Support\\libdispatch.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Mobile Device Support\\libdispatch.dll" not found (c0000034)
warn:module:load_builtin_dll failed to load .so lib for builtin L"C:\\Program Files\\Common Files\\Apple\\Apple Application Support\\libdispatch.dll": /home/kevin/.wine/dosdevices/c:/Program Files/Common Files/Apple/Apple Application Support/libdispatch.dll: invalid ELF header
warn:module:load_builtin_dll cannot open .so lib for builtin L"libdispatch.dll": /usr/bin/../lib/wine/libdispatch.dll.so: cannot open shared object file: No such file or directory
warn:module:alloc_module disabling no-exec because of L"libdispatch.dll"
warn:actctx:parse_file_elem asmv2:hash (undocumented) not supported
warn:actctx:parse_file_elem asmv2:hash (undocumented) not supported
warn:actctx:parse_file_elem asmv2:hash (undocumented) not supported
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Mobile Device Support\\icuin40.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Mobile Device Support\\icuin40.dll" not found (c0000034)
warn:module:load_builtin_dll failed to load .so lib for builtin L"C:\\Program Files\\Common Files\\Apple\\Apple Application Support\\icuin40.dll": /home/kevin/.wine/dosdevices/c:/Program Files/Common Files/Apple/Apple Application Support/icuin40.dll: invalid ELF header
warn:module:load_builtin_dll cannot open .so lib for builtin L"icuin40.dll": /usr/bin/../lib/wine/icuin40.dll.so: cannot open shared object file: No such file or directory
warn:actctx:parse_file_elem asmv2:hash (undocumented) not supported
warn:actctx:parse_file_elem asmv2:hash (undocumented) not supported
warn:actctx:parse_file_elem asmv2:hash (undocumented) not supported
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Mobile Device Support\\icuuc40.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Mobile Device Support\\icuuc40.dll" not found (c0000034)
warn:module:load_builtin_dll failed to load .so lib for builtin L"C:\\Program Files\\Common Files\\Apple\\Apple Application Support\\icuuc40.dll": /home/kevin/.wine/dosdevices/c:/Program Files/Common Files/Apple/Apple Application Support/icuuc40.dll: invalid ELF header
warn:module:load_builtin_dll cannot open .so lib for builtin L"icuuc40.dll": /usr/bin/../lib/wine/icuuc40.dll.so: cannot open shared object file: No such file or directory
warn:keyboard:X11DRV_KEYBOARD_DetectLayout 6 keysyms per keycode not supported, set to 4
warn:actctx:parse_file_elem asmv2:hash (undocumented) not supported
warn:actctx:parse_file_elem asmv2:hash (undocumented) not supported
warn:actctx:parse_file_elem asmv2:hash (undocumented) not supported
warn:keyboard:X11DRV_KEYBOARD_DetectLayout Using closest match (United States keyboard layout (phantom key version)) for scan/virtual codes mapping.
warn:keyboard:X11DRV_InitKeyboard vkey 0008 is being used by more than one keycode
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Mobile Device Support\\icudt40.dll" not found (c0000034)
warn:keyboard:X11DRV_InitKeyboard vkey 010D is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0124 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0126 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0121 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0125 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0127 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0123 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0128 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0122 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 012D is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 012E is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 00A4 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 01A5 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 01B3 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 01B3 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 012C is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 01B4 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0003 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard No more vkeys available!
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Mobile Device Support\\icudt40.dll" not found (c0000034)
warn:module:load_builtin_dll failed to load .so lib for builtin L"C:\\Program Files\\Common Files\\Apple\\Apple Application Support\\icudt40.dll": /home/kevin/.wine/dosdevices/c:/Program Files/Common Files/Apple/Apple Application Support/icudt40.dll: invalid ELF header
warn:module:load_builtin_dll cannot open .so lib for builtin L"icudt40.dll": /usr/bin/../lib/wine/icudt40.dll.so: cannot open shared object file: No such file or directory
warn:class:CLASS_RegisterClass Win extra bytes 44 is > 40
warn:winspool:WINSPOOL_GetDWORDFromReg Got ret = 2 on name dnsTimeout
warn:winspool:WINSPOOL_GetDWORDFromReg Got ret = 2 on name txTimeout
warn:winspool:WINSPOOL_GetDWORDFromReg Got ret = 2 on name dnsTimeout
warn:winspool:WINSPOOL_GetDWORDFromReg Got ret = 2 on name txTimeout
warn:winspool:WINSPOOL_GetDWORDFromReg Got ret = 2 on name dnsTimeout
warn:winspool:WINSPOOL_GetDWORDFromReg Got ret = 2 on name txTimeout
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Mobile Device Support\\localspl.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Apple Application Support\\localspl.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\localspl.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Mobile Device Support\\localspl.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Apple Application Support\\localspl.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\localspl.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Mobile Device Support\\spoolss.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Apple Application Support\\spoolss.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\spoolss.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Mobile Device Support\\uxtheme.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Apple Application Support\\uxtheme.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\uxtheme.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Mobile Device Support\\ole32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Apple Application Support\\ole32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\ole32.dll" not found (c0000034)
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows\\system32\\(None)" not found (c0000034)
warn:file:CreateFileW Unable to create file L"(None)" (status c0000034)
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows\\(None)" not found (c0000034)
warn:file:CreateFileW Unable to create file L"C:\\windows\\(None)" (status c0000034)
warn:ntdll:FILE_CreateFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Apple Application Support\\CoreFoundation.resources\\Info-windows.plist" not found (c0000034)
warn:file:CreateFileW Unable to create file L"C:\\Program Files\\Common Files\\Apple\\Apple Application Support\\CoreFoundation.resources\\Info-windows.plist" (status c0000034)
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
warn:sync:SetNamedPipeHandleState stub: 0xf0 0xbae45c/2 (nil) (nil)
warn:setupapi:SetupDiGetClassDevsExW unsupported flags 00000002
warn:setupapi:SetupDiGetClassDevsExW unsupported flags 00000002
fixme:win:RegisterDeviceNotificationA (hwnd=0x150010, filter=0xcae9d4,flags=0x00000001) returns a fake device notification handle!
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program.exe" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] \n\t===================================\n\t AppleMobileDeviceService.exe ends\n\t===================================\n"
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Mobile Device Support\\mscoree.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\mscoree.dll" not found (c0000034)
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] EXCEPTION_ACCESS_VIOLATION: The thread tried to read from or write to a virtual address for which it does not have the appropriate access.\n"
warn:debugstr:OutputDebugStringA "[YSLoader AppleMobileDeviceService.exe] \n\t====================\n\t  thread 27 crashes\n\t====================\n"
wine: Unhandled page fault on write access to 0xfeeeff1a at address 0x382dc5 (thread 001b), starting debugger...
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Mobile Device Support\\winedbg.exe" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Common Files\\Apple\\Apple Application Support\\winedbg.exe" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\winedbg.exe" not found (c0000034)
warn:rpc:RPCRT4_default_receive_fragment Short read of header, -1 bytes
warn:rpc:RPCRT4_io_thread receive failed with error 6be
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows" not found (c0000035)
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows\\system32" not found (c0000035)
warn:actctx:parse_assembly_elem unknown element L"trustInfo"
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Bonjour\\WS2_32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\WS2_32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Bonjour\\IPHLPAPI.DLL" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\IPHLPAPI.DLL" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Bonjour\\IPHLPAPI.DLL" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\IPHLPAPI.DLL" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Bonjour\\advapi32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\advapi32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Bonjour\\advapi32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\advapi32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Bonjour\\NETAPI32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\NETAPI32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Bonjour\\NETAPI32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\NETAPI32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Bonjour\\POWRPROF.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\POWRPROF.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Bonjour\\POWRPROF.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\POWRPROF.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Bonjour\\USER32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\USER32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Bonjour\\gdi32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\gdi32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Bonjour\\version.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\version.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Bonjour\\ole32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\ole32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Bonjour\\rpcrt4.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\rpcrt4.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Bonjour\\OLEAUT32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\OLEAUT32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Bonjour\\OLEAUT32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\OLEAUT32.dll" not found (c0000034)
warn:module:load_builtin_dll failed to load .so lib for builtin L"C:\\windows\\system32\\OLEAUT32.dll": /home/kevin/.wine/dosdevices/c:/windows/system32/OLEAUT32.DLL: invalid ELF header
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:font:AddFontToList Unable to load font "/home/kevin/.wine/dosdevices/c:/windows/Fonts/vgasys.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/home/kevin/.wine/dosdevices/c:/windows/Fonts/vga850.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/usr/bin/../share/wine/fonts/vga850.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/home/kevin/.wine/dosdevices/c:/windows/Fonts/vgafix.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/usr/bin/../share/wine/fonts/vgafix.fon"/(nil) err = 1
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smae1255.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smae1257.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//ssee1257.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//hvgasys.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//jsmalle.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coure.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smallet.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coue1256.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smallee.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgas874.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//couree.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//ssee1256.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smae1256.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserife.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coue1257.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasysr.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserifee.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasyse.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coue1255.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserifet.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgas1255.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smalleg.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgas1256.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//ssee874.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasys.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasyst.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasysg.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//courer.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgas1257.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//jvgasys.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//cvgasys.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserifeg.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//ssee1255.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smaller.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smalle.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//couret.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//svgasys.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserifer.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coureg.fon"/(nil)
warn:font:AddFontToList Unable to load font "/home/kevin/.wine/dosdevices/c:/windows/Fonts/coure.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/home/kevin/.wine/dosdevices/c:/windows/Fonts/sserife.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/home/kevin/.wine/dosdevices/c:/windows/Fonts/serife.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/usr/bin/../share/wine/fonts/serife.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/home/kevin/.wine/dosdevices/c:/windows/Fonts/smalle.fon"/(nil) err = 1
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Bonjour\\winex11.drv" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\winex11.drv" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Bonjour\\imm32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\imm32.dll" not found (c0000034)
warn:keyboard:X11DRV_KEYBOARD_DetectLayout 6 keysyms per keycode not supported, set to 4
warn:keyboard:X11DRV_KEYBOARD_DetectLayout Using closest match (United States keyboard layout (phantom key version)) for scan/virtual codes mapping.
warn:keyboard:X11DRV_InitKeyboard vkey 0008 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 010D is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0124 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0126 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0121 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0125 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0127 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0123 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0128 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0122 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 012D is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 012E is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 00A4 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 01A5 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 01B3 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 01B3 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 012C is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 01B4 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0003 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard No more vkeys available!
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:class:CLASS_RegisterClass Win extra bytes 44 is > 40
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
warn:sync:SetNamedPipeHandleState stub: 0x4c 0x68e45c/2 (nil) (nil)
fixme:advapi:RegisterEventSourceW ((null),L"Bonjour Service"): stub
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\Bonjour\\crypt32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\crypt32.dll" not found (c0000034)
warn:winsock:WS_bind 	failure - errno = 98
warn:winsock:wsaErrno errno 98, (Address already in use).
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:winsock:WS_setsockopt Unknown IPPROTO_IPV6 optname 0x00000013
warn:winsock:wsaErrno errno 22, (Invalid argument).
fixme:winsock:WSAIoctl -> SIO_ADDRESS_LIST_CHANGE request: stub
fixme:iphlpapi:DeleteIpForwardEntry (pRoute 0x78e8b4): stub
fixme:iphlpapi:CreateIpForwardEntry (pRoute 0x78e87c): stub
fixme:service:EnumServicesStatusW resume handle not supported
fixme:service:EnumServicesStatusW resume handle not supported
fixme:advapi:ReportEventA (0xcafe4242,0x0004,0x0000,0x00000064,(nil),0x0001,0x00000000,0x78e5f8,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x00000064,(nil),0x0001,0x00000000,0x138508,(nil)): stub
fixme:netapi32:NetGetJoinInformation Semi-stub (null) 0x78e688 0x78e690
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows" not found (c0000035)
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows\\system32" not found (c0000035)
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows\\Microsoft.NET\\Framework\\v4.0.30319\\mscorsvw.exe.manifest" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\Microsoft.NET\\Framework\\v4.0.30319\\MSVCR100_CLR0400.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\MSVCR100_CLR0400.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\Microsoft.NET\\Framework\\v4.0.30319\\MSVCR100_CLR0400.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\MSVCR100_CLR0400.dll" not found (c0000034)
warn:module:load_builtin_dll failed to load .so lib for builtin L"C:\\windows\\system32\\MSVCR100_CLR0400.dll": /home/kevin/.wine/dosdevices/c:/windows/system32/msvcr100_clr0400.dll: invalid ELF header
warn:module:load_builtin_dll cannot open .so lib for builtin L"MSVCR100_CLR0400.dll": /usr/bin/../lib/wine/msvcr100_clr0400.dll.so: cannot open shared object file: No such file or directory
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\Microsoft.NET\\Framework\\v4.0.30319\\ADVAPI32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\ADVAPI32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\Microsoft.NET\\Framework\\v4.0.30319\\ADVAPI32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\ADVAPI32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\Microsoft.NET\\Framework\\v4.0.30319\\USER32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\USER32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\Microsoft.NET\\Framework\\v4.0.30319\\gdi32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\gdi32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\Microsoft.NET\\Framework\\v4.0.30319\\version.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\version.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\Microsoft.NET\\Framework\\v4.0.30319\\mscoree.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\mscoree.dll" not found (c0000034)
warn:module:load_builtin_dll failed to load .so lib for builtin L"C:\\windows\\system32\\mscoree.dll": /home/kevin/.wine/dosdevices/c:/windows/system32/mscoree.dll: invalid ELF header
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\Microsoft.NET\\Framework\\v4.0.30319\\dbghelp.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\dbghelp.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\Microsoft.NET\\Framework\\v4.0.30319\\psapi.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\psapi.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\Microsoft.NET\\Framework\\v4.0.30319\\shell32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\shell32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\Microsoft.NET\\Framework\\v4.0.30319\\shlwapi.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\shlwapi.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\Microsoft.NET\\Framework\\v4.0.30319\\comctl32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\comctl32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\Microsoft.NET\\Framework\\v4.0.30319\\comctl32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\comctl32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\Microsoft.NET\\Framework\\v4.0.30319\\ole32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\ole32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\Microsoft.NET\\Framework\\v4.0.30319\\rpcrt4.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\rpcrt4.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\Microsoft.NET\\Framework\\v4.0.30319\\ole32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\ole32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\Microsoft.NET\\Framework\\v4.0.30319\\rpcrt4.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\rpcrt4.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\Microsoft.NET\\Framework\\v4.0.30319\\OLEAUT32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\OLEAUT32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\Microsoft.NET\\Framework\\v4.0.30319\\OLEAUT32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\OLEAUT32.dll" not found (c0000034)
warn:module:load_builtin_dll failed to load .so lib for builtin L"C:\\windows\\system32\\OLEAUT32.dll": /home/kevin/.wine/dosdevices/c:/windows/system32/OLEAUT32.DLL: invalid ELF header
warn:font:AddFontToList Unable to load font "/home/kevin/.wine/dosdevices/c:/windows/Fonts/vgasys.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/home/kevin/.wine/dosdevices/c:/windows/Fonts/vga850.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/usr/bin/../share/wine/fonts/vga850.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/home/kevin/.wine/dosdevices/c:/windows/Fonts/vgafix.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/usr/bin/../share/wine/fonts/vgafix.fon"/(nil) err = 1
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smae1255.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smae1257.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//ssee1257.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//hvgasys.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//jsmalle.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coure.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smallet.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coue1256.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smallee.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgas874.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//couree.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//ssee1256.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smae1256.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserife.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coue1257.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasysr.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserifee.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasyse.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coue1255.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserifet.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgas1255.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smalleg.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgas1256.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//ssee874.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasys.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasyst.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasysg.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//courer.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgas1257.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//jvgasys.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//cvgasys.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserifeg.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//ssee1255.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smaller.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smalle.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//couret.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//svgasys.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserifer.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coureg.fon"/(nil)
warn:font:AddFontToList Unable to load font "/home/kevin/.wine/dosdevices/c:/windows/Fonts/coure.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/home/kevin/.wine/dosdevices/c:/windows/Fonts/sserife.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/home/kevin/.wine/dosdevices/c:/windows/Fonts/serife.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/usr/bin/../share/wine/fonts/serife.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/home/kevin/.wine/dosdevices/c:/windows/Fonts/smalle.fon"/(nil) err = 1
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\Microsoft.NET\\Framework\\v4.0.30319\\winex11.drv" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\winex11.drv" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\Microsoft.NET\\Framework\\v4.0.30319\\imm32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\imm32.dll" not found (c0000034)
warn:keyboard:X11DRV_KEYBOARD_DetectLayout 6 keysyms per keycode not supported, set to 4
warn:keyboard:X11DRV_KEYBOARD_DetectLayout Using closest match (United States keyboard layout (phantom key version)) for scan/virtual codes mapping.
warn:keyboard:X11DRV_InitKeyboard vkey 0008 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 010D is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0124 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0126 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0121 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0125 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0127 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0123 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0128 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0122 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 012D is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 012E is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 00A4 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 01A5 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 01B3 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 01B3 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 012C is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 01B4 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0003 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard No more vkeys available!
warn:class:CLASS_RegisterClass Win extra bytes 44 is > 40
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:process:SetProcessDEPPolicy (1): stub
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\Microsoft.NET\\Framework\\v4.0.30319\\ndpsetup.bat" not found (c0000034)
warn:sync:SetNamedPipeHandleState stub: 0x60 0x77e45c/2 (nil) (nil)
warn:rpc:RPCRT4_default_receive_fragment Short read of header, -1 bytes
warn:rpc:RPCRT4_io_thread receive failed with error 6be
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows" not found (c0000035)
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows\\system32" not found (c0000035)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows\\system32\\winedevice.exe.manifest" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:sync:SetNamedPipeHandleState stub: 0x24 0x44e45c/2 (nil) (nil)
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows" not found (c0000035)
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows\\system32" not found (c0000035)
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows\\system32\\plugplay.exe.manifest" not found (c0000034)
warn:sync:SetNamedPipeHandleState stub: 0x24 0x44e45c/2 (nil) (nil)
warn:font:AddFontToList Unable to load font "/home/kevin/.wine/dosdevices/c:/windows/Fonts/vgasys.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/home/kevin/.wine/dosdevices/c:/windows/Fonts/vga850.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/usr/bin/../share/wine/fonts/vga850.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/home/kevin/.wine/dosdevices/c:/windows/Fonts/vgafix.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/usr/bin/../share/wine/fonts/vgafix.fon"/(nil) err = 1
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smae1255.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smae1257.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//ssee1257.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//hvgasys.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//jsmalle.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coure.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smallet.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coue1256.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smallee.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgas874.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//couree.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//ssee1256.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smae1256.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserife.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coue1257.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasysr.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserifee.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasyse.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coue1255.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserifet.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgas1255.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smalleg.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgas1256.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//ssee874.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasys.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasyst.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasysg.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//courer.fon"/(nil)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgas1257.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//jvgasys.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//cvgasys.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserifeg.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//ssee1255.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smaller.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smalle.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//couret.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//svgasys.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserifer.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coureg.fon"/(nil)
warn:font:AddFontToList Unable to load font "/home/kevin/.wine/dosdevices/c:/windows/Fonts/coure.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/home/kevin/.wine/dosdevices/c:/windows/Fonts/sserife.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/home/kevin/.wine/dosdevices/c:/windows/Fonts/serife.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/usr/bin/../share/wine/fonts/serife.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/home/kevin/.wine/dosdevices/c:/windows/Fonts/smalle.fon"/(nil) err = 1
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:keyboard:X11DRV_KEYBOARD_DetectLayout 6 keysyms per keycode not supported, set to 4
warn:keyboard:X11DRV_KEYBOARD_DetectLayout Using closest match (United States keyboard layout (phantom key version)) for scan/virtual codes mapping.
warn:keyboard:X11DRV_InitKeyboard vkey 0008 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 010D is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0124 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0126 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0121 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0125 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0127 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0123 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0128 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0122 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 012D is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 012E is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 00A4 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 01A5 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 01B3 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 01B3 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 012C is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 01B4 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0003 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard No more vkeys available!
warn:class:CLASS_RegisterClass Win extra bytes 44 is > 40
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:module:alloc_module disabling no-exec because of L"Binding_of_Isaac.exe"
warn:actctx:parse_assembly_identity_elem Unsupported yet language attribute (L"*")
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\.local\\share\\wineprefixes\\steam\\drive_c\\Program Files\\Steam\\steamapps\\common\\the binding of isaac\\ADVAPI32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\source\\cliftonstudios.ca\\ADVAPI32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\.local\\share\\wineprefixes\\steam\\drive_c\\Program Files\\Steam\\steamapps\\common\\the binding of isaac\\ADVAPI32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\source\\cliftonstudios.ca\\ADVAPI32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\.local\\share\\wineprefixes\\steam\\drive_c\\Program Files\\Steam\\steamapps\\common\\the binding of isaac\\user32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\source\\cliftonstudios.ca\\user32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\.local\\share\\wineprefixes\\steam\\drive_c\\Program Files\\Steam\\steamapps\\common\\the binding of isaac\\gdi32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\source\\cliftonstudios.ca\\gdi32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\.local\\share\\wineprefixes\\steam\\drive_c\\Program Files\\Steam\\steamapps\\common\\the binding of isaac\\version.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\source\\cliftonstudios.ca\\version.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\.local\\share\\wineprefixes\\steam\\drive_c\\Program Files\\Steam\\steamapps\\common\\the binding of isaac\\comdlg32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\source\\cliftonstudios.ca\\comdlg32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\.local\\share\\wineprefixes\\steam\\drive_c\\Program Files\\Steam\\steamapps\\common\\the binding of isaac\\comdlg32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\source\\cliftonstudios.ca\\comdlg32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\.local\\share\\wineprefixes\\steam\\drive_c\\Program Files\\Steam\\steamapps\\common\\the binding of isaac\\shell32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\source\\cliftonstudios.ca\\shell32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\.local\\share\\wineprefixes\\steam\\drive_c\\Program Files\\Steam\\steamapps\\common\\the binding of isaac\\shlwapi.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\source\\cliftonstudios.ca\\shlwapi.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\.local\\share\\wineprefixes\\steam\\drive_c\\Program Files\\Steam\\steamapps\\common\\the binding of isaac\\winspool.drv" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\source\\cliftonstudios.ca\\winspool.drv" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\.local\\share\\wineprefixes\\steam\\drive_c\\Program Files\\Steam\\steamapps\\common\\the binding of isaac\\winspool.drv" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\source\\cliftonstudios.ca\\winspool.drv" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\.local\\share\\wineprefixes\\steam\\drive_c\\Program Files\\Steam\\steamapps\\common\\the binding of isaac\\DDRAW.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\source\\cliftonstudios.ca\\DDRAW.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\.local\\share\\wineprefixes\\steam\\drive_c\\Program Files\\Steam\\steamapps\\common\\the binding of isaac\\wined3d.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\source\\cliftonstudios.ca\\wined3d.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\.local\\share\\wineprefixes\\steam\\drive_c\\Program Files\\Steam\\steamapps\\common\\the binding of isaac\\ole32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\source\\cliftonstudios.ca\\ole32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\.local\\share\\wineprefixes\\steam\\drive_c\\Program Files\\Steam\\steamapps\\common\\the binding of isaac\\rpcrt4.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\source\\cliftonstudios.ca\\rpcrt4.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\.local\\share\\wineprefixes\\steam\\drive_c\\Program Files\\Steam\\steamapps\\common\\the binding of isaac\\OLEAUT32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\source\\cliftonstudios.ca\\OLEAUT32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\.local\\share\\wineprefixes\\steam\\drive_c\\Program Files\\Steam\\steamapps\\common\\the binding of isaac\\OLEAUT32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\source\\cliftonstudios.ca\\OLEAUT32.dll" not found (c0000034)
warn:module:load_builtin_dll failed to load .so lib for builtin L"C:\\windows\\system32\\OLEAUT32.dll": /home/kevin/.wine/dosdevices/c:/windows/system32/OLEAUT32.DLL: invalid ELF header
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\.local\\share\\wineprefixes\\steam\\drive_c\\Program Files\\Steam\\steamapps\\common\\the binding of isaac\\WINMM.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\source\\cliftonstudios.ca\\WINMM.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\.local\\share\\wineprefixes\\steam\\drive_c\\Program Files\\Steam\\steamapps\\common\\the binding of isaac\\msacm32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\source\\cliftonstudios.ca\\msacm32.dll" not found (c0000034)
warn:font:AddFontToList Unable to load font "/home/kevin/.wine/dosdevices/c:/windows/Fonts/vgasys.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/home/kevin/.wine/dosdevices/c:/windows/Fonts/vga850.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/usr/bin/../share/wine/fonts/vga850.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/home/kevin/.wine/dosdevices/c:/windows/Fonts/vgafix.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/usr/bin/../share/wine/fonts/vgafix.fon"/(nil) err = 1
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smae1255.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smae1257.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//ssee1257.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//hvgasys.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//jsmalle.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coure.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smallet.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coue1256.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smallee.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgas874.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//couree.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//ssee1256.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smae1256.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserife.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coue1257.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasysr.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserifee.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasyse.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coue1255.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserifet.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgas1255.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smalleg.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgas1256.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//ssee874.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasys.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasyst.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasysg.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//courer.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgas1257.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//jvgasys.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//cvgasys.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserifeg.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//ssee1255.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smaller.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smalle.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//couret.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//svgasys.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserifer.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coureg.fon"/(nil)
warn:font:AddFontToList Unable to load font "/home/kevin/.wine/dosdevices/c:/windows/Fonts/coure.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/home/kevin/.wine/dosdevices/c:/windows/Fonts/sserife.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/home/kevin/.wine/dosdevices/c:/windows/Fonts/serife.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/usr/bin/../share/wine/fonts/serife.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/home/kevin/.wine/dosdevices/c:/windows/Fonts/smalle.fon"/(nil) err = 1
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\.local\\share\\wineprefixes\\steam\\drive_c\\Program Files\\Steam\\steamapps\\common\\the binding of isaac\\winex11.drv" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\source\\cliftonstudios.ca\\winex11.drv" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\.local\\share\\wineprefixes\\steam\\drive_c\\Program Files\\Steam\\steamapps\\common\\the binding of isaac\\imm32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\source\\cliftonstudios.ca\\imm32.dll" not found (c0000034)
warn:keyboard:X11DRV_KEYBOARD_DetectLayout 6 keysyms per keycode not supported, set to 4
warn:keyboard:X11DRV_KEYBOARD_DetectLayout Using closest match (United States keyboard layout (phantom key version)) for scan/virtual codes mapping.
warn:keyboard:X11DRV_InitKeyboard vkey 0008 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 010D is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0124 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0126 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0121 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0125 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0127 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0123 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0128 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0122 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 012D is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 012E is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 00A4 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 01A5 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 01B3 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 01B3 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 012C is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 01B4 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0003 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard No more vkeys available!
warn:class:CLASS_RegisterClass Win extra bytes 44 is > 40
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\.local\\share\\wineprefixes\\steam\\drive_c\\Program Files\\Steam\\steamapps\\common\\the binding of isaac\\uxtheme.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\source\\cliftonstudios.ca\\uxtheme.dll" not found (c0000034)
warn:winspool:WINSPOOL_GetDWORDFromReg Got ret = 2 on name dnsTimeout
warn:winspool:WINSPOOL_GetDWORDFromReg Got ret = 2 on name txTimeout
warn:winspool:WINSPOOL_GetDWORDFromReg Got ret = 2 on name dnsTimeout
warn:winspool:WINSPOOL_GetDWORDFromReg Got ret = 2 on name txTimeout
warn:winspool:WINSPOOL_GetDWORDFromReg Got ret = 2 on name dnsTimeout
warn:winspool:WINSPOOL_GetDWORDFromReg Got ret = 2 on name txTimeout
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\.local\\share\\wineprefixes\\steam\\drive_c\\Program Files\\Steam\\steamapps\\common\\the binding of isaac\\localspl.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\source\\cliftonstudios.ca\\localspl.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\.local\\share\\wineprefixes\\steam\\drive_c\\Program Files\\Steam\\steamapps\\common\\the binding of isaac\\localspl.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\source\\cliftonstudios.ca\\localspl.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\.local\\share\\wineprefixes\\steam\\drive_c\\Program Files\\Steam\\steamapps\\common\\the binding of isaac\\spoolss.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\source\\cliftonstudios.ca\\spoolss.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:FILE_CreateFile L"\\??\\Z:\\home\\kevin\\.local\\share\\wineprefixes\\steam\\drive_c\\Program Files\\Steam\\steamapps\\common\\the binding of isaac\\plugins\\" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:menubuilder:open_module_icon found no icon
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\QuickTime\\QTSystem\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\QuickTime\\QTSystem\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\QuickTime\\QTSystem\\%1.dll" not found (c0000034)
warn:module:load_builtin_dll cannot open .so lib for builtin L"%1.dll": /usr/bin/../lib/wine/%1.dll.so: cannot open shared object file: No such file or directory
warn:module:load_dll Failed to load module L"%1"; status=c0000135
warn:menubuilder:open_module_icon LoadLibraryExW (L"%1") failed, error 126
warn:menubuilder:open_module_icon found no icon
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\QuickTime\\QTSystem\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\QuickTime\\QTSystem\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\QuickTime\\QTSystem\\%1.dll" not found (c0000034)
warn:module:load_builtin_dll cannot open .so lib for builtin L"%1.dll": /usr/bin/../lib/wine/%1.dll.so: cannot open shared object file: No such file or directory
warn:module:load_dll Failed to load module L"%1"; status=c0000135
warn:menubuilder:open_module_icon LoadLibraryExW (L"%1") failed, error 126
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\.local\\share\\wineprefixes\\steam\\drive_c\\Program Files\\Steam\\steamapps\\common\\the binding of isaac\\CRYPT32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\source\\cliftonstudios.ca\\CRYPT32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\.local\\share\\wineprefixes\\steam\\drive_c\\Program Files\\Steam\\steamapps\\common\\the binding of isaac\\DSOUND.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\source\\cliftonstudios.ca\\DSOUND.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\.local\\share\\wineprefixes\\steam\\drive_c\\Program Files\\Steam\\steamapps\\common\\the binding of isaac\\mscms.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\source\\cliftonstudios.ca\\mscms.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\.local\\share\\wineprefixes\\steam\\drive_c\\Program Files\\Steam\\steamapps\\common\\the binding of isaac\\WS2_32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\source\\cliftonstudios.ca\\WS2_32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\profiles\\kevin\\Temp\\wrd-8-9-528.~lk" not found (c0000034)
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows\\profiles\\kevin\\Temp\\wrd-8-9-528.~lk\\" not found (c0000034)
warn:module:load_builtin_dll failed to load .so lib for builtin L"C:\\windows\\profiles\\kevin\\Temp\\wrd-8-9-528.~lk\\1.mdd": /home/kevin/.wine/dosdevices/c:/windows/profiles/kevin/Temp/wrd-8-9-528.~lk/1.mdd: invalid ELF header
warn:module:load_builtin_dll cannot open .so lib for builtin L"1.mdd": /usr/bin/../lib/wine/1.mdd.so: cannot open shared object file: No such file or directory
warn:module:alloc_module disabling no-exec because of L"1.mdd"
warn:module:load_builtin_dll failed to load .so lib for builtin L"C:\\windows\\profiles\\kevin\\Temp\\wrd-8-9-528.~lk\\3.mdd": /home/kevin/.wine/dosdevices/c:/windows/profiles/kevin/Temp/wrd-8-9-528.~lk/3.mdd: invalid ELF header
warn:module:load_builtin_dll cannot open .so lib for builtin L"3.mdd": /usr/bin/../lib/wine/3.mdd.so: cannot open shared object file: No such file or directory
warn:module:alloc_module disabling no-exec because of L"3.mdd"
warn:module:load_builtin_dll failed to load .so lib for builtin L"C:\\windows\\profiles\\kevin\\Temp\\wrd-8-9-528.~lk\\2.mdd": /home/kevin/.wine/dosdevices/c:/windows/profiles/kevin/Temp/wrd-8-9-528.~lk/2.mdd: invalid ELF header
warn:module:load_builtin_dll cannot open .so lib for builtin L"2.mdd": /usr/bin/../lib/wine/2.mdd.so: cannot open shared object file: No such file or directory
warn:module:alloc_module disabling no-exec because of L"2.mdd"
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:module:load_builtin_dll failed to load .so lib for builtin L"C:\\windows\\profiles\\kevin\\Temp\\wrd-8-9-528.~lk\\4.mdd": /home/kevin/.wine/dosdevices/c:/windows/profiles/kevin/Temp/wrd-8-9-528.~lk/4.mdd: invalid ELF header
warn:module:load_builtin_dll cannot open .so lib for builtin L"4.mdd": /usr/bin/../lib/wine/4.mdd.so: cannot open shared object file: No such file or directory
warn:module:alloc_module disabling no-exec because of L"4.mdd"
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:module:load_builtin_dll failed to load .so lib for builtin L"C:\\windows\\profiles\\kevin\\Temp\\wrd-8-9-528.~lk\\0.mdd": /home/kevin/.wine/dosdevices/c:/windows/profiles/kevin/Temp/wrd-8-9-528.~lk/0.mdd: invalid ELF header
warn:module:load_builtin_dll cannot open .so lib for builtin L"0.mdd": /usr/bin/../lib/wine/0.mdd.so: cannot open shared object file: No such file or directory
warn:module:alloc_module disabling no-exec because of L"0.mdd"
warn:ntdll:FILE_CreateFile L"\\??\\Z:\\home\\kevin\\source\\cliftonstudios.ca\\\00f4_\00ca{" not found (c0000034)
warn:file:CreateFileW Unable to create file L"\00f4_\00ca{" (status c0000034)
warn:file:OpenFile (Z:\home\kevin\.local\share\wineprefixes\steam\drive_c\Program Files\Steam\steamapps\common\the binding of isaac\Binding_of_Isaac.exe): return = HFILE_ERROR error= 2
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\.local\\share\\wineprefixes\\steam\\drive_c\\Program Files\\Steam\\steamapps\\common\\the binding of isaac\\Binding_of_Isaac.ex_" not found (c0000034)
warn:file:OpenFile (Z:\home\kevin\.local\share\wineprefixes\steam\drive_c\Program Files\Steam\steamapps\common\the binding of isaac\Binding_of_Isaac.ex_): return = HFILE_ERROR error= 2
warn:ntdll:FILE_CreateFile L"\\??\\Z:\\home\\kevin\\source\\cliftonstudios.ca\\Nm\00c4{" not found (c0000034)
warn:file:CreateFileW Unable to create file L"Nm\00c4{" (status c0000034)
warn:file:OpenFile (Z:\home\kevin\.local\share\wineprefixes\steam\drive_c\Program Files\Steam\steamapps\common\the binding of isaac\Binding_of_Isaac.exe): return = HFILE_ERROR error= 2
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\kevin\\.local\\share\\wineprefixes\\steam\\drive_c\\Program Files\\Steam\\steamapps\\common\\the binding of isaac\\Binding_of_Isaac.ex_" not found (c0000034)
warn:file:OpenFile (Z:\home\kevin\.local\share\wineprefixes\steam\drive_c\Program Files\Steam\steamapps\common\the binding of isaac\Binding_of_Isaac.ex_): return = HFILE_ERROR error= 2
warn:debugstr:OutputDebugStringA "wm_setfocus\n"
warn:debugstr:OutputDebugStringA "wm_killfocus\n"
warn:debugstr:OutputDebugStringA "killfocus main form 0\n"
warn:debugstr:OutputDebugStringA "setfocus main form 0\n"
warn:debugstr:OutputDebugStringA "wm_setfocus\n"
warn:debugstr:OutputDebugStringA "wm_killfocus\n"
warn:debugstr:OutputDebugStringA "killfocus main form 0\n"
warn:debugstr:OutputDebugStringA "setfocus main form 0\n"
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\hh.exe" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\hh.exe %1" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\hh.exe" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\hh.exe %1" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%WinDir%\\System32\\notepad.exe" not found (c000003a)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%WinDir%\\System32\\notepad.exe" not found (c000003a)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%WinDir%\\System32\\notepad.exe" not found (c000003a)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system\\%WinDir%\\System32\\notepad.exe" not found (c000003a)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%WinDir%\\System32\\notepad.exe" not found (c000003a)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%WinDir%\\System32\\notepad.exe" not found (c000003a)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%WinDir%\\System32\\notepad.exe" not found (c000003a)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\QuickTime\\QTSystem\\%WinDir%\\System32\\notepad.exe" not found (c000003a)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%WinDir%\\System32\\notepad.exe" not found (c000003a)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%WinDir%\\System32\\notepad.exe" not found (c000003a)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%WinDir%\\System32\\notepad.exe" not found (c000003a)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system\\%WinDir%\\System32\\notepad.exe" not found (c000003a)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%WinDir%\\System32\\notepad.exe" not found (c000003a)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%WinDir%\\System32\\notepad.exe" not found (c000003a)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%WinDir%\\System32\\notepad.exe" not found (c000003a)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\QuickTime\\QTSystem\\%WinDir%\\System32\\notepad.exe" not found (c000003a)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:menubuilder:open_module_icon found no icon
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\QuickTime\\QTSystem\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\QuickTime\\QTSystem\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\QuickTime\\QTSystem\\%1.dll" not found (c0000034)
warn:module:load_builtin_dll cannot open .so lib for builtin L"%1.dll": /usr/bin/../lib/wine/%1.dll.so: cannot open shared object file: No such file or directory
warn:module:load_dll Failed to load module L"%1"; status=c0000135
warn:menubuilder:open_module_icon LoadLibraryExW (L"%1") failed, error 126
warn:menubuilder:open_module_icon found no icon
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\QuickTime\\QTSystem\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\QuickTime\\QTSystem\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\QuickTime\\QTSystem\\%1.dll" not found (c0000034)
warn:module:load_builtin_dll cannot open .so lib for builtin L"%1.dll": /usr/bin/../lib/wine/%1.dll.so: cannot open shared object file: No such file or directory
warn:module:load_dll Failed to load module L"%1"; status=c0000135
warn:menubuilder:open_module_icon LoadLibraryExW (L"%1") failed, error 126
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\msiexec" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\msiexec" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\msiexec" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system\\msiexec" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\msiexec" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\msiexec" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\msiexec" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\QuickTime\\QTSystem\\msiexec" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\msiexec \\p" not found (c000003a)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\msiexec \\p" not found (c000003a)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\msiexec \\p" not found (c000003a)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system\\msiexec \\p" not found (c000003a)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\msiexec \\p" not found (c000003a)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\msiexec \\p" not found (c000003a)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\msiexec \\p" not found (c000003a)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\QuickTime\\QTSystem\\msiexec \\p" not found (c000003a)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\msiexec \\p \"%1\"" not found (c0000033)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\msiexec \\p \"%1\"" not found (c0000033)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\msiexec \\p \"%1\"" not found (c0000033)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system\\msiexec \\p \"%1\"" not found (c0000033)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\msiexec \\p \"%1\"" not found (c0000033)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\msiexec \\p \"%1\"" not found (c0000033)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\msiexec \\p \"%1\"" not found (c0000033)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\QuickTime\\QTSystem\\msiexec \\p \"%1\"" not found (c0000033)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\msiexec" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\msiexec" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\msiexec" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system\\msiexec" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\msiexec" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\msiexec" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\msiexec" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\QuickTime\\QTSystem\\msiexec" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\msiexec \\p" not found (c000003a)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\msiexec \\p" not found (c000003a)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\msiexec \\p" not found (c000003a)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system\\msiexec \\p" not found (c000003a)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\msiexec \\p" not found (c000003a)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\msiexec \\p" not found (c000003a)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\msiexec \\p" not found (c000003a)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\QuickTime\\QTSystem\\msiexec \\p" not found (c000003a)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\msiexec \\p \"%1\"" not found (c0000033)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\msiexec \\p \"%1\"" not found (c0000033)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\msiexec \\p \"%1\"" not found (c0000033)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system\\msiexec \\p \"%1\"" not found (c0000033)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\msiexec \\p \"%1\"" not found (c0000033)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\msiexec \\p \"%1\"" not found (c0000033)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\msiexec \\p \"%1\"" not found (c0000033)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\QuickTime\\QTSystem\\msiexec \\p \"%1\"" not found (c0000033)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program" not found (c0000034)
warn:menubuilder:open_module_icon found no icon
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\QuickTime\\QTSystem\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\QuickTime\\QTSystem\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\QuickTime\\QTSystem\\%1.dll" not found (c0000034)
warn:module:load_builtin_dll cannot open .so lib for builtin L"%1.dll": /usr/bin/../lib/wine/%1.dll.so: cannot open shared object file: No such file or directory
warn:module:load_dll Failed to load module L"%1"; status=c0000135
warn:menubuilder:open_module_icon LoadLibraryExW (L"%1") failed, error 126
warn:wincodecs:PngDecoder_Frame_GetResolution no pHYs block present
warn:wincodecs:PngDecoder_Frame_GetResolution no pHYs block present
warn:menubuilder:open_module_icon found no icon
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\QuickTime\\QTSystem\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\QuickTime\\QTSystem\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\%1.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\Program Files\\QuickTime\\QTSystem\\%1.dll" not found (c0000034)
warn:module:load_builtin_dll cannot open .so lib for builtin L"%1.dll": /usr/bin/../lib/wine/%1.dll.so: cannot open shared object file: No such file or directory
warn:module:load_dll Failed to load module L"%1"; status=c0000135
warn:menubuilder:open_module_icon LoadLibraryExW (L"%1") failed, error 126
^C
```

---

### Post by suzumeuta on 2011-10-22
I got the game to work after a long load time, but sounds seems to fail shortly after starting...
However, everything else seems to work perfectly, on the latest WINE release (as of today Oct.22), although a little slow.

Anyone else tried this game?

---

### Post by Luksion Knight on 2011-11-01
I bought the native version through humble bundle and it works like a dream. Slows down at some points when battles get complex, I can only guess its linux's notoriously high quality flash plugin/player

---

### Post by Kimos on 2011-11-01
Amazing. I'll get that load up that .deb right away.

Thanks!

---

