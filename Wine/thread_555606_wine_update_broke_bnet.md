---
title: "wine update broke bnet"
date: 2007-09-20
forum: Wine
---

### Post by yowshi on 2007-09-20
the recent update to wine ver .45  which i got today has made bnet unseable for starcraft. the programme freezes up and i have to kill it using my system monitor

---

### Post by cogadh on 2007-09-20
Not sure what changed to cause that, but you can just downgrade to the previous version. Uninstall Wine then install the .deb package from here:
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)
After you install it, you will be prompted to update Wine to the latest again. To prevent that from happening, open Synaptic, search for Wine, select it and then click on the Packages menu and choose "Force version". Select the currently installed version and click Force. Then click Apply on the toolbar and Apply on the dialog. You will now not be prompted to update to whatever latest version is out, but you can still manually install the latest.

---

### Post by yowshi on 2007-09-20
personally i would rather be told how to find out what broke and how i might go about fixing it then take the easy way out. i put this post out there just to see if anyone else came up against this and if they figured out how to fix it

---

### Post by cogadh on 2007-09-20
Are there any errors produced in the terminal when you run bnet?

I only suggested the downgrade since new versions of Wine can frequently contain some significant regressions that prevent applications from working. So far this current version does seem to improve some graphics performance, but has other really significant performance problems. Games that worked almost perfectly with 0.9.44 have now stopped working for me since the upgrade and the only errors I get are page faults, which usually can't be fixed.

---

### Post by yowshi on 2007-09-20
deleted because i forgot to remove smiles

---

### Post by yowshi on 2007-09-20
i dont normally use the terminal ro run stuff in wine. but i did and it didnt look like any thing that would cause a graphical error. see before the update i could see the text on bnet but none of the actual gui. (IE i see the word join but not the join button for joining games) it was funky but useable. now i see the buttons but no text and the screen freezes. anyway because i aint versed in this stuff i posted the output from the terminal


yoshi@ubuntu:/media/cdrom0$ wine setup.exe
yoshi@ubuntu:/media/cdrom0$ fixme:bitblt:X11DRV_ClientSideDIBCopy potential optimization: client-side color-index mode DIB copy
fixme:bitblt:X11DRV_ClientSideDIBCopy potential optimization: client-side color-index mode DIB copy
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x34f458,0x00000000), stub!
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x131920) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x12fa98)->(0x10026,00000013)
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:ras:RasEnumConnectionsA (0x2110094,0x34f7cc,0x34f7e0),stub!
fixme:ras:RasEnumConnectionsA RAS support is not implemented! Configure program to use LAN connection/winsock instead!
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (9800000c)
fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x12fa98)->(1,(nil)): Stub

---

### Post by Mr. T on 2007-09-20
Heh. I guess it was sheer coincidence that when I saw this thread, I went immediately to winehq.org and saw the random screenshot at the top displaying Starcraft. :)

---

### Post by yowshi on 2007-09-20
single player works fine but Bnet doesnt any more

---

