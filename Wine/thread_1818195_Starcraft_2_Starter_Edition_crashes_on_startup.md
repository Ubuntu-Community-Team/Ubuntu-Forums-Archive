---
title: "Starcraft 2 Starter Edition crashes on startup"
date: 2011-08-04
forum: Wine
---

### Post by anthony62490 on 2011-08-04
I realize that the free version of Starcraft 2 was only released yesterday, but I figured I would post a question here in case anyone has any ideas.

I have downloaded the installer from [[COLOR="Blue"]here[/COLOR]]("https://us.battle.net/account/sc2/starter-edition/").

**Specs:**
Wine 1.2.2 (freshly installed with no tweaking. Configured for Windows 7 with no DLLs)
AMD Sempron Processor 3300+
2GB RAM
Ubuntu 10.04.3 LTS
YMF724F - Yamaha DS-1 (YMF724F) GFX Card

```
/.wine/drive_c/Program Files/StarCraft II$ env WINEPREFIX="/home/johnathan/.wine" wine C:\\Program\ Files\\StarCraft\ II\\StarCraft\ II.exe

fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (2000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 2000
fixme:win:EnumDisplayDevicesW ((null),0,0xe3c10c,0x00000000), stub!
fixme:ddraw:DirectDrawEnumerateExA flags 0x00000003 not handled
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (3000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 3000
johnathan@johnathan-desktop:~/.wine/drive_c/Program Files/StarCraft II$ fixme:hnetcfg:fw_profile_get_FirewallEnabled 0x144128, 0x458f0d4
fixme:process:GetProcessWorkingSetSize (0xffffffff,0x458ed54,0x458ed58): stub
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:win:EnumDisplayDevicesW ((null),0,0x458e7fc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x458e740,0x00000000), stub!
fixme:d3d:debug_d3dformat Unrecognized 909198916 (as fourcc: DF16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909198916) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909198916 (as fourcc: DF16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909198916) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(875710020) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(875710020) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1280070990) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1280070990) in the format lookup table
fixme:win:EnumDisplayDevicesW ((null),0,0x458ecf0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x458e5c8,0x00000000), stub!
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:win:EnumDisplayDevicesW ((null),0,0x458e5a0,0x00000000), stub!
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Audio",0x7f6ea38): stub
fixme:msctf:ThreadMgrSource_AdviseSink (0x76c33a8) Unhandled Sink: {71c6e74e-0f28-11d8-a82a-00065b84435c}
err:d3d:resource_init Out of adapter memory
fixme:process:GetProcessWorkingSetSize (0xffffffff,0x394cd60,0x394cd64): stub
fixme:process:GetProcessWorkingSetSize (0xffffffff,0x394c9ec,0x394c9f0): stub
fixme:ntdll:NtPowerInformation semi-stub: SystemPowerCapabilities
AL lib: ALc.c:1879: exit(): closing 1 Device
AL lib: ALc.c:1808: alcCloseDevice(): destroying 1 Context(s)
AL lib: ALc.c:1420: alcDestroyContext(): deleting 1 Source(s)
Inconsistency detected by ld.so: dl-close.c: 731: _dl_close: Assertion `map->l_init_called' failed!

```

I'm not too good with wine, but maybe you see something I don't?

---

### Post by 3Miro on 2011-08-04
Have you looked at WineHQ:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=20882](http://appdb.winehq.org/objectManager.php?sClass=version&iId=20882)

My guess is that you need to overwrite mmdevapi as stated in the WineHQ howto.

---

### Post by sffvba[e0rt on 2011-08-04
Get yourself the latest version of PlayOnLinux... works for the full game, should work for this version.

---

### Post by 8Kuula on 2011-08-04
> **anthony62490 said:**
> I realize that the free version of Starcraft 2 was only released yesterday, but I figured I would post a question here in case anyone has any ideas.

I have downloaded the installer from [[COLOR="Blue"]here[/COLOR]]("https://us.battle.net/account/sc2/starter-edition/").

**Specs:**
Wine 1.2.2 (freshly installed with no tweaking. Configured for Windows 7 with no DLLs)
AMD Sempron Processor 3300+
2GB RAM
Ubuntu 10.04.3 LTS
YMF724F - Yamaha DS-1 (YMF724F) GFX Card

```
/.wine/drive_c/Program Files/StarCraft II$ env WINEPREFIX="/home/johnathan/.wine" wine C:\\Program\ Files\\StarCraft\ II\\StarCraft\ II.exe

fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (2000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 2000
fixme:win:EnumDisplayDevicesW ((null),0,0xe3c10c,0x00000000), stub!
fixme:ddraw:DirectDrawEnumerateExA flags 0x00000003 not handled
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (3000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 3000
johnathan@johnathan-desktop:~/.wine/drive_c/Program Files/StarCraft II$ fixme:hnetcfg:fw_profile_get_FirewallEnabled 0x144128, 0x458f0d4
fixme:process:GetProcessWorkingSetSize (0xffffffff,0x458ed54,0x458ed58): stub
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:win:EnumDisplayDevicesW ((null),0,0x458e7fc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x458e740,0x00000000), stub!
fixme:d3d:debug_d3dformat Unrecognized 909198916 (as fourcc: DF16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909198916) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909198916 (as fourcc: DF16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909198916) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(875710020) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(875710020) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1280070990) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1280070990) in the format lookup table
fixme:win:EnumDisplayDevicesW ((null),0,0x458ecf0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x458e5c8,0x00000000), stub!
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:win:EnumDisplayDevicesW ((null),0,0x458e5a0,0x00000000), stub!
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Audio",0x7f6ea38): stub
fixme:msctf:ThreadMgrSource_AdviseSink (0x76c33a8) Unhandled Sink: {71c6e74e-0f28-11d8-a82a-00065b84435c}
err:d3d:resource_init Out of adapter memory
fixme:process:GetProcessWorkingSetSize (0xffffffff,0x394cd60,0x394cd64): stub
fixme:process:GetProcessWorkingSetSize (0xffffffff,0x394c9ec,0x394c9f0): stub
fixme:ntdll:NtPowerInformation semi-stub: SystemPowerCapabilities
AL lib: ALc.c:1879: exit(): closing 1 Device
AL lib: ALc.c:1808: alcCloseDevice(): destroying 1 Context(s)
AL lib: ALc.c:1420: alcDestroyContext(): deleting 1 Source(s)
Inconsistency detected by ld.so: dl-close.c: 731: _dl_close: Assertion `map->l_init_called' failed!

```

I'm not too good with wine, but maybe you see something I don't?

Try with Wine v1.3.x

1.) Remove wine 1.2.x

2.)
 $ sudo add-apt-repository ppa:ubuntu-wine/ppa
 $ sudo apt-get update
 $ sudo apt-get install wine1.3

3.) I think you next hit problem with mouse not working good (problem came after v1.3.19), so...
$ winecfg

On "Graphics" tab enable "emulate a virtual desktop" and set desktop size to what your desktop size is (1920x1080 for example).

Look that "automatically capture the mouse in full-screen windows" checkbox is not checked.

"Allow the windows manager..." both checked.

Retail version works for me like this, there is little graphical hickup on terran workers (they have like long spike on their shoulder). I havent played SC2 beyond few custom games now and then since October 2010 I think, so do not know how other areas work.

---

