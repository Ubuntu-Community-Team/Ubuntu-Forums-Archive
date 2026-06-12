---
title: "Running OUTLAST with wine"
date: 2013-09-12
forum: Wine
---

### Post by Reynaldo2333 on 2013-09-12
i've installed it underwine with a 32bit environment, the thing is i keep getting this error.. game wont even open

```
err:menubuilder:convert_to_native_icon error 0x80004005 creating bitmap encoder
err:wincodecs:PngEncoder_CreateInstance Failed writing PNG because unable to find libpng16.so.16
fixme:ole:CoCreateInstance no instance created for interface {00000103-a8f2-4877-ba0a-fd2b6645fb94} of class {27949969-876a-41d7-9447-568f6a35a4dc}, hres is 0x80004005
err:menubuilder:convert_to_native_icon error 0x80004005 creating bitmap encoder
err:wincodecs:PngEncoder_CreateInstance Failed writing PNG because unable to find libpng16.so.16
fixme:ole:CoCreateInstance no instance created for interface {00000103-a8f2-4877-ba0a-fd2b6645fb94} of class {27949969-876a-41d7-9447-568f6a35a4dc}, hres is 0x80004005
err:menubuilder:convert_to_native_icon error 0x80004005 creating bitmap encoder
err:wincodecs:PngEncoder_CreateInstance Failed writing PNG because unable to find libpng16.so.16
fixme:ole:CoCreateInstance no instance created for interface {00000103-a8f2-4877-ba0a-fd2b6645fb94} of class {27949969-876a-41d7-9447-568f6a35a4dc}, hres is 0x80004005
err:menubuilder:convert_to_native_icon error 0x80004005 creating bitmap encoder
err:wincodecs:PngEncoder_CreateInstance Failed writing PNG because unable to find libpng16.so.16
fixme:ole:CoCreateInstance no instance created for interface {00000103-a8f2-4877-ba0a-fd2b6645fb94} of class {27949969-876a-41d7-9447-568f6a35a4dc}, hres is 0x80004005
err:menubuilder:convert_to_native_icon error 0x80004005 creating bitmap encoder
err:wincodecs:PngEncoder_CreateInstance Failed writing PNG because unable to find libpng16.so.16
fixme:ole:CoCreateInstance no instance created for interface {00000103-a8f2-4877-ba0a-fd2b6645fb94} of class {27949969-876a-41d7-9447-568f6a35a4dc}, hres is 0x80004005
err:menubuilder:convert_to_native_icon error 0x80004005 creating bitmap encoder
err:wincodecs:PngEncoder_CreateInstance Failed writing PNG because unable to find libpng16.so.16
fixme:ole:CoCreateInstance no instance created for interface {00000103-a8f2-4877-ba0a-fd2b6645fb94} of class {27949969-876a-41d7-9447-568f6a35a4dc}, hres is 0x80004005

```

some russian managed to do it.. link here

[www.youtube.com/watch?v=ldhIwiMa68Q](www.youtube.com/watch?v=ldhIwiMa68Q)

