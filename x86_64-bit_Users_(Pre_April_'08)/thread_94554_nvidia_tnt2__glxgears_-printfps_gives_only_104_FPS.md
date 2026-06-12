---
title: "nvidia tnt2 :: glxgears -printfps gives only 104 FPS is it ok ?"
date: 2005-11-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by jvictor on 2005-11-24
Hi I have ubuntu running on AMD64 + nvidia riva tnt2 i have enabled glxconfig and all .. but does this seem ok ? 

432 frames in 5.0 seconds = 86.326 FPS
516 frames in 5.0 seconds = 103.070 FPS
524 frames in 5.0 seconds = 104.654 FPS
525 frames in 5.0 seconds = 104.877 FPS
525 frames in 5.0 seconds = 104.823 FPS

I remember elive linux 32 bit edition giving me a very high FPS than this.. dont remember the exact FPS though ..

---

### Post by bonzodog on 2005-11-24
I have a similar thing with mine on the amd64 nvidia drivers...framerates are lower than they should be. I've tried searching for an answer to the problem, but have so far failed to find out why...

---

### Post by Padraic on 2005-11-24
I have a Geforce 440Go and get about 2200fps...  Do you have the Nvidia-glx-legacy packages installed through Synaptic?  Those are the support packages for the TNT series of cards...

Oops, forgot to mention, if you run glxinfo in a command line you'll get a bunch of information about which glx drivers your using.  If you scroll back to the top of the output you should see somthing like:

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.3
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control
client glx vendor string: NVIDIA Corporation
client glx version string: 1.3

If  you see Mesa mentioned you're not using hardware acceleration it's all software, which would mean you don't have the correct drivers loaded.

Padraic

---

### Post by jvictor on 2005-11-26
This is the o/p of my glxinfo

juby@powercube:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.3
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control
client glx vendor string: NVIDIA Corporation
client glx version string: 1.3
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_NV_float_buffer
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: RIVA TNT2/AGP/SSE2
OpenGL version string: 1.5.3 NVIDIA 71.74
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_point_parameters, 
    GL_ARB_texture_env_add, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, GL_ARB_window_pos, 
    GL_EXT_texture_env_add, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_compiled_vertex_array, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, 
    GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_vertex_array, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_KTX_buffer_region, GL_NV_blend_square, GL_NV_fog_distance, 
    GL_NV_light_max_exponent, GL_NV_packed_depth_stencil, 
    GL_NV_texgen_reflection, GL_NV_texture_env_combine4, GL_SGIS_multitexture, 
    GL_SUN_slice_accum
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 16 tc  0 16  0 r  y  .  5  6  5  0  4 16  0 16 16 16 16  0 0 None
0x22 16 dc  0 16  0 r  y  .  5  6  5  0  4 16  0 16 16 16 16  0 0 None
0x23 16 tc  0 16  0 r  .  .  5  6  5  0  4 16  0 16 16 16 16  0 0 None
0x24 16 tc  0 16  0 r  y  .  5  6  5  0  4  0  0 16 16 16 16  0 0 None
0x25 16 tc  0 16  0 r  .  .  5  6  5  0  4  0  0 16 16 16 16  0 0 None
0x26 16 dc  0 16  0 r  .  .  5  6  5  0  4 16  0 16 16 16 16  0 0 None
0x27 16 dc  0 16  0 r  y  .  5  6  5  0  4  0  0 16 16 16 16  0 0 None
0x28 16 dc  0 16  0 r  .  .  5  6  5  0  4  0  0 16 16 16 16  0 0 None

juby@powercube:~$ glxgears -printfps
451 frames in 5.0 seconds = 90.167 FPS
527 frames in 5.0 seconds = 105.382 FPS
527 frames in 5.0 seconds = 105.365 FPS
527 frames in 5.0 seconds = 105.280 FPS


Any idea wts happening ?

---

### Post by TmP on 2005-11-26
I don't like to sound like a geezer, but the naked eye can see at about 22 FPS 
:-& ;-) =D> 
Don't fret.

---

### Post by akiro.yamamoto on 2005-11-26
I don't know if this help but this is what I got when I ran that code:
akiro@sysguru:~/e17$ glxgears -printfps
7837 frames in 5.0 seconds = 1567.309 FPS
7903 frames in 5.0 seconds = 1580.488 FPS
7902 frames in 5.0 seconds = 1580.236 FPS
7784 frames in 5.0 seconds = 1556.800 FPS
X connection to :0.0 broken (explicit kill or server shutdown).

And I'm using an old system...
:smile:

---

### Post by akiro.yamamoto on 2005-11-26
And this is the Info that glxinfo provides........


akiro@sysguru:~/e17$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.3
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control
client glx vendor string: NVIDIA Corporation
client glx version string: 1.3
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info,
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync,
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,
    GLX_SGI_swap_control, GLX_NV_float_buffer
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce2 GTS/AGP/3DNOW!
OpenGL version string: 1.5.3 NVIDIA 71.74
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_point_parameters,
    GL_ARB_point_sprite, GL_ARB_shader_objects, GL_ARB_shading_language_100,
    GL_ARB_texture_compression, GL_ARB_texture_cube_map,
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine,
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat,
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix,
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader,
    GL_ARB_window_pos, GL_S3_s3tc, GL_EXT_texture_env_add, GL_EXT_abgr,
    GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_minmax,
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_compiled_vertex_array, GL_EXT_Cg_shader,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays,
    GL_EXT_packed_pixels, GL_EXT_paletted_texture, GL_EXT_pixel_buffer_object,
    GL_EXT_point_parameters, GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shared_texture_palette,
    GL_EXT_stencil_wrap, GL_EXT_texture_compression_s3tc,
    GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod,
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_vertex_array,
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat,
    GL_KTX_buffer_region, GL_NV_blend_square, GL_NV_fence,
    GL_NV_fog_distance, GL_NV_light_max_exponent, GL_NV_packed_depth_stencil,
    GL_NV_pixel_data_range, GL_NV_point_sprite, GL_NV_register_combiners,
    GL_NV_texgen_reflection, GL_NV_texture_env_combine4,
    GL_NV_texture_rectangle, GL_NV_vertex_array_range,
    GL_NV_vertex_array_range2, GL_NV_vertex_program, GL_NV_vertex_program1_1,
    GL_SGIS_generate_mipmap, GL_SGIS_multitexture, GL_SGIS_texture_lod,
    GL_SUN_slice_accum
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x2a 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x2b 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x2e 24 dc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x2f 24 dc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
akiro@sysguru:~/e17$


Hope that helps....
Personally I'd get a better card. TNT2 is a little oldschool......
I'm thinking of doing a complete upgrade in the not so distant future....

---

### Post by bonzodog on 2005-11-26
I don't quite know why this is, but beacause I played a lot with my ubuntu install, I decided to do a clean re-install off the ship-it CD and I am now getting much better fps rates with the nvidia drivers than I did before.

---

