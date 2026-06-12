---
title: "overdrive won't install"
date: 2015-11-25
forum: Wine
---

### Post by Kilarin on 2015-11-25
I'm trying to install overdrive media console [http://omc.overdrive.com/windows.php](http://omc.overdrive.com/windows.php)
I'm running Xubuntu 14.04.  My old 32bit system is dying, so I just got a new 64bit system and installed xubuntu 14.04 on it.
Overdrive was working fine on my old 32bit system, but when I attempted to install it on my new 64bit system, I started getting a lot of problems similar to what has been documented in this closed thread: [http://ubuntuforums.org/showthread.php?t=2171414](http://ubuntuforums.org/showthread.php?t=2171414)

What I have accomplished so far:
I was able to install windows media player 10 using winetricks and a wineprefix:
WINEARCH=win32 WINEPREFIX=~/.wine32 wineboot
WINEPREFIX=~/.wine32 winetricks wmp10

then I tried to install overdrive using this:
WINEPREFIX=~/.wine32 wine msiexec /i ODMediaConsoleSetup.msi
but I get these errors:
```

fixme:advapi:RegisterTraceGuidsW (0x100778a, 0x100a060, {485e7de8-0a80-11d8-ad15-505054503030}, 1, 0x33fdd0, (null), (null), 0x100a068,): stub
fixme:advapi:RegisterTraceGuidsW (0x100778a, 0x100a080, {485e7de9-0a80-11d8-ad15-505054503030}, 1, 0x33fdd0, (null), (null), 0x100a088,): stub
fixme:advapi:RegisterTraceGuidsW (0x100778a, 0x100a0a0, {485e7dea-0a80-11d8-ad15-505054503030}, 1, 0x33fdd0, (null), (null), 0x100a0a8,): stub
fixme:advapi:RegisterTraceGuidsW (0x100778a, 0x100a0c0, {485e7deb-0a80-11d8-ad15-505054503030}, 1, 0x33fdd0, (null), (null), 0x100a0c8,): stub
fixme:advapi:RegisterTraceGuidsW (0x100778a, 0x100a0e0, {485e7dec-0a80-11d8-ad15-505054503030}, 1, 0x33fdd0, (null), (null), 0x100a0e8,): stub
fixme:advapi:RegisterTraceGuidsW (0x100778a, 0x100a100, {485e7ded-0a80-11d8-ad15-505054503030}, 1, 0x33fdd0, (null), (null), 0x100a108,): stub
fixme:win:RegisterDeviceNotificationW (hwnd=0x135818, filter=0x53e89c,flags=0x00000001) returns a fake device notification handle!

```

Any help would be greatly appreciated.

---

### Post by Kilarin on 2015-11-30
I'm not marking this as solved, because I still don't know how to install overdrive under wine in 64bit Xubuntu 14.04.
But I was having other problems (Long delays and errors when attempting to log off or shut down) so I installed 32bit Xubuntu 14.04, and overdrive installs fine under that.

---

