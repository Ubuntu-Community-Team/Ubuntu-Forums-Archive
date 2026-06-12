---
title: "GTA: San Andreas (close but no cigar)"
date: 2008-04-17
forum: Wine
---

### Post by melat0nin on 2008-04-17
Hi all

Trying to get San Andreas running in Wine. It installed fine and I have updated it to 1.01 and added the no-dvd crack (I own the game, by the way).

When I run it from the terminal I get the following output:-

[PHP]laurence@melat0nin:~/.wine/drive_c/Program Files/Rockstar Games/GTA San Andreas$ wine gta_sa.exe
ALSA lib conf.c:3949:(snd_config_expand) Unknown parameters 0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:0
fixme:system:SystemParametersInfoW Unimplemented action: 8193 (SPI_SETFOREGROUNDLOCKTIMEOUT)
fixme:win:EnumDisplayDevicesW ((null),0,0x34f78c,0x00000000), stub!
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x12dc60)->((nil),00000008)
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x12dbb8)->((nil),00000008)
fixme:d3d:IWineD3DImpl_CheckDeviceMultiSampleType Quality levels unsupported at present
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x133938) : stub
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
*********************************WARN_ONCE*********************************
File r300_render.c function r300Fallback line 469
Software fallback:ctx->Multisample.Enabled
***************************************************************************
[/PHP]

It looks as though the game isn't being rendered in 3D, although I'm no expert.

The screen goes dark and (very) slowly fades to white in several steps, like it's fading in before the menus or something.  So it's running at the very least.  The only way to get out of it is to get back to terminal and Ctrl-C out of it.

Any thoughts?  I run Compiz absolutely fine.  I've tried disabling it and going to Metacity but the same thing happens when I run the game.

I'm running an ATi 9800Pro/XT on the standard Gutsy driver (ati)

---

### Post by Hairy_Palms on 2008-04-17
weird, i played san andreas on wine perfectly, win version set to win2k i think, that was a few versions of wine ago, but nothing substantial has changed, the only problem i had was sometimes carls entire body would become the colour of his hair, (very weird with green hair :D)

one thing would be to find an old version of wine, it mustve been about 0.9.45 that i last played it under.

---

### Post by melat0nin on 2008-04-18
I switched over to the restricted ATi driver and I managed to get it running, and could get into the game and walk about.  It was slow as hell and eventually crashed but at least it worked.

Alas, CompizFusion doesn't work on my machine with the proprietary driver and since I use non-3D apps more that is more important to me.

Can't quite understand why CF (accelerated) shouldn't work while 3D (accelerated) does, it's really annoying, and alas I don't have the money to buy an nVidia card.

---

