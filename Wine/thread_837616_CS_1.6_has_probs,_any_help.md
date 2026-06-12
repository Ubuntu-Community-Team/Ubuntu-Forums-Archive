---
title: "CS 1.6 has probs, any help?"
date: 2008-06-22
forum: Wine
---

### Post by bobandirus on 2008-06-22
I have got CS 1.6 to work, but there are 2 probs, one is that once you have chosen a level, it loads, and at the screan where you choose team, like the first screan, there is no text and the whole computer hangs there. I have to then log out and log in. 
The other problem is that in the Wine CFG it doesnt show up as one of the applications in the applications tab....


Im very new to this still, so s-p-e-a-k    s-l-o-w-l-y   a-n-d   s-i-m-p-a-l-l-y p-l-e-a-s-e :)

Many thanks :)


EDIT: forgot to say, Ubuntu 8.40, not sure what Wine I have, and Im dual booting with windows, and I can tell you that it works well in windows, I want it to work in Ubuntu, so I can shift more over this way :D

---

### Post by Cup of Squirrels on 2008-06-23
wine CFG should be able to be run through your terminal. Open up your terminal, and type in "winecfg".

As for your in-game issue, do you know if you're using opengl or direct3d? As far as I know, wine has a few issues with D3D. Before joining a game, go to your video options and change it to opengl (If it's already opengl, it might be worth trying Direct3d if the option is there. Don't use software though!)

Good luck!

---

### Post by bobandirus on 2008-06-23
Yea ill tryi that - am at school but about to walk home, so ill let you know in 1/2 hr or so...

---

### Post by bobandirus on 2008-06-23
It came out with this when I typed winecfg into the terminal, is this normal?

```

andrew@andrew-laptop:~$ winecfg
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:vxd:VXD_Open Unknown/unsupported VxD L"bcmdmccp.vxd". Try setting Windows version to 'nt40' or 'win31'.
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:vxd:VXD_Open Unknown/unsupported VxD L"smartvsd.vxd". Try setting Windows version to 'nt40' or 'win31'.
fixme:mountmgr:harddisk_ioctl unsupported ioctl 560000
fixme:vxd:VXD_Open Unknown/unsupported VxD L"smartvsd.vxd". Try setting Windows version to 'nt40' or 'win31'.
fixme:mountmgr:harddisk_ioctl unsupported ioctl 560000
fixme:vxd:VXD_Open Unknown/unsupported VxD L"smartvsd.vxd". Try setting Windows version to 'nt40' or 'win31'.
fixme:mountmgr:harddisk_ioctl unsupported ioctl 560000
err:dosmem:load_winedos Could not load winedos.dll, DOS subsystem unavailable
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:vxd:VXD_Open Unknown/unsupported VxD L"sice.vxd". Try setting Windows version to 'nt40' or 'win31'.
fixme:vxd:VXD_Open Unknown/unsupported VxD L"ntice.vxd". Try setting Windows version to 'nt40' or 'win31'.
fixme:vxd:VXD_Open Unknown/unsupported VxD L"siwdebug.vxd". Try setting Windows version to 'nt40' or 'win31'.
fixme:vxd:VXD_Open Unknown/unsupported VxD L"siwvid.vxd". Try setting Windows version to 'nt40' or 'win31'.

```


Also, it came up with this error box, but it did load:

Error:
Error while unpacking program, code C. Please report to author.




and changeing the video thing didnt work either, D3D was crap (all the text was squashed together, will try it again), and I tryed software, which gave the same prob as OpenGL

---

### Post by Cup of Squirrels on 2008-06-23
That doesn't look healthy - not normal at all.

Personally I don't know what's going wrong here (best to wait for someone with a little more expertise to pinpoint the exact problem)

Until then, it might be wise to try a wine reinstall. For info on that, read this thread (linked thread is useful too):

[http://ubuntuforums.org/showthread.php?t=499138](http://ubuntuforums.org/showthread.php?t=499138)

---

### Post by bobandirus on 2008-06-23
Thanks for the help, ill try the re-install, and I hope someone with more experiance comes along :)

---

### Post by bobandirus on 2008-06-24
*Bump*

---

