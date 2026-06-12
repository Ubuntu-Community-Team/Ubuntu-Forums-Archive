---
title: "Halo + Wine"
date: 2007-10-17
forum: Wine
---

### Post by Misbah on 2007-10-17
Ok so I play lots of FPS games, but I still love Halo Combat Evolved and I kick *** at it so now that I have switched fully to ubuntu it would be nice to have support. I downloaded wine 9.47, installed the game as per the directions, got it updated, installed the no CD patch, set a few settings in winecfg, and added the -vidmode 1280,1024,60 -novideo tags to the launcher. Now when I launch it through the desktop launcher, it loads up the initial splash screen, I get no sound, and my RAM usage goes to 100% and I have 1GB and it just freezes. Have to force quit or log in/log out to get out of it. When I launch through terminal, and a halo pop up error comes saying it "Cannot find H:\\config.txt"

I've searched through the forums and found lots of halo+wine threads, but none that relate to my problem, and I've searched wineHQ as well.

Any help?

This is on Feisty 64 bit. I have a 7800GT. 100.14.19 nvidia drivers.

---

### Post by Misbah on 2007-10-17
Thought I would add in terminal output. A bunch of "fixme's". I would gladly fix you. But I do not know how oh fickle ubuntu64.

```
misbah@misbah-ubuntu:~$ wine "C:\Program Files\Microsoft Games\Halo\halo.exe" -vidmode 1280,1024,60 -novideo
fixme:win:EnumDisplayDevicesW ((null),0,0x33d4e0,0x00000000), stub!
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1399a0, L"dwDirectXVersionMajor", 0x33d940)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1399a0, L"dwDirectXVersionMinor", 0x33d940)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1399a0, L"szDirectXVersionLetter", 0x33d940)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1399a0, L"szDirectXVersionEnglish", 0x33d940)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1399a0, L"szDirectXVersionLongEnglish", 0x33d940)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1399a0, L"bDebug", 0x33d940)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x139980, L"DxDiag_SystemInfo", 0x1399a0)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x139980, L"DxDiag_SystemDevices", 0x13a9c8)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x139980, L"DxDiag_LogicalDisks", 0x13aa38)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x13aaa0,L"ddraw.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szPath", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szName", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"bExists", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szVersion", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szAttributes", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szLanguageEnglish", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"dwFileTimeHigh", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"dwFileTimeLow", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"bBeta", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"bDebug", 0x33d190)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x13aaa0,L"dplayx.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szPath", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szName", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"bExists", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szVersion", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szAttributes", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szLanguageEnglish", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"dwFileTimeHigh", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"dwFileTimeLow", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"bBeta", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"bDebug", 0x33d190)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x13aaa0,L"dpnet.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szPath", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szName", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"bExists", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szVersion", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szAttributes", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szLanguageEnglish", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"dwFileTimeHigh", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"dwFileTimeLow", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"bBeta", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"bDebug", 0x33d190)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x13aaa0,L"dinput.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szPath", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szName", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"bExists", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szVersion", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szAttributes", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szLanguageEnglish", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"dwFileTimeHigh", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"dwFileTimeLow", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"bBeta", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"bDebug", 0x33d190)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x13aaa0,L"dinput8.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szPath", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szName", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"bExists", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szVersion", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szAttributes", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szLanguageEnglish", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"dwFileTimeHigh", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"dwFileTimeLow", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"bBeta", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"bDebug", 0x33d190)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x13aaa0,L"dsound.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szPath", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szName", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"bExists", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szVersion", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szAttributes", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szLanguageEnglish", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"dwFileTimeHigh", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"dwFileTimeLow", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"bBeta", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"bDebug", 0x33d190)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x13aaa0,L"dswave.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szPath", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szName", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"bExists", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szVersion", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szAttributes", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szLanguageEnglish", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"dwFileTimeHigh", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"dwFileTimeLow", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"bBeta", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"bDebug", 0x33d190)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x13aaa0,L"d3d8.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szPath", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szName", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"bExists", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szVersion", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szAttributes", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szLanguageEnglish", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"dwFileTimeHigh", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"dwFileTimeLow", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"bBeta", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"bDebug", 0x33d190)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x13aaa0,L"d3d9.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szPath", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szName", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"bExists", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szVersion", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szAttributes", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szLanguageEnglish", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"dwFileTimeHigh", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"dwFileTimeLow", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"bBeta", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"bDebug", 0x33d190)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x13aaa0,L"dmband.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szPath", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szName", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"bExists", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szVersion", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szAttributes", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szLanguageEnglish", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"dwFileTimeHigh", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"dwFileTimeLow", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"bBeta", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"bDebug", 0x33d190)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x13aaa0,L"dmcompos.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szPath", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szName", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"bExists", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szVersion", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szAttributes", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szLanguageEnglish", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"dwFileTimeHigh", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"dwFileTimeLow", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"bBeta", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"bDebug", 0x33d190)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x13aaa0,L"dmime.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szPath", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szName", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"bExists", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szVersion", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szAttributes", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szLanguageEnglish", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"dwFileTimeHigh", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"dwFileTimeLow", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"bBeta", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"bDebug", 0x33d190)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x13aaa0,L"dmloader.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szPath", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szName", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"bExists", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szVersion", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szAttributes", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szLanguageEnglish", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"dwFileTimeHigh", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"dwFileTimeLow", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"bBeta", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"bDebug", 0x33d190)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x13aaa0,L"dmscript.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szPath", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szName", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"bExists", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szVersion", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szAttributes", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szLanguageEnglish", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"dwFileTimeHigh", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"dwFileTimeLow", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"bBeta", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"bDebug", 0x33d190)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x13aaa0,L"dmstyle.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szPath", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szName", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"bExists", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szVersion", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szAttributes", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szLanguageEnglish", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"dwFileTimeHigh", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"dwFileTimeLow", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"bBeta", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"bDebug", 0x33d190)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x13aaa0,L"dmsynth.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szPath", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szName", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"bExists", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szVersion", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szAttributes", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szLanguageEnglish", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"dwFileTimeHigh", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"dwFileTimeLow", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"bBeta", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"bDebug", 0x33d190)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x13aaa0,L"dmusic.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szPath", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szName", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"bExists", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szVersion", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szAttributes", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szLanguageEnglish", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"dwFileTimeHigh", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"dwFileTimeLow", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"bBeta", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"bDebug", 0x33d190)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x13aaa0,L"devenum.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szPath", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szName", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"bExists", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szVersion", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szAttributes", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szLanguageEnglish", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"dwFileTimeHigh", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"dwFileTimeLow", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"bBeta", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"bDebug", 0x33d190)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x13aaa0,L"quartz.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szPath", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szName", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"bExists", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szVersion", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szAttributes", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"szLanguageEnglish", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"dwFileTimeHigh", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"dwFileTimeLow", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"bBeta", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aaa0, L"bDebug", 0x33d190)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x139980, L"DxDiag_DirectXFiles", 0x13aaa0)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x13fe90, L"0", 0x13feb0)
fixme:win:EnumDisplayDevicesW ((null),0,0x33d214,0x00000000), stub!
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13feb0, L"szDeviceName", 0x33d910)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13feb0, L"szDescription", 0x33d900)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13feb0, L"szDisplayMemoryLocalized", 0x33d930)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13feb0, L"szDisplayMemoryEnglish", 0x33d920)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13feb0, L"dwWidth", 0x33d8f0)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13feb0, L"dwHeight", 0x33d8e0)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13feb0, L"dwBpp", 0x33d8d0)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13feb0, L"szVendorId", 0x33d8c0)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13feb0, L"szDeviceId", 0x33d8b0)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13feb0, L"szKeyDeviceKey", 0x33d8a0)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13feb0, L"szKeyDeviceID", 0x33d890)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x139980, L"DxDiag_DisplayDevices", 0x13fe90)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x1405f0, L"DxDiag_SoundDevices", 0x140610)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x1405f0, L"DxDiag_SoundCaptureDevices", 0x140660)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x139980, L"DxDiag_DirectSound", 0x1405f0)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x139980, L"DxDiag_DirectMusic", 0x140720)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x139980, L"DxDiag_DirectInput", 0x140788)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x139980, L"DxDiag_DirectPlay", 0x1407f0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({083863f1-70de-11d0-bd40-00a0c911ce86}) pEnum(0x140b80)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x140b80, 1, 0x140b98)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szCatName", 0x33d168)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szClsidCat", 0x33d168)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szName", 0x33d168)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"AVI Splitter"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{1B544C20-FD0B-11CE-8C63-00AA0044B51E}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szClsidFilter", 0x33d168)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szName", 0x33d158)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"dwMerit", 0x33d158)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"dwInputs", 0x33d158)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"dwOutputs", 0x33d158)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x140b80, 1, 0x140bb0)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szCatName", 0x33d168)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szClsidCat", 0x33d168)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szName", 0x33d168)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"MPEG-I Stream Splitter"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{336475D0-942A-11CE-A870-00AA002FEAB5}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szClsidFilter", 0x33d168)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szName", 0x33d158)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"dwMerit", 0x33d158)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"dwInputs", 0x33d158)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"dwOutputs", 0x33d158)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x140b80, 1, 0x141028)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szCatName", 0x33d168)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szClsidCat", 0x33d168)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szName", 0x33d168)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"ACM Wrapper"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{6A08CF80-0E18-11CF-A24D-0020AFD79767}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szClsidFilter", 0x33d168)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szName", 0x33d158)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"dwMerit", 0x33d158)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"dwInputs", 0x33d158)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"dwOutputs", 0x33d158)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x140b80, 1, 0x141418)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szCatName", 0x33d168)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szClsidCat", 0x33d168)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szName", 0x33d168)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Video Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{70E102B0-5556-11CE-97C0-00AA0055595A}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szClsidFilter", 0x33d168)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szName", 0x33d158)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"dwMerit", 0x33d158)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"dwInputs", 0x33d158)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"dwOutputs", 0x33d158)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x140b80, 1, 0x141a00)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szCatName", 0x33d168)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szClsidCat", 0x33d168)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szName", 0x33d168)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"AVI Decompressor"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{CF49D4E0-1115-11CE-B03A-0020AF0BA770}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szClsidFilter", 0x33d168)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szName", 0x33d158)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"dwMerit", 0x33d158)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"dwInputs", 0x33d158)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"dwOutputs", 0x33d158)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x140b80, 1, 0x141e28)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szCatName", 0x33d168)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szClsidCat", 0x33d168)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szName", 0x33d168)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Wave Parser"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{D51BD5A1-7548-11CF-A520-0080C77EF58A}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szClsidFilter", 0x33d168)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szName", 0x33d158)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"dwMerit", 0x33d158)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"dwInputs", 0x33d158)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"dwOutputs", 0x33d158)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x140b80, 1, 0x142280)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szCatName", 0x33d168)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szClsidCat", 0x33d168)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szName", 0x33d168)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"File Source (Async.)"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{E436EBB5-524F-11CE-9F53-0020AF0BA770}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szClsidFilter", 0x33d168)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szName", 0x33d158)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"dwMerit", 0x33d158)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"dwInputs", 0x33d158)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"dwOutputs", 0x33d158)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({33d9a760-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x140940)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({33d9a761-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x140940)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({33d9a762-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x140948)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x140948, 1, 0x140960)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szCatName", 0x33d168)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szClsidCat", 0x33d168)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szName", 0x33d168)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"ADC Capture/Standard PCM Playba"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{E30629D2-27E5-11CE-875D-00608CB78066}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szClsidFilter", 0x33d168)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szName", 0x33d158)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"dwMerit", 0x33d158)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"dwInputs", 0x33d158)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"dwOutputs", 0x33d158)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({4efe2452-168a-11d1-bc76-00c04fb9453b}) pEnum(0x140910)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x140910, 1, 0x140928)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szCatName", 0x33d168)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szClsidCat", 0x33d168)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szName", 0x33d168)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Audigy 2 ZS [SB0350]"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{07B65360-C445-11CE-AFDE-00AA006C14F4}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szClsidFilter", 0x33d168)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szName", 0x33d158)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"dwMerit", 0x33d158)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"dwInputs", 0x33d158)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"dwOutputs", 0x33d158)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x140910, 1, 0x140940)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szCatName", 0x33d168)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szClsidCat", 0x33d168)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szName", 0x33d168)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Emu10k1 Port 3"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{07B65360-C445-11CE-AFDE-00AA006C14F4}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szClsidFilter", 0x33d168)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szName", 0x33d158)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"dwMerit", 0x33d158)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"dwInputs", 0x33d158)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"dwOutputs", 0x33d158)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x140910, 1, 0x143418)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szCatName", 0x33d168)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szClsidCat", 0x33d168)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szName", 0x33d168)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Emu10k1 WaveTable"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{07B65360-C445-11CE-AFDE-00AA006C14F4}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szClsidFilter", 0x33d168)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szName", 0x33d158)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"dwMerit", 0x33d158)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"dwInputs", 0x33d158)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"dwOutputs", 0x33d158)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x140910, 1, 0x143850)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szCatName", 0x33d168)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szClsidCat", 0x33d168)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szName", 0x33d168)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Midi Through"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{07B65360-C445-11CE-AFDE-00AA006C14F4}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szClsidFilter", 0x33d168)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szName", 0x33d158)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"dwMerit", 0x33d158)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"dwInputs", 0x33d158)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"dwOutputs", 0x33d158)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({860bb310-5d01-11d0-bd3b-00a0c911ce86}) pEnum(0x143c88)
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({cc7bfb41-f175-11d1-a392-00e0291f3959}) pEnum((nil))
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({cc7bfb46-f175-11d1-a392-00e0291f3959}) pEnum((nil))
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({e0f158e1-cb04-11d0-bd4e-00a0c911ce86}) pEnum(0x143c88)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x143c88, 1, 0x1440b8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szCatName", 0x33d168)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szClsidCat", 0x33d168)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szName", 0x33d168)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"ADC Capture/Standard PCM Playba"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{E30629D1-27E5-11CE-875D-00608CB78066}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szClsidFilter", 0x33d168)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szName", 0x33d158)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"dwMerit", 0x33d158)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"dwInputs", 0x33d158)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"dwOutputs", 0x33d158)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x143c88, 1, 0x1440d0)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szCatName", 0x33d168)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szClsidCat", 0x33d168)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szName", 0x33d168)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"DirectSound: ADC Capture/Standard PCM Playba"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{79376820-07D0-11CF-A24D-0020AFD79767}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szClsidFilter", 0x33d168)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"szName", 0x33d158)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"dwMerit", 0x33d158)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"dwInputs", 0x33d158)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x140858, L"dwOutputs", 0x33d158)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x139980, L"DxDiag_DirectShowFilters", 0x140858)
fixme:dxdiag:IDxDiagContainerImpl_GetChildContainer (0x139980, L"DxDiag_DirectSound.DxDiag_SoundDevices", 0x33d9cc)
misbah@misbah-ubuntu:~$ 

```