but no information .. :{

more information: 
im a old user dont hesitate to ask or to show any information that is complicated, since i have time to read.. atm downloading d3dx11 d3dx9 from winetricks

---

### Post by Toz on 2013-09-12
> err:wincodecs:PngEncoder_CreateInstance Failed writing PNG because [COLOR="#FF0000"]**unable to find libpng16.so.16**[/COLOR]
I'm thinking that this may have something to do with it. Unfortunately, ubuntu hasn't yet moved up to libpng16 (it still uses libpng12). Perhaps the youtube author compiled libpng16 from source?

---

### Post by dsong0305 on 2013-09-12
I am having similar problem. Would be nice if someone could add a detailed process on how to get it working on wine.

This is my problem :
err:module:import_dll Library d3dx11_43.dll (which is needed by L"C:\\Games\\Outlast\\Binaries\\Win64\\OLGame.exe") not found
err:module:import_dll Library X3DAudio1_7.dll (which is needed by L"C:\\Games\\Outlast\\Binaries\\Win64\\OLGame.exe") not found
err:module:import_dll Library XAPOFX1_5.dll (which is needed by L"C:\\Games\\Outlast\\Binaries\\Win64\\OLGame.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Games\\Outlast\\Binaries\\Win64\\OLGame.exe" failed, status c0000135

---

### Post by Toz on 2013-09-13
Hello and welcome to the forums.

> **dsong0305 said:**
> 
This is my problem :
err:module:import_dll Library d3dx11_43.dll (which is needed by L"C:\\Games\\Outlast\\Binaries\\Win64\\OLGame.exe") not found
err:module:import_dll Library X3DAudio1_7.dll (which is needed by L"C:\\Games\\Outlast\\Binaries\\Win64\\OLGame.exe") not found
err:module:import_dll Library XAPOFX1_5.dll (which is needed by L"C:\\Games\\Outlast\\Binaries\\Win64\\OLGame.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Games\\Outlast\\Binaries\\Win64\\OLGame.exe" failed, status c0000135
Looks like your missing directx 11 and xact. Try:
```
winetricks d3dx11 xact
```
> I am having similar problem. Would be nice if someone could add a detailed process on how to get it working on wine.
The [Wine HQ Application Database]("http://appdb.winehq.org/") is the place to go for instructions on how to (if possible) get windows applications running via wine. Unfortunately, this game is very new and doesn't have an entry in their database yet.

Whoever figures it out should create an entry there for others to follow.

---

### Post by Mateusz Stachowski on 2013-09-13
> **Toz said:**
> I'm thinking that this may have something to do with it. Unfortunately, ubuntu hasn't yet moved up to libpng16 (it still uses libpng12). Perhaps the youtube author compiled libpng16 from source?

This is related to winemenubuilder the thing in Wine responisble for creating menu entries. Obviously it doesn't prevent the game from running.

Wine doesn't have support for Direct3D 11 so I think it's better to disable it entirely in winecfg add d3d11 and set it to disabled (the game supports Direct3D 9) . I would also install xact_jun2010 instead of xact because the game is new so it probably uses newer version of those libraries.

In Steam recommended hardware spec to run this game there is also a this in additional notes:
> 
[LIST]
[*][COLOR=#626366]Additional Notes:[/COLOR] * 32 bits systems are not officially supported, but should work if configured to provide 3Gb of user-mode address space. See [http://msdn.microsoft.com/en-us/windows/bb613473](http://msdn.microsoft.com/en-us/windows/bb613473) or [http://steamcommunity.com/sharedfiles/filedetails/?id=175801311](http://steamcommunity.com/sharedfiles/filedetails/?id=175801311)
[/LIST]


This definitely needs to be addressed in 32-bit Wineprefix to make the game to work.

---

### Post by Reynaldo2333 on 2013-09-13
im running at 32 wine environment, d3dx11 and xact made the game start and crash, perhaps now its something about the game and not wine,  gonna check and report back, thanks everyone.

editt: latest log. Game opens, show initial Screen and then follows to crash.
edit2: i've tried to disable d3dx11, but it wont start without it. 

```

./Outlast.desktop: line 1: [Desktop: command not found
fixme:exec:SHELL_execute flags ignored: 0x00000100
fixme:exec:SHELL_execute flags ignored: 0x00004100
./Outlast.desktop: line 6: Files/Outlast/Binaries/Win32: No such file or directory
[rey@kael Desktop]$ err:module:load_builtin_dll failed to load .so lib for builtin L"winemp3.acm": libmpg123.so.0: cannot open shared object file: No such file or directory
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
Connection to "Provider=sqloledb;Data Source=production-db;Initial Catalog=EngineTaskPerf;Trusted_Connection=Yes;Connection Timeout=2" or "10.1.20.20" failed
fixme:gameux:GameExplorerImpl_VerifyAccess (0x151248, L"C:\\Program Files\\Outlast\\Binaries\\Win32\\OLGame.exe", 0x203f1b8)
fixme:win:EnumDisplayDevicesW ((null),0,0x203f2e8,0x00000000), stub!
fixme:d3d11:D3D11CreateDevice stub: adapter 0x1511c8, driver_type D3D_DRIVER_TYPE_UNKNOWN, swrast (nil), flags 0x1, feature_levels 33813856, levels 0x1, sdk_version 7, device 0x203f564, feature_level 0x203f7fc, context 0x203f568
fixme:win:EnumDisplayDevicesW ((null),0,0x203f2f8,0x00000000), stub!
fixme:alsa:AudioSessionControl_RegisterAudioSessionNotification (0x1602d8)->(0x5739b7c) - stub
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Audio",0x66ae938): stub
fixme:avrt:AvSetMmThreadPriority (0x12345678)->(1) stub
Warning, Failed to load 'PostProcessChain Asylum_post_process.asylum_PostProcess': Failed to find object 'PostProcessChain Asylum_post_process.asylum_PostProcess'
Warning, Failed to load 'PostProcessChain Asylum_post_process.asylum_PostProcess': Failed to find object 'PostProcessChain Asylum_post_process.asylum_PostProcess'
Warning, Failed to load 'PostProcessChain Asylum_post_process.asylum_PostProcess': Failed to find object 'PostProcessChain Asylum_post_process.asylum_PostProcess'
Couldn't find Master sound class! This class is required for the audio sound mode system to function!
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 53 (SPI_SETTOGGLEKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 51 (SPI_SETFILTERKEYS)
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
fixme:d3d:debug_d3dformat Unrecognized 0x34324644 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x34324644) in the format lookup table
fixme:d3d9:D3DPERF_SetOptions (0x1) : stub
fixme:d3d:query_init Unhandled query type 0xc.
Warning, Failed to load 'PostProcessChain Asylum_post_process.asylum_PostProcess': Failed to find object 'PostProcessChain Asylum_post_process.asylum_PostProcess'
Warning, Failed to load 'PostProcessChain Asylum_post_process.asylum_PostProcess': Failed to find object 'PostProcessChain Asylum_post_process.asylum_PostProcess'
LocalPlayer 0 - Failed to setup default post process...
fixme:thread:SetThreadIdealProcessor (0x2f0): stub
Warning, Failed to load 'Class None.': Failed to find object 'Class None.'
Warning, Failed to find object 'Class None.'
Warning, Failed to load 'Class None.': Failed to find object 'Class None.'
Warning, Failed to find object 'Class None.'
Warning, Failed to load 'Class None.': Failed to find object 'Class None.'
Warning, Failed to find object 'Class None.'
Warning, Failed to load 'Class None.': Failed to find object 'Class None.'
Warning, Failed to find object 'Class None.'
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
*** WARNING - PATHS MAY NOT BE VALID ***
fixme:win:EnumDisplayDevicesW ((null),0,0x20398c8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x2039668,0x00000000), stub!
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
fixme:ole:RemUnknown_QueryInterface No interface for iid {00000019-0000-0000-c000-000000000046}
err:ole:marshal_object couldn't get IPSFactory buffer for interface {aa80e801-2021-11d2-93e0-0060b067b86e}
err:ole:StdMarshalImpl_MarshalInterface Failed to create ifstub, hres=0x80040155
err:ole:CoMarshalInterface Failed to marshal the interface {aa80e801-2021-11d2-93e0-0060b067b86e}, 80040155
fixme:ole:NdrClearOutParameters (0x203ba40,0x7e6f9e00,0x203bc54): stub
fixme:ole:CoCreateInstance no instance created for interface {aa80e801-2021-11d2-93e0-0060b067b86e} of class {529a9e6b-6587-4f23-ab9e-9c7d683e3c50}, hres is 0x80040155
err:ole:marshal_object couldn't get IPSFactory buffer for interface {aa80e801-2021-11d2-93e0-0060b067b86e}
err:ole:StdMarshalImpl_MarshalInterface Failed to create ifstub, hres=0x80040155
err:ole:CoMarshalInterface Failed to marshal the interface {aa80e801-2021-11d2-93e0-0060b067b86e}, 80040155
fixme:ole:NdrClearOutParameters (0x203ba50,0x7e6f9e00,0xa0e9fd4): stub
fixme:ole:CoCreateInstance no instance created for interface {aa80e801-2021-11d2-93e0-0060b067b86e} of class {529a9e6b-6587-4f23-ab9e-9c7d683e3c50}, hres is 0x80040155
err:ole:marshal_object couldn't get IPSFactory buffer for interface {1f02b6c5-7842-4ee6-8a0b-9a24183a95ca}
err:ole:StdMarshalImpl_MarshalInterface Failed to create ifstub, hres=0x80040155
err:ole:CoMarshalInterface Failed to marshal the interface {1f02b6c5-7842-4ee6-8a0b-9a24183a95ca}, 80040155
fixme:ole:NdrClearOutParameters (0x203b770,0x7e6f9e00,0x203b9c0): stub
fixme:ole:CoCreateInstance no instance created for interface {1f02b6c5-7842-4ee6-8a0b-9a24183a95ca} of class {33c53a50-f456-4884-b049-85fd643ecfed}, hres is 0x80040155
fixme:msvcrt:MSVCRT__set_abort_behavior _WRITE_CALL_REPORTFAULT unhandled
fixme:msvcrt:__clean_type_info_names_internal (0x1016f408) stub
fixme:msvcrt:__clean_type_info_names_internal (0x29834c) stub
fixme:msvcrt:__clean_type_info_names_internal (0x21ca464) stub
fixme:msvcrt:__clean_type_info_names_internal (0x2a601c) stub
fixme:msvcrt:__clean_type_info_names_internal (0x28459c) stub

```

---

### Post by dsong0305 on 2013-09-15
Im still getting the same errors. I installed the xact and xact_jun2010 thing but i dont know if i have direct x installed and i dont know how :P.

---

### Post by vince15 on 2014-08-10
Hi, i've searched at google for the same problem, loading ''outlast'' and i've also the same startup and than it crashes. did you found the problem? i would seriously be happy if i can run it. thanks a lot in advance.

---

