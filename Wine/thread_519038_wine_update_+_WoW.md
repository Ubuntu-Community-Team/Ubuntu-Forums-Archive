---
title: "wine update + WoW"
date: 2007-08-06
forum: Wine
---

### Post by Delvien on 2007-08-06
So recently I have updated Wine,  and now when i run World of Warcraft, and alt tab to switch to a different window, it switches resolution twice, and then WoW no longer has sound, untill i restart it.

here is the output. Maybe yall can make some sense of it.

```
fixme:win:EnumDisplayDevicesW ((null),0,0x33daa4,0x00000000), stub!
fixme:wgl:X11DRV_wglQueryPbufferARB unsupported WGL_PBUFFER_LOST_ARB (need glXSelectEvent/GLX_DAMAGED work)
fixme:wgl:X11DRV_wglQueryPbufferARB unsupported WGL_PBUFFER_LOST_ARB (need glXSelectEvent/GLX_DAMAGED work)
fixme:wgl:X11DRV_wglQueryPbufferARB unsupported WGL_PBUFFER_LOST_ARB (need glXSelectEvent/GLX_DAMAGED work)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x33daa4,0x00000000), stub!
fixme:wgl:X11DRV_wglQueryPbufferARB unsupported WGL_PBUFFER_LOST_ARB (need glXSelectEvent/GLX_DAMAGED work)
fixme:wgl:X11DRV_wglQueryPbufferARB unsupported WGL_PBUFFER_LOST_ARB (need glXSelectEvent/GLX_DAMAGED work)
fixme:wgl:X11DRV_wglQueryPbufferARB unsupported WGL_PBUFFER_LOST_ARB (need glXSelectEvent/GLX_DAMAGED work)

```

---

### Post by cogadh on 2007-08-06
Those are all developer debug messages (they aren't really errors) and none of them have anything to do with sound. I think the problem is the ALT-TAB, you shouldn't do that when playing games through Wine, they don't deal with it well.

---

### Post by hikaricore on 2007-08-06
Solution to this problem would be pretty much the following:

1. Run WoW in _windowed_ mode.
2. Set WoW to be _maximized_ in windowed mode.

Saves all those pesky resolution changes that are causing you grief.

To this day I believe the only way to change display setting is WoW is in D3D mode or manually in the config.wtf file.

---

### Post by sparau on 2007-08-06
Yes i have had the same problem...  But since there was an nvidia driver update i wasnt sure which was to blame.

I run dual monitor setup - with wow in native res - same as desktop...

i used to be able to mouse out to the other desktop and surf web etc etc without anything happening - since the updates of wine and nvidia it changes res twice and kills sound...

---

### Post by sparau on 2007-08-06
btw - to roll back the wine version...

do u just uninstall via dpkg then re-install the old one (i seem to remember the update cache is in something like /var/apt/cache? and there has been at least 2 updates of wine in the last few weeks so it should be there) or is there a GUI for this that i havent seen yet?

---

### Post by cogadh on 2007-08-06
Just uninstall either through Synaptic or "sudo apt-get remove wine" in the terminal. Then download and install an older package from the Wine repositories:
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

---

### Post by wereHamster on 2007-08-06
If you look into the wine appdb entry for WoW, you'll see that the bug has already been created in the wine bugzilla: [http://bugs.winehq.org/show_bug.cgi?id=9087](http://bugs.winehq.org/show_bug.cgi?id=9087). You'll also see some people suggest other workarounds than the 'windowed mode' suggestion.

---

### Post by sparau on 2007-08-06
Thanx guys.

To be honest i will still roll back to the previous version though - cause as well as sound stopping the machine becomes unresponsive for a sec whenever i mouse out to the other x-session...

This never used to happen - i love the seamless integration of the 2 sessions running.

---

### Post by sisslack on 2007-08-11
There is a quick and easy fix for the sound issue:
1. Go to WoW sound options.
2. Check the box in the lower left that says "Enable Sound in Background".
3. You may have to restart WoW.

Now you can alt+tab and you won't loose your sound.  :)

---

