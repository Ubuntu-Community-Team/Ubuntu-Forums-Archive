---
title: "Problem drawing Chessmaster X"
date: 2008-05-29
forum: Wine
---

### Post by CPesyna on 2008-05-29
I've verified that I've installed the game properly, but after splash screens and intro movies, I am presented with a black window. This is what I get when I run in the terminal:
```

err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on Intel ICH6 Modem, disabling mixer
fixme:imm:ImmDisableIME (-1): stub
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:win:LockWindowUpdate (0x10028), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:win:LockWindowUpdate (0x10028), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:win:LockWindowUpdate (0x10028), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
```

The hardware I'm running on is nothing fancy, just onboard video. Anyway, I started messing around with xorg.conf -- here are the relevant portions:

Section "Device"
       Identifier      "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
       Driver          (see below)
       BusID           "PCI:0:2:0"

EndSection

If I use a driver named Intel, native OpenGL applications run reasonably well, but direct rendering (as checked by glxinfo | grep -i direct) isn't enabled. If I use another driver, i810, native OpenGL apps run beautifully, and direct rendering is enabled. With either of these drivers enabled, the game loads, but draws a black (or sometimes noisy, totally unusable) game window. Interestingly, if I switch the drive to the failsafe vesa I get no direct rendering, but the game draws perfectly, but runs with a terrible framerate.

I've tried messing around a little with winecfg, tried to emulate different Windows versions, enabled/disabled various graphics settings, but got the same problem each time.

Anyway, I'd appreciate any thoughts or ideas anyone might have.
> 
PS I'm using Wine 1.0 rc2...under rc1 with the Intel driver, the game would draw properly and run smoothly, but the body of the window would be shifted the width of the window to the left. It was usable, but really irritating, because it essentially cut my screen in half, and the game needed the mouse to be in the empty window frame, so manipulating menus and stuff was a real pain.

---

### Post by CPesyna on 2008-05-30
Bump/No love from 1.0 rc3 either. Exact same problem

I've decided to use 1.0 rc1 as a workaround for the time being, but would really appreciate any other insights as to what's going on. Is everyone as stumped as me?

Anyway, off to the appdb to give me experiences over there.

---

### Post by ajackson on 2008-05-31
Run cmsettings.exe and choose OpenGL rather than Direct3D, that works fine for me.

---

### Post by CPesyna on 2008-05-31
Probably should have mentioned this, but I am running in OpenGL and with only 2D boards. Thanks for the tip though. What graphics card are you using?

---

### Post by ajackson on 2008-05-31
NVidia 7600GT, I only need to set OpenGL, 3d boards seem to work OK for me.

---

### Post by CPesyna on 2008-05-31
Hmm, you're lucky. I can live with using a half screen width game window and entering moves via the keyboard for now. Thanks for letting me know about the hardware (I'm thinking of a bug about the window drawing, so the data could be useful).

---

