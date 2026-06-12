---
title: "Unrecoverable graphics error in Guild Wars (ATI, Hardy)"
date: 2008-05-09
forum: Wine
---

### Post by WiFlag on 2008-05-09
Some background: I ran Guild Wars fine in Gutsy using -dx8 -dsound and -noshaders, as of Hardy I can't get it to work...

Wine versions: currently running wine-1.0-rc1 but this was happening in 60 and 59 as well. Not sure what version I had in Gutsy, but it was pre-59

GFX: ATI Radeon x800SE, glxgears churns along fine at 7000FPS. I have tried it with the fresh Hardy unsupported ATI drivers, with compiz removed, AIGLX turned off in xorg.conf, and then I installed EnvyNG and let it update fglrx

Other tweaks: I've put in every regedit fix in the Wine AppDB for GW, have tried every permutation of OSS, ALSA, emulation and emulate driver, and have tried Win2000, XP, and 98 compatibility (in Gutsy it ran fine with XP). Also have played with turning off vertex and pixel shaders in winecfg

console output:
$ WINEDEBUG="fixme-all" wine Gw.exe -noshaders -dx8 -nosound -windowed
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
err:ntdll:RtlpWaitForCriticalSection section 0x7e5f2b20 "x11drv_main.c: X11DRV_CritSection" wait timed out in thread 002d, blocked by 001b, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7e5f2b20 "x11drv_main.c: X11DRV_CritSection" wait timed out in thread 0020, blocked by 001b, retrying (60 sec)
err:seh:raise_exception Exception frame is not in stack limits => unable to dispatch exception.

I'm running windowed to avoid the 1-2min timeout while it's crashing and to prevent it from reseting my resolution each time - in full screen I get the GW mouse cursor and a dark gray/blue screen. In windowed I get an error: Guild Wars has encountered an unrecoverable graphics error and must terminate (followed by web links etc).
-dx9 and -dx7 ignore the -windowed switch, and I've been running -nosound to completely eliminate that variable.

So any ideas? If I had to hazard a guess, I'd say Hardy updated the ATI driver and hosed me.

Aside: WoW works in Wine as well as it did in Gutsy, just had to turn off shaders (SET M2UseShaders "0", which I do not remember having to do in Gutsy). I would imagine that -noshaders knocks this out in GW though.

---

### Post by WiFlag on 2008-05-11
Here's a dump of glxinfo:

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
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
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 GT
OpenGL version string: 2.1.7412 Release
OpenGL extensions:
    GL_AMD_performance_monitor, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_shader, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shader_objects, 
    GL_ARB_shading_language_100, GL_ARB_shadow, GL_ARB_shadow_ambient, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_float, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, 
    GL_ATI_draw_buffers, GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader, 
    GL_ATI_meminfo, GL_ATI_separate_stencil, GL_ATI_texture_compression_3dc, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_float, GL_EXT_abgr, 
    GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_framebuffer_object, GL_EXT_gpu_program_parameters, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texgen_reflection, GL_EXT_texture3D, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, GL_EXT_vertex_array, 
    GL_KTX_buffer_region, GL_NV_blend_square, GL_NV_texgen_reflection, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, 
    GL_WIN_swap_hint, WGL_EXT_swap_control

---

### Post by WiFlag on 2008-05-28
In the interest of aiding those who will find this via google, the problem is in fglrx, bug is reported here:
[http://bugs.winehq.org/show_bug.cgi?id=12870](http://bugs.winehq.org/show_bug.cgi?id=12870)

---

### Post by Vakman on 2008-07-19
I have the exact same problem. Have you found a solution?

---

