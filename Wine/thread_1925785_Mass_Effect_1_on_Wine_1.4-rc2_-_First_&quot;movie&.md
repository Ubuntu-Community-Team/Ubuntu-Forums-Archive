---
title: "Mass Effect 1 on Wine 1.4-rc2 - First &quot;movie&quot; freezes"
date: 2012-02-15
forum: Wine
---

### Post by Nathan_U on 2012-02-15
Hey there,

So I've managed to install Mass Effect 1 on Wine 1.4-rc2. Everything starts, the menu and menu's animation works perfectly, but when starting the game, when the first "movie" starts, the one with big planet and Normandy flying (according to YouTube videos :P), everything freezes. The music goes on, but nothing else happens.

The console shows the following:

```
fixme:ole:CoInitializeSecurity (0x142828,-1,(nil),(nil),4,3,(nil),0,(nil)) - stub!
fixme:advapi:RegisterEventSourceA ((null),"RichVideo"): stub
fixme:advapi:RegisterEventSourceW (L"",L"RichVideo"): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0004,0x0000,0x00000000,(nil),0x0001,0x00000000,0x63e88c,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x00000000,(nil),0x0001,0x00000000,0x145270,(nil)): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:gameux:GameExplorerImpl_VerifyAccess (0x135a68, L"C:\\Program Files\\Mass Effect\\Binaries\\MassEffectGDF.dll", 0x92ed64)
fixme:gameux:GameExplorerImpl_VerifyAccess (0x16ea18, L"C:\\Program Files\\Mass Effect\\Binaries\\MassEffect.exe", 0x92eab8)
fixme:win:EnumDisplayDevicesW ((null),0,0x92f50c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 53 (SPI_SETTOGGLEKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 51 (SPI_SETFILTERKEYS)
fixme:d3d:debug_d3dformat Unrecognized 0x34324644 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x34324644) in the format lookup table
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d:state_zfunc D3DCMP_NOTEQUAL and D3DCMP_EQUAL do not work correctly yet.
```

Any suggestions where should I move from here?

---

### Post by ravensqu on 2012-02-23
I can confirm the same problem here. Did you notice any problems with the opening cinematics (when BioWare is shown and such)? I have also noticed sound problems during these cinematics. This makes we wonder if it is a driver issue. What graphics card/drivers are you using?

Edit:

Also from reading the error message, it kindof looks like d3dx is the problem. I dont know too much about wine or linux yet, but maybe this can help us find a solution.

---

### Post by Jezzze on 2012-02-24
I have the exact same problem, here they are speaking about a solution, disable the motion blur. Going to try it right now.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=19578&iTestingId=52071](http://appdb.winehq.org/objectManager.php?sClass=version&iId=19578&iTestingId=52071)

EDIT: *sigh* never mind, did not work.

---

### Post by Nathan_U on 2012-02-29
> **ravensqu said:**
> Did you notice any problems with the opening cinematics (when BioWare is shown and such)?

Nope, opening cinematics work just fine.

---

### Post by Jezzze on 2012-03-02
It seemed to work with older version of Ubuntu, but wit the newer, it seems people have more problems running the game.

---