---

### Post by Misbah on 2007-10-17
So i changed the setting to virtual desktop , set it to 800x600, matched the resolution to 800x600 and 60hz in the launcher window. and i got it to start! Wahoo! buuut. I get sound. My mouse works. but NO keyboard inputs. none. Didn't try playing the actual game.. just.. screwing around in the m enu, trying to create a profile.

---

### Post by Tom Mann on 2007-10-17
I find cd'ing to the directory the windows executable is located always helps. Have you tried it? It worked for my Drumkit from Hell installation the other day :)

---

### Post by Misbah on 2007-10-17
So I have halo working fully on Ubuntu 64 and wine 9.47 after much effort. It's running at 1280x1024 in a virtual desktop with all the eye candy turned on, using ALSA drivers with the highest sound options, no visual glitches. single player works great. when i try to connect to multi it says the usual checking for updates but never gets past that. Any help?

I post here because I have a feeling this is a halo/wine issue, not a firewall/internet issue. I've port forwarded 2301 and 2302 anyways or whatever the halo client/server ports are.

---

### Post by santiagoward2000 on 2007-10-17
We should ask Microsoft to make a Linux native Halo version! #-o

---

### Post by gwoodard on 2007-11-12
To that I bid you good luck (Microsoft cooperating with Linux users may never happen)

---

### Post by Bigbob22 on 2009-09-19
Misbah, I have ran into the same problem you have ( with the cannot find config.txt) how did you get it to work??

---

### Post by dmizer on 2009-09-20
> **Bigbob22 said:**
> Misbah, I have ran into the same problem you have ( with the cannot find config.txt) how did you get it to work??

Try posting a new thread. This one is over two years old, so the information here is hopelessly outdated.

---

