---
title: "ATI X600 Direct Rendering: No"
date: 2009-01-22
forum: x86 64-bit Users
---

### Post by nienaber on 2009-01-22
I have been looking around on the forums for the possible fix to my problem but I have been rather unsuccessfully at getting it to work. I have had direct rendering working on this machine but a couple of updates later it seems to be somewhat broken.

My machine: Linux 2.6.24-19-generic #1 SMP x86_64 GNU/Linux
Kubuntu: 8.04.2
Video card: ATI x600
Software: Catalyst Version 8.53
2D Driver Version 8.56.v4

```
name of display: :0.0
display: :0  screen: 0
**direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)**
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method,
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe,
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method,
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control,
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group,
    GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method,
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
    GLX_EXT_texture_from_pixmap
[B]OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)[/B]
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program,
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture,
    GL_ARB_occlusion_query, GL_ARB_point_parameters, GL_ARB_point_sprite,
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp,
    GL_ARB_texture_compression, GL_ARB_texture_cube_map,
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine,
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3,
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two,
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_program,
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color,
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate,
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements,
    GL_EXT_fog_coord, GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays,
    GL_EXT_packed_pixels, GL_EXT_paletted_texture, GL_EXT_point_parameters,
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs,
    GL_EXT_shared_texture_palette, GL_EXT_stencil_wrap, GL_EXT_subtexture,
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp,
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias,
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object,
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels,
    GL_ATI_draw_buffers, GL_ATI_texture_env_combine3,
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3,
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate,
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square,
    GL_NV_fragment_program, GL_NV_light_max_exponent, GL_NV_point_sprite,
    GL_NV_texgen_reflection, GL_NV_texture_rectangle, GL_NV_vertex_program,
    GL_NV_vertex_program1_1, GL_SGI_color_matrix, GL_SGI_color_table,
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture,
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x3d 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

Partial output from my Xorg.log.0
```
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(WW) fglrx(0): could not detect X server version (query_status=-1)
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized.
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0x0 FBMappedSize: 0x08000000
(==) fglrx(0): Write-combining range (0xd0000000,0x8000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(2560,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(2560,1024) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 2560 x 7167
(==) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Initialized in-driver Xinerama extension
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
        Screen to screen bit blits
        Solid filled rectangles
        Solid Horizontal and Vertical Lines
        Setting up tile and stipple cache:
                32 128x128 slots
                32 256x256 slots
                16 512x512 slots
(II) fglrx(0): Acceleration enabled

```

I don't understand why mesa is driving the machine when I have ATI installed and initialzed

xorg.conf:

```
Section "ServerLayout"
        Identifier      "Default Layout"
  screen 0 "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
        Load            "glx"
        Load            "dri"
EndSection

Section "ServerFlags"
        Option          "Xinerama"      "off"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "microsoft"
        Option          "XkbLayout"     "us"
        Option          "XkbOptions"    "lv3:menu_switch"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Monitor"
        Identifier      "aticonfig-Monitor[0]-0"
        Option          "VendorName"    "ATI Proprietary Driver"
        Option          "ModelName"     "Generic Autodetecting Monitor"
        Option          "DPMS"  "true"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
       ** Driver          "fglrx"**
EndSection

Section "Device"
        Identifier      "aticonfig-Device[0]-0"
        **Driver          "fglrx"**
        Busid           "PCI:3:0:0"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Configured Video Device"
        Monitor         "Configured Monitor"
        Defaultdepth    24
EndSection

Section "Screen"
        Identifier      "aticonfig-Screen[0]-0"
        Device          "aticonfig-Device[0]-0"
        Monitor         "aticonfig-Monitor[0]-0"
        Defaultdepth    24
        SubSection "Display"
                Viewport        0       0
                Depth   24
        EndSubSection
EndSection

Section "DRI"
        Mode    0666
EndSection

```

---

### Post by martinbaselier on 2009-01-23
Apparently it uses the mesa driver, since it can't load the fglrx. This should make you happy, since at least you have video. Have you tried re-installing the ati-driver, following the instructions on the unofficial ati wiki?
[http://wiki.cchtml.com/index.php/Main_Page]("http://wiki.cchtml.com/index.php/Main_Page")

---

