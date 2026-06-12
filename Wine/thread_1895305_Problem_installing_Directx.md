---
title: "Problem installing Directx"
date: 2011-12-14
forum: Wine
---

### Post by fluizp on 2011-12-14
Hello there!

I am trying to install Directx9.0c to be able to play a game using wine.

I followed this tutorial: [http://www.dedoimedo.com/games/wine-directx.html](http://www.dedoimedo.com/games/wine-directx.html).

After configuring wine, downloading the .dlls and so on, I finally installed the directx.

After this, following the tutorial, I tried to test the directx by running the following command:

wine ~/.wine/drive_c/windows/system32/dxdiag.exe

Well, according to the tutorial, a window should appear, but instead the following error appears on console:

rodrigo@Fluzao:~/Downloads/directx9.0c$ wine ~/.wine/drive_c/windows/system32/dxdiag.exe
fixme:wbemprox:wbem_locator_ConnectServer 0x12c898, L"\\\\.\\root\\cimv2", (null), (null), (null), 0x00000000, (null), (nil), 0x4c91b4)
fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias 180, std (d/m/y): 20/02/2011, dlt (d/m/y): 16/10/2011
fixme:dsound:IKsPrivatePropertySetImpl_Get unsupported property: {f2957840-260c-11d1-a4d8-00c04fc28aca}
fixme:dxdiag:wWinMain Information dialog is not implemented

Any suggestions?

---

### Post by Dlambert on 2011-12-14
Installing direct X in WINE is not advised now. May I ask what Game? Maybe try PlayOnLinux for an easier WINE experience. I myself have never got the dxdiag window to appear, so I gave up. But my games run fine!

---

### Post by bluexrider on 2011-12-14
> **Dlambert said:**
> Installing direct X in WINE is not advised now. May I ask what Game? Maybe try PlayOnLinux for an easier WINE experience. I myself have never got the dxdiag window to appear, so I gave up. But my games run fine!

WINE directX to do:
[http://wiki.winehq.org/DirectX-ToDo](http://wiki.winehq.org/DirectX-ToDo)

---

### Post by ricard9 on 2012-09-06
I have the same problem, three hours steady slogging, some promising signs with wine, but no go, game still crashes after the intro after following instructions (upto install directx 9.0 which flunks) at

[www.dedoimedo.com/games/wine-directx.html](www.dedoimedo.com/games/wine-directx.html)

The questions:
Is there a way to install direct x9 or play the Steam game Dungeon Siege (2002) on Linux?

My clapped out poc mac couldn't do it so kudos if you have a solution for this rather archaic but fun game.
-r

---

