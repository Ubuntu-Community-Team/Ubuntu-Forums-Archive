---
title: "Nvidia problems with nvidia-glx-new &amp; compiz or any 3d stuff"
date: 2008-06-01
forum: x86 64-bit Users
---

### Post by David E. Fox on 2008-06-01
OK, been using ubuntu 64 hardy heron for about a week.

System is an ECS Geforce 6100-pm-m which has an onboard geforce 6100 graphics card. cpu is amd64, dual core.

I can get 3d acceleration to work, but it corrupts the display. I also saw this with the "regular" nvidia-glx setup. But it's worse with the nvidia-glx-new driver set up and installed.

Compiz works, but obliterates so much of the screen (particularly text in windows, firefox gmail sessions and such) that it's unusable. Mostly anything 3d will eventually corrupt the screen, or hang it requiring that I kill the X session.

dfox@newbox:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   KDE
 Graphics chip:         nVidia Corporation GeForce 6100 nForce 430 (rev a2)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

Here's what glxinfo reports:

ame of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer,
    GLX_ARB_fbconfig_float
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info,
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync,
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float,
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap,
    GLX_EXT_framebuffer_sRGB


My nvidia packages installed:

fox@newbox:~$ dpkg -l | grep nvidia
ii  nvidia-glx-new                             169.12+2.6.24.12-17.36                             NVIDIA binary XFree86 4.x/X.Org 'new' driver
ii  nvidia-kernel-2.6.24-16-generic            169.12-0ubuntu3+2.6.24-16.30                       NVIDIA binary kernel module for Linux 2.6.24
ii  nvidia-kernel-common                       20051028+1ubuntu8                                  NVIDIA binary kernel module common files
ii  nvidia-new-kernel-source                   169.12+2.6.24.12-17.36                             NVIDIA binary 'new' kernel module source
ii  nvidia-settings                            1.0+20080304-0ubuntu1                              Tool of configuring the NVIDIA graphics driv

At the moment, I'm using my xorg.conf from my debian lenny system, which compiz mostly worked on, although it was using an FX 5200. But the graphics system string shouldn't matter? 


I put up a screenshot here. Note the black stuff all over certain parts, like window titles and text. Almost as if the CIA got into my computer :)


[http://img240.imageshack.us/my.php?image=screen1kc5.png](http://img240.imageshack.us/my.php?image=screen1kc5.png)

You can see the black stuff all over the ksirc window, for example.

Here's the current xorg.conf I am using:

[http://www.pastebin.ca/1034583](http://www.pastebin.ca/1034583)

Do I need (or want) Envy? I've heard about it, but the same thing happens more or less when I run sabayon 3.5 loop3 from the DVD on this machine. It says it's using the nvidia beta driver.

---

### Post by Sef on 2008-06-02
How did you install the NVidia drivers?

---

### Post by David E. Fox on 2008-06-02
> **Sef said:**
> How did you install the NVidia drivers?

The normal way. aptitude install nvidia-kernel-source and nvidia-glx (originally, then I retried using the "new" source and glx debs, and in both cases I ran module-assistant auto-install nvidia-kernel-source-(new).

---

