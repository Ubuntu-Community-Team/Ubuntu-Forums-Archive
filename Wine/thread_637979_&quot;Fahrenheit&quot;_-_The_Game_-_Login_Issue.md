---
title: "&quot;Fahrenheit&quot; - The Game - Login Issue"
date: 2007-12-11
forum: Wine
---

### Post by b0rka7a on 2007-12-11
Hi, guys :)
I just installed Fahrenheit. The installation went fine, when I start the game everything is fine too. But when I create a New Login and I try to Login with it my game freezes and the screen becomes black. Here's the game output:
```
boris@boris-ubuntu710:~/.wine/drive_c/Program Files/Atari/Fahrenheit$ wine Fahrenheit.exe 
fixme:mixer:ALSA_MixerInit No master control found on MPU-401 UART, disabling mixer
MEM_POOL_HEADER::AddMemPool Size:8 Total: 2212 Allocated: 2148 Free: 64
fixme:win:EnumDisplayDevicesW ((null),0,0x35f778,0x00000000), stub!
fixme:d3d:IWineD3DImpl_CheckDeviceMultiSampleType Quality levels unsupported at present
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 53 (SPI_SETTOGGLEKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 51 (SPI_SETFILTERKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 55 (SPI_SETMOUSEKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 53 (SPI_SETTOGGLEKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 51 (SPI_SETFILTERKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 55 (SPI_SETMOUSEKEYS)
fixme:dinput:SysMouseAImpl_Acquire Clipping cursor to (0,0)-(640,480)
MEM_POOL_HEADER::AddMemPool Size:64 Total: 800 Allocated: 768 Free: 32
MEM_POOL_HEADER::AddMemPool Size:64 Total: 832 Allocated: 800 Free: 32
MEM_POOL_HEADER::AddMemPool Size:64 Total: 864 Allocated: 832 Free: 32
MEM_POOL_HEADER::AddMemPool Size:64 Total: 896 Allocated: 864 Free: 32
MEM_POOL_HEADER::AddMemPool Size:64 Total: 928 Allocated: 896 Free: 32
MEM_POOL_HEADER::AddMemPool Size:64 Total: 960 Allocated: 928 Free: 32
MEM_POOL_HEADER::AddMemPool Size:64 Total: 992 Allocated: 960 Free: 32
MEM_POOL_HEADER::AddMemPool Size:64 Total: 1024 Allocated: 992 Free: 32
MEM_POOL_HEADER::AddMemPool Size:64 Total: 1056 Allocated: 1024 Free: 32
MEM_POOL_HEADER::AddMemPool Size:64 Total: 1088 Allocated: 1056 Free: 32
MEM_POOL_HEADER::AddMemPool Size:64 Total: 1120 Allocated: 1088 Free: 32
MEM_POOL_HEADER::AddMemPool Size:64 Total: 1152 Allocated: 1120 Free: 32
MEM_POOL_HEADER::AddMemPool Size:64 Total: 1184 Allocated: 1152 Free: 32
MEM_POOL_HEADER::AddMemPool Size:64 Total: 1216 Allocated: 1184 Free: 32
MEM_POOL_HEADER::AddMemPool Size:64 Total: 1248 Allocated: 1216 Free: 32
MEM_POOL_HEADER::AddMemPool Size:64 Total: 1280 Allocated: 1248 Free: 32
MEM_POOL_HEADER::AddMemPool Size:64 Total: 1312 Allocated: 1280 Free: 32
MEM_POOL_HEADER::AddMemPool Size:64 Total: 1344 Allocated: 1312 Free: 32
MEM_POOL_HEADER::AddMemPool Size:64 Total: 1376 Allocated: 1344 Free: 32
MEM_POOL_HEADER::AddMemPool Size:64 Total: 1408 Allocated: 1376 Free: 32
MEM_POOL_HEADER::AddMemPool Size:64 Total: 1440 Allocated: 1408 Free: 32
MEM_POOL_HEADER::AddMemPool Size:64 Total: 1472 Allocated: 1440 Free: 32
MEM_POOL_HEADER::AddMemPool Size:64 Total: 1504 Allocated: 1472 Free: 32
MEM_POOL_HEADER::AddMemPool Size:64 Total: 1536 Allocated: 1504 Free: 32
MEM_POOL_HEADER::AddMemPool Size:64 Total: 1568 Allocated: 1536 Free: 32
MEM_POOL_HEADER::AddMemPool Size:64 Total: 1600 Allocated: 1568 Free: 32
MEM_POOL_HEADER::AddMemPool Size:64 Total: 1632 Allocated: 1600 Free: 32
MEM_POOL_HEADER::AddMemPool Size:64 Total: 1664 Allocated: 1632 Free: 32
MEM_POOL_HEADER::AddMemPool Size:64 Total: 1696 Allocated: 1664 Free: 32
MEM_POOL_HEADER::AddMemPool Size:64 Total: 1728 Allocated: 1696 Free: 32
MEM_POOL_HEADER::AddMemPool Size:64 Total: 1760 Allocated: 1728 Free: 32
MEM_POOL_HEADER::AddMemPool Size:64 Total: 1792 Allocated: 1760 Free: 32
MEM_POOL_HEADER::AddMemPool Size:64 Total: 1824 Allocated: 1792 Free: 32
MEM_POOL_HEADER::AddMemPool Size:64 Total: 1856 Allocated: 1824 Free: 32
MEM_POOL_HEADER::AddMemPool Size:64 Total: 1888 Allocated: 1856 Free: 32
MEM_POOL_HEADER::AddMemPool Size:64 Total: 1920 Allocated: 1888 Free: 32
MEM_POOL_HEADER::AddMemPool Size:64 Total: 1952 Allocated: 1920 Free: 32
MEM_POOL_HEADER::AddMemPool Size:64 Total: 1984 Allocated: 1952 Free: 32
MEM_POOL_HEADER::AddMemPool Size:64 Total: 2016 Allocated: 1984 Free: 32
MEM_POOL_HEADER::AddMemPool Size:64 Total: 2048 Allocated: 2016 Free: 32
MEM_POOL_HEADER::AddMemPool Size:64 Total: 2080 Allocated: 2048 Free: 32
MEM_POOL_HEADER::AddMemPool Size:64 Total: 2112 Allocated: 2080 Free: 32
MEM_POOL_HEADER::AddMemPool Size:64 Total: 2144 Allocated: 2112 Free: 32
MEM_POOL_HEADER::AddMemPool Size:64 Total: 2176 Allocated: 2144 Free: 32
MEM_POOL_HEADER::AddMemPool Size:64 Total: 2208 Allocated: 2176 Free: 32
MEM_POOL_HEADER::AddMemPool Size:64 Total: 2240 Allocated: 2208 Free: 32
MEM_POOL_HEADER::AddMemPool Size:64 Total: 2272 Allocated: 2240 Free: 32
MEM_POOL_HEADER::AddMemPool Size:64 Total: 2304 Allocated: 2272 Free: 32
MEM_POOL_HEADER::AddMemPool Size:64 Total: 2336 Allocated: 2304 Free: 32
MEM_POOL_HEADER::AddMemPool Size:64 Total: 2368 Allocated: 2336 Free: 32
MEM_POOL_HEADER::AddMemPool Size:64 Total: 2400 Allocated: 2368 Free: 32
MEM_POOL_HEADER::AddMemPool Size:64 Total: 2432 Allocated: 2400 Free: 32
MEM_POOL_HEADER::AddMemPool Size:64 Total: 2464 Allocated: 2432 Free: 32
MEM_POOL_HEADER::AddMemPool Size:64 Total: 2496 Allocated: 2464 Free: 32
MEM_POOL_HEADER::AddMemPool Size:64 Total: 2528 Allocated: 2496 Free: 32
MEM_POOL_HEADER::AddMemPool Size:64 Total: 2560 Allocated: 2528 Free: 32
MEM_POOL_HEADER::AddMemPool Size:64 Total: 2592 Allocated: 2560 Free: 32
MEM_POOL_HEADER::AddMemPool Size:64 Total: 2624 Allocated: 2592 Free: 32
MEM_POOL_HEADER::AddMemPool Size:64 Total: 2656 Allocated: 2624 Free: 32
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 53 (SPI_SETTOGGLEKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 51 (SPI_SETFILTERKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 55 (SPI_SETMOUSEKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 53 (SPI_SETTOGGLEKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 51 (SPI_SETFILTERKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 55 (SPI_SETMOUSEKEYS)
preload son stereo 70
boris@boris-ubuntu710:~/.wine/drive_c/Program Files/Atari/Fahrenheit$
```
So... I don't have a clue what to do (as always). :)
Could you help me solve this ? Thanks!

---

### Post by cogadh on 2007-12-11
That's a known bug in Wine with the game:
[http://bugs.winehq.org/show_bug.cgi?id=6861](http://bugs.winehq.org/show_bug.cgi?id=6861)

---

### Post by b0rka7a on 2007-12-12
So there is no answer to my question how to fix that bug :(
If anyone else knows how to fix it....

---

