---
title: "G3 iBook - Graphics Hardware Acceleration?"
date: 2005-12-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by disabled_20220313 on 2005-12-23
Hi,

I am about to install Ubuntu 5.10 onto my Clamshell iBook G3 - But wondered if the ATI Rage Mobility (All 4Mb of it!) is actually supported? 

Would rather know that it is before putting Ubuntu onto the iBook as I dont have the OS X discs to rescue my system should it all go tits up.

Thanks,

---

### Post by Rxke on 2005-12-24
Nothing stellar, but it works.
> direct rendering: yes

(I'm a Clamshel-owner, BTW)

---

### Post by disabled_20220313 on 2005-12-24
Well have you got any tips on getting it to work?

I install ubuntu anyway and it doesnt seem to have enabled DRI. 

To be honest its working OK. But would rather have the extra work not done by my CPU as I only have 300mhz :D

---

### Post by Rxke on 2005-12-24
How do you know it's not working?

I thought > glxinfo  says: yaddayaddayadda....direct rendering:yes yaddayaddayadda....

 so i assumed all was well...

---

### Post by disabled_20220313 on 2005-12-25
Well mine says "Direct Rendering : No" when I put glxinfo in.

Bit annoying really.

If anyone can help here is the full output of glxinfo

```
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method,
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control,
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method,
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_imaging, GL_ARB_multitexture,
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shadow,
    GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar,
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat,
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_window_pos,
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate,
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements,
    GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels,
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_rescale_normal,
    GL_EXT_secondary_color, GL_EXT_separate_specular_color,
    GL_EXT_shadow_funcs, GL_EXT_stencil_two_side, GL_EXT_stencil_wrap,
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle,
    GL_EXT_vertex_array, GL_APPLE_packed_pixels, GL_ATI_texture_env_combine3,
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3,
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate,
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square,
    GL_NV_point_sprite, GL_NV_texgen_reflection, GL_NV_texture_rectangle,
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture,
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x24 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 None
0x25 16 tc  0 24  0 r  y  .  5  6  5  8  0 16  8 16 16 16 16  0 0 None
0x26 16 tc  0 24  0 r  .  .  5  6  5  8  0 16  8 16 16 16 16  0 0 None
0x27 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x28 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 None
0x29 16 dc  0 24  0 r  y  .  5  6  5  8  0 16  8 16 16 16 16  0 0 None
0x2a 16 dc  0 24  0 r  .  .  5  6  5  8  0 16  8 16 16 16 16  0 0 None

```

Looks to me its using MESA instead of an ATI driver. But thats only a guess as I have no idea what I'm looking for.

---

### Post by Rxke on 2005-12-25
weird, where it says OpenGL vendor string: Mesa Project... etc mine says OpenGL... .... VA Linux Systems, Inc."
OpenGL renderer string: Mesa DRI Rage 128 Mobility 20041026 AGP 1x
OpenGL version string: 1.2 Mesa 6.3.2...

---

