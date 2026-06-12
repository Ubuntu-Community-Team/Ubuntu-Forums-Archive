---
title: "rendering much slower on 64bit than 32bit (HDMI 3200/fglrx)"
date: 2008-10-28
forum: x86 64-bit Users
---

### Post by joey101 on 2008-10-28
Hello,

I recently went from 32 bit to 64 bit ubuntu because I ordered more ram. Well, the drawing of my desktop and Software rendering has slowed dramatically. I am using the fglrx drivers just like before and it's all the same hardware (the AMD 780g integrated graphics).

It's only software rendering though; For instance glxgears shows just as fast or even faster than what it was on 32 bit ubuntu - but playing simcity in wine is now impossible due to lowered frame-rate. And the window manager makes it look painful when drawing stuff.

If anyone has any insight on the problem that would be great!

fglrxinfo:
```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3200 Graphics
OpenGL version string: 2.1.7412 Release

```

glxinfo:
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
OpenGL renderer string: ATI Radeon HD 3200 Graphics                                 
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
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two,                
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix,                              
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader,       
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_envmap_bumpmap,                  
    GL_ATI_fragment_shader, GL_ATI_meminfo, GL_ATI_separate_stencil,                
    GL_ATI_texture_compression_3dc, GL_ATI_texture_env_combine3,                    
    GL_ATI_texture_float, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color,             
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract,         
    GL_EXT_compiled_vertex_array, GL_EXT_copy_texture,                              
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object,        
    GL_EXT_gpu_program_parameters, GL_EXT_multi_draw_arrays,                        
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels,                              
    GL_EXT_point_parameters, GL_EXT_rescale_normal, GL_EXT_secondary_color,         
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap,       
    GL_EXT_subtexture, GL_EXT_texgen_reflection, GL_EXT_texture3D,                  
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map,                       
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add,                              
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,                            
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias,                     
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object,                             
    GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, GL_EXT_vertex_array,             
    GL_KTX_buffer_region, GL_NV_blend_square, GL_NV_texgen_reflection,              
    GL_SGIS_generate_mipmap, GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod,       
    GL_WIN_swap_hint, WGL_EXT_swap_control                                          

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x30 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x31 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x33 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x34 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x35 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x36 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x37 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x38 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x39 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x3a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x3b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3f 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x40 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x41 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x42 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x43 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x44 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x45 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x46 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x47 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x48 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x49 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x4a 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x4b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x50 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x51 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x52 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x53 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x54 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x55 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x56 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x57 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x59 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x5a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x5b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x60 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x61 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x62 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x63 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x64 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x65 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x66 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x67 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x68 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x69 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x6a 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x6b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x6c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x6d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x6e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x6f 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x70 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x71 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x72 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x85 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  8 1 Ncon

```


Thanks!
Joey

---

### Post by markbuntu on 2008-10-29
You can try some of the tweaks here:

[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

Please note that these are unofficial and some of them do not work with all cards or all drivers.

These will probably help you a lot though

Option "XAANoOffscreenPixmaps" "on" 
Option "UseFastTLS" "1" 
Option "BackingStore" "on"
Option "TexturedVideo" "on" 
Option "VideoOverlay" "off"
Option "OpenGLOverlay" "off"

Under Section "Screen":
DefaultDepth 24

Under Section "DRI":
Mode 0666

Under Section "Extensions": ->See Note 5 for details...
Option "RENDER" "Enable"
Option "DAMAGE" "Enable"
Option "Composite" "Enable"

---

### Post by joey101 on 2008-10-29
My problem isn't with graphics acceleration, that works just as good or better than on my 32 bit OS. My problem is the software renderer. For instance if I enable compize-fusion everything is much more responsive and draws faster apposed to it being off; which is rather backwards.

---

### Post by joey101 on 2008-10-30
Does anyone else not have this problem? I'd really like to be able to use my full 4 GB of ram

---

