---
title: "Counter Strike 2D In WINE"
date: 2007-10-25
forum: Wine
---

### Post by blithen on 2007-10-25
So I want to play a version of Counter Strike that is a 2D port. Now what happens when I run it under WINE this happens.

```
blithen@Sparky:/media/disk-1/Counter-Strike-2d$ sudo wine CounterStrike2D.exe
[sudo] password for blithen:
fixme:win:EnumDisplayDevicesW ((null),0,0x34f820,0x00000000), stub!
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x11f550)->((nil),00000008)
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x11f550)->(0x10024,00000008)
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x11f550)->((nil),00000008)
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x11f550)->(0x10024,00000013)
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:ddraw:IDirectDrawImpl_RestoreAllSurfaces (0x11f550): Stub
fixme:d3d7:IDirect3DImpl_7_EvictManagedTextures (0x11f550): Stub!
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x11f550)->((nil),00000008)
blithen@Sparky:/media/disk-1/Counter-Strike-2d$ glxinfo | grep rendering
direct rendering: Yes

```

---

### Post by karth on 2007-10-26
I can see that your system complains about not being able to switch to 16 bpp...
Aren't there any graphical options in the game menus that would allow you to run the game in 32 bpp?

Or you could try to run in a wine virtual desktop (winecfg > Graphics > Enable virtual desktop), I think it'll allow specific configuration changes made by games.

One last thing that has nothing to do with your issue, Wine devs recommend running wine in user mode, and not root, for security reasons. You shouldn't (and needn't) run wine using sudo...

Hope that helps :)

---

### Post by blithen on 2007-10-26
> **karth said:**
> I can see that your system complains about not being able to switch to 16 bpp...
Aren't there any graphical options in the game menus that would allow you to run the game in 32 bpp?

Or you could try to run in a wine virtual desktop (winecfg > Graphics > Enable virtual desktop), I think it'll allow specific configuration changes made by games.

One last thing that has nothing to do with your issue, Wine devs recommend running wine in user mode, and not root, for security reasons. You shouldn't (and needn't) run wine using sudo...

Hope that helps :)

I usually don't run it in root. I was just trying it to see what happens.

---

### Post by cogadh on 2007-10-26
Running Wine with a root account or sudo can lead to very bad things. There is nothing to be gained from trying it.

I tried running the game myself and got it to launch while producing the same errors you received (the "fixme" messages are usually just developer notes that mean nothing to a normal user), but after it launched I got a "memory access violation" and the game crashed. Nothing of use is output to the terminal. This game has no entry in Wine's AppDB, which doesn't necessarily mean anything, but I have often found that games with no entry are games that don't work at all.

Chances are the game is looking for some function that has not been implemented in Wine yet, hence the "fixme" messages that end with "Stub". Stubs are placeholders in the Wine code for features that are still in development. Sometimes the presence of a stub can allow the program to get past some minor unimplemented function and still run, but it looks like that is not the case with this game.

---

### Post by blithen on 2007-10-26
> **cogadh said:**
> Running Wine with a root account or sudo can lead to very bad things. There is nothing to be gained from trying it.

I tried running the game myself and got it to launch while producing the same errors you received (the "fixme" messages are usually just developer notes that mean nothing to a normal user), but after it launched I got a "memory access violation" and the game crashed. Nothing of use is output to the terminal. This game has no entry in Wine's AppDB, which doesn't necessarily mean anything, but I have often found that games with no entry are games that don't work at all.

Chances are the game is looking for some function that has not been implemented in Wine yet, hence the "fixme" messages that end with "Stub". Stubs are placeholders in the Wine code for features that are still in development. Sometimes the presence of a stub can allow the program to get past some minor unimplemented function and still run, but it looks like that is not the case with this game.
w00t. Thanks for the info!

---

