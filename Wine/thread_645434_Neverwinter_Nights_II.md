---
title: "Neverwinter Nights II"
date: 2007-12-20
forum: Wine
---

### Post by Trampis on 2007-12-20
Having followed all the instructions from WineHQ's useful database
[[COLOR="Red"]here[/COLOR]]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=8688") 
I was still getting the error message about 3D support, so I changed wine to version 9.38 the earliest one i could find, now i have no error message but the game still does not run just flashes the screen and closes.  So I went back to the latest wine. 

I also can't update the game using the built in updater at the load menus. The error it gives is such: "a connection to the internet was not detected, or the patch server may be down" I fixed this by logging in as root and attempting to update it again and still to no avail. Any help would be appreciated I have looked all over for a fix to this a number of people have this problem.

When I play the game this is what terminal spits out

```
0x163e464)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x1357d0,L"d3d8.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szPath", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szName", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"bExists", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szVersion", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szAttributes", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szLanguageEnglish", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"dwFileTimeHigh", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"dwFileTimeLow", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"bBeta", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"bDebug", 0x163e464)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x1357d0,L"d3d9.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szPath", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szName", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"bExists", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szVersion", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szAttributes", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szLanguageEnglish", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"dwFileTimeHigh", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"dwFileTimeLow", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"bBeta", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"bDebug", 0x163e464)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x1357d0,L"dmband.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szPath", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szName", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"bExists", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szVersion", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szAttributes", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szLanguageEnglish", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"dwFileTimeHigh", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"dwFileTimeLow", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"bBeta", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"bDebug", 0x163e464)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x1357d0,L"dmcompos.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szPath", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szName", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"bExists", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szVersion", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szAttributes", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szLanguageEnglish", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"dwFileTimeHigh", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"dwFileTimeLow", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"bBeta", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"bDebug", 0x163e464)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x1357d0,L"dmime.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szPath", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szName", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"bExists", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szVersion", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szAttributes", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szLanguageEnglish", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"dwFileTimeHigh", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"dwFileTimeLow", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"bBeta", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"bDebug", 0x163e464)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x1357d0,L"dmloader.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szPath", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szName", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"bExists", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szVersion", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szAttributes", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szLanguageEnglish", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"dwFileTimeHigh", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"dwFileTimeLow", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"bBeta", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"bDebug", 0x163e464)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x1357d0,L"dmscript.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szPath", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szName", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"bExists", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szVersion", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szAttributes", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szLanguageEnglish", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"dwFileTimeHigh", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"dwFileTimeLow", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"bBeta", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"bDebug", 0x163e464)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x1357d0,L"dmstyle.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szPath", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szName", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"bExists", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szVersion", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szAttributes", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szLanguageEnglish", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"dwFileTimeHigh", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"dwFileTimeLow", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"bBeta", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"bDebug", 0x163e464)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x1357d0,L"dmsynth.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szPath", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szName", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"bExists", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szVersion", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szAttributes", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szLanguageEnglish", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"dwFileTimeHigh", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"dwFileTimeLow", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"bBeta", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"bDebug", 0x163e464)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x1357d0,L"dmusic.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szPath", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szName", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"bExists", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szVersion", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szAttributes", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szLanguageEnglish", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"dwFileTimeHigh", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"dwFileTimeLow", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"bBeta", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"bDebug", 0x163e464)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x1357d0,L"devenum.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szPath", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szName", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"bExists", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szVersion", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szAttributes", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szLanguageEnglish", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"dwFileTimeHigh", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"dwFileTimeLow", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"bBeta", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"bDebug", 0x163e464)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x1357d0,L"quartz.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szPath", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szName", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"bExists", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szVersion", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szAttributes", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"szLanguageEnglish", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"dwFileTimeHigh", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"dwFileTimeLow", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"bBeta", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1357d0, L"bDebug", 0x163e464)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x1351a8, L"DxDiag_DirectXFiles", 0x1357d0)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x3800498, L"0", 0x38004b8)
fixme:win:EnumDisplayDevicesW ((null),0,0x163e4e8,0x00000000), stub!
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38004b8, L"szDeviceName", 0x163ebe4)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38004b8, L"szDescription", 0x163ebd4)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38004b8, L"szDisplayMemoryLocalized", 0x163ec04)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38004b8, L"szDisplayMemoryEnglish", 0x163ebf4)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38004b8, L"dwWidth", 0x163ebc4)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38004b8, L"dwHeight", 0x163ebb4)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38004b8, L"dwBpp", 0x163eba4)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38004b8, L"szVendorId", 0x163eb94)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38004b8, L"szDeviceId", 0x163eb84)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38004b8, L"szKeyDeviceKey", 0x163eb74)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38004b8, L"szKeyDeviceID", 0x163eb64)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x1351a8, L"DxDiag_DisplayDevices", 0x3800498)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x34f0ed8, L"DxDiag_SoundDevices", 0x31e0e70)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x34f0ed8, L"DxDiag_SoundCaptureDevices", 0x3800eb0)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x1351a8, L"DxDiag_DirectSound", 0x34f0ed8)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x1351a8, L"DxDiag_DirectMusic", 0x3800688)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x1351a8, L"DxDiag_DirectInput", 0x38006f0)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x1351a8, L"DxDiag_DirectPlay", 0x3800758)
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80040111
err:ole:CoGetClassObject no class object {da4e3da0-d07d-11d0-bd50-00a0c911ce86} could be created for context 0x1
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({083863f1-70de-11d0-bd40-00a0c911ce86}) pEnum(0x1b7e40)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x1b7e40, 1, 0x1b7058)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"szCatName", 0x163e43c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"szClsidCat", 0x163e43c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"szName", 0x163e43c)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"AVI Splitter"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{1B544C20-FD0B-11CE-8C63-00AA0044B51E}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"szClsidFilter", 0x163e43c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"szName", 0x163e42c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"dwMerit", 0x163e42c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"dwInputs", 0x163e42c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"dwOutputs", 0x163e42c)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x1b7e40, 1, 0x1b7210)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"szCatName", 0x163e43c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"szClsidCat", 0x163e43c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"szName", 0x163e43c)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"MPEG-I Stream Splitter"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{336475D0-942A-11CE-A870-00AA002FEAB5}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"szClsidFilter", 0x163e43c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"szName", 0x163e42c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"dwMerit", 0x163e42c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"dwInputs", 0x163e42c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"dwOutputs", 0x163e42c)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x1b7e40, 1, 0x1b73c8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"szCatName", 0x163e43c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"szClsidCat", 0x163e43c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"szName", 0x163e43c)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"ACM Wrapper"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{6A08CF80-0E18-11CF-A24D-0020AFD79767}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"szClsidFilter", 0x163e43c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"szName", 0x163e42c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"dwMerit", 0x163e42c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"dwInputs", 0x163e42c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"dwOutputs", 0x163e42c)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x1b7e40, 1, 0x1b7580)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"szCatName", 0x163e43c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"szClsidCat", 0x163e43c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"szName", 0x163e43c)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Video Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{70E102B0-5556-11CE-97C0-00AA0055595A}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"szClsidFilter", 0x163e43c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"szName", 0x163e42c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"dwMerit", 0x163e42c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"dwInputs", 0x163e42c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"dwOutputs", 0x163e42c)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x1b7e40, 1, 0x1b7738)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"szCatName", 0x163e43c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"szClsidCat", 0x163e43c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"szName", 0x163e43c)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"AVI Decompressor"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{CF49D4E0-1115-11CE-B03A-0020AF0BA770}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"szClsidFilter", 0x163e43c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"szName", 0x163e42c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"dwMerit", 0x163e42c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"dwInputs", 0x163e42c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"dwOutputs", 0x163e42c)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x1b7e40, 1, 0x1b78f0)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"szCatName", 0x163e43c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"szClsidCat", 0x163e43c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"szName", 0x163e43c)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Wave Parser"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{D51BD5A1-7548-11CF-A520-0080C77EF58A}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"szClsidFilter", 0x163e43c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"szName", 0x163e42c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"dwMerit", 0x163e42c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"dwInputs", 0x163e42c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"dwOutputs", 0x163e42c)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x1b7e40, 1, 0x1b7aa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"szCatName", 0x163e43c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"szClsidCat", 0x163e43c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"szName", 0x163e43c)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Cinepak Video codec"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{D76E2820-1563-11CF-AC98-00AA004C0FA9}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"szClsidFilter", 0x163e43c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"szName", 0x163e42c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"dwMerit", 0x163e42c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"dwInputs", 0x163e42c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"dwOutputs", 0x163e42c)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x1b7e40, 1, 0x1b7c60)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"szCatName", 0x163e43c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"szClsidCat", 0x163e43c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"szName", 0x163e43c)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"File Source (Async.)"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{E436EBB5-524F-11CE-9F53-0020AF0BA770}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"szClsidFilter", 0x163e43c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"szName", 0x163e42c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"dwMerit", 0x163e42c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"dwInputs", 0x163e42c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"dwOutputs", 0x163e42c)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({33d9a760-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x1b9fc0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x1b9fc0, 1, 0x1b9b98)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"szCatName", 0x163e43c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"szClsidCat", 0x163e43c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"szName", 0x163e43c)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L""
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L""
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x38007c0, L"szClsidFilter", 0x163e43c)
fixme:dbghelp:MiniDumpWriteDump NIY MiniDumpWithDataSegs
wine: Unhandled page fault on read access to 0x00000000 at address 0x7cb76381 (thread 000d), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x7cb76381).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7cb76381 ESP:0163e3b0 EBP:0163e494 EFLAGS:00210246(   - 00      -RIZP1)
 EAX:7cb74109 EBX:7cb7c4bc ECX:00000000 EDX:038007c0
 ESI:00000000 EDI:001b9fc0
Stack dump:
0x0163e3b0:  0163e450 80000001 00000000 7bc9e749
0x0163e3c0:  001b9b98 00000000 000000a0 000000c9
0x0163e3d0:  00000011 000000ce 00000086 0163e42c
0x0163e3e0:  7cb792c4 0163e458 0163e470 7cb7923c
0x0163e3f0:  7cb79222 7cb79a00 7cb792c4 7cb79222
0x0163e400:  0163e464 7cb7923c 0163e43c 7cb79a00
Backtrace:
=>1 0x7cb76381 in dxdiagn (+0x6381) (0x0163e494)
  2 0x7cb7735c DXDiag_InitRootDXDiagContainer+0x98c() in dxdiagn (0x0163ec44)
  3 0x7cb775a1 in dxdiagn (+0x75a1) (0x0163ec74)
  4 0x006176fa in nwn2main (+0x2176fa) (0x019ce138)
  5 0x00000001 (0x00137228)
  6 0x00000001 (0x7e9073e0)
  7 0x7e8ef2b0 in d3d9 (+0xf2b0) (0x7e8f33f0)
  8 0xe5890000 (0x0010b955)
  9 0x00000000 (0x00000000)
0x7cb76381: movl        0x0(%esi),%eax
Modules:
Module  Address                 Debug info      Name (117 modules)
PE        400000- 1427000       Export          nwn2main
PE       1640000- 18a0000       Deferred        d3dx9_30
PE      10000000-1000e000       Deferred        nwn2_memorymgr
PE      21100000-21164000       Deferred        mss32
PE      22300000-22338000       Deferred        msseax.m3d
PE      22400000-22419000       Deferred        msssoft.m3d
PE      22600000-22618000       Deferred        mssdx7.m3d
PE      22700000-22776000       Deferred        mssrsx.m3d
PE      24100000-24120000       Deferred        mssdsp.flt
PE      26400000-26439000       Deferred        mssvoice.asi
PE      26f00000-26f2e000       Deferred        mssmp3.asi
PE      30000000-3006d000       Deferred        binkw32
PE      35680000-356a3000       Deferred        devenum
PE      50000000-50090000       Deferred        granny2
PE      78130000-781cb000       Deferred        msvcr80
ELF     7b800000-7b929000       Deferred        kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca0000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca0000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
PE      7c420000-7c4a7000       Deferred        msvcp80
ELF     7ca91000-7caa9000       Deferred        msdmo<elf>
  \-PE  7caa0000-7caa9000       \               msdmo
ELF     7caa9000-7cb0d000       Deferred        setupapi<elf>
  \-PE  7cac0000-7cb0d000       \               setupapi
ELF     7cb0d000-7cb62000       Deferred        ddraw<elf>
  \-PE  7cb20000-7cb62000       \               ddraw
ELF     7cb62000-7cb7d000       Export          dxdiagn<elf>
  \-PE  7cb70000-7cb7d000       \               dxdiagn
ELF     7d42c000-7d475000       Deferred        dsound<elf>
  \-PE  7d430000-7d475000       \               dsound
ELF     7d4a2000-7d4d4000       Deferred        uxtheme<elf>
  \-PE  7d4b0000-7d4d4000       \               uxtheme
ELF     7d4f4000-7d51a000       Deferred        msacm32<elf>
  \-PE  7d500000-7d51a000       \               msacm32
ELF     7d51a000-7d556000       Deferred        wineoss<elf>
  \-PE  7d520000-7d556000       \               wineoss
ELF     7d79e000-7d7b3000       Deferred        midimap<elf>
  \-PE  7d7a0000-7d7b3000       \               midimap
ELF     7d7b3000-7d7cb000       Deferred        msacm32<elf>
  \-PE  7d7c0000-7d7cb000       \               msacm32
ELF     7d7cb000-7d7d0000       Deferred        libxfixes.so.3
ELF     7d7d0000-7d7d9000       Deferred        libxcursor.so.1
ELF     7d7d9000-7d7df000       Deferred        libxrandr.so.2
ELF     7d7df000-7d7e7000       Deferred        libxrender.so.1
ELF     7d7e7000-7d7f3000       Deferred        libgcc_s.so.1
ELF     7d813000-7e1ab000       Deferred        libglcore.so.1
ELF     7e1ab000-7e241000       Deferred        libgl.so.1
ELF     7e241000-7e246000       Deferred        libxdmcp.so.6
ELF     7e246000-7e249000       Deferred        libxau.so.6
ELF     7e249000-7e33a000       Deferred        libx11.so.6
ELF     7e33a000-7e348000       Deferred        libxext.so.6
ELF     7e348000-7e360000       Deferred        libice.so.6
ELF     7e360000-7e369000       Deferred        libsm.so.6
ELF     7e377000-7e402000       Deferred        winex11<elf>
  \-PE  7e390000-7e402000       \               winex11
ELF     7e484000-7e4a4000       Deferred        libexpat.so.1
ELF     7e4a4000-7e4cf000       Deferred        libfontconfig.so.1
ELF     7e4cf000-7e4e3000       Deferred        libz.so.1
ELF     7e4e3000-7e54e000       Deferred        libfreetype.so.6
ELF     7e54e000-7e5ec000       Deferred        oleaut32<elf>
  \-PE  7e560000-7e5ec000       \               oleaut32
ELF     7e5ec000-7e6aa000       Deferred        comctl32<elf>
  \-PE  7e600000-7e6aa000       \               comctl32
ELF     7e6aa000-7e7ad000       Deferred        shell32<elf>
  \-PE  7e6c0000-7e7ad000       \               shell32
ELF     7e7ad000-7e7ca000       Deferred        imm32<elf>
  \-PE  7e7b0000-7e7ca000       \               imm32
ELF     7e7ca000-7e7de000       Deferred        lz32<elf>
  \-PE  7e7d0000-7e7de000       \               lz32
ELF     7e7de000-7e7f8000       Deferred        version<elf>
  \-PE  7e7e0000-7e7f8000       \               version
ELF     7e7f8000-7e8d9000       Deferred        wined3d<elf>
  \-PE  7e810000-7e8d9000       \               wined3d
ELF     7e8d9000-7e908000       Export          d3d9<elf>
  \-PE  7e8e0000-7e908000       \               d3d9
ELF     7e908000-7e93e000       Deferred        dinput<elf>
  \-PE  7e910000-7e93e000       \               dinput
ELF     7e93e000-7e957000       Deferred        dinput8<elf>
  \-PE  7e940000-7e957000       \               dinput8
ELF     7e957000-7e984000       Deferred        ws2_32<elf>
  \-PE  7e960000-7e984000       \               ws2_32
ELF     7e984000-7e9dd000       Deferred        shlwapi<elf>
  \-PE  7e990000-7e9dd000       \               shlwapi
ELF     7e9dd000-7ea45000       Deferred        msvcrt<elf>
  \-PE  7e9f0000-7ea45000       \               msvcrt
ELF     7ea45000-7ea58000       Deferred        libresolv.so.2
ELF     7ea66000-7ea84000       Deferred        iphlpapi<elf>
  \-PE  7ea70000-7ea84000       \               iphlpapi
ELF     7ea84000-7eadd000       Deferred        rpcrt4<elf>
  \-PE  7ea90000-7eadd000       \               rpcrt4
ELF     7eadd000-7eb7e000       Deferred        ole32<elf>
  \-PE  7eaf0000-7eb7e000       \               ole32
ELF     7eb7e000-7eb93000       Deferred        psapi<elf>
  \-PE  7eb80000-7eb93000       \               psapi
ELF     7eb93000-7ebdd000       Deferred        dbghelp<elf>
  \-PE  7eba0000-7ebdd000       \               dbghelp
ELF     7ebdd000-7ec26000       Deferred        advapi32<elf>
  \-PE  7ebf0000-7ec26000       \               advapi32
ELF     7ec26000-7ecc1000       Deferred        gdi32<elf>
  \-PE  7ec40000-7ecc1000       \               gdi32
ELF     7ecc1000-7edff000       Deferred        user32<elf>
  \-PE  7ece0000-7edff000       \               user32
ELF     7edff000-7ee8d000       Deferred        winmm<elf>
  \-PE  7ee10000-7ee8d000       \               winmm
ELF     7ef9f000-7efaa000       Deferred        libnss_files.so.2
ELF     7efaa000-7efb4000       Deferred        libnss_nis.so.2
ELF     7efb4000-7efcb000       Deferred        libnsl.so.1
ELF     7efcb000-7eff2000       Deferred        libm.so.6
ELF     7eff2000-7eff7000       Deferred        libxxf86vm.so.1
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7ca0000-b7ca2000       Deferred        libnvidia-tls.so.1
ELF     b7ca6000-b7caa000       Deferred        libdl.so.2
ELF     b7caa000-b7deb000       Deferred        libc.so.6
ELF     b7dec000-b7e03000       Deferred        libpthread.so.0
ELF     b7e11000-b7f25000       Deferred        libwine.so.1
ELF     b7f27000-b7f42000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000e 
        00000010    0
        0000000f    0
0000000c (D) Z:\home\john\Desktop\nwn2\nwn2main.exe
        00000014   15
        00000013   15
        00000012   15
        0000000d    0 <==
fixme:dbghelp:MiniDumpWriteDump NIY MiniDumpWithDataSegs
fixme:winmm:MMDRV_Exit Closing while ll-driver open

```

