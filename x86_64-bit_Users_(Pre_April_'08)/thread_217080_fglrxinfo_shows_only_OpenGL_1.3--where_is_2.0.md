---
title: "fglrxinfo shows only OpenGL 1.3--where is 2.0?"
date: 2006-07-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by mfeller on 2006-07-16
I am working through issues trying to get ATI's driver working correctly for 64-bit.  I have installed the driver from the website using the instructions at [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#General](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#General) (Method 2).

When I run fglrxinfo, I get the following: 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 8500 DDR Generic
OpenGL version string: 1.3.1080 (X4.3.0-8.26.18)

If you will note, the OpenGL version being reported is 1.3.1080, not 2.x.  Any advice on getting the newest OpenGL?

The first bits of glxinfo are as follows:
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 8500 DDR Generic
OpenGL version string: 1.3.1080 (X4.3.0-8.26.18)



(I am ultimately trying to run Doom3.  I'm not a big gamer, but since it runs on Linux, I thought I'd try it out--and now of course I must figure this out.  Doom3 now exits with the error message:

----- R_InitOpenGL -----
Setup X display connection
dlopen(libGL.so.1)
dlopen(libGL.so.1)
idRenderSystem::Shutdown()
signal caught: Segmentation fault
si_code 1
Was in fatal error shutdown: Unable to initialize OpenGL
Trying to exit gracefully..

The first thing I want to do is get the correct OpenGL version...but if anyone has additional things that I should try, please let me know).

Thanks...

---

### Post by amcquown on 2006-07-17
The problem lies within your Graphics card - the Radeon 8500 is NOT OpenGL 2.0 compliant, it's 1.3

---

