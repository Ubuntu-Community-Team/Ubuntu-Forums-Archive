---
title: "half life 2 does NOT respond in wine, please help!!"
date: 2012-09-26
forum: Wine
---

### Post by bigbus on 2012-09-26
Hi everyone.

I installed Half Life 2 recently on steam under wine. 
  
But when I load a game, the game is so slow it doesn't respond to simple keyboard commands or mouse movements (it can take me about 5 minutes just to move my game character forward).

I'm running Ubuntu 12.04 LTS, Wine 1.4, OpenGL version string: 1.4 Mesa 8.0.2

Direct rendering of my OpenGL is enabled because I checked using the glxinfo|more command.

My computer has a dual core processor, 1GB ram and a Intel 945GME graphics card. And I know this works with Half Life 2 because I've run the game at a 5-15 FPS on Windows before I changed to ubuntu.

Half Life 2 is currently installed under this directory:

/home/kie/.local/share/wineprefixes/steam/drive_c/Program Files/Steam/steamapps/final_orange_box/half-life 2

I ran a shortcut of half-life 2 through a terminal and got this:
```
fixme:exec:SHELL_execute flags ignored: 0x00000100
kie@zoostorm:~$ fixme:advapi:EventRegister {47a9201e-73b0-42ce-9821-7e134361bc6f}, 0x3f005160, 0x3f036b20, 0x3f036b18
fixme:advapi:EventRegister {58a9201e-73b0-42ce-9821-7e134361bc70}, 0x3f005160, 0x3f036b58, 0x3f036b50
fixme:advapi:EventRegister {3fa9201e-73b0-43fe-9821-7e145359bc6f}, 0x3f005160, 0x3f036ae8, 0x3f036ae0
fixme:advapi:EventRegister {1432afee-73b0-42ce-9821-7e134361b433}, 0x3f005160, 0x3f036b90, 0x3f036b88
fixme:advapi:EventRegister {4372afee-73b0-42ce-9821-7e134361b519}, 0x3f005160, 0x3f036bc8, 0x3f036bc0
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
fixme:iphlpapi:NotifyAddrChange (Handle 0x493d72c, overlapped 0x4754d80): stub
fixme:winsock:WSALookupServiceBeginW (0x493d82c 0x00000ff0 0x493d874) Stub!
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
err:ole:CoGetClassObject class {77f10cf0-3db5-4966-b520-b7c54fd35ed6} not registered
err:ole:CoGetClassObject no class object {77f10cf0-3db5-4966-b520-b7c54fd35ed6} could be created for context 0x1
fixme:wbemprox:wbem_locator_ConnectServer 0x1cda88, L"ROOT\\CIMV2", (null), (null), (null), 0x00000080, (null), (nil), 0x6d1c4cc)
err:ole:CoGetClassObject class {dff32fea-3331-48da-a272-ccfc238695be} not registered
err:ole:CoGetClassObject class {dff32fea-3331-48da-a272-ccfc238695be} not registered
err:ole:create_server class {dff32fea-3331-48da-a272-ccfc238695be} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {dff32fea-3331-48da-a272-ccfc238695be} could be created for context 0x17
fixme:winhttp:WinHttpDetectAutoProxyConfigUrl discovery via DHCP not supported
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:win:RegisterDeviceNotificationA (hwnd=0x100b6, filter=0x33d3ac,flags=0x00000004) returns a fake device notification handle!
fixme:win:EnumDisplayDevicesW ((null),0,0x33b944,0x00000000), stub!

```Help is greatly needed and I would appreciate anyone who takes the time out of their day to help me. :KS

---

### Post by oldos2er on 2012-09-26
Moved to Wine.

---

### Post by bigbus on 2012-10-06
OK everyone, ignore my previous message, I think it's just ubuntu isn't utilising my graphics properly. (Intel 945GME)

I've checked glxinfo to see if there are any problems, but there's nothing...

What can I do now?

---

### Post by thatguruguy on 2012-10-06
I suppose it would be too much trouble to post the output of glxinfo here.

If you do decide to do so, wrap it in [CODE] tags.

---

