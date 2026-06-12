---
title: "Trying to run Starcraft in fullscreen mode"
date: 2007-11-04
forum: Wine
---

### Post by Fireblend on 2007-11-04
Hey. I just installed Starcraft through Wine, and it works fine, however, it works windowed on a 640x480 window, and I'd like it to run fullscreen.

First I tried to run the game directly after installing it, what I got was this error:

[IMG]http://i13.tinypic.com/67zprok.png[/IMG]

After that, I made it work windowed on 640x480 using the graphics tab on winecfg, that's how I'm playing now.

However, I would really like to play on fullscreen mode as the 640x480 window is kinda little :p

I checked my xorg.conf file and it seems to have 640x480 support enabled, so I don't know where to go now. I also tried running it without Compiz, but got the same result. Any help would be greatly appreciated.

Thanks in advance!

---

### Post by Stormspireiv on 2007-11-04
These are the settings I use to run Starcraft:

---

### Post by Fireblend on 2007-11-04
> **Stormspireiv said:**
> These are the settings I use to run Starcraft:

Thanks, however it's still giving me the same error. The output on terminal is:

```
fixme:win:EnumDisplayDevicesW ((null),0,0x33f4bc,0x00000000), stub!
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x12c068)->(0x10024,00000013)
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8
err:xrandr:X11DRV_XRandR_SetCurrentMode Resolution change not successful -- perhaps display has changed?
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8
err:xrandr:X11DRV_XRandR_SetCurrentMode Resolution change not successful -- perhaps display has changed?
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x12c068)->((nil),00000008)

```

It will only run if I enable "Emulate virtual desktop" at 640 x 480 which gets me back to windowed mode :p

---

### Post by Stormspireiv on 2007-11-04
What kind of video card do you have?

---

### Post by amunimanghi on 2007-11-04
> **Fireblend said:**
> Thanks, however it's still giving me the same error. The output on terminal is:

```
fixme:win:EnumDisplayDevicesW ((null),0,0x33f4bc,0x00000000), stub!
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x12c068)->(0x10024,00000013)
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8
err:xrandr:X11DRV_XRandR_SetCurrentMode Resolution change not successful -- perhaps display has changed?
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8
err:xrandr:X11DRV_XRandR_SetCurrentMode Resolution change not successful -- perhaps display has changed?
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x12c068)->((nil),00000008)

```

It will only run if I enable "Emulate virtual desktop" at 640 x 480 which gets me back to windowed mode :p

I am your saviour today. Open up a console and type 'regedit'. Then go to  ```
HKEY_current_user > software > wine > X11 driver
```
Right click in the white area and select "New > String Value". Type in "UseXRandR" without the quotes and hit enter. Then double click what you just made and type 'N'. Quit regedit and start your game up. It should work in full screen.

---

### Post by Fireblend on 2007-11-04
> **amunimanghi said:**
> I am your saviour today. Open up a console and type 'regedit'. Then go to  ```
HKEY_current_user > software > wine > X11 driver
```
Right click in the white area and select "New > String Value". Type in "UseXRandR" without the quotes and hit enter. Then double click what you just made and type 'N'. Quit regedit and start your game up. It should work in full screen.

Thanks. It does seem to help, although even tho it is not giving me the error like before, the screen appears not centered, so I can only see part of the screen. I've attached a picture that should explain it better.

Curious thing is, sometimes it is more centered than others, so sometimes it looks like this and sometimes I can barely see the "exit" option.

Edit: Ok, I have figured it out a little more. Apparently, it's got something to do with the position of the cursor when the game starts. If I place the cursor on the top-left corner of the screen before the resolution changes, it works just fine. Weird :p

At least now I have my fullscreen mode. Thanks!

---

### Post by kerheol on 2011-08-24
> **amunimanghi said:**
> I am your saviour today. Open up a console and type 'regedit'. Then go to  ```
HKEY_current_user > software > wine > X11 driver
```
Right click in the white area and select "New > String Value". Type in "UseXRandR" without the quotes and hit enter. Then double click what you just made and type 'N'. Quit regedit and start your game up. It should work in full screen.

2011 and you just save me... thanks a lot!!!

---

### Post by KIAaze on 2011-08-25
It's a very old thread, but just in case: [http://www.playonlinux.com/](http://www.playonlinux.com/) offers starcraft+starcraft broodwar installers. ;)

---

### Post by Perfect Storm on 2011-08-25
Thread closed and moved to Wine section.

---