Is there a Linux client for NWN2 like there was for NWN? 

I also bought F.E.A.R today but my research has shown me that that is not going to work, while i hear stories about NWN2 running fine.

I am assuming my problem lies in not being able to update the game, as i did everything else fine how do i manually install patches I got them from [[COLOR="Blue"]here[/COLOR]]("http://nwvault.ign.com/View.php?view=NWN2Articles.Detail&id=230") and extracted them and put them in my NWN directory to no avail how do i manually patch the game? Is it a problem that i put the NWN2 directory on my desktop and not in the virtual "program files" folder wine wanted to put it in?

---

### Post by cogadh on 2007-12-20
First of all, [NEVER RUN WINE AS ROOT OR WITH SUDO!!](http://wiki.winehq.org/FAQ#head-96bebfa287b4288974de0df23351f278b0d41014)

Secondly, it would have been nice to have that additional info about how you installed the game in the second thread you made on this. Yes, installing outside of Wine's "fake Windows" directory will sometimes cause problems. It is usually best to just install games in the default directory. As for patching, instead of using the incremental zip patches, get the executable patch from Atari's website and run it in Wine. Here is the question I posted in your other thread:

What video card/chipset do you have and have you installed the 3D accelerated drivers for it?

---

### Post by Trampis on 2007-12-20
sorry about the 2 threads i did not realize i was making 2, i kept researching and working with the problem while i was creating the threat so i might have clicked post too soon.

anyway I have Nvidia Geforce 8800 ultra and i have the drivers for it, it does not specify whether they are 3D accelerated or not but they are the latest ones.  How I installed the game is [[COLOR="Magenta"]linked[/COLOR]]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=8688") in the first post and detailed here

[quote=winehq]

1. Move or delete any existing ~/.wine directory.

2. Run winecfg and make the following settings:

* Applications tab: Change the Windows version to Windows XP

* Libraries tab: Add overrides for devenum.dll and dxdiagn.dll

* Graphics tab: Flag "Emulate a virtual desktop" and set Desktop
size to 1024 x 768

* Audio tab: Click OK on the message that pops up, then click
the Apply button

* Click the OK button to exit winecfg

3. Run regedit and add the following key and string values:

[HKEY_CURRENT_USER\Software\Wine\Direct3D]
OffscreenRenderingMode = fbo
UseGLSL = enabled
VideoMemorySize = 256

4. Copy devenum.dll and dxdiagn.dll to ~/.wine/drive_c/windows/system32/

5. Copy the contents of your NWN2 DVD to a directory on the hard drive.

6. Install NWN2 by going into that directory and running: wine setup.exe

NOTES ON THIS STEP:

* If you are having trouble entering your CD key, click in the box that says "Please enter your CD key below", then click in the first key entry box and start typing.

* Installing .NET will fail. That's OK.

* You may get errors about DirectX not being installed correctly. That's OK, too.

* I didn't try installing Xfire. Probably won't work.

7. Copy d3dx9_30.dll, devenum.dll, and dxdiagn.dll to your newly installed NWN2 directory, usually:

~/.wine/drive_c/Program Files/Atari/Neverwinter Nights 2/

8. Copy the contents of microsoft.vc80.crt.zip (Microsoft.VC80.CRT.manifest, msvcm80.dll, msvcp80.dll, and msvcr80.dll) to your NWN2 directory.

9. Copy all the necessary game patch files (nwn2_pc_english_*.zip) to the same NWN2 directory.

10. From within the NWN2 directory, run: wine NWN2Launcher.exe

11. Click the Update button do an update. After one update, you will have to exit back to the main NWN2 menu and click the Update button again. Keep doing this until there are no more updates found.

12. Exit from NWN2Launcher.exe

13. Still in the NWN2 directory, rename nwn2main.exe to nwn2main.exe.bak, and nwn2main_amdxp.exe to nwn2main_amdxp.exe.bak

14. Unzip the NOCD patched nwn2main.exe and nwn2main_amdxp.exe to your NWN2 directory.

15. Launch the game with the command: wine nwn2main.exe

16. If all goes well... enjoy! [/quote]

With the one step that i did not do is the updating as I could not get it to work. Still don't know how to manually update the game. All I managed to do was download the updates and put them in the nwn2 directory. I reinstalled the game into the fake windows folder and the same problem "could not find any compatible direct 3d devices"

I will look on the nvidia website for a newer driver that is marked 3D but other than that I have no ideas.

-Edit-
I found [this]("http://www.nvnews.net/vbulletin/showpost.php?p=872079&postcount=7") while looking up the problem i am not sure if it is useful or even how to implement it

I downloaded the exe updater and it updated the game, but the problem still persists.

---

### Post by cogadh on 2007-12-20
If you installed the Nvidia drivers using the Restricted Drivers Manager, then they are 3D accelerated. If you are using the default "nv" driver that Ubuntu comes with, it is not 3D accelerated (well, not fully, it does have limited acceleration abilities).

---

### Post by Trampis on 2007-12-20
You may have found the problem, when going into the restricted drivers manager i am simply told that "your hardware does not need any restricted drivers" I used envy to install the nvidia drivers, is there something wrong with my restricted drivers? When i go inot xorg.conf i see that under devices the driver is listed as nvidia not nv

---

### Post by Trampis on 2007-12-21
a bump to ask the question why does it say " your hardware does not need any restricted drivers"

---

### Post by cogadh on 2007-12-21
If you already installed the drivers with Envy, then you already have the accelerated drivers, just not the pre-packaged one that is available through the Restricted Drivers Manager. That's probably why it says you don't need any restricted driver.

---

### Post by Trampis on 2007-12-22
oh ok, so its not that then any other ideas why wine would have this error?

---

### Post by Trampis on 2007-12-29
i have been fiddling with this over at the wine boards to no avail, maby one of you can shed some light on the problem. When I try to run nwn2 the screen pops up black then closes the error is as such:

```
 00000008 (D) C:\Program Files\Atari\Neverwinter Nights 2\nwn2main.exe
        00000010   15
        0000000f   15
        0000000e   15
        00000009    0 <==
Backtrace:
=>1 0x7cbae371 in dxdiagn (+0xe371) (0x0170e494)
  2 0x7cbaf34c DXDiag_InitRootDXDiagContainer+0x98c() in dxdiagn (0x0170ec44)
  3 0x7cbaf591 in dxdiagn (+0xf591) (0x0170ec74)
  4 0x006176fa in nwn2main (+0x2176fa) (0x01cbe350)
  5 0x00000001 (0x00154700)
  6 0x00000001 (0x7ebdd3e0)
  7 0x7ebc52b0 in d3d9 (+0x52b0) (0x7ebc93f0)
  8 0xe5890000 (0x0010b955)
  9 0x00000000 (0x00000000)
fixme:dbghelp:MiniDumpWriteDump NIY MiniDumpWithDataSegs
fixme:winmm:MMDRV_Exit Closing while ll-driver open

```

what does this mean i should do?

---

