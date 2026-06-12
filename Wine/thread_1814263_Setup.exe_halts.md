---
title: "Setup.exe halts"
date: 2011-07-29
forum: Wine
---

### Post by Mathias1 on 2011-07-29
I'm trying to install Photoshop 7, but when I click the "setup.exe", the only thing that happens is the splash screen's coming up and the loading bar reaches 99%. Then it just closes down. No setup-program or dialog.

I'm running Ubuntu 11.04 with Intel GMA HD graphics.

WINEDEBUG=warn+all gives this output: 
```
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows\\system32\\winedevice.exe.manifest" not found (c0000034)
warn:sync:SetNamedPipeHandleState stub: 0x24 0x44e45c/2 (nil) (nil)
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows" not found (c0000035)
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows\\system32" not found (c0000035)
warn:module:load_builtin_dll cannot open .so lib for builtin L"plugplay.exe": /usr/bin/../lib/wine/plugplay.exe.so: cannot open shared object file: No such file or directory
warn:module:load_dll Failed to load module L"C:\\windows\\system32\\plugplay.exe"; status=c0000135
warn:keyboard:X11DRV_KEYBOARD_DetectLayout 6 keysyms per keycode not supported, set to 4
wine: cannot find L"C:\\windows\\system32\\plugplay.exe"
warn:keyboard:X11DRV_KEYBOARD_DetectLayout Using closest match (Swedish keyboard layout) for scan/virtual codes mapping.
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
warn:keyboard:X11DRV_InitKeyboard vkey 01B3 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 01B3 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 012C is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 01B4 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0003 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard No more vkeys available!
warn:class:CLASS_RegisterClass Win extra bytes 44 is > 40
warn:font:AddFontToList Unable to load font "/home/mathias/.wine/dosdevices/c:/windows/Fonts/vgasys.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/home/mathias/.wine/dosdevices/c:/windows/Fonts/vgaoem.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/usr/bin/../share/wine/fonts/vgaoem.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/home/mathias/.wine/dosdevices/c:/windows/Fonts/vgafix.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/usr/bin/../share/wine/fonts/vgafix.fon"/(nil) err = 1
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//ssee1255.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserifee.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserifet.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//ssee874.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//jvgasys.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasysr.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgas874.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasyse.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserifeg.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smae1257.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasysg.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//hvgasys.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgas1256.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smallet.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserife.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserifer.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//ssee1257.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smaller.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//jsmalle.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//ssee1256.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smalleg.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coue1256.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smalle.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coue1257.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//svgasys.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//couree.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smae1256.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coure.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgas1255.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgas1257.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasyst.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//couret.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//cvgasys.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coureg.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasys.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smallee.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//courer.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smae1255.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coue1255.fon"/(nil)
warn:font:AddFontToList Unable to load font "/home/mathias/.wine/dosdevices/c:/windows/Fonts/coure.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/home/mathias/.wine/dosdevices/c:/windows/Fonts/sserife.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/home/mathias/.wine/dosdevices/c:/windows/Fonts/serife.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/usr/bin/../share/wine/fonts/serife.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/home/mathias/.wine/dosdevices/c:/windows/Fonts/smalle.fon"/(nil) err = 1
warn:keyboard:X11DRV_KEYBOARD_DetectLayout 6 keysyms per keycode not supported, set to 4
warn:keyboard:X11DRV_KEYBOARD_DetectLayout Using closest match (Swedish keyboard layout) for scan/virtual codes mapping.
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
warn:keyboard:X11DRV_InitKeyboard vkey 01B3 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 01B3 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 012C is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 01B4 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0003 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard No more vkeys available!
warn:class:CLASS_RegisterClass Win extra bytes 44 is > 40
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\hh.exe" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\system32\\hh.exe %1" not found (c0000034)
warn:module:alloc_module disabling no-exec because of L"setup.exe"
warn:ntdll:FILE_CreateFile L"\\??\\Z:\\home\\mathias\\Downloads\\Photoshop 7\\Ps_7\\setup.exe.manifest" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\mathias\\Downloads\\Photoshop 7\\Ps_7\\VERSION.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\mathias\\Downloads\\Photoshop 7\\Ps_7\\VERSION.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\mathias\\Downloads\\Photoshop 7\\Ps_7\\lz32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\mathias\\Downloads\\Photoshop 7\\Ps_7\\lz32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\mathias\\Downloads\\Photoshop 7\\Ps_7\\USER32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\mathias\\Downloads\\Photoshop 7\\Ps_7\\USER32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\mathias\\Downloads\\Photoshop 7\\Ps_7\\gdi32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\mathias\\Downloads\\Photoshop 7\\Ps_7\\gdi32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\mathias\\Downloads\\Photoshop 7\\Ps_7\\advapi32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\mathias\\Downloads\\Photoshop 7\\Ps_7\\advapi32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\mathias\\Downloads\\Photoshop 7\\Ps_7\\advapi32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\mathias\\Downloads\\Photoshop 7\\Ps_7\\advapi32.dll" not found (c0000034)
warn:font:AddFontToList Unable to load font "/home/mathias/.wine/dosdevices/c:/windows/Fonts/vgasys.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/home/mathias/.wine/dosdevices/c:/windows/Fonts/vgaoem.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/usr/bin/../share/wine/fonts/vgaoem.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/home/mathias/.wine/dosdevices/c:/windows/Fonts/vgafix.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/usr/bin/../share/wine/fonts/vgafix.fon"/(nil) err = 1
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//ssee1255.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserifee.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserifet.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//ssee874.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//jvgasys.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasysr.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgas874.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasyse.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserifeg.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smae1257.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasysg.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//hvgasys.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgas1256.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smallet.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserife.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserifer.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//ssee1257.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smaller.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//jsmalle.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//ssee1256.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smalleg.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coue1256.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smalle.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coue1257.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//svgasys.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//couree.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smae1256.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coure.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgas1255.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgas1257.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasyst.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//couret.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//cvgasys.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coureg.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasys.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smallee.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//courer.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smae1255.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coue1255.fon"/(nil)
warn:font:AddFontToList Unable to load font "/home/mathias/.wine/dosdevices/c:/windows/Fonts/coure.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/home/mathias/.wine/dosdevices/c:/windows/Fonts/sserife.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/home/mathias/.wine/dosdevices/c:/windows/Fonts/serife.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/usr/bin/../share/wine/fonts/serife.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/home/mathias/.wine/dosdevices/c:/windows/Fonts/smalle.fon"/(nil) err = 1
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\mathias\\Downloads\\Photoshop 7\\Ps_7\\winex11.drv" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\mathias\\Downloads\\Photoshop 7\\Ps_7\\winex11.drv" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\mathias\\Downloads\\Photoshop 7\\Ps_7\\imm32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\mathias\\Downloads\\Photoshop 7\\Ps_7\\imm32.dll" not found (c0000034)
warn:keyboard:X11DRV_KEYBOARD_DetectLayout 6 keysyms per keycode not supported, set to 4
warn:keyboard:X11DRV_KEYBOARD_DetectLayout Using closest match (Swedish keyboard layout) for scan/virtual codes mapping.
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
warn:keyboard:X11DRV_InitKeyboard vkey 01B3 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 01B3 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 012C is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 01B4 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0003 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard No more vkeys available!
warn:class:CLASS_RegisterClass Win extra bytes 44 is > 40
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows\\_delis32.ini" not found (c0000034)
warn:file:CreateFileW Unable to create file L"C:\\windows\\_delis32.ini" (status c0000034)
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows" not found (c0000035)
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows\\system32" not found (c0000035)
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows\\system32\\explorer.exe.manifest" not found (c0000034)
warn:font:AddFontToList Unable to load font "/home/mathias/.wine/dosdevices/c:/windows/Fonts/vgasys.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/home/mathias/.wine/dosdevices/c:/windows/Fonts/vgaoem.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/usr/bin/../share/wine/fonts/vgaoem.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/home/mathias/.wine/dosdevices/c:/windows/Fonts/vgafix.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/usr/bin/../share/wine/fonts/vgafix.fon"/(nil) err = 1
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//ssee1255.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserifee.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserifet.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//ssee874.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//jvgasys.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasysr.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgas874.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasyse.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserifeg.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smae1257.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasysg.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//hvgasys.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgas1256.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smallet.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserife.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserifer.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//ssee1257.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smaller.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//jsmalle.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//ssee1256.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smalleg.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coue1256.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smalle.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coue1257.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//svgasys.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//couree.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smae1256.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coure.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgas1255.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgas1257.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasyst.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//couret.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//cvgasys.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coureg.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasys.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smallee.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//courer.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smae1255.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coue1255.fon"/(nil)
warn:font:AddFontToList Unable to load font "/home/mathias/.wine/dosdevices/c:/windows/Fonts/coure.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/home/mathias/.wine/dosdevices/c:/windows/Fonts/sserife.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/home/mathias/.wine/dosdevices/c:/windows/Fonts/serife.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/usr/bin/../share/wine/fonts/serife.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/home/mathias/.wine/dosdevices/c:/windows/Fonts/smalle.fon"/(nil) err = 1
warn:keyboard:X11DRV_KEYBOARD_DetectLayout 6 keysyms per keycode not supported, set to 4
warn:keyboard:X11DRV_KEYBOARD_DetectLayout Using closest match (Swedish keyboard layout) for scan/virtual codes mapping.
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
warn:keyboard:X11DRV_InitKeyboard vkey 01B3 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 01B3 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 012C is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 01B4 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0003 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard No more vkeys available!
warn:class:CLASS_RegisterClass Win extra bytes 44 is > 40
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows\\system32\\(None)" not found (c0000034)
warn:file:CreateFileW Unable to create file L"(None)" (status c0000034)
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows\\(None)" not found (c0000034)
warn:file:CreateFileW Unable to create file L"C:\\windows\\(None)" (status c0000034)
warn:module:load_builtin_dll failed to load .so lib for builtin L"Z:\\home\\mathias\\Downloads\\Photoshop 7\\Ps_7\\_SETUP.DLL": /home/mathias/.wine/dosdevices/z:/home/mathias/Downloads/Photoshop 7/Ps_7/_Setup.dll: invalid ELF header
warn:module:load_builtin_dll cannot open .so lib for builtin L"_SETUP.DLL": /usr/bin/../lib/wine/_setup.dll.so: cannot open shared object file: No such file or directory
warn:module:alloc_module disabling no-exec because of L"_SETUP.DLL"
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows\\profiles\\mathias\\Temp\\_ISTMP1.DIR\\_INS33IS._MP" not found (c0000034)
warn:file:CreateFileW Unable to create file L"C:\\windows\\profiles\\mathias\\Temp\\_ISTMP1.DIR\\_INS33IS._MP" (status c0000034)
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows\\profiles\\mathias\\Temp\\_ISTMP1.DIR\\_INS33IS._MP" not found (c0000034)
warn:file:CreateFileW Unable to create file L"C:\\windows\\profiles\\mathias\\Temp\\_ISTMP1.DIR\\_INS33IS._MP" (status c0000034)
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows\\profiles\\mathias\\Temp\\_ISTMP1.DIR\\_INS5576._MP" not found (c0000034)
warn:file:CreateFileW Unable to create file L"C:\\windows\\profiles\\mathias\\Temp\\_ISTMP1.DIR\\_INS5576._MP" (status c0000034)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows\\_iserr31.ini" not found (c0000034)
warn:file:CreateFileW Unable to create file L"C:\\windows\\_iserr31.ini" (status c0000034)
warn:profile:PROFILE_Open profile file L"C:\\windows\\_iserr31.ini" not found
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows" not found (c0000035)
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows\\system32" not found (c0000035)
warn:module:alloc_module disabling no-exec because of L"_INS5576._MP"
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows\\profiles\\mathias\\Temp\\_ISTMP1.DIR\\_INS5576._MP.manifest" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\profiles\\mathias\\Temp\\_ISTMP1.DIR\\USER32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\mathias\\Downloads\\Photoshop 7\\Ps_7\\USER32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\profiles\\mathias\\Temp\\_ISTMP1.DIR\\gdi32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\mathias\\Downloads\\Photoshop 7\\Ps_7\\gdi32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\profiles\\mathias\\Temp\\_ISTMP1.DIR\\advapi32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\mathias\\Downloads\\Photoshop 7\\Ps_7\\advapi32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\profiles\\mathias\\Temp\\_ISTMP1.DIR\\advapi32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\mathias\\Downloads\\Photoshop 7\\Ps_7\\advapi32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\profiles\\mathias\\Temp\\_ISTMP1.DIR\\WINSPOOL.DRV" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\mathias\\Downloads\\Photoshop 7\\Ps_7\\WINSPOOL.DRV" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\profiles\\mathias\\Temp\\_ISTMP1.DIR\\WINSPOOL.DRV" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\mathias\\Downloads\\Photoshop 7\\Ps_7\\WINSPOOL.DRV" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\profiles\\mathias\\Temp\\_ISTMP1.DIR\\comdlg32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\mathias\\Downloads\\Photoshop 7\\Ps_7\\comdlg32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\profiles\\mathias\\Temp\\_ISTMP1.DIR\\comdlg32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\mathias\\Downloads\\Photoshop 7\\Ps_7\\comdlg32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\profiles\\mathias\\Temp\\_ISTMP1.DIR\\shell32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\mathias\\Downloads\\Photoshop 7\\Ps_7\\shell32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\profiles\\mathias\\Temp\\_ISTMP1.DIR\\shlwapi.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\mathias\\Downloads\\Photoshop 7\\Ps_7\\shlwapi.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\profiles\\mathias\\Temp\\_ISTMP1.DIR\\comctl32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\mathias\\Downloads\\Photoshop 7\\Ps_7\\comctl32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\profiles\\mathias\\Temp\\_ISTMP1.DIR\\comctl32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\mathias\\Downloads\\Photoshop 7\\Ps_7\\comctl32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\profiles\\mathias\\Temp\\_ISTMP1.DIR\\ole32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\mathias\\Downloads\\Photoshop 7\\Ps_7\\ole32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\profiles\\mathias\\Temp\\_ISTMP1.DIR\\rpcrt4.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\mathias\\Downloads\\Photoshop 7\\Ps_7\\rpcrt4.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\profiles\\mathias\\Temp\\_ISTMP1.DIR\\VERSION.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\mathias\\Downloads\\Photoshop 7\\Ps_7\\VERSION.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\profiles\\mathias\\Temp\\_ISTMP1.DIR\\lz32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\mathias\\Downloads\\Photoshop 7\\Ps_7\\lz32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\profiles\\mathias\\Temp\\_ISTMP1.DIR\\WINMM.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\mathias\\Downloads\\Photoshop 7\\Ps_7\\WINMM.dll" not found (c0000034)
warn:font:AddFontToList Unable to load font "/home/mathias/.wine/dosdevices/c:/windows/Fonts/vgasys.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/home/mathias/.wine/dosdevices/c:/windows/Fonts/vgaoem.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/usr/bin/../share/wine/fonts/vgaoem.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/home/mathias/.wine/dosdevices/c:/windows/Fonts/vgafix.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/usr/bin/../share/wine/fonts/vgafix.fon"/(nil) err = 1
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//ssee1255.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserifee.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserifet.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//ssee874.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//jvgasys.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasysr.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgas874.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasyse.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserifeg.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smae1257.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasysg.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//hvgasys.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgas1256.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smallet.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserife.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserifer.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//ssee1257.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smaller.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//jsmalle.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//ssee1256.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smalleg.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coue1256.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smalle.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coue1257.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//svgasys.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//couree.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smae1256.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coure.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgas1255.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgas1257.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasyst.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//couret.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//cvgasys.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coureg.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasys.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smallee.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//courer.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smae1255.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coue1255.fon"/(nil)
warn:font:AddFontToList Unable to load font "/home/mathias/.wine/dosdevices/c:/windows/Fonts/coure.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/home/mathias/.wine/dosdevices/c:/windows/Fonts/sserife.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/home/mathias/.wine/dosdevices/c:/windows/Fonts/serife.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/usr/bin/../share/wine/fonts/serife.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/home/mathias/.wine/dosdevices/c:/windows/Fonts/smalle.fon"/(nil) err = 1
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\profiles\\mathias\\Temp\\_ISTMP1.DIR\\winex11.drv" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\mathias\\Downloads\\Photoshop 7\\Ps_7\\winex11.drv" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\profiles\\mathias\\Temp\\_ISTMP1.DIR\\imm32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\mathias\\Downloads\\Photoshop 7\\Ps_7\\imm32.dll" not found (c0000034)
warn:keyboard:X11DRV_KEYBOARD_DetectLayout 6 keysyms per keycode not supported, set to 4
warn:keyboard:X11DRV_KEYBOARD_DetectLayout Using closest match (Swedish keyboard layout) for scan/virtual codes mapping.
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
warn:keyboard:X11DRV_InitKeyboard vkey 01B3 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 01B3 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 012C is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 01B4 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0003 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard No more vkeys available!
warn:class:CLASS_RegisterClass Win extra bytes 44 is > 40
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\profiles\\mathias\\Temp\\_ISTMP1.DIR\\uxtheme.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\mathias\\Downloads\\Photoshop 7\\Ps_7\\uxtheme.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\mathias\\Downloads\\Photoshop" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\mathias\\Downloads\\Photoshop.exe" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\mathias\\Downloads\\Photoshop" not found (c0000034)
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows" not found (c0000035)
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows\\system32" not found (c0000035)
warn:module:alloc_module disabling no-exec because of L"_ISDel.exe"
warn:ntdll:FILE_CreateFile L"\\??\\Z:\\home\\mathias\\Downloads\\Photoshop 7\\Ps_7\\_ISDel.exe.manifest" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\profiles\\mathias\\Temp\\_ISTMP1.DIR\\_ISTMP0.DIR" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\C:\\windows\\profiles\\mathias\\Temp\\_ISTMP1.DIR\\_ISTMP0.DIR" not found (c0000034)
warn:ntdll:FILE_CreateFile L"\\??\\Z:\\home\\mathias\\Downloads\\Photoshop 7\\Ps_7\\_user1.cab" not found (c0000034)
warn:file:CreateFileW Unable to create file L"Z:\\home\\mathias\\Downloads\\Photoshop 7\\Ps_7\\_user1.cab" (status c0000034)
warn:ntdll:FILE_CreateFile L"\\??\\Z:\\home\\mathias\\Downloads\\Photoshop 7\\Ps_7\\_user1.cab" not found (c0000034)
warn:file:CreateFileW Unable to create file L"Z:\\home\\mathias\\Downloads\\Photoshop 7\\Ps_7\\_user1.cab" (status c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\mathias\\Downloads\\Photoshop 7\\Ps_7\\USER32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\mathias\\Downloads\\Photoshop 7\\Ps_7\\USER32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\mathias\\Downloads\\Photoshop 7\\Ps_7\\gdi32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\mathias\\Downloads\\Photoshop 7\\Ps_7\\gdi32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\mathias\\Downloads\\Photoshop 7\\Ps_7\\advapi32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\mathias\\Downloads\\Photoshop 7\\Ps_7\\advapi32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\mathias\\Downloads\\Photoshop 7\\Ps_7\\advapi32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\mathias\\Downloads\\Photoshop 7\\Ps_7\\advapi32.dll" not found (c0000034)
warn:font:AddFontToList Unable to load font "/home/mathias/.wine/dosdevices/c:/windows/Fonts/vgasys.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/home/mathias/.wine/dosdevices/c:/windows/Fonts/vgaoem.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/usr/bin/../share/wine/fonts/vgaoem.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/home/mathias/.wine/dosdevices/c:/windows/Fonts/vgafix.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/usr/bin/../share/wine/fonts/vgafix.fon"/(nil) err = 1
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//ssee1255.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserifee.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserifet.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//ssee874.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//jvgasys.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasysr.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgas874.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasyse.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserifeg.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smae1257.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasysg.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//hvgasys.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgas1256.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smallet.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserife.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//sserifer.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//ssee1257.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smaller.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//jsmalle.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//ssee1256.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smalleg.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coue1256.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smalle.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coue1257.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//svgasys.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//couree.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smae1256.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coure.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgas1255.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgas1257.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasyst.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//couret.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//cvgasys.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coureg.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//vgasys.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smallee.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//courer.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//smae1255.fon"/(nil)
warn:font:AddFontToList Ignoring font "/usr/bin/../share/wine/fonts//coue1255.fon"/(nil)
warn:font:AddFontToList Unable to load font "/home/mathias/.wine/dosdevices/c:/windows/Fonts/coure.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/home/mathias/.wine/dosdevices/c:/windows/Fonts/sserife.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/home/mathias/.wine/dosdevices/c:/windows/Fonts/serife.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/usr/bin/../share/wine/fonts/serife.fon"/(nil) err = 1
warn:font:AddFontToList Unable to load font "/home/mathias/.wine/dosdevices/c:/windows/Fonts/smalle.fon"/(nil) err = 1
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\mathias\\Downloads\\Photoshop 7\\Ps_7\\winex11.drv" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\mathias\\Downloads\\Photoshop 7\\Ps_7\\winex11.drv" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\mathias\\Downloads\\Photoshop 7\\Ps_7\\imm32.dll" not found (c0000034)
warn:ntdll:NtQueryAttributesFile L"\\??\\Z:\\home\\mathias\\Downloads\\Photoshop 7\\Ps_7\\imm32.dll" not found (c0000034)
warn:keyboard:X11DRV_KEYBOARD_DetectLayout 6 keysyms per keycode not supported, set to 4
warn:keyboard:X11DRV_KEYBOARD_DetectLayout Using closest match (Swedish keyboard layout) for scan/virtual codes mapping.
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
warn:keyboard:X11DRV_InitKeyboard vkey 01B3 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 01B3 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 012C is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 01B4 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard vkey 0003 is being used by more than one keycode
warn:keyboard:X11DRV_InitKeyboard No more vkeys available!
warn:class:CLASS_RegisterClass Win extra bytes 44 is > 40
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows\\_INS33IS._MP" not found (c0000034)
warn:driver:CloseDriver Failed to close driver
warn:driver:CloseDriver Failed to close driver
warn:driver:CloseDriver Failed to close driver
warn:driver:CloseDriver Failed to close driver
warn:driver:CloseDriver Failed to close driver
warn:driver:CloseDriver Failed to close driver
warn:driver:CloseDriver Failed to close driver
warn:driver:CloseDriver Failed to close driver
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows\\_delis32.ini" not found (c0000034)
warn:file:CreateFileW Unable to create file L"C:\\windows\\_delis32.ini" (status c0000034)
warn:profile:PROFILE_Open profile file L"C:\\windows\\_delis32.ini" not found
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows\\_delis32.ini" not found (c0000034)
warn:file:CreateFileW Unable to create file L"C:\\windows\\_delis32.ini" (status c0000034)
mathias@mathias-u31:~/Downloads/Photoshop 7/Ps_7$ warn:ntdll:FILE_CreateFile L"\\??\\C:\\stopthis.now" not found (c0000034)
warn:file:CreateFileW Unable to create file L"c:\\stopthis.now" (status c0000034)
warn:ntdll:FILE_CreateFile L"\\??\\C:\\windows\\profiles\\mathias\\Temp\\_ISTMP1.DIR\\_INS5576._MP" not found (c0000034)
warn:file:CreateFileW Unable to create file L"C:\\windows\\profiles\\mathias\\Temp\\_ISTMP1.DIR\\_INS5576._MP" (status c0000034)
```

---

### Post by Mathias1 on 2011-08-01
The problem is partially solved.
I didn't need to install the application, I could simply copy the files from my Wine directory on my other Ubuntu-computer.
Although I wouldn't recommend this, this was an last attempt and it was the only application I had installed under Wine.

---

