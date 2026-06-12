---
title: "Guild Wars Opens and Closes"
date: 2008-07-19
forum: Wine
---

### Post by Vakman on 2008-07-19
I have installed Guild Wars under Wine. But whenever I open it, it starts to open and looks like it is going to load but does not boot into the game. It just disappears with no error messages or anything. Any ideas? 
Oh and I am running Ubuntu 8.04.
I believe I am running Wine wine 0.9.59 now, but I was running with the most updated one. I just heard that wine 0.9.59 worked better for Guild Wars.

---

### Post by Kennyz79 on 2008-07-19
Yes, the updated version of Wine works much better for Guild Wars.  I use the original Guild Wars, with no addons, just have never purchased them is all.  I had a few problems with it, but lately it has been running fine.  I recommend updating your version of Wine, anytime you can.

> **Thisislaw said:**
> I have installed Guild Wars under Wine. But whenever I open it, it starts to open and looks like it is going to load but does not boot into the game. It just disappears with no error messages or anything. Any ideas? 
Oh and I am running Ubuntu 8.04.
I believe I am running Wine wine 0.9.59 now, but I was running with the most updated one. I just heard that wine 0.9.59 worked better for Guild Wars.

---

### Post by Vakman on 2008-07-19
Thank you. But I did have the updated version of Wine. I decided to go back because I still experienced the same issue. So I am still not sure what the problem is.

---

### Post by Vakman on 2008-07-19
So I installed Wine version 1.1.0. New problem with Guild Wars now. I believe it said:
"Guild Wars has encountered an unrecoverable graphical error..."
Any ideas?

---

### Post by The Tronyx on 2008-07-20
It's a problem with fglrx.  It has been reported on multiple threads and even on winehq.  As far as I know there is currently no fix/patch and there may be no rush as nvidia users aren't having any problems (that I have read).  I am guessing you are using an ATI card/fglrx?

---

### Post by Vakman on 2008-07-20
Yes, I am using an ATI card. I stopped commenting after I read [http://bugs.winehq.org/show_bug.cgi?id=12870](http://bugs.winehq.org/show_bug.cgi?id=12870)
But there is one comment on that page and he said he got it working. I do not understand what he did though. I am planning on emailing him and asking him to explain. Thank you.

---

### Post by Vakman on 2008-08-20
Well I have Guild Wars able to open to the login screen and even login but only if I do it quickly now. It always closes soon after I have logged in or whether it is just sitting open. Any ideas?

---

### Post by Ferrat on 2008-08-21
run it in a terminal and post the output just before it crashes :)

---

