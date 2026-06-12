---
title: "[SOLVED] counter strike 2d memory error?"
date: 2008-05-13
forum: Wine
---

### Post by crazyfuturamanoob on 2008-05-13
I downloaded cs2d and tried to run it. For first, it 
complained about missing dlls that I downloaded. But
now it gives these errors:
```

arho@ohra-desktop:~/css/:D/cs2d_0104$ wine CounterStrike2D.exe
preloader: Warning: failed to reserve range 00000000-60000000
**err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report**
fixme:midi:OSS_MidiInit Synthesizer supports MIDI in. Not yet supported.
fixme:win:EnumDisplayDevicesW ((null),0,0x7f21f7f0,0x00000000), stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:ddraw:IDirectDrawImpl_RestoreAllSurfaces (0x7f022ec8): Stub
fixme:d3d7:IDirect3DImpl_7_EvictManagedTextures (0x7f022ec8): Stub!
arho@ohra-desktop:~/css/:D/cs2d_0104$ 

```
I can't play it because of that memory
error. How to fix it?

---

### Post by happyhamster on 2008-05-13
Concerning the memory error, see:
[http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem)

---

