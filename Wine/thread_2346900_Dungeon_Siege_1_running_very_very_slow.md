---
title: "Dungeon Siege 1 running very very slow"
date: 2016-12-19
forum: Wine
---

### Post by Kilarin on 2016-12-19
Hello folks.
I had Dungeon Siege 1 running just fine under wine with xubuntu 14.04 32bit.  I recently backed everything up and installed xubuntu 16.04 64bit.  
I copied my backup of the already installed Dungeon Siege 1 to ~/.wine32/dosdevices/c:/Program Files/Microsoft Games/Dungeon Siege/ 

And tried to run it with:

env WINEPREFIX=~/.wine32 WINEARCH=win32 wine "C:\Program Files\Microsoft Games\Dungeon Siege\DungeonSiege.Exe" width=1024 height=768 bpp=16

And, well, it SORT of works.  The intro movie is fine, but once it gets to the main menu, everything slows to a crawl.  The mouse freezes up for 5 to 10 seconds between moves.  If I go ahead and start the game, it does load, but again, the game screen will freeze for 10, 20, or even 30 seconds, during which time I can hear sounds that imply the game is running, then suddenly the screen will update and run for a few seconds before freezing again.

the terminal shows:
```
$ env WINEPREFIX=~/.wine32 WINEARCH=win32 wine "C:\Program Files\Microsoft Games\Dungeon Siege\DungeonSiege.Exe" width=1024 height=768 bpp=16
err:winediag:schan_imp_init Failed to load libgnutls, secure connections will not be available.
err:winediag:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path. Usually, you can find it in the winbind package of your distribution.
fixme:advapi:RegisterTraceGuidsW (0x100778a, 0x100a060, {485e7de8-0a80-11d8-ad15-505054503030}, 1, 0x33fdb0, (null), (null), 0x100a068): stub
fixme:advapi:RegisterTraceGuidsW   register trace class {485e7de8-0a80-11d8-ad15-505054503030}
fixme:advapi:RegisterTraceGuidsW (0x100778a, 0x100a080, {485e7de9-0a80-11d8-ad15-505054503030}, 1, 0x33fdb0, (null), (null), 0x100a088): stub
fixme:advapi:RegisterTraceGuidsW   register trace class {485e7de9-0a80-11d8-ad15-505054503030}
fixme:advapi:RegisterTraceGuidsW (0x100778a, 0x100a0a0, {485e7dea-0a80-11d8-ad15-505054503030}, 1, 0x33fdb0, (null), (null), 0x100a0a8): stub
fixme:advapi:RegisterTraceGuidsW   register trace class {485e7dea-0a80-11d8-ad15-505054503030}
fixme:advapi:RegisterTraceGuidsW (0x100778a, 0x100a0c0, {485e7deb-0a80-11d8-ad15-505054503030}, 1, 0x33fdb0, (null), (null), 0x100a0c8): stub
fixme:advapi:RegisterTraceGuidsW   register trace class {485e7deb-0a80-11d8-ad15-505054503030}
fixme:advapi:RegisterTraceGuidsW (0x100778a, 0x100a0e0, {485e7dec-0a80-11d8-ad15-505054503030}, 1, 0x33fdb0, (null), (null), 0x100a0e8): stub
fixme:advapi:RegisterTraceGuidsW   register trace class {485e7dec-0a80-11d8-ad15-505054503030}
fixme:advapi:RegisterTraceGuidsW (0x100778a, 0x100a100, {485e7ded-0a80-11d8-ad15-505054503030}, 1, 0x33fdb0, (null), (null), 0x100a108): stub
fixme:advapi:RegisterTraceGuidsW   register trace class {485e7ded-0a80-11d8-ad15-505054503030}
fixme:win:RegisterDeviceNotificationW (hwnd=0x142558, filter=0x64e87c,flags=0x00000001) returns a fake device notification handle!
fixme:ddraw:DirectDrawEnumerateExA flags 0x00000006 not handled
fixme:thread:start_thread Started native thread 00000030
fixme:win:EnumDisplayDevicesW ((null),0,0x33eef4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33eb64,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33eb64,0x00000000), stub!
fixme:ddraw:ddraw7_Initialize Ignoring guid {aeb2cdd4-6e41-43ea-941c-8361cc760781}.
fixme:win:EnumDisplayDevicesW ((null),0,0x33f374,0x00000000), stub!
fixme:ddraw:ddraw7_Initialize Ignoring guid {00000000-0000-0000-0000-000000000000}.
fixme:ddraw:ddraw7_FlipToGDISurface iface 0x14e500 stub!
fixme:font:freetype_SelectFont Untranslated charset 255
fixme:ddraw:ddraw_surface7_Flip Ignoring flags 0x1.
fixme:imm:ImmDisableTextFrameService Stub
fixme:ddraw:ddraw7_FlipToGDISurface iface 0x14e500 stub!

```
(the last line repeats over and over)

Details:
I have a Lenovo ThinkPad Edge E555 20DH002QUS AMD Dual Core A6-7000
with Graphics adapter: AMD Radeon R5 (Kaveri), Core: 514 MHz, 14.201.1003.1001
Running Xubuntu 16.04 
wine-1.8
Winetricks shows version as 20140817

Is there something simple I'm missing that would make this more likely to work?

thank you in advance!

---

### Post by DuckHook on 2016-12-20
With WINE, it's really by guess and by golly. My guess (and it is a guess) is that when you upgraded to a 64 bit architecture, the need to translate system calls back and forth to and from 32 bits has degraded the performance of your old wine install.

Since you know how to use prefixes, I would suggest installing another instance of your game into a new prefix. The hope is that by installing to a "native" container, the arcane configurations of WINE will be set up more optimally.

wineDB also returns varied results for your game ranging from platinum to silver. But they are all rather old, so that really doesn't tell you anything either. Your box is not really powerful enough to game within a VM. Otherwise, that would be another option.

It is also possible that Xenial's version of wine suffers from a regression that breaks your game, whereas the older WINE version was more stable for your particular app. This is a known general problem with WINE, but one can hardly blame them&#8213;they're trying to work their magic by reverse-engineering the convolutions of another OS without the benefit of their source code.

If all else fails, you can try replacing the WINE in your default install with the latest from the WINE developers. While I don't normally recommend installing PPAs, I make an exception in the case of WINE. The maintained one is:```
deb http://ppa.launchpad.net/wine/wine-builds/ubuntu xenial main
```
Be sure to not only remove, but purge your old WINE first. You don't want any of the old config files hanging around when you add the PPA.

---

### Post by Kilarin on 2016-12-27
Thank you, I'll try installing into a new prefix.

---