### Post by Vakman on 2008-08-21
> **Ferrat said:**
> run it in a terminal and post the output just before it crashes :)
Well without the debug code there are a lot of fixme things. If I have it in full screen and also not in Virtual environment then it will not crash but the keyboard doesn't work. If I put it in virtual environment, then the keyboard works. I will post two outputs of without the debug run and with.
Without:
```
thisislaw@ubuntu:~$ wine "C:/Program Files/Guild Wars/Gw.exe"
fixme:win:EnumDisplayDevicesW ((null),0,0x33ec58,0x00000000), stub!
fixme:dxdiag:DXDiag_AddFileDescContainer (0x133960,L"ddraw.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x133960,L"dplayx.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x133960,L"dpnet.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x133960,L"dinput.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x133960,L"dinput8.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x133960,L"dsound.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x133960,L"dswave.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x133960,L"d3d8.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x133960,L"d3d9.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x133960,L"dmband.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x133960,L"dmcompos.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x133960,L"dmime.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x133960,L"dmloader.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x133960,L"dmscript.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x133960,L"dmstyle.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x133960,L"dmsynth.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x133960,L"dmusic.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x133960,L"devenum.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x133960,L"quartz.dll")
fixme:win:EnumDisplayDevicesW ((null),0,0x33e58c,0x00000000), stub!
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({083863f1-70de-11d0-bd40-00a0c911ce86}) pEnum(0x13a2b0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x13a2b0, 1, 0x13a2c8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"AVI Splitter"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{1B544C20-FD0B-11CE-8C63-00AA0044B51E}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x13a2b0, 1, 0x13a2e0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"MPEG-I Stream Splitter"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{336475D0-942A-11CE-A870-00AA002FEAB5}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x13a2b0, 1, 0x13a9b8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"ACM Wrapper"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{6A08CF80-0E18-11CF-A24D-0020AFD79767}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x13a2b0, 1, 0x13ada8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Video Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{6BC1CFFA-8FC1-4261-AC22-CFB4CC38DB50}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x13a2b0, 1, 0x13b390)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Video Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{70E102B0-5556-11CE-97C0-00AA0055595A}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x13a2b0, 1, 0x13b7b8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Audio Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{79376820-07D0-11CF-A24D-0020AFD79767}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x13a2b0, 1, 0x13bbe0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Null Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{C1F400A4-3F08-11D3-9F0B-006008039E37}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x13a2b0, 1, 0x13c008)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"AVI Decompressor"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{CF49D4E0-1115-11CE-B03A-0020AF0BA770}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x13a2b0, 1, 0x13c430)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Wave Parser"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{D51BD5A1-7548-11CF-A520-0080C77EF58A}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x13a2b0, 1, 0x13c888)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"File Source (Async.)"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{E436EBB5-524F-11CE-9F53-0020AF0BA770}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({33d9a760-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x13a080)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({33d9a761-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x13a080)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({33d9a762-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x13a088)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x13a088, 1, 0x13a0a0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"dsnoop:0"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{E30629D2-27E5-11CE-875D-00608CB78066}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({4efe2452-168a-11d1-bc76-00c04fb9453b}) pEnum(0x13a050)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x13a050, 1, 0x13a068)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Midi Through"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{07B65360-C445-11CE-AFDE-00AA006C14F4}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({860bb310-5d01-11d0-bd3b-00a0c911ce86}) pEnum(0x13a080)
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({cc7bfb41-f175-11d1-a392-00e0291f3959}) pEnum((nil))
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({cc7bfb46-f175-11d1-a392-00e0291f3959}) pEnum((nil))
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({e0f158e1-cb04-11d0-bd4e-00a0c911ce86}) pEnum(0x13a080)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x13a080, 1, 0x13d9e8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"DirectSound: dmix:0"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{79376820-07D0-11CF-A24D-0020AFD79767}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x13a080, 1, 0x13da00)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"dmix:0"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{E30629D1-27E5-11CE-875D-00608CB78066}"
fixme:dxdiag:DXDiag_AddFileDescContainer (0x13e868,L"ddraw.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x13e868,L"dplayx.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x13e868,L"dpnet.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x13e868,L"dinput.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x13e868,L"dinput8.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x13e868,L"dsound.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x13e868,L"dswave.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x13e868,L"d3d8.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x13e868,L"d3d9.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x13e868,L"dmband.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x13e868,L"dmcompos.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x13e868,L"dmime.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x13e868,L"dmloader.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x13e868,L"dmscript.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x13e868,L"dmstyle.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x13e868,L"dmsynth.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x13e868,L"dmusic.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x13e868,L"devenum.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x13e868,L"quartz.dll")
fixme:win:EnumDisplayDevicesW ((null),0,0x33e628,0x00000000), stub!
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({083863f1-70de-11d0-bd40-00a0c911ce86}) pEnum(0x143758)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x143758, 1, 0x143770)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"AVI Splitter"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{1B544C20-FD0B-11CE-8C63-00AA0044B51E}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x143758, 1, 0x143788)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"MPEG-I Stream Splitter"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{336475D0-942A-11CE-A870-00AA002FEAB5}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x143758, 1, 0x143c00)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"ACM Wrapper"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{6A08CF80-0E18-11CF-A24D-0020AFD79767}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x143758, 1, 0x144230)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Video Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{6BC1CFFA-8FC1-4261-AC22-CFB4CC38DB50}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x143758, 1, 0x144810)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Video Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{70E102B0-5556-11CE-97C0-00AA0055595A}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x143758, 1, 0x144c38)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Audio Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{79376820-07D0-11CF-A24D-0020AFD79767}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x143758, 1, 0x145060)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Null Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{C1F400A4-3F08-11D3-9F0B-006008039E37}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x143758, 1, 0x145488)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"AVI Decompressor"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{CF49D4E0-1115-11CE-B03A-0020AF0BA770}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x143758, 1, 0x1458b0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Wave Parser"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{D51BD5A1-7548-11CF-A520-0080C77EF58A}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x143758, 1, 0x145d08)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"File Source (Async.)"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{E436EBB5-524F-11CE-9F53-0020AF0BA770}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({33d9a760-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x143730)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({33d9a761-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x143730)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({33d9a762-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x143738)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x143738, 1, 0x143750)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"dsnoop:0"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{E30629D2-27E5-11CE-875D-00608CB78066}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({4efe2452-168a-11d1-bc76-00c04fb9453b}) pEnum(0x143710)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x143710, 1, 0x143728)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Midi Through"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{07B65360-C445-11CE-AFDE-00AA006C14F4}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({860bb310-5d01-11d0-bd3b-00a0c911ce86}) pEnum(0x1460d8)
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({cc7bfb41-f175-11d1-a392-00e0291f3959}) pEnum((nil))
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({cc7bfb46-f175-11d1-a392-00e0291f3959}) pEnum((nil))
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({e0f158e1-cb04-11d0-bd4e-00a0c911ce86}) pEnum(0x1436e0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x1436e0, 1, 0x1436f8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"DirectSound: dmix:0"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{79376820-07D0-11CF-A24D-0020AFD79767}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x1436e0, 1, 0x146e80)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"dmix:0"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{E30629D1-27E5-11CE-875D-00608CB78066}"
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x151a40) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x151a40) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x151a40) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x151a40) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x151a40) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x151a40) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x151a40) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x151a40) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x151a40) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x151a40) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x151a40) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x151a40) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x151a40) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x151a40) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x151a40) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x151a40) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x151a40) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x151a40) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x151a40) : stub
fixme:d3d:state_zfunc D3DCMP_NOTEQUAL and D3DCMP_EQUAL do not work correctly yet
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x151a40) : stub
dontfixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x151a40) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x151a40) : stub

```
And when it has the debug run and closes, it says nothing at all. No output in terminal.

---

