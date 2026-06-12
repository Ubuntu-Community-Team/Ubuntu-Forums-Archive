---
title: "BERYL+EDGY+glx"
date: 2006-10-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by alek66 on 2006-10-29
Trying to making it work, i used this [guide]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL")

But heres a doubt:
glxinfo, shows this:
> alek@darkstar:~$ glxinfo 
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_ARB_multisample, GLX_NV_float_buffer
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_ARB_multisample, GLX_NV_float_buffer, GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce FX Go5700/AGP/SSE2
OpenGL version string: 2.0.2 NVIDIA 87.74

startxgl.sh, shows this:
> #!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:fbo -accel glx:pbuffer &
sleep 4  
export DISPLAY=:1
exec gnome-session


But here, after xgl instead of a one and in export display=:1, should I put 0, cause that what it says in glxinfo rigth?

---

