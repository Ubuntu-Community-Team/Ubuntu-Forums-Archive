---
title: "No music with old games made with Game Maker."
date: 2013-01-04
forum: Wine
---

### Post by Vyst on 2013-01-04
I went digging through my hard drive and found some old games I made with Game Maker several years ago. I wanted to show them to a friend, so I loaded them up with Wine (when I made them I was using Windows XP). The game worked but I got an error with the "Direct Music Audio". After some searching I was recommended to use Winetricks to download directmusic, dsound, and wmp10, as well as deleting the Audio string in HKEY_CURRENT_USER using regedit. After doing this I quit receiving the error and the sound effects worked (although delayed). However, the music still doesn't work.

I've been playing around with all the different Audio configurations in WineConfig and the result is always the same: I have delayed sound effects and no music whatsoever. Anyone have an idea what I could try next?

I'm running Ubuntu 12.10 and Wine 1.4.1. Wine is set to Windows XP and the files are executables.

Thanks!
-Vyst

---

### Post by Vyst on 2013-01-04
Ah yes, forgot to include the code output. I've gotten all sort of things so far, but this is the most current one:

```
vyst@SchmuckHaven:~/Desktop$ wine Mazegame.exe
fixme:advapi:RegisterTraceGuidsW (0x100778a, 0x100a060, {485e7de8-0a80-11d8-ad15-505054503030}, 1, 0x33fde0, (null), (null), 0x100a068,): stub
fixme:advapi:RegisterTraceGuidsW (0x100778a, 0x100a080, {485e7de9-0a80-11d8-ad15-505054503030}, 1, 0x33fde0, (null), (null), 0x100a088,): stub
fixme:advapi:RegisterTraceGuidsW (0x100778a, 0x100a0a0, {485e7dea-0a80-11d8-ad15-505054503030}, 1, 0x33fde0, (null), (null), 0x100a0a8,): stub
fixme:advapi:RegisterTraceGuidsW (0x100778a, 0x100a0c0, {485e7deb-0a80-11d8-ad15-505054503030}, 1, 0x33fde0, (null), (null), 0x100a0c8,): stub
fixme:advapi:RegisterTraceGuidsW (0x100778a, 0x100a0e0, {485e7dec-0a80-11d8-ad15-505054503030}, 1, 0x33fde0, (null), (null), 0x100a0e8,): stub
fixme:advapi:RegisterTraceGuidsW (0x100778a, 0x100a100, {485e7ded-0a80-11d8-ad15-505054503030}, 1, 0x33fde0, (null), (null), 0x100a108,): stub
fixme:win:RegisterDeviceNotificationW (hwnd=0x133148, filter=0x54e8ec,flags=0x00000001) returns a fake device notification handle!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f648,0x00000000), stub!
```

---

