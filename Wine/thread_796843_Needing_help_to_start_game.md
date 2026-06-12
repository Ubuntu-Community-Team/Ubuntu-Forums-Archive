---
title: "Needing help to start game"
date: 2008-05-16
forum: Wine
---

### Post by Samzen on 2008-05-16
Hey, I'm needing some help to start this game....I'm using the latest wine & ubuntu hardy....

The output I get is this:

preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:mixer:ALSA_MixerInit No master control found on USB Device 0x46d:0x8ce, disabling mixer
fixme:mixer:ALSA_MixerInit No master control found on MPU-401 UART, disabling mixer
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:imm:ImmGetDefaultIMEWnd (0x2002e - (nil) 0x7f026980 ): semi-stub
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:winmm:MMDRV_Exit Closing while ll-driver open

I'm wondering if anyone has any tip or idea? It would be much appreciated.

---

### Post by Gunman1982 on 2008-05-16
Would help to know which game you want to run with wine ;)

---

### Post by cogadh on 2008-05-16
First things first, get rid of the preloader errors:
[http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem)

---

