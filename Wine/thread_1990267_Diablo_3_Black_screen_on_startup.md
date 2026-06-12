---
title: "Diablo 3 Black screen on startup"
date: 2012-05-29
forum: Wine
---

### Post by otherethe on 2012-05-29
Alright So everything installed prefect ect so on so forth but when I start the game it gives me nothing more then a black screen but the music is playing in the back ground I've installed it using playonlinux,  My term out put is as followed

```
 fixme:d3d:wined3d_get_format Can't find format urecogized (0x3432644) in the format lookup table     
```

I was gonna copy past it all but when I try to my debugger closes :(

---

### Post by Erik1984 on 2012-05-29
Have you looked in AppDB? Don't know if it helps for this specific issue but there seems quite some info on this game: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=25953](http://appdb.winehq.org/objectManager.php?sClass=version&iId=25953)

---

### Post by sffvba[e0rt on 2012-05-29
Could help to have more info...

Distro you are using (32-bit vs 64-bit etc.)
Hardware (graphics card, drivers etc.)


404

---

### Post by donkyhotay on 2012-05-30
post is in wrong forum, should be moved to wine

---

### Post by nothingspecial on 2012-05-30
*Thread moved to **Wine**.*

---

### Post by nixIT on 2012-05-31
> **otherethe said:**
> Alright So everything installed prefect ect so on so forth but when I start the game it gives me nothing more then a black screen but the music is playing in the back ground I've installed it using playonlinux,  My term out put is as followed

```
 fixme:d3d:wined3d_get_format Can't find format urecogized (0x3432644) in the format lookup table     
```

I was gonna copy past it all but when I try to my debugger closes :(

I have successfully run diablo 3 by installing vcrun2008 with winetricks and starting the executable with the "-launch" parameter.

I did do the install and update from my windows partition, and then just copied over the directory.

---

### Post by otherethe on 2012-06-11
I'm running PlayonLinux with the wine version it gives for Diablo 3 My system is 64bit Ubuntu 12.04, Nvidia Geforce 7900 GTX but Diablo says it's 7800 I have to use the esc key to make it go away to start the game up then black screen from there here is term out put is as follow

```
  fixme:process:GetLogicalProcessorInformation (0x13be368,0x13be968): stub
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:process:GetLogicalProcessorInformation (0x245e358,0x245e958): stub
fixme:process:GetLogicalProcessorInformation (0x245e358,0x245e958): stub
fixme:process:GetLogicalProcessorInformation (0x245e358,0x245e958): stub
fixme:process:GetLogicalProcessorInformation (0x245e358,0x245e958): stub
fixme:process:GetLogicalProcessorInformation (0x33ef10,0x33f510): stub
fixme:process:GetLogicalProcessorInformation (0x33f008,0x33f608): stub
fixme:process:GetLogicalProcessorInformation (0x33f008,0x33f608): stub
Handle Event: "auth validation event"
Removing uri "/update/diablo3_enus" since it has no process interested in it.
Request Issued: DELETE /update/diablo3_enus
Database Remove: /update/diablo3_enus
Queue 'async_task' Resource for delete
Deferred delete of 'async_task' Resource
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
err:ntdll:RtlpWaitForCriticalSection section 0x9799cc "?" wait timed out in thread 003b, blocked by 0030, retrying (60 sec)
fixme:win:EnumDisplayDevicesW ((null),0,0x33f678,0x00000000), stub!
ERROR: 
    Could Not Find D3DKMTEscape in gdi32.dll
    Could Not Find D3DKMTOpenAdapterFromHdc in gdi32.dll
fixme:d3d:query_init Unhandled query type 0x11.
fixme:d3d:query_init Unhandled query type 0x12.
fixme:d3d:query_init Unhandled query type 0xe.
fixme:d3d:query_init Unhandled query type 0xd.
fixme:d3d:query_init Unhandled query type 0x6.
fixme:d3d:query_init Unhandled query type 0xf.
fixme:d3d:query_init Unhandled query type 0x5.
fixme:win:EnumDisplayDevicesW ((null),0,0x33f2e0,0x00000000), stub!
fixme:d3d:debug_d3dformat Unrecognized 0x34324644 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x34324644) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x34324644 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x34324644) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x34324644 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x34324644) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x36314644 (as fourcc: DF16) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x36314644) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x36314644 (as fourcc: DF16) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x36314644) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x36314644 (as fourcc: DF16) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x36314644) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x5a574152 (as fourcc: RAWZ) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x5a574152) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x5a574152 (as fourcc: RAWZ) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x5a574152) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x5a574152 (as fourcc: RAWZ) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x5a574152) in the format lookup table
ALSA lib conf.c:3314:(snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM default
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Audio",0xf15e9a8): stub
fixme:process:GetLogicalProcessorInformation (0x33f6d0,0x33fcd0): stub
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d_draw:drawPrimitive Using software emulation because manual fog coordinates are provided
  
```

---

### Post by otherethe on 2012-06-14
Anyone?

---

### Post by sffvba[e0rt on 2012-06-14
Not sure what the specific issue is, I have to mention however I have had much less issues making things work in 32-bit linux then in 64-bit linux.


404

---

### Post by ergo-proxy on 2012-06-14
For the best compatibility you should use 32bit wine, either patched, compiled on virtualbox running ubuntu x32 and copied to host or just use PoL, both options work.

---

