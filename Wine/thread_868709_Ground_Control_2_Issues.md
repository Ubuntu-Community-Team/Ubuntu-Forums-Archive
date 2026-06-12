---
title: "Ground Control 2 Issues"
date: 2008-07-24
forum: Wine
---

### Post by Plasma_NZ on 2008-07-24
FIrst off, i have a

Bus 001 Device 007: ID 046d:c216 Logitech, Inc. Dual Action Gamepad

Which is seen in games but doesnt work, e.g. buttons and axis pads.. no idea whats the story there..

secondly

Have installed etc.. cant get it to launch...


```

physics@physics:/media/hdb5/Installed_games/Ground Control II$ wine gcii.exe 
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on CA0106, disabling mixer
fixme:dxdiag:DXDiag_AddFileDescContainer (0x121d40,L"ddraw.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x121d40,L"dplayx.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x121d40,L"dpnet.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x121d40,L"dinput.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x121d40,L"dinput8.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x121d40,L"dsound.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x121d40,L"dswave.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x121d40,L"d3d8.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x121d40,L"d3d9.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x121d40,L"dmband.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x121d40,L"dmcompos.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x121d40,L"dmime.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x121d40,L"dmloader.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x121d40,L"dmscript.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x121d40,L"dmstyle.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x121d40,L"dmsynth.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x121d40,L"dmusic.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x121d40,L"devenum.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x121d40,L"quartz.dll")
fixme:win:EnumDisplayDevicesW ((null),0,0x32aa6c,0x00000000), stub!
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x32a4a8,0x00000000), stub!
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	ClassEnumerator for clsid({083863f1-70de-11d0-bd40-00a0c911ce86}) pEnum(0x145f60)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x145f60, 1, 0x148028)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"AVI Splitter"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{1B544C20-FD0B-11CE-8C63-00AA0044B51E}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x145f60, 1, 0x148040)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"MPEG-I Stream Splitter"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{336475D0-942A-11CE-A870-00AA002FEAB5}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x145f60, 1, 0x146e80)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"ACM Wrapper"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{6A08CF80-0E18-11CF-A24D-0020AFD79767}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x145f60, 1, 0x147288)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"Video Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{6BC1CFFA-8FC1-4261-AC22-CFB4CC38DB50}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x145f60, 1, 0x147720)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"Video Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{70E102B0-5556-11CE-97C0-00AA0055595A}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x145f60, 1, 0x147a38)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"Audio Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{79376820-07D0-11CF-A24D-0020AFD79767}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x145f60, 1, 0x14a070)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"Null Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{C1F400A4-3F08-11D3-9F0B-006008039E37}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x145f60, 1, 0x14a420)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"AVI Decompressor"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{CF49D4E0-1115-11CE-B03A-0020AF0BA770}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x145f60, 1, 0x14a7b8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"Wave Parser"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{D51BD5A1-7548-11CF-A520-0080C77EF58A}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x145f60, 1, 0x14abf0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"Audio Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{E30629D1-27E5-11CE-875D-00608CB78066}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x145f60, 1, 0x14aeb0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"File Source (Async.)"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{E436EBB5-524F-11CE-9F53-0020AF0BA770}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	ClassEnumerator for clsid({33d9a760-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x145e70)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	ClassEnumerator for clsid({33d9a761-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x145e70)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	ClassEnumerator for clsid({33d9a762-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x14b740)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x14b740, 1, 0x14b678)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"dsnoop:CA0106"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{E30629D2-27E5-11CE-875D-00608CB78066}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	ClassEnumerator for clsid({4efe2452-168a-11d1-bc76-00c04fb9453b}) pEnum(0x14b708)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x14b708, 1, 0x14b720)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"CA0106"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{07B65360-C445-11CE-AFDE-00AA006C14F4}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x14b708, 1, 0x14b738)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"Emu10k1 WaveTable"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{07B65360-C445-11CE-AFDE-00AA006C14F4}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x14b708, 1, 0x14bd48)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"Midi Through"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{07B65360-C445-11CE-AFDE-00AA006C14F4}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x14b708, 1, 0x14c1d0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"SB Live 5.1"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{07B65360-C445-11CE-AFDE-00AA006C14F4}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	ClassEnumerator for clsid({860bb310-5d01-11d0-bd3b-00a0c911ce86}) pEnum(0x14b708)
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	ClassEnumerator for clsid({cc7bfb41-f175-11d1-a392-00e0291f3959}) pEnum((nil))
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	ClassEnumerator for clsid({cc7bfb46-f175-11d1-a392-00e0291f3959}) pEnum((nil))
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	ClassEnumerator for clsid({e0f158e1-cb04-11d0-bd4e-00a0c911ce86}) pEnum(0x14b708)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x14b708, 1, 0x14c560)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"DirectSound: dmix:CA0106"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{79376820-07D0-11CF-A24D-0020AFD79767}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x14b708, 1, 0x14c900)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"dmix:CA0106"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{E30629D1-27E5-11CE-875D-00608CB78066}"
fixme:imm:ImmReleaseContext (0x20056, 0x1458e0): stub
physics@physics:/media/hdb5/Installed_games/Ground Control II$ 

```

Any ideas? im total noob with wine..

---

### Post by Plasma_NZ on 2008-07-25
Bump

---

### Post by Plasma_NZ on 2008-07-27
bump...killin for a fix !! winehq forums has yield no results

---

### Post by Plasma_NZ on 2008-07-28
Bumpppp

---

### Post by Plasma_NZ on 2008-07-30
Bump....

---

### Post by Plasma_NZ on 2008-07-31
Bump

---

### Post by Plasma_NZ on 2008-08-03
Bummmmmp....

---

### Post by Plasma_NZ on 2008-08-04
Man this is more a Bump thread than a help thread :( Find it hard to believe no one is able help, here or at winehq forums..

Totally amazing... or the guru's dont visit the help forums..

---

### Post by Ptero-4 on 2008-08-04
You might want to post your thread in 
[this](http://ubuntuforums.org/showthread.php?t=520091) one.
It's quite active.

---

### Post by Plasma_NZ on 2008-08-05
I don't think that'd be appropriate

---

### Post by Ptero-4 on 2008-08-05
> **Plasma_NZ said:**
> I don't think that'd be appropriate

Sorry couldn´t resist. With those other ppl crossposting to the BUMP thread to get their support threads seen.

---

