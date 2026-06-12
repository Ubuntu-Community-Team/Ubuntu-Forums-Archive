---
title: "diablo 3 ubuntu 13.10 and nvidia"
date: 2014-02-02
forum: Wine
---

### Post by ovidiu3 on 2014-02-02
hy there

i am new to ubuntu, i swtiched because of windows TDR -.-"

the problem i have is this

i installed play on linux, installed diablo 3 adn run it.

everything worked like a charm.

but even if i have the settings to play it with full screen with a resolution of 1920x1080  it is windowed :S and that is not good.

and after a few seconds of playing the game stops and the computer freeze and i have to reboot it the hard way.


direct rendering: Yes
    GL_AMD_multi_draw_indirect, GL_AMD_seamless_cubemap_per_texture, 
    GL_ARB_draw_elements_base_vertex, GL_ARB_draw_indirect, 
    GL_ARB_multi_draw_indirect, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_EXT_direct_state_access, GL_EXT_draw_buffers2, GL_EXT_draw_instanced, 
    GL_AMD_multi_draw_indirect, GL_AMD_seamless_cubemap_per_texture, 
    GL_ARB_draw_indirect, GL_ARB_draw_instanced, 
    GL_ARB_multi_draw_indirect, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_EXT_direct_state_access, GL_EXT_draw_buffers2, GL_EXT_draw_instanced

i have an nvidia gtx 650 TI with this drivers
ovidio-X58-USB3 kernel: [   14.421041] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  319.32  Wed Jun 19 15:51:20 PDT 2013

and the same thing happes with dota2 from steam

i installed steam, dota2, and when i try to play it, it takes me to the champ selection and it freezes.

any help?

---

### Post by howefield on 2014-02-02
Hello and welcome to the forums.

Thread moved to the "*Wine*" forum.

---

### Post by George_Bush on 2014-03-05
I have been playing Diablo III since shortly after it was released with only a few minor problems, mostly caused by Blizzard updates.
I have a GeForce GTX 465 and nvidia-304 driver.
```
[~]**$ dpkg -l|grep nvidia-**
ii  nvidia-304-updates                    304.108-0ubuntu1                              amd64        NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-common                         1:0.2.83                                      amd64        transitional package for ubuntu-drivers-common
rc  nvidia-current                        295.40-0ubuntu1                               amd64        NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-current-updates                304.108-0ubuntu1                              amd64        Transitional package for nvidia-current-updates
rc  nvidia-settings                       295.33-0ubuntu1                               amd64        Tool of configuring the NVIDIA graphics driver
ii  nvidia-settings-304-updates           304.88-0ubuntu2                               amd64        Tool for configuring the NVIDIA graphics driver
rc  nvidia-settings-updates               304.88-0ubuntu0.2                             amd64        Tool for configuring the NVIDIA graphics driver
```

Only thing I would suggest is make sure you are using the correct and updated nvidia driver. I also think it is suggested you run winecfg and set Diablo III.exe to run in Windows 7 environment. 
I have winecfg set to run Diablo III.exe with these graphics settings checked
Allow the window manager to decorate the windows 
and 
Allow the window manager to control the windows

---

