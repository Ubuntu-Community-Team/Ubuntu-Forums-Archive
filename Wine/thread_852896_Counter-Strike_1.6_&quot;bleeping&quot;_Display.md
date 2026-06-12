---
title: "Counter-Strike 1.6 &quot;bleeping&quot; Display"
date: 2008-07-08
forum: Wine
---

### Post by encikraju on 2008-07-08
I got a bleeping display with my CS 1.6. Does anyone know how to solve this.
Terminal output:

> x0x@kdjfs:~$ env WINEPREFIX="/home/x0x/.wine" wine "C:\Program Files\Valve\hl.exe" -nomaster -game cstrike
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:spoolsv:serv_main (0 (nil))
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed
fixme:win:EnumDisplayDevicesW ((null),0,0x7f21f5f8,0x00000000), stub!
fixme:d3d:test_pbo_functionality >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Loading the PBO test texture
 @ directx.c / 3413
fixme:shdocvw:ViewObject_SetAdvise (0x7f0746c8)->(1 00000002 0x7f799288)
fixme:shdocvw:PersistStreamInit_InitNew (0x7f0746c8)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x7f0746c8)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x7f0746c8)->(ffffffff)
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x7f0746c8)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x7f0746c8)
fixme:shdocvw:OleObject_Close (0x7f0746c8)->(1)


Everything just fine except that bleeping display that show the background of the first menu(2 CTs holding pistol).

---

