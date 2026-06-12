---
title: "Ragnarok Online"
date: 2008-06-16
forum: Wine
---

### Post by evanct on 2008-06-16
this is a private client. specifically RebirthRO. when i run wine RebirthRO.bin 1rag1 i get this:

[http://img294.imageshack.us/img294/9940/screenshotrt7.png](http://img294.imageshack.us/img294/9940/screenshotrt7.png)

and here is the output: 
```
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:spoolsv:serv_main (0 (nil))
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:win:EnumDisplayDevicesW ((null),0,0x7f21f594,0x00000000), stub!
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report

```

any ideas? i've tried it with cedega and haven't had any more luck.

---

### Post by cogadh on 2008-06-16
This will take care of those preloader errors:
[http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem)

After applying that fix, try running it again.

---

### Post by evanct on 2008-06-18
ok, i upgraded wine to 1.0 and applied that fix. now i still get the same thing as in the screenshot, however the output is different:

```
fixme:win:EnumDisplayDevicesW ((null),0,0x32f57c,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface

```

---

### Post by cogadh on 2008-06-18
What video card do you have and have you installed the restricted drivers for it? Are you running Desktop Effects/Compiz?

---

