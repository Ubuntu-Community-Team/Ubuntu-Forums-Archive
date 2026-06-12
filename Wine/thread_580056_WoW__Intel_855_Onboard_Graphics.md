---
title: "WoW  Intel 855 Onboard Graphics"
date: 2007-10-18
forum: Wine
---

### Post by The Frozen Mage on 2007-10-18
Hello everyone

Using a Laptop with an Intel 855 Intergrated Graphics. 

GlxGears returns average 3000fps.

Have tried to load World of Warcraft and had serious graphic issues.

Opengl - Using the Opengl command and the suggested tweaks from the Ubuntu installation guide

Login screen Is approx two thirds black screen and very jerky. 
The Chara screen is a serious of coloured shapes and impossible to make out.

Inside a building an inn, or inside a major city for example Ironforge all the graphics are loaded, but lines run down from top of screen to any chat boxes opened, and no text is displayed. FPS hits max of 9

Outside the ground texture is extremely blocky and impossible to identify differences between roads, ground and rivers. FPS hits max of 4

D3D - Taking out the set opengl command from the config file 

Login screen works normally, no problems
Chara screen works normally, no problems

Inside inn no problems FPS hits 11

Outside same blocky indistinguishable terrain.

For both Opengl and D3d attempts all video settings are set to lowest possible variable.

 glxinfo 

name of display: :0.0 
display: :0 screen: 0 
direct rendering: Yes 
server glx vendor string: SGI 
server glx version string: 1.2 
server glx extensions: 
GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group 
client glx vendor string: SGI 
client glx version string: 1.4 
client glx extensions: 
GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap 
GLX version: 1.2 
GLX extensions: 
GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_make_current_read, 
GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group 
OpenGL vendor string: Tungsten Graphics, Inc 
OpenGL renderer string: Mesa DRI Intel(R) 852GM/855GM 20061017 x86/MMX/SSE2 
OpenGL version string: 1.3 Mesa 6.5.2 
OpenGL extensions: 
GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
GL_ARB_point_parameters, GL_ARB_texture_border_clamp, 
GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
GL_ARB_vertex_program, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, 
GL_EXT_blend_color, GL_EXT_blend_equation_separate, 
GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
GL_EXT_clip_volume_hint, GL_EXT_cull_vertex, GL_EXT_compiled_vertex_array, 
GL_EXT_convolution, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
GL_EXT_fog_coord, GL_EXT_histogram, GL_EXT_multi_draw_arrays, 
GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset, 
GL_EXT_rescale_normal, GL_EXT_secondary_color, 
GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle, 
GL_EXT_vertex_array, GL_3DFX_texture_compression_FXT1, 
GL_APPLE_client_storage, GL_APPLE_packed_pixels, 
GL_ATI_blend_equation_separate, GL_IBM_rasterpos_clip, 
GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_MESA_window_pos, 
GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_texture_rectangle, 
GL_NV_texgen_reflection, GL_NV_vertex_program, GL_NV_vertex_program1_1, 
GL_OES_read_format, GL_SGI_color_matrix, GL_SGI_color_table, 
GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays 

visual x bf lv rg d st colorbuffer ax dp st accumbuffer ms cav 
id dep cl sp sz l ci b ro r g b a bf th cl r g b a ns b eat 
---------------------------------------------------------------------- 
0x23 24 tc 0 32 0 r y . 8 8 8 8 0 0 0 0 0 0 0 0 0 None 
0x24 24 tc 0 32 0 r . . 8 8 8 8 0 0 0 0 0 0 0 0 0 None 
0x25 24 tc 0 32 0 r y . 8 8 8 8 0 24 8 0 0 0 0 0 0 None 
0x26 24 tc 0 32 0 r . . 8 8 8 8 0 24 8 0 0 0 0 0 0 None 
0x27 24 tc 0 32 0 r y . 8 8 8 8 0 0 0 16 16 16 16 0 0 Slow 
0x28 24 tc 0 32 0 r . . 8 8 8 8 0 0 0 16 16 16 16 0 0 Slow 
0x29 24 tc 0 32 0 r y . 8 8 8 8 0 24 8 16 16 16 16 0 0 Slow 
0x2a 24 tc 0 32 0 r . . 8 8 8 8 0 24 8 16 16 16 16 0 0 Slow 
0x2b 24 dc 0 32 0 r y . 8 8 8 8 0 0 0 0 0 0 0 0 0 None 
0x2c 24 dc 0 32 0 r . . 8 8 8 8 0 0 0 0 0 0 0 0 0 None 
0x2d 24 dc 0 32 0 r y . 8 8 8 8 0 24 8 0 0 0 0 0 0 None 
0x2e 24 dc 0 32 0 r . . 8 8 8 8 0 24 8 0 0 0 0 0 0 None 
0x2f 24 dc 0 32 0 r y . 8 8 8 8 0 0 0 16 16 16 16 0 0 Slow 
0x30 24 dc 0 32 0 r . . 8 8 8 8 0 0 0 16 16 16 16 0 0 Slow 
0x31 24 dc 0 32 0 r y . 8 8 8 8 0 24 8 16 16 16 16 0 0 Slow 
0x32 24 dc 0 32 0 r . . 8 8 8 8 0 24 8 16 16 16 16 0 0 Slow 
0x4b 32 tc 0 32 0 r . . 8 8 8 8 0 0 0 0 0 0 0 0 0 Ncon 

Does anyone use the same card and can give me advice on how to get Opengl working properly?

Is there anyway to increase the 855's Ram usage (under windows it could go upto 64mb video, no idea what it's currently running at).

Tried to install the Intel driver from the Package Manager, and everytime I tried to start WOW I was kicked out to the login screen.

Latest Wine installed, using latest 7.04 upgrade.

Can anyone help at all please. Really missing my gametime and need to get a fix of Arcane blasting. At this point I am seriously thinking of going back to XP and that is so annoying when I like Ubuntu for everything else.

---

### Post by LauraSakura on 2008-02-11
I also got it working in XP but in Ubuntu the graphics were all distorted. I think that I read somewhere that the Intel drivers for Linux don't yet have all the 3D things implimented correctly. Even in Windows though, with this graphics card it is very hard for me to play since there is so much mouse lag (unable to select hardware mouse and smooth mouse because the card does not support it, i believe). Do other games run OK for you? It would be nice to see if a solution is found for the intel drivers because I tried as well, and ended up with weird colors everywhere, and missing polygons and such. In Windows did you get the really bad mouse lag as well? 

UPDATE:
I don't remember where I read it, but the main problem with the mouse lag is due to the the 855GM's inability to support hardware mouse and smooth mouse. Also... something seems strange with the way it reports FPS. Sometimes it will say that I am only getting 10 fps, but it seems less jerky than when my desktop computer reports 20fps. (in XO)  Now for in Ubuntu... even though the guides say to use the openGL switch... On my desktop it worked MUCH better in D3D Mode.  
I have mixed results with this card...WoW will run in XP but not Ubuntu...... but on the flipside, Second Life will run in Ubuntu but not in XP.

---

