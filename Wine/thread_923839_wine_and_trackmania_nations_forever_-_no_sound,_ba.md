---
title: "wine and trackmania nations forever - no sound, bad graphics"
date: 2008-09-18
forum: Wine
---

### Post by themusicalduck on 2008-09-18
**Edit:** Since writing this post I've somehow managed to work out everything I needed, after spending hours trying to get it to work. Seem to do that occasionally. :)

I'm trying to run Trackmania Nations on wine with Ubuntu 8.04.

I can install the game fine, at first it wouldn't work at all through a Steam installation, but after doing a standalone installation, I could at least get as far as the menus. If i try to load a track on single player mode, it will get stuck at about 80% loaded. The graphics also seem to be choppy and the system generally gets pretty laggy.

Also there is no sound at all, just a loud crackling noise.

I have tried searching around for solutions to this, but none of them seem to be useful so far.. Most places say I need to install directx, but while doing this I get an error. This is from the DXError.log file in the Windows folder:

--------------------

[09/19/08 00:40:08] module: dsetup32(May 31 2006), file: instcat.cpp, line: 42, function: LoadSfcDLL



    Failed API:		GetProcAddress()

    Error:		(127) - Procedure not found





    Module: sfc.dll



--------------------

[09/19/08 00:40:14] module: dxupdate(May 31 2006), file: dxupdate.cpp, line: 6438, function: CMDXCheck::IsAssemblyInUse



    GetAssemblyList() failed, error = 0x80004001.



--------------------

[09/19/08 00:40:14] module: dxupdate(May 31 2006), file: dxupdate.cpp, line: 6438, function: CMDXCheck::IsAssemblyInUse



    GetAssemblyList() failed, error = 0x80004001.



--------------------

[09/19/08 00:40:14] module: dxupdate(May 31 2006), file: dxupdate.cpp, line: 6438, function: CMDXCheck::IsAssemblyInUse



    GetAssemblyList() failed, error = 0x80004001.



--------------------

[09/19/08 00:40:14] module: dxupdate(May 31 2006), file: dxupdate.cpp, line: 6438, function: CMDXCheck::IsAssemblyInUse



    GetAssemblyList() failed, error = 0x80004001.



--------------------

[09/19/08 00:40:14] module: dxupdate(May 31 2006), file: dxupdate.cpp, line: 6438, function: CMDXCheck::IsAssemblyInUse



    GetAssemblyList() failed, error = 0x80004001.



--------------------

[09/19/08 00:40:14] module: dxupdate(May 31 2006), file: dxupdate.cpp, line: 6438, function: CMDXCheck::IsAssemblyInUse



    GetAssemblyList() failed, error = 0x80004001.



--------------------

[09/19/08 00:40:14] module: dxupdate(May 31 2006), file: dxupdate.cpp, line: 6438, function: CMDXCheck::IsAssemblyInUse



    GetAssemblyList() failed, error = 0x80004001.



--------------------

[09/19/08 00:40:14] module: dxupdate(May 31 2006), file: dxupdate.cpp, line: 6438, function: CMDXCheck::IsAssemblyInUse



    GetAssemblyList() failed, error = 0x80004001.



--------------------

[09/19/08 00:40:14] module: dxupdate(May 31 2006), file: dxupdate.cpp, line: 6438, function: CMDXCheck::IsAssemblyInUse



    GetAssemblyList() failed, error = 0x80004001.



--------------------

[09/19/08 00:40:14] module: dsetup32(May 31 2006), file: dxupdate.cpp, line: 280, function: CSetup::InstallPlugIn



    DirectXUpdateInstallPlugIn() failed.


I've been using this guide: [http://www.wine-reviews.net/microsoft/directx-90c-march-2008-redistributable-on-linux-with-wine.html](http://www.wine-reviews.net/microsoft/directx-90c-march-2008-redistributable-on-linux-with-wine.html)



I also read somewhere that I need to change something like PC1 to PC0, but unfortunately I don't know what this means or where I can do it..

And apparently there is a registry tweak that I can do in HKEY_CURRENT_USER > Software > Wine > Direct3D, but there isn't a Direct3D folder there.. Only OpenGL.

---

### Post by ooobuntooo on 2008-09-19
Replace the OpenAL32.dll in the game folder *with [http://schmatzler.de/openal32.dll](http://schmatzler.de/openal32.dll)

---

