---
title: "Installation issues."
date: 2008-12-05
forum: x86 64-bit Users
---

### Post by whyisitalwaysme on 2008-12-05
Okay im having some problems, today i took a fresh 8.10 ubuntu dvd and ran the installer. it ran perfectly with no errors and i booted into ubuntu.

I did find however that my boot time was very long, so i removed the splash parameter in grubs menu.1st, which solved it bringing it down from 10 minutes to about 1 minute. 

I then installed all updates from the update manager. I now have 2 kernels one is 9 and the other 7. Im using the 9 and i assume the 7 is there just incase 9 screws it up (which it has).

Its now slow again. I re-removed the splash argument but the problem is different this time. Im getting "this device is not 8139 compatible, use 8139too instead" or words to that effect and it also freezes for a good 5 minutes while waiting for "Disabling IRQ19" after which it prints [fail] in red and boots normally.

Also compiz does not function correctly (see compiz log below). not only can i not access the advanced visual effects settings like on other systems (menu option just isnt there) but things like icons from the alt tab switch arent there. i installed the fglrx drivers through ubuntu hardware device interface.

ALL i have done since fresh installing was install fglrx drivers and run the update and reboot.

Any ideas/suggestions welcome.

Relevant information:

Compiz -

```

Checking for Xgl: [1] 5941
callum@Ubuntu:~$ not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```

```

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
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
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3450
OpenGL version string: 2.1.8087 Release
OpenGL shading language version string: 1.20
OpenGL extensions:
    GL_AMD_performance_monitor, GL_ARB_color_buffer_float, 
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_draw_instanced, 
    GL_ARB_fragment_program, GL_ARB_fragment_shader, GL_ARB_half_float_pixel, 
    GL_ARB_half_float_vertex, GL_ARB_instanced_arrays, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shader_objects, 
    GL_ARB_shader_texture_lod, GL_ARB_shading_language_100, GL_ARB_shadow, 
    GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_float, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, 
    GL_ATI_draw_buffers, GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader, 
    GL_ATI_meminfo, GL_ATI_separate_stencil, GL_ATI_texture_compression_3dc, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_float, GL_EXT_abgr, 
    GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_equation_separate, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_compiled_vertex_array, GL_EXT_copy_texture, 
    GL_EXT_depth_buffer_float, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXT_framebuffer_object, GL_EXT_gpu_program_parameters, 
    GL_EXT_gpu_shader4, GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_float, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texgen_reflection, GL_EXT_texture3D, 
    GL_EXT_texture_compression_latc, GL_EXT_texture_compression_rgtc, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, 
    GL_EXT_texture_shared_exponent, GL_EXT_vertex_array, GL_KTX_buffer_region, 
    GL_NV_blend_square, GL_NV_texgen_reflection, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_WIN_swap_hint, 
    WGL_EXT_swap_control

```

---