### Post by bigbus on 2012-10-06
All right, after more searching the internet on the issue, I followed this article: [http://askubuntu.com/questions/185506/how-may-i-know-if-my-devices-have-their-drivers-installed](http://askubuntu.com/questions/185506/how-may-i-know-if-my-devices-have-their-drivers-installed) and created a sysinfo.txt file.

My sysinfo.txt file says  ```
*-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express
```

Which according to the article means I haven't got a driver for my graphics card. I think this has been the problem all along, as since I got ubuntu there have been no propriety drivers available on my system and I have not been unable to find any open source drivers on the internet...

So how can I can find these drivers??

> **thatguruguy said:**
> I suppose it would be too much trouble to post the output of glxinfo here.

If you do decide to do so, wrap it in ```
 tags.
Thanks for your reply.

Even though the glxinfo says everything's fine, here it is anyway:

[CODE]name of display: :0

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
OpenGL renderer string: Mesa DRI Intel(R) 945GME x86/MMX/SSE2
OpenGL version string: 1.4 Mesa 8.0.2
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
    GL_NV_texgen_reflection, GL_NV_texture_env_combine4, GL_S3_s3tc, 
    GL_SUN_multi_draw_arrays, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_EXT_framebuffer_object, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_MESA_window_pos, GL_NV_packed_depth_stencil, 
    GL_NV_texture_rectangle, GL_NV_vertex_program, GL_ARB_depth_texture, 
    GL_ARB_shadow, GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_window_pos, GL_EXT_stencil_two_side, GL_EXT_texture_cube_map, 
    GL_NV_vertex_program1_1, GL_APPLE_packed_pixels, 
    GL_APPLE_vertex_array_object, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_shader, GL_ARB_shader_objects, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ATI_draw_buffers, 
    GL_ATI_texture_env_combine3, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_ARB_half_float_pixel, 
    GL_ARB_point_sprite, GL_ARB_shading_language_100, GL_ARB_sync, 
    GL_ARB_texture_non_power_of_two, GL_ARB_vertex_buffer_object, 
    GL_ATI_blend_equation_separate, GL_EXT_blend_equation_separate, 
    GL_OES_read_format, GL_ARB_pixel_buffer_object, GL_ARB_texture_rectangle, 
    GL_EXT_pixel_buffer_object, GL_EXT_texture_compression_dxt1, 
    GL_EXT_texture_rectangle, GL_ARB_framebuffer_object, 
    GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXT_packed_depth_stencil, GL_APPLE_object_purgeable, 
    GL_ARB_vertex_array_object, GL_ATI_separate_stencil, 
    GL_EXT_gpu_program_parameters, GL_OES_EGL_image, GL_ARB_copy_buffer, 
    GL_ARB_map_buffer_range, GL_EXT_separate_shader_objects, 
    GL_ARB_ES2_compatibility, GL_ARB_draw_elements_base_vertex, 
    GL_ARB_explicit_attrib_location, GL_ARB_provoking_vertex, 
    GL_ARB_sampler_objects, GL_EXT_provoking_vertex, GL_ARB_robustness

32 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x022 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x08c 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x08d 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x08e 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x08f 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x090 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x091 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x092 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x093 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x094 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x095 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x096 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x097 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x098 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x099 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x09a 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x09b 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x09c 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x09d 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x09e 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x09f 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a0 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a1 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a2 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a3 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0a4 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0a5 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a6 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0a7 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0a8 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x05b 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None

48 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x05c  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x05d  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x05e  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x05f  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x060  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x061  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x062 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x063 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x064 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x065 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x066 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x067 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x068 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x069 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x06a 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x06b 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x06c 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x06d 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x06e  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x06f  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x070 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x071 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x072 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x073 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x074  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x075  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x076  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x077  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x078  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x079  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x07a 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x07b 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x07c 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x07d 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x07e 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x07f 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x080 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x081 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x082 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x083 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x084 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x085 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x086  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x087  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x088 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x089 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x08a 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x08b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow

```

---

### Post by thatguruguy on 2012-10-06
> **bigbus said:**
> 
My sysinfo.txt file says  ```
*-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express
```Which according to the article means I haven't got a driver for my graphics card. I think this has been the problem all along, as since I got ubuntu there have been no propriety drivers available on my system and I have not been unable to find any open source drivers on the internet...

So how can I can find these drivers??


No. Look under display:0, unless you have more than one monitor hooked up. Computers count from 0, not from 1.

I think the problem is here:

> **bigbus said:**
> 
```

OpenGL version string: 1.4 Mesa 8.0.2

```

That's an old version of OpenGL; the laptop I have that uses an integrated intel GPU (GM965/GL960) runs OpenGL 2.1.

You *may* have some luck trying to get updated drivers by installing the ppa available [here]("https://launchpad.net/~ubuntu-x-swat/+archive/intel-graphics-updates"). Doing a quick google search on your hardware, however, does not return any results that make me particularly hopeful.

---

