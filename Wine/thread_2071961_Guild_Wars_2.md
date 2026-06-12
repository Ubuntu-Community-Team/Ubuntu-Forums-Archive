---
title: "Guild Wars 2"
date: 2012-10-16
forum: Wine
---

### Post by Thunder7102 on 2012-10-16
Alright, I have a dual-boot setup and since I usually game on my Windows partition, I thought I'd save some time and try to game from Ubuntu (since I use it the most anyway) without a reboot into Windows. 

I downloaded Wine 1.4 and tried running GW2 and after a couple seconds of downloading, I was greeted to a very tall black box. If I hovered my mouse over certain aspects of the box, the curser changed to show me that an invisible box entry was there (most likely username or password). 

I have tried launching the old launcher with the: *wine gw2.exe -oldlauncher* or something like that and had no luck. 

Here is a little more detail about what happened: 
My input:
**/media/System/Program Files (x86)/Guild Wars 2$ wine gw2.exe -useoldlauncher**

My Output:
```

p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory
fixme:heap:HeapSetInformation 0x1ccb000 0 0x32fd98 4
fixme:process:SetProcessDEPPolicy (1): stub
fixme:process:GetLogicalProcessorInformation (0x32f294,0x32f8c0): stub
fixme:process:GetLogicalProcessorInformation ((nil),0x350ddd0c): stub
fixme:process:GetLogicalProcessorInformation (0x350ddd34,0x350ddd0c): stub
fixme:process:GetLogicalProcessorInformation ((nil),0x350ddd14): stub
fixme:process:GetLogicalProcessorInformation (0x350ddd3c,0x350ddd14): stub
fixme:process:GetLogicalProcessorInformation ((nil),0x350ddd08): stub
fixme:process:GetLogicalProcessorInformation (0x350ddd30,0x350ddd08): stub
fixme:winsock:WS_getsockopt WS_SO_CONNECT_TIME - faking results
fixme:win:EnumDisplayDevicesW ((null),0,0x350d31f8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x350d2068,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x350d1f88,0x00000000), stub!
fixme:ddraw:ddraw7_Initialize Ignoring guid {aeb2cdd4-6e41-43ea-941c-8361cc760781}.
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 1920x1080x32 @0! (XRandR)
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {33d9a760-90c8-11d0-bd43-00a0c911ce86} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {33d9a761-90c8-11d0-bd43-00a0c911ce86} not found
ALSA lib conf.c:3314:(snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM default
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:d3d:debug_d3dformat Unrecognized 0x434f5441 (as fourcc: ATOC) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x434f5441) in the format lookup table
fixme:imm:ImmDisableTextFrameService Stub
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x60022 0x00000000
fixme:win:RegisterRawInputDevices (pRawInputDevices=0x350d3450, uiNumDevices=1, cbSize=12) stub!
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Audio",0x381ee9b8): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x350d2d40,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x350d3078,0x00000000), stub!
err:x11settings:X11DRV_ChangeDisplaySettingsEx No
```I'm running 8GB RAM and a GeForce GTX560, and a 2nd gen i5 on my system so I doubt hardware is the culprit. Supposedly, GTX560 drivers are decently supported by Ubuntu. Any ideas?

---

### Post by Sworddragon on 2012-10-19
The use of -dx9single should avoid the black flickering. There is a bug report on WineHQ about it and somebody is already working on this problem.

But you will encounter a few another problems if you continue. For example the installation will crash randomly. Wine has even some trouble with multithreading which will impact the performance of Guild Wars 2 heavily (Oh wait, I got a warning on WineHQ for this because they said I'm lying. Then all should be fine and you will surely have no performance problems :rolleyes:).

There is even a problem with chromium based applications and https connections. This means that you can't use the gem trading thingy menu. But there is an inofficial patch that will solve this problem. But I recommend you to use the newest Wine version because it supports Raw Input (otherwise you can't move around with the mouse).

---

