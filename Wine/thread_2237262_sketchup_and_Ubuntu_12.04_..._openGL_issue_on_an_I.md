---
title: "sketchup and Ubuntu 12.04 ... openGL issue on an Integrated 950 graphic card"
date: 2014-07-31
forum: Wine
---

### Post by pierreu1 on 2014-07-31
I did follow the instruction on how to install Sketchup8 (I downloaded sketchup 2014, but uninstalled it because ...) it does not go beyond the selection of the template step.

Here is the error message I get after I try to load SKetchup8 using wine WIN XP and WIN 7 config

[IMG]https://lh4.googleusercontent.com/-FYRmUbeOd6Y/U9rOGjVCR_I/AAAAAAAAE4A/eIm9byhaalM/w310-h143-no/skup.png[/IMG]

What could be the problem?

Thanks.

BTW, if it matters, I have 2 RAM.

---

### Post by pierreu1 on 2014-08-02
[COLOR=#4D5259][FONT=Open Sans]From Ketchup

Compatibility Issues[/FONT][/COLOR]
[COLOR=#4D5259][FONT=Open Sans]OpenGL incompatibility is a significant system configuration issue leading to problems with SketchUp. Difficulties with Sketchup tools, performance, and rendering (such as mysterious graphics appearing on your screen) are usually the result of a video card not fully supporting OpenGL (despite claims by the manufacturer), an out-of-date video card driver, or incompatibility with 32-bit color depth. A temporary solution is to disable hardware acceleration in SketchUp while troubleshooting the problem.[/FONT][/COLOR]
[COLOR=#4D5259][FONT=Open Sans]Consult the Video Card Compatibility section of the Readme file (in the SketchUp installation directory) for additional details regarding compatibility issues for specific video cards.[/FONT][/COLOR]

---

### Post by Yellow Pasque on 2014-08-03
What is glxinfo reporting? You may not have a recent enough GPU.
```
sudo apt-get install mesa-utils
glxinfo
```

---

### Post by pierreu1 on 2014-08-03
For mesa:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
mesa-utils is already the newest version.
mesa-utils set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


For GLX:

name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_swap_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_INTEL_swap_event
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_create_context_es2_profile, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_swap_control, 
    GLX_OML_swap_method, GLX_OML_sync_control, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap, GLX_INTEL_swap_event
GLX version: 1.4
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_swap_control, 
    GLX_OML_swap_method, GLX_OML_sync_control, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 945GM x86/MMX/SSE2
OpenGL version string: 1.4 Mesa 8.0.4
OpenGL extensions:
    GL_ARB_multisample, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_copy_texture, 
    GL_EXT_polygon_offset, GL_EXT_subtexture, GL_EXT_texture_object, 
    GL_EXT_vertex_array, GL_EXT_compiled_vertex_array, GL_EXT_texture, 
    GL_EXT_texture3D, GL_IBM_rasterpos_clip, GL_ARB_point_parameters, 
    GL_EXT_draw_range_elements, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_separate_specular_color, 
    GL_EXT_texture_edge_clamp, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_ARB_multitexture, GL_IBM_multimode_draw_arrays, 
    GL_IBM_texture_mirrored_repeat, GL_3DFX_texture_compression_FXT1, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, GL_ARB_transpose_matrix, 
    GL_EXT_blend_func_separate, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, 
    GL_EXT_secondary_color, GL_EXT_texture_env_add, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_INGR_blend_func_separate, GL_NV_blend_square, GL_NV_light_max_exponent, 
    GL_NV_texgen_reflection, GL_NV_texture_env_combine4, 
    GL_SUN_multi_draw_arrays, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_EXT_framebuffer_object, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, GL_MESA_window_pos, 
    GL_NV_packed_depth_stencil, GL_NV_texture_rectangle, GL_NV_vertex_program, 
    GL_ARB_depth_texture, GL_ARB_shadow, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_window_pos, 
    GL_EXT_stencil_two_side, GL_EXT_texture_cube_map, GL_NV_vertex_program1_1, 
    GL_APPLE_packed_pixels, GL_APPLE_vertex_array_object, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_shader, GL_ARB_shader_objects, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ATI_draw_buffers, 
    GL_ATI_texture_env_combine3, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_ARB_half_float_pixel, 
    GL_ARB_point_sprite, GL_ARB_shading_language_100, GL_ARB_sync, 
    GL_ARB_texture_non_power_of_two, GL_ARB_vertex_buffer_object, 
    GL_ATI_blend_equation_separate, GL_EXT_blend_equation_separate, 
    GL_OES_read_format, GL_ARB_pixel_buffer_object, GL_ARB_texture_rectangle, 
    GL_EXT_pixel_buffer_object, GL_EXT_texture_rectangle, 
    GL_ARB_framebuffer_object, GL_EXT_framebuffer_blit, 
    GL_EXT_framebuffer_multisample, GL_EXT_packed_depth_stencil, 
    GL_APPLE_object_purgeable, GL_ARB_vertex_array_object, 
    GL_ATI_separate_stencil, GL_EXT_gpu_program_parameters, GL_OES_EGL_image, 
    GL_ARB_copy_buffer, GL_ARB_map_buffer_range, 
    GL_EXT_separate_shader_objects, GL_ARB_ES2_compatibility, 
    GL_ARB_draw_elements_base_vertex, GL_ARB_explicit_attrib_location, 
    GL_ARB_provoking_vertex, GL_ARB_sampler_objects, GL_EXT_provoking_vertex, 
    GL_ARB_robustness


32 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x022 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x08e 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x08f 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x090 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x091 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x092 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x093 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x094 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x095 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x096 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x097 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x098 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x099 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x09a 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x09b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x09c 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x09d 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x09e 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x09f 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a0 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a1 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a2 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a3 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a4 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a5 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0a6 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0a7 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a8 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0a9 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0aa 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x05d 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None


48 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x05e  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x05f  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x060  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x061  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x062  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x063  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x064 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x065 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x066 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x067 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x068 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x069 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x06a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x06b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x06c 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x06d 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x06e 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x06f 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x070  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x071  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x072 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x073 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x074 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x075 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x076  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x077  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x078  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x079  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x07a  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x07b  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x07c 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x07d 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x07e 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x07f 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x080 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x081 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x082 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x083 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x084 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x085 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x086 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x087 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x088  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x089  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x08a 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x08b 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x08c 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x08d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow

I hope I did this right! Thanks!

---

### Post by Yellow Pasque on 2014-08-03
```
OpenGL version string: 1.4
```

Sketchup says it needs OpenGL 2.0. I can't remember if using Trusty/14.04 allows OpenGL 2.0 on GMA950 (you could try LiveUSB/CD). Otherwise, I think you're out of luck.

---

### Post by pierreu1 on 2014-08-03
Oh! Thanks! I will try and let people know if I was successful! Thanks!

---

### Post by pierreu1 on 2014-08-04
Ok, last kick at the can!

I found the following intel graphics drivers for Linux on the Intel download, which led me to this [Linux graphics webpage]("https://01.org/linuxgraphics/downloads/2013/2013q1-intel-graphics-stack-release") (I have cut and pasted everything down below). 

It says it supports a 945GM chipset, which I believe I have (from my SYSTEM INFO: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub)

This download is supposed to upgrade the openGL version to 3.0. However, I have a 3.2 Kernel, but this talks about a 3.8.3 Kernel! Is it safe to upgrade this on Precise Pangolin 12.04? Is the processor I have still an issue?

Thanks!

HTML SOURCES: ([https://01.org/linuxgraphics/downloads/2013/2013q1-intel-graphics-stack-release](https://01.org/linuxgraphics/downloads/2013/2013q1-intel-graphics-stack-release)) from [https://01.org/linuxgraphics/downloads](https://01.org/linuxgraphics/downloads) and from [https://downloadcenter.intel.com/Detail_Desc.aspx?DwnldID=13815&lang=eng&ProdId=2301](https://downloadcenter.intel.com/Detail_Desc.aspx?DwnldID=13815&lang=eng&ProdId=2301))


[B][COLOR=#848484][/COLOR][COLOR=#ff0000][SIZE=4]Linux Graphics webpage info[/SIZE][/COLOR][COLOR=#848484]

[/COLOR]2013Q1 Intel Graphics Stack Release[/B]

**Details**

**Release Date:**

26 Mar 2013

**Version:**


[LIST]
[*]2013Q1
[/LIST]
**Type:**


[LIST]
[*]Stack Release
[/LIST]

**Downloads**

[Kernel - 3.8.2]("https://www.kernel.org/pub/linux/kernel/v3.x/linux-3.8.2.tar.gz")
[Mesa - 9.1]("ftp://freedesktop.org/pub/mesa/9.1/")
[xf86-video-intel - 2.21.3]("http://xorg.freedesktop.org/archive/individual/driver/xf86-video-intel-2.21.3.tar.gz")
[Libdrm - 2.4.42]("http://dri.freedesktop.org/libdrm/libdrm-2.4.42.tar.gz")
[Libva - 1.1.1]("http://www.freedesktop.org/software/vaapi/releases/libva/libva-1.1.1.tar.bz2")
[vaapi intel-driver - 1.0.20]("http://www.freedesktop.org/software/vaapi/releases/libva-intel-driver/libva-intel-driver-1.0.20.tar.bz2")
[Cairo - 1.12.14]("http://cairographics.org/news/cairo-1.12.14/")
[Xserver - 1.13.2.902]("ftp://ftp.x.org/pub/individual/xserver/xorg-server-1.13.2.902.tar.gz")



**Intel 2013Q1 Linux Graphics Stack**


**Components**



[LIST]
[*]Kernel: Linux 3.8.2 [http://www.kernel.org/pub/linux/kernel/v3.x/](http://www.kernel.org/pub/linux/kernel/v3.x/)
[*]3D Driver: Mesa 9.1 [ftp://ftp.freedesktop.org/pub/mesa/9.1/](ftp://ftp.freedesktop.org/pub/mesa/9.1/)
[*]2D Driver: xf86-video-intel 2.21.3 [http://xorg.freedesktop.org/archive/individual/driver/xf86-video-intel-2.21.3.tar.gz](http://xorg.freedesktop.org/archive/individual/driver/xf86-video-intel-2.21.3.tar.gz)
[*]Libdrm: 2.4.42: [http://dri.freedesktop.org/libdrm/libdrm-2.4.42.tar.gz](http://dri.freedesktop.org/libdrm/libdrm-2.4.42.tar.gz)
[*]Libva: 1.1.1 [http://www.freedesktop.org/software/vaapi/releases/libva/libva-1.1.1.tar.bz2](http://www.freedesktop.org/software/vaapi/releases/libva/libva-1.1.1.tar.bz2)
[*]Vaapi-driver-intel: 1.0.20 [http://www.freedesktop.org/software/vaapi/releases/libva-intel-driver/libva-intel-driver-1.0.20.tar.bz2](http://www.freedesktop.org/software/vaapi/releases/libva-intel-driver/libva-intel-driver-1.0.20.tar.bz2)
[*]Cairo: 1.12.14 [http://cairographics.org/news/cairo-1.12.14/](http://cairographics.org/news/cairo-1.12.14/)
[*]X Server: Xorg 1.13.2.902 [ftp://ftp.x.org/pub/individual/xserver/xorg-server-1.13.2.902.tar.bz2](ftp://ftp.x.org/pub/individual/xserver/xorg-server-1.13.2.902.tar.bz2)
[/LIST]

**Release description**


[COLOR=#333333][FONT=ClearSans-Light]The 2013Q1 highlights are: Full Haswell Support, OpenGL ES 3.0 support and many new OpenGL extensions.[/FONT][/COLOR]

**Highlighted new features**


[COLOR=#333333][FONT=ClearSans-Light]New features: Full Haswell support including 2D, 3D and hardware accelerated video decoding, and encoding. OpenGL ES 3.0.[/FONT][/COLOR]
[COLOR=#333333][FONT=ClearSans-Light]Since the last release, there were major improvements and bug fixes in all the areas of our drivers. The following list contains some of the important highlights for features and bug fixes.[/FONT][/COLOR]

**Kernel**



[LIST]
[*]Modeset rework
[*]HSW HDMI audio support
[*]Improved instdone dumping for gen7
[*]Improve mmio error reporting for HSW
[*]GPU Hungs fixes
[*]VLV fixes
[*]DP train fixes
[*]SDVO fixes
[*]HSW stability fixes
[*]IVB FDI B/C fixes
[*]HSW sprite/plane offset fixes
[*]Unified DP/HDMI encoder for HSW
[*]DP support on HSW
[*]HSW VGA fixes
[*]VLV DP support
[*]Panel fitter scaling modes
[*]Panel power improvements
[*]Secure batchbuffer support
[*]IVB 3 pipes fix
[/LIST]

**2D driver**



[LIST]
[*]Enable render acceleration for Haswell GT1/GT2
[*]Prevent 16-bit overflow
[*]Disable RandR hotplug events if Xinerama is enabled
[*]Prevent use of invalid damage pointers when redirecting rendering
[*]Fix the gen4/5 opacity shader
[*]Improve handing of texture fallbacks for 830/845
[*]Tune batch flushing after an operation to an exported surface under a compositor.
[*]Immediately flush in the block handler after a split batch to reduce latency between the two halves of an operation.
[*]Install a fallback config if we fail to install the desired config at VT switch - (IVB 3 pipes fix)
[*]Pin batches to avoid CS incoherence on 830/845
[*]Implement the GNOME Build API.
[*]Explicity prevent ring-switching for synchronized rendering to scanouts (for vsync)
[*]Clip dirty region to slave pixmaps
[*]Enable multi-threaded rasterization of trapezoids and fallback composition
[*]PRIME support for hotplug GPUs and hybrid systems
[*]Support for IvyBridge GT1 machines, aka HD2500 graphics
[*]Stable 830gm/845g support
[*]Make driver more robust against its own failures to submit batches
[*]Fix the UXA render programs for projective transforms on Ivybridge
[/LIST]

**3D driver**



[LIST]
[*]OpenGL ES 3.0 support
[*]GL_ANGLE_texture_compression_dxt3
[*]GL_ANGLE_texture_compression_dxt5
[*]GL_ARB_ES3_compatibility
[*]GL_ARB_internalformat_query
[*]GL_ARB_map_buffer_alignment
[*]GL_ARB_shading_language_packing
[*]GL_ARB_texture_buffer_object_rgb32
[*]GL_ARB_texture_cube_map_array
[*]GL_EXT_color_buffer_float
[*]GL_OES_depth_texture_cube_map
[/LIST]

**Media driver - Libva/Intel-vaapi-driver**


[LIST]
[*]HSW Support
[*]&#376;Decode Support
[LIST]
[*]&#8203;H.264/AVC Decode(Progressive/Interlaced)
[*]VC1 Decode(Progressive)
[*]MPEG2 Decode
[*]JPEG/MJPEG Decode
[/LIST]

[*]AVC Progressive Encode Support
[*]Video Processing
[LIST]
[*]&#8203;Scaling
[*]Sub-picture
[/LIST]
[/LIST]

**Known issues**

[COLOR=#333333][FONT=ClearSans-Light]There are important known fixed bugs and performance improvements coming on newest individual components releases that weren't included in this stack release.[/FONT][/COLOR]

[LIST]
[*]Mesa - 9.1.1 contains important fixes and performance improvements compared to 9.1 validated in this stack
[*]xf86-video-intel 2.21.5 contains important fixes for HSW like "Fix scanline waits for Haswell" and "Fix Haswell CRW PCI-IDs"
[/LIST]
[COLOR=#333333][FONT=ClearSans-Light]All these fixes and improvements will be included and validated only on next stack release 2013Q2.[/FONT][/COLOR]

**Validation Hardware**


[COLOR=#333333][FONT=ClearSans-Light]This release was validated on the following hardware, and part of the test results are published [here]("https://01.org/linuxgraphics/node/78").[/FONT][/COLOR]
[COLOR=#333333][FONT=ClearSans-Light]

[LIST]
[*]Intel® 2013 Core Processor (Haswell)
[*]Intel® HD Graphics 4000 (Ivy Bridge): Core i7 3610QM, Core i7 3770K
[*]Intel® HD Graphics 2500 (Ivy Bridge): Core i5 3550
[*]Intel® HD Graphics 3000 (Sandy Bridge): Core i7 2720QM, Core i7 2630QM, Core i7 2600K, Core i5 2500K
[*]Intel® HD Graphics 2000 (Sandy Bridge): Core i7 2400S
[*]Intel® HD Graphics (Ironlake): Core i5 670, Core i5 520M
[*]GMA 3150 (Pineview): Atom N450
[*]GM45
[*]GM965
[*]Q965
[/LIST]
[/FONT][/COLOR][B][COLOR=#000000][FONT=ClearSans-Light]
[LIST]
[*]945GM
[/LIST]
[/FONT][/COLOR][/B]

---

### Post by Yellow Pasque on 2014-08-04
> This download is supposed to upgrade the openGL version to 3.0
Your hardware only supports 2.0, so Intel is tlaking about more recent GPU's there.

Again, the easiest way to test it is to use Live USB/CD of Ubuntu 14.04/Trusty, which has a recent graphics stack. If glxinfo still reports 1.4 there, then it is not worth altering (and potentially breaking) your Precise installation trying to install unsupported drivers.

---

### Post by pierreu1 on 2014-08-04
Thanks a lot! I will do this as this is indeed the wisest move! Still a bit of a newbie! Thanks for the great advice, Temujin!

---

