---
title: "Heroes of might and magic 2 in WINE"
date: 2011-12-27
forum: Wine
---

### Post by RuneLacroix on 2011-12-27
Hey.

Im trying to launch Heroes of might and magic 2 in wine. No succes.

This is what happends. Any help?

```
runelacroix@Shakti:~$ env WINEPREFIX="/home/runelacroix/.wine" wine C:\\windows\\command\\start.exe /Unix /home/runelacroix/.wine/dosdevices/c:/users/Public/Desktop/Heroes\ of\ Might\ and\ Magic\ 2\ GOLD.lnk

fixme:exec:SHELL_execute flags ignored: 0x00000100
fixme:exec:SHELL_execute flags ignored: 0x00004100
runelacroix@Shakti:~$ fixme:win:EnumDisplayDevicesW ((null),0,0x268f360,0x00000000), stub!
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:win:EnumDisplayDevicesW ((null),0,0x268f260,0x00000000), stub!
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:d3d:wined3d_device_decref Device released with resources still bound, acceptable but unexpected.
fixme:d3d:wined3d_device_decref Leftover resource 0x186048 with type WINED3DRTYPE_SURFACE (0x1).
err:d3d:wined3d_device_decref Context array not freed!

```

---

### Post by mateo14 on 2011-12-27
> **RuneLacroix said:**
> Hey.

Im trying to launch Heroes of might and magic 2 in wine. No succes.

This is what happends. Any help?

```
runelacroix@Shakti:~$ env WINEPREFIX="/home/runelacroix/.wine" wine C:\\windows\\command\\start.exe /Unix /home/runelacroix/.wine/dosdevices/c:/users/Public/Desktop/Heroes\ of\ Might\ and\ Magic\ 2\ GOLD.lnk

fixme:exec:SHELL_execute flags ignored: 0x00000100
fixme:exec:SHELL_execute flags ignored: 0x00004100
runelacroix@Shakti:~$ fixme:win:EnumDisplayDevicesW ((null),0,0x268f360,0x00000000), stub!
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:win:EnumDisplayDevicesW ((null),0,0x268f260,0x00000000), stub!
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:d3d:wined3d_device_decref Device released with resources still bound, acceptable but unexpected.
fixme:d3d:wined3d_device_decref Leftover resource 0x186048 with type WINED3DRTYPE_SURFACE (0x1).
err:d3d:wined3d_device_decref Context array not freed!

```

Try this:

[http://www.lgdb.org/game/heroes_might_and_magic_ii_fheroes_2](http://www.lgdb.org/game/heroes_might_and_magic_ii_fheroes_2)

---

### Post by howefield on 2011-12-27
Thread moved to the "*Wine*" forum.

---

