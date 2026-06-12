---
title: "32bit Chroot GLX problems"
date: 2007-02-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by mrbrdo on 2007-02-27
Stdout says a thousand words:

Not in chroot:
```
$ glxinfo | grep GL_EXT_framebuffer_object
    GL_EXT_framebuffer_object, GL_EXT_gpu_program_parameters,
$ glxinfo | grep pbuffer
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
```

In chroot:
```
(mychroot) $ glxinfo | grep GL_EXT_framebuffer_object
(mychroot) $ glxinfo | grep pbuffer
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,
    GLX_SGIX_pbuffer, GLX_EXT_texture_from_pixmap
```

So my question is, why there are some glx modules not available in my 32bit chroot, while they are available outside of it? I use "dchroot -d" to enter mychroot. Note: 3D apps run in chroot, but without support of the modules which are suddenly not available inside the chroot.
Also, in chroot it does not support direct rendering while outside of it it does. I use beryl sometimes, but it does not matter here if i use it or not (i have a session set up for beryl and without (kwin), but it doesn't make any difference except that with beryl the 3d apps run much slower). I use the "new" nvidia setup for beryl without xgl or aiglx btw. But when i am trying the glxinfo i am not using beryl or anything special, only kwin (KDE) and the nvidia drivers which work with beryl also.

Here is the full extensions list outside of chroot:
```
GL_ARB_color_buffer_float GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_half_float_pixel GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_texture_float GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_depth_bounds_test GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_framebuffer_object GL_EXT_gpu_program_parameters GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_sRGB GL_EXT_timer_query GL_EXT_vertex_array GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_copy_depth_to_color GL_NV_depth_clamp GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_fragment_program2 GL_NV_framebuffer_multisample_coverage GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_texgen_reflection GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_NV_vertex_program3 GL_NVX_conditional_render GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum
```

Here is the full extensions list in chroot:
```
GL_ARB_depth_texture GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_imaging GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_program GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_ATI_texture_float GL_ATI_texture_mirror_once GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_NV_blend_square GL_NV_copy_depth_to_color GL_NV_depth_clamp GL_NV_fog_distance GL_NV_fragment_program_option GL_NV_fragment_program2 GL_NV_light_max_exponent GL_NV_multisample_filter_hint GL_NV_texgen_reflection GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_rectangle GL_NV_vertex_program2_option GL_NV_vertex_program3 GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_multi_draw_arrays GL_SUN_slice_accum
```

**EDIT: SOLUTION: You need to install THE SAME graphic card drivers as you are using on the x64 system (outside of the chroot).** The same version, different architecture. For me it was just "sudo apt-get install nvidia-glx".

Thanks!

---

### Post by Kilz on 2007-02-27
Why on earth are you using a chroot?

---

### Post by mrbrdo on 2007-02-27
What kind of a question in the name of god is that?
I'm compiling some apps for 32-bit in a 32-bit chroot because my main arch is x64.

Re

---

### Post by Kilz on 2007-02-27
> **mrbrdo said:**
> What kind of a question in the name of god is that?
I'm compiling some apps for 32-bit in a 32-bit chroot because my main arch is x64.

Re

Its a good question, some people think they need to use a chroot to run 32bit applications.

---

### Post by NickK1066 on 2007-02-28
I'm assuming you've tried -m32 and disabling any multilib support?

I've had problems in the past compiling some badly written 32bit applications with precompiled libraries. I've solved with configure's --disable-multilib flag.

---

### Post by mrbrdo on 2007-02-28
Like i said, installing the graphics card drivers fixed the problem.
Can't say glxinfo is badly written, so.. :)

---

