---
title: "No 3D with fglrx (ATI)"
date: 2005-01-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by kagou on 2005-01-26
I have some problems with fglrx
For 2D all is OK

glxgears give me 144FPS
fgl_glxgears crash :
```
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  145 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  32
  Current serial number in output stream:  32
```
fglrxinfo :
```
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
```
fgl_glxgears -info :
```
GL_RENDERER   = Mesa GLX Indirect
GL_VERSION    = 1.2 (1.5 Mesa 6.2.1)
GL_VENDOR     = Mesa project: www.mesa3d.org
GL_EXTENSIONS = GL_ARB_imaging GL_ARB_multitexture GL_ARB_texture_border_clamp GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_transpose_matrix GL_EXT_abgr GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod_bias
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  145 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  36
  Current serial number in output stream:  36
```

---

### Post by Nadir on 2005-01-26
I have the same problem. 
/var/log/Xorg.0.log gives me:

```
[drm] failed to load kernel module "fglrx"
(II) fglrx(0): [drm] drmOpen failed
(EE) fglrx(0): DRIScreenInit failed!
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
```

If I try to insert the fglrx module I get:


```
FATAL: Error inserting fglrx (/lib/modules/2.6.10-2-amd64-k8/kernel/drivers/video/fglrx.ko): No such device

```

Can anybody help me ?

Thanks

Tristan

---

### Post by kagou on 2005-01-26
Yes i have the same log for X.

I have a problem with fglrx module
dmesg :
```
[fglrx:firegl_init_32compat_ioctls] *ERROR* unable to register ioctl32 0
[fglrx:firegl_init] *ERROR* Couldn't register compat32 ioctls!
```

---

### Post by Kareema on 2005-01-26
I really don't know why people seem to be unable to use the search function of this forum... ;-)

Problem is known. See [http://www.ubuntuforums.org/showthread.php?p=55610#post55610](http://www.ubuntuforums.org/showthread.php?p=55610#post55610) for the description and a work-around. Here's the short version:
Install the previous kernel image with "dpkg -i /var/cache/apt/archives/linux-image-2.6.10-2-amd64-k8_2.6.10-10_amd64.deb" (or whatever kernel version you are using).

---

### Post by Nadir on 2005-01-26
Well, I have cleaned my /var/apt/cache with apt-get clean, so I don't have the package and it is gone from all the mirrors I've looked at.

Tristan

---

### Post by kagou on 2005-01-26
old packages -> [http://morgue.ubuntulinux.org/](http://morgue.ubuntulinux.org/)

---

### Post by kagou on 2005-01-26
With previous kernel version, i'v a black screen  :-?

---

### Post by Kareema on 2005-01-27
[QUOTE=kagou]With previous kernel version, i'v a black screen  :-?[/QUOTE]

Try to play around with the 'UseInternalAGPGART' setting in xorg.conf. Perhaps that solves your problem. Take a look at my xorg.conf in the thread mentioned above, too.

BTW: Just tested the new kernel image (2.6.10-12) and it has the same problem loading the fglrx module as the one before.

---

### Post by j3no on 2005-04-13
ya,
I have had the same problem...
I use Radeon 9000 with X-Org but is same with X-F86

Go to /etc/X11 and modify xorg.conf or XF86conf.conf (or similar)

Change the PCI:01:00:01 in PCI:01:00:00 (or put "lspci" in shell too see the right address" ) and in the line "use internal agpgart" put "no".

Sorry for my bad english...

---

### Post by bigbluevan on 2006-10-25
I found that running the following as suggested in [here](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)  was the final step I needed to do```
sudo dpkg-reconfigure xserver-xorg
```

---

