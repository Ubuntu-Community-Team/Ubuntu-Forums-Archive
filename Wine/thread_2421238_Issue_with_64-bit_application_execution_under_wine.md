---
title: "Issue with 64-bit application execution under wine (missing “Microsoft.VC80.CRT”)"
date: 2019-06-18
forum: Wine
---

### Post by awebtech on 2019-06-18
[COLOR=#242729][FONT=Arial]Hello, I face the following errors when I try to run 64-bit console application with wine:[/FONT][/COLOR]
```
002a:fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
002a:fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
002a:fixme:nls:GetThreadPreferredUILanguages 00000038, 0x23e480, 0x23e490 0x23e484
002a:fixme:nls:get_dummy_preferred_ui_language (0x38 0x23e480 0x23e490 0x23e484) returning a dummy value (current locale)
002a:fixme:heap:RtlSetHeapInformation 0xa80000 0 0x23e7a0 4 stub
002a:err:module:attach_dlls "MSVCR80.dll" failed to initialize, aborting
002a:err:module:attach_dlls Initializing dlls for L"Z:\\home\\user\\test\\x64\\process.exe" failed, status c0000142

```[COLOR=#242729][FONT=Arial]I must mention that MS Visual C++ 2005 Redistributable Package is already installed using command[/FONT][/COLOR]
```
[FONT=inherit]winetricks vcrun2005[/FONT]
```[COLOR=#242729][FONT=Arial]Also I have downloaded the "msvcr80.dll" file with the exact same version (8.0.50727.762) and I have put it in the application folder.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]And the issue is still not resolved unfortunately.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Any help would be greatly appreciated! Thanks in advance.[/FONT][/COLOR]

---

