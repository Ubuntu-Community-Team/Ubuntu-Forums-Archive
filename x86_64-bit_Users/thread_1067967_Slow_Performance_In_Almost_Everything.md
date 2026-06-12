---
title: "Slow Performance In Almost Everything"
date: 2009-02-12
forum: x86 64-bit Users
---

### Post by ku5165 on 2009-02-12
I am not getting satisfactory performance from Ubuntu,

My system is 
Intel Core 2 Duo 1.6ghz
1gb ram
100gb hdd
intel gma 950 graphics
Ubuntu Intrepid Ibex 8.10 with all latest updates

Now for details:

1. The processor fan keeps kicking on even if i just want to open firefox, or load a new page in it.
2. Also i tried to run Nexuiz or Tuxcart or 3d pool game, however i get VERY  slow fps, (maybe around 1-2).
3. Sometimes the card reader does not work (not a real big one, the above two are.)

I have read around the forum that the main cause might be my graphics driver. If someone can tell me how this can be reinstalled or changed id love to give it a try. Also a fix for making the fan start up less often would also be helpful as my laptop fan is TOO loud. 
Thanks A lot,
Ku

P.s. I am pretty advanced with computers, however being new to linux platform i need some help (step by step would be nice)

---

### Post by Cope57 on 2009-02-12
Sounds like a simple video driver install.
But since I use a Nvidia card and driver, I am sure someone will be here shortly to help with your video card.

**Edit:** To bad this thread is not called, "Need help installing intel gma 950 graphics driver".
I would have not come in here if it had nothing to do with me, but good luck anyway.

---

### Post by ku5165 on 2009-02-12
Im sorry bout that, i need help with other aspects also, ill change it to something more appropriate.
Thanks for the help though

---

### Post by joey-elijah on 2009-02-12
[LIST]
[*]The GMA950 shouldn't be as bad as that and should run SuperTuxKart, compiz etc with total ease. As someone else suggested, it's possibly a driver issue. I would suggest installing **"envyng"** which will find the correct driver for you *(Go to Synpatic Package manager and search for it in there, if you can't find it then a quick google will.)*
[/LIST]

[LIST]
[*] You fan switching on due to simple strains is also probably somewhat related to your graphics issue; by the GPU not working it puts extra strain on the CPU. My processor fan, for some reason, always stays on. I have an AMDx2 @3.Ghz and a fancy pants cooler fan (which i replaced the stock one with thinking it was just a crap fan, but no. Ubuntu still needs to have ti whirring 24/7. good job it's silent.)
[/LIST]

[LIST]
[*]Your cardreader may just be due to it not always being mounted.I assume it's internal. Run the command: "lspci" in a terminal (without quotemarks) and post the response back here.
[/LIST]

---

### Post by ku5165 on 2009-02-12
thanks a lot buddy i will try that to see if it works.
Let you know very soon

---

### Post by ku5165 on 2009-02-12
it turns out that EnvyNG is only for Nvida graphics and ATI graphics, is there anything like such for Intel Graphics?? Or a procedure to install a new graphics driver that is known to work.
Thanks Again for all your help.

---

### Post by ku5165 on 2009-02-13
I have yet to get the problem fixed, can someone please tell me how to reinstall the graphics driver, as I am beginning to think it is what is causing the problem. If i can fix that they maybe the system will run more efficiently.
Thanks in Advance,
Ku

---

### Post by Yellow Pasque on 2009-02-13
Can you post the output of:
```
glxinfo
cat /var/log/Xorg.0.log
```
Please use [ code ][ /code ] blocks, (or better yet [http://ubuntu.pastebin.com/](http://ubuntu.pastebin.com/) ).

You could use this command to reinstall the intel video package:
```
sudo apt-get --reinstall xserver-xorg-video-intel
```
I recommend booting into "recovery mode" and dropping to a root prompt to perform the command. (You have to hit 'Esc' after your BIOS does its POST and boots your hard disk, so you can get to the GRUB menu and choose the recovery kernel).

---

### Post by soxs on 2009-02-13
I doubt it's a problem with your intel GMA driver. It's integrated into the mesa stack (correct me if that is wrong) so it is part of the kernel and or X.org, but for goods sake do:

```
sudo apt-get install xserver-xorg-video-intel
```and  append the output from
```

ps ax | grep tracker
```It's more likly to be busy I/O than a intel integrated chipset. I have an 9xx one in my laptop aswell and inteprid x86_64 works pretty fine.

Edit. Though spinning up fan would suggest CPU/GPU temp increment and thus more load...
How does your desktop behave? Do you get a delay when clicking or do you have "sqasihy" mouse pointers (so your refresh rate is VERY low)? You may explain this alittle deeper

---

### Post by ku5165 on 2009-02-13
> **Temüjin said:**
> Can you post the output of:
```
glxinfo
cat /var/log/Xorg.0.log
```
Please use [ code ][ /code ] blocks, (or better yet [http://ubuntu.pastebin.com/](http://ubuntu.pastebin.com/) ).

You could use this command to reinstall the intel video package:
```
sudo apt-get --reinstall xserver-xorg-video-intel
```
I recommend booting into "recovery mode" and dropping to a root prompt to perform the command. (You have to hit 'Esc' after your BIOS does its POST and boots your hard disk, so you can get to the GRUB menu and choose the recovery kernel).

This is what I get when I do the above command:
It seems as if the driver is ok, then that would mean that something else is wrong...:(
Also when I try to reinstall this error comes up:
```
 E: Invalid operation xserver-xorg-video-intel 
```
```

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
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.2
OpenGL shading language version string: 1.10
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, 
    GL_ARB_half_float_pixel, GL_ARB_imaging, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shader_objects, 
    GL_ARB_shading_language_100, GL_ARB_shadow, GL_ARB_shadow_ambient, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_compiled_vertex_array, GL_EXT_convolution, 
    GL_EXT_copy_texture, GL_EXT_depth_bounds_test, GL_EXT_draw_range_elements, 
    GL_EXT_framebuffer_object, GL_EXT_framebuffer_blit, GL_EXT_fog_coord, 
    GL_EXT_gpu_program_parameters, GL_EXT_histogram, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, 
    GL_EXT_paletted_texture, GL_EXT_pixel_buffer_object, 
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_shadow_funcs, GL_EXT_shared_texture_palette, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, 
    GL_EXT_vertex_array, GL_APPLE_packed_pixels, GL_APPLE_vertex_array_object, 
    GL_ATI_blend_equation_separate, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATI_fragment_shader, 
    GL_ATI_separate_stencil, GL_IBM_multimode_draw_arrays, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_program_debug, 
    GL_MESA_resize_buffers, GL_MESA_texture_array, GL_MESA_ycbcr_texture, 
    GL_MESA_window_pos, GL_NV_blend_square, GL_NV_fragment_program, 
    GL_NV_light_max_exponent, GL_NV_point_sprite, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_NV_vertex_program, GL_NV_vertex_program1_1, 
    GL_OES_read_format, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGI_texture_color_table, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SGIX_shadow, 
    GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

3 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x44 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None

32 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x45  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x46  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x47  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x48  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x49  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  8  0  0  0  0  0 0 None
0x4a  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  8 16 16 16 16  0 0 Slow
0x4b  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  8  0  0  0  0  0 0 None
0x4c  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  8 16 16 16 16  0 0 Slow
0x4d  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x4e  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x4f  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x50  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x51  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x52  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x53  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x54  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x55  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x56  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x57  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x58  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x59  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  8  0  0  0  0  0 0 None
0x5a  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  8 16 16 16 16  0 0 Slow
0x5b  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  8  0  0  0  0  0 0 None
0x5c  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  8 16 16 16 16  0 0 Slow
0x5d  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x5e  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x5f  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x60  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x61  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x62  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x63  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x64  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow

```

---

### Post by ku5165 on 2009-02-13
> **soxs said:**
> I doubt it's a problem with your intel GMA driver. It's integrated into the mesa stack (correct me if that is wrong) so it is part of the kernel and or X.org, but for goods sake do:

```
sudo apt-get install xserver-xorg-video-intel
```and  append the output from
```

ps ax | grep tracker
```It's more likly to be busy I/O than a intel integrated chipset. I have an 9xx one in my laptop aswell and inteprid x86_64 works pretty fine.

Edit. Though spinning up fan would suggest CPU/GPU temp increment and thus more load...
How does your desktop behave? Do you get a delay when clicking or do you have "sqasihy" mouse pointers (so your refresh rate is VERY low)? You may explain this alittle deeper

I am going to try those commands and see if anything improves.
My desktop "seems" fine, when i start playing videos it gets choppy at times, I can notice the slow speeds VERY easily in games, SuperTUXkart and Nexuiz, and Billard-GL seem to be lagging, which would indicate something is wrong because in such games I am exceeding the recommended amount of hardware.

Everything seems running fine, no mouse pointer issue, refresh rate anything, but then I do not understand why the rest is not workings as great.

Thanks for all of your replies, I am going to reboot and try the above commands. 
Ku

this is my output:
```
  5539 ?        S      0:00 tracker-applet
 5543 ?        SNl    0:00 trackerd
18308 pts/0    S+     0:00 grep tracker

```

---

### Post by soxs on 2009-02-14
Ok, goto session mangment, and disable tracker from autosrtaing, when it indexes your files, {everything} gets slow.
If that won't help, well.. then lets see what it could be.

---

### Post by ku5165 on 2009-02-14
> **soxs said:**
> Ok, goto session mangment, and disable tracker from autosrtaing, when it indexes your files, {everything} gets slow.
If that won't help, well.. then lets see what it could be.
I tried disabling tracker and restarting (btw what is tracker??) however the same problem is still there :(.
Please help  me resolve this.

---

### Post by Yellow Pasque on 2009-02-15
> OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
This is part of your problem - you're using software video acceleration, which is relatively slower than using video hardware accel. It also makes heavy use of the CPU.
Vendor should say "Tungsten Graphics" and renderer string should say something like "Mesa DRI Intel", and not "Software Rasterizer".
To check if it's a permissions error, could you post the output of:
```
sudo LIBGL_DEBUG=verbose glxinfo
```

EDIT:
> E: Invalid operation xserver-xorg-video-intel
Sorry, there's no reinstall option for apt (my fault). You would have to remove/purge and then install, but I doubt that will help you. I've never seen a direct rendering issue solved that way.

---

### Post by ku5165 on 2009-02-15
> **Temüjin said:**
> This is part of your problem - you're using software video acceleration, which is relatively slower than using video hardware accel. It also makes heavy use of the CPU.
Vendor should say "Tungsten Graphics" and renderer string should say something like "Mesa DRI Intel", and not "Software Rasterizer".
To check if it's a permissions error, could you post the output of:
```
sudo LIBGL_DEBUG=verbose glxinfo
```

EDIT:

Sorry, there's no reinstall option for apt (my fault). You would have to remove/purge and then install, but I doubt that will help you. I've never seen a direct rendering issue solved that way.

Thanks for all your help, I hope I can fix this once and for all.

This is my output:
```

ajmera@Toshiba-user:~$ sudo LIBGL_DEBUG=verbose glxinfo
[sudo] password for ajmera: 
name of display: :0.0
libGL: OpenDriver: trying /usr/lib/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/dri/swrast_dri.so
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
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.2
OpenGL shading language version string: 1.10
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, 
    GL_ARB_half_float_pixel, GL_ARB_imaging, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shader_objects, 
    GL_ARB_shading_language_100, GL_ARB_shadow, GL_ARB_shadow_ambient, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_compiled_vertex_array, GL_EXT_convolution, 
    GL_EXT_copy_texture, GL_EXT_depth_bounds_test, GL_EXT_draw_range_elements, 
    GL_EXT_framebuffer_object, GL_EXT_framebuffer_blit, GL_EXT_fog_coord, 
    GL_EXT_gpu_program_parameters, GL_EXT_histogram, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, 
    GL_EXT_paletted_texture, GL_EXT_pixel_buffer_object, 
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_shadow_funcs, GL_EXT_shared_texture_palette, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, 
    GL_EXT_vertex_array, GL_APPLE_packed_pixels, GL_APPLE_vertex_array_object, 
    GL_ATI_blend_equation_separate, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATI_fragment_shader, 
    GL_ATI_separate_stencil, GL_IBM_multimode_draw_arrays, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_program_debug, 
    GL_MESA_resize_buffers, GL_MESA_texture_array, GL_MESA_ycbcr_texture, 
    GL_MESA_window_pos, GL_NV_blend_square, GL_NV_fragment_program, 
    GL_NV_light_max_exponent, GL_NV_point_sprite, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_NV_vertex_program, GL_NV_vertex_program1_1, 
    GL_OES_read_format, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGI_texture_color_table, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SGIX_shadow, 
    GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

3 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x44 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None

32 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x45  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x46  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x47  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x48  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x49  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  8  0  0  0  0  0 0 None
0x4a  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  8 16 16 16 16  0 0 Slow
0x4b  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  8  0  0  0  0  0 0 None
0x4c  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  8 16 16 16 16  0 0 Slow
0x4d  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x4e  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x4f  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x50  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x51  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x52  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x53  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x54  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x55  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x56  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x57  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x58  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x59  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  8  0  0  0  0  0 0 None
0x5a  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  8 16 16 16 16  0 0 Slow
0x5b  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  8  0  0  0  0  0 0 None
0x5c  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  8 16 16 16 16  0 0 Slow
0x5d  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x5e  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x5f  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x60  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x61  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x62  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x63  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x64  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
 
```

---

### Post by ku5165 on 2009-02-17
ok the above problem is still there, but a new one has arisen, the computer will no longer suspend, the only differences i have done are using brasero, installing smplayer thats it.
Please someone help me as suspend is a major used item on my laptop.
Thanks

---

### Post by Yellow Pasque on 2009-02-17
- Make sure you have these packages installed (I believe they're installed by default, but double-check): libgl1-mesa-dri libdrm2 

- Try some of the suggestions/commands in this document: [http://dri.freedesktop.org/wiki/DriTroubleshooting](http://dri.freedesktop.org/wiki/DriTroubleshooting)

---

### Post by ku5165 on 2009-02-17
> **Temüjin said:**
> - Make sure you have these packages installed (I believe they're installed by default, but double-check): libgl1-mesa-dri libdrm2 

- Try some of the suggestions/commands in this document: [http://dri.freedesktop.org/wiki/DriTroubleshooting](http://dri.freedesktop.org/wiki/DriTroubleshooting)

I have both of those packaged installed, I am now reading the above document, to see if I can figure out what they are saying, and if I can, how to make it help me. I saw your  yahoo/aim do you mind if I contact you via those?
Anyways thanks for all your help, Im off to read that webpage.
Ku

---

### Post by soxs on 2009-02-18
you may attch your ```
/var/log/Xorg.0.log
```

---

### Post by Yellow Pasque on 2009-02-18
I don't get on IM's much anymore and I'm usually intoxicated when I do.:P 
Besides, it's hard for me to troubleshoot problems in that manner.
As soxs indicated, please post your Xorg log.

---

### Post by crjackson on 2009-02-18
> **ku5165 said:**
> I am not getting satisfactory performance from Ubuntu,

My system is 
Intel Core 2 Duo 1.6ghz
1gb ram
100gb hdd
intel gma 950 graphics
Ubuntu Intrepid Ibex 8.10 with all latest updates

Now for details:

1. The processor fan keeps kicking on even if i just want to open firefox, or load a new page in it.
2. Also i tried to run Nexuiz or Tuxcart or 3d pool game, however i get VERY  slow fps, (maybe around 1-2).
3. Sometimes the card reader does not work (not a real big one, the above two are.)

I have read around the forum that the main cause might be my graphics driver. If someone can tell me how this can be reinstalled or changed id love to give it a try. Also a fix for making the fan start up less often would also be helpful as my laptop fan is TOO loud. 
Thanks A lot,
Ku

P.s. I am pretty advanced with computers, however being new to linux platform i need some help (step by step would be nice)

I notice you're running 8.10 - Some of the Intel gma cards have issues with 8.10. Mine did, and i had problems similar to yours.

I installed 8.04.2 on my lappy with intel video and it's much faster now. Graphics speed is about 2.5 times faster.  You may want to give 8.04 a try.  I'm staying with 8.04 until Junty is about 6 weeks old, then I'll try Juanty.

---

### Post by ku5165 on 2009-02-18
xorg log

```
 
X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-16-server x86_64 Ubuntu
Current Operating System: Linux Toshiba-user 2.6.27-9-generic #1 SMP Thu Nov 20 22:15:32 UTC 2008 x86_64
Build Date: 24 October 2008  09:06:49AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@crested.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Feb 17 17:46:43 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7b7320
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@0:2:0) Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller rev 3, Mem @ 0xffd80000/524288, 0xe0000000/268435456, 0xffd40000/262144, I/O @ 0x0000cff8/8
(--) PCI: (0@0:2:1) Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller rev 3, Mem @ 0x54000000/524288
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(==) AIGLX enabled
(==) Exporting typical set of GLX visuals
(II) Loading extension GLX
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.5.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(II) Matched intel from file name intel.ids
(==) Matched intel for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"

(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.4.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
	965GM, 965GME/GLE, G33, Q35, Q33,
	Mobile Intel® GM45 Express Chipset,
	Intel Integrated Graphics Device, G45/G43, Q45/Q43
(II) Primary Device is: PCI 00@00:02:0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"

(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.1.0
	ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"

(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 4.1
(==) intel(0): Depth 24, (==) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 945GM
(--) intel(0): Chipset: "945GM"
(--) intel(0): Linear framebuffer at 0xE0000000
(--) intel(0): IO registers at addr 0xFFD80000
(II) intel(0): 2 display pipes available.
(==) intel(0): Using EXA for acceleration
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) intel(0): initializing int10
(II) intel(0): Primary V_BIOS segment is: 0xc000
(II) intel(0): VESA BIOS detected
(II) intel(0): VESA VBE Version 3.0
(II) intel(0): VESA VBE Total Mem: 7872 kB
(II) intel(0): VESA VBE OEM: Intel(r) 82945GM Chipset Family Graphics Chip Accelerated VGA BIOS
(II) intel(0): VESA VBE OEM Software Rev: 1.0
(II) intel(0): VESA VBE OEM Vendor: Intel Corporation
(II) intel(0): VESA VBE OEM Product: Intel(r) 82945GM Chipset Family Graphics Controller
(II) intel(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) intel(0): Output VGA using monitor section Configured Monitor
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): Output LVDS has no monitor section
(II) intel(0): I2C bus "LVDSDDC_C" initialized.
(II) intel(0): Attempting to determine panel fixed mode.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): EDID vendor "SEC", prod id 16961
(II) intel(0): found backlight control method /sys/class/backlight/acpi_video0
(II) intel(0): EDID vendor "SEC", prod id 16961
(II) intel(0): Output VGA disconnected
(II) intel(0): Output LVDS connected
(II) intel(0): Using exact sizes for initial modes
(II) intel(0): Output LVDS using initial mode 1280x800
(II) intel(0): Monitoring connected displays enabled
(II) intel(0): detected 256 kB GTT.
(II) intel(0): detected 7932 kB stolen memory.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Will not try to enable page flipping
(==) intel(0): Triple buffering disabled
(==) intel(0): Intel XvMC decoder disabled
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "exa"
(II) LoadModule: "exa"

(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.4.0
	ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) intel(0): Comparing regs from server start up to After PreInit
(WW) intel(0): Register 0x61200 (PP_STATUS) changed from 0xc0000008 to 0xd0000009
(WW) intel(0): PP_STATUS before: on, ready, sequencing idle
(WW) intel(0): PP_STATUS after: on, ready, sequencing on
(WW) intel(0): Register 0x70024 (PIPEASTAT) changed from 0x80000a03 to 0x00000000
(WW) intel(0): PIPEASTAT before: status: FIFO_UNDERRUN GMBUS_INT_STATUS VSYNC_INT_STATUS VBLANK_INT_STATUS OREG_UPDATE_STATUS
(WW) intel(0): PIPEASTAT after: status:
(WW) intel(0): Register 0x71024 (PIPEBSTAT) changed from 0x80000202 to 0x00000202
(WW) intel(0): PIPEBSTAT before: status: FIFO_UNDERRUN VSYNC_INT_STATUS VBLANK_INT_STATUS
(WW) intel(0): PIPEBSTAT after: status: VSYNC_INT_STATUS VBLANK_INT_STATUS
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) intel(0): Kernel reported 238848 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 955388 kB available
(EE) intel(0): Cannot support DRI with frame buffer width > 2048.
(**) intel(0): Framebuffer compression enabled
(**) intel(0): Tiling enabled
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Tiled allocation successful.
(II) intel(0): adjusting plane->pipe mappings to allow for framebuffer compression
(II) intel(0): Page Flipping disabled
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) EXA(0): Offscreen pixmap area of 50331648 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x007bf000 (pgoffset 1983)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x02e40000 (pgoffset 11840)
(II) intel(0): Fixed memory allocation layout:
(II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)
(II) intel(0): 0x00020000-0x0061ffff: compressed frame buffer (6144 kB, 0x000000003f820000 physical
)
(II) intel(0): 0x00620000-0x00620fff: compressed ll buffer (4 kB, 0x000000003fe20000 physical
)
(II) intel(0): 0x00621000-0x0062afff: HW cursors (40 kB, 0x000000003fe21000 physical
)
(II) intel(0): 0x0062b000-0x00632fff: logical 3D context (32 kB)
(II) intel(0): 0x00633000-0x00633fff: overlay registers (4 kB, 0x000000003fe33000 physical
)
(II) intel(0): 0x00640000-0x02e3ffff: front buffer (40960 kB)
(II) intel(0): 0x007bf000:            end of stolen memory
(II) intel(0): 0x02e40000-0x05e3ffff: exa offscreen (49152 kB)
(II) intel(0): 0x10000000:            end of aperture
(II) intel(0): Selecting standard 18 bit TMDS pixel format.
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is off
(II) intel(0):   Display plane B is now disabled and connected to pipe A.
(II) intel(0):   Pipe B is on
(II) intel(0):   Display plane A is now enabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe none
(II) intel(0):   Output LVDS is connected to pipe B
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) intel(0): Selecting standard 18 bit TMDS pixel format.
(II) intel(0): DPMS enabled
(II) intel(0): Set up overlay video
(II) intel(0): direct rendering: Disabled
(--) RandR disabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) intel(0): Setting screen physical size to 261 x 163
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"

(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.0.99
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Configuring as mouse
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device AlpsPS/2 ALPS GlidePoint
(II) LoadModule: "synaptics"

(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 0.15.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(II) Synaptics touchpad driver version 0.15.2
(II) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
(II) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
(**) Option "Device" "/dev/input/event8"
(--) AlpsPS/2 ALPS GlidePoint touchpad found
(**) AlpsPS/2 ALPS GlidePoint: always reports core events
(II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD)
(II) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
(II) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
(--) AlpsPS/2 ALPS GlidePoint touchpad found
(II) config/hal: Adding input device PS/2 Mouse
(**) PS/2 Mouse: always reports core events
(**) PS/2 Mouse: Device: "/dev/input/event7"
(II) PS/2 Mouse: Found x and y relative axes
(II) PS/2 Mouse: Found 3 mouse buttons
(II) PS/2 Mouse: Configuring as mouse
(II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE)
(**) PS/2 Mouse: YAxisMapping: buttons 4 and 5
(**) PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event1"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event5"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Video Bus: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Video Bus: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Video Bus: xkb_layout: "us"
(II) intel(0): EDID vendor "SEC", prod id 16961
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) intel(0): EDID vendor "SEC", prod id 16961
AUDIT: Tue Feb 17 17:46:55 2009: 5187 X: client 4 rejected from local host ( uid=0 gid=0 pid=5389 )
AUDIT: Tue Feb 17 17:47:02 2009: 5187 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=5405 )
  Auth name: MIT-MAGIC-COOKIE-1 ID: -1
AUDIT: Tue Feb 17 17:47:02 2009: 5187 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=5406 )
  Auth name: MIT-MAGIC-COOKIE-1 ID: -1
AUDIT: Tue Feb 17 17:47:02 2009: 5187 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=5407 )
  Auth name: MIT-MAGIC-COOKIE-1 ID: -1
(II) intel(0): EDID vendor "SEC", prod id 16961
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) intel(0): EDID vendor "SEC", prod id 16961
(II) intel(0): EDID vendor "SEC", prod id 16961
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) intel(0): EDID vendor "SEC", prod id 16961
(II) intel(0): EDID vendor "SEC", prod id 16961
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) intel(0): EDID vendor "SEC", prod id 16961
(II) intel(0): EDID vendor "SEC", prod id 16961
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) intel(0): EDID vendor "SEC", prod id 16961
(II) intel(0): EDID vendor "SEC", prod id 16961
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) intel(0): EDID vendor "SEC", prod id 16961
(II) intel(0): xf86UnbindGARTMemory: unbind key 0
(II) intel(0): xf86UnbindGARTMemory: unbind key 1
(II) Open ACPI successful (/var/run/acpid.socket)
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x007bf000 (pgoffset 1983)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x02e40000 (pgoffset 11840)
(II) intel(0): Fixed memory allocation layout:
(II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)
(II) intel(0): 0x00020000-0x0061ffff: compressed frame buffer (6144 kB, 0x000000003f820000 physical
)
(II) intel(0): 0x00620000-0x00620fff: compressed ll buffer (4 kB, 0x000000003fe20000 physical
)
(II) intel(0): 0x00621000-0x0062afff: HW cursors (40 kB, 0x000000003fe21000 physical
)
(II) intel(0): 0x0062b000-0x00632fff: logical 3D context (32 kB)
(II) intel(0): 0x00633000-0x00633fff: overlay registers (4 kB, 0x000000003fe33000 physical
)
(II) intel(0): 0x00640000-0x02e3ffff: front buffer (40960 kB)
(II) intel(0): 0x007bf000:            end of stolen memory
(II) intel(0): 0x02e40000-0x05e3ffff: exa offscreen (49152 kB)
(II) intel(0): 0x10000000:            end of aperture
(II) intel(0): Selecting standard 18 bit TMDS pixel format.
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is off
(II) intel(0):   Display plane B is now disabled and connected to pipe B.
(II) intel(0):   Pipe B is on
(II) intel(0):   Display plane A is now enabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe none
(II) intel(0):   Output LVDS is connected to pipe B
(II) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
(II) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
(--) AlpsPS/2 ALPS GlidePoint touchpad found
(II) Macintosh mouse button emulation: Device reopened after 10 attempts.
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) PS/2 Mouse: Device reopened after 10 attempts.
(**) PS/2 Mouse: YAxisMapping: buttons 4 and 5
(**) PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) AT Translated Set 2 keyboard: Device reopened after 10 attempts.
(II) Video Bus: Device reopened after 10 attempts.
(II) intel(0): xf86UnbindGARTMemory: unbind key 0
(II) intel(0): xf86UnbindGARTMemory: unbind key 1
(II) Open ACPI successful (/var/run/acpid.socket)
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x007bf000 (pgoffset 1983)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x02e40000 (pgoffset 11840)
(II) intel(0): Fixed memory allocation layout:
(II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)
(II) intel(0): 0x00020000-0x0061ffff: compressed frame buffer (6144 kB, 0x000000003f820000 physical
)
(II) intel(0): 0x00620000-0x00620fff: compressed ll buffer (4 kB, 0x000000003fe20000 physical
)
(II) intel(0): 0x00621000-0x0062afff: HW cursors (40 kB, 0x000000003fe21000 physical
)
(II) intel(0): 0x0062b000-0x00632fff: logical 3D context (32 kB)
(II) intel(0): 0x00633000-0x00633fff: overlay registers (4 kB, 0x000000003fe33000 physical
)
(II) intel(0): 0x00640000-0x02e3ffff: front buffer (40960 kB)
(II) intel(0): 0x007bf000:            end of stolen memory
(II) intel(0): 0x02e40000-0x05e3ffff: exa offscreen (49152 kB)
(II) intel(0): 0x10000000:            end of aperture
(II) intel(0): Selecting standard 18 bit TMDS pixel format.
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is off
(II) intel(0):   Display plane B is now disabled and connected to pipe B.
(II) intel(0):   Pipe B is on
(II) intel(0):   Display plane A is now enabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe none
(II) intel(0):   Output LVDS is connected to pipe B
(II) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
(II) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
(--) AlpsPS/2 ALPS GlidePoint touchpad found
(II) Macintosh mouse button emulation: Device reopened after 10 attempts.
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) PS/2 Mouse: Device reopened after 10 attempts.
(**) PS/2 Mouse: YAxisMapping: buttons 4 and 5
(**) PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) AT Translated Set 2 keyboard: Device reopened after 10 attempts.
(II) Video Bus: Device reopened after 10 attempts.
(II) intel(0): xf86UnbindGARTMemory: unbind key 0
(II) intel(0): xf86UnbindGARTMemory: unbind key 1
(II) Open ACPI successful (/var/run/acpid.socket)
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x007bf000 (pgoffset 1983)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x02e40000 (pgoffset 11840)
(II) intel(0): Fixed memory allocation layout:
(II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)
(II) intel(0): 0x00020000-0x0061ffff: compressed frame buffer (6144 kB, 0x000000003f820000 physical
)
(II) intel(0): 0x00620000-0x00620fff: compressed ll buffer (4 kB, 0x000000003fe20000 physical
)
(II) intel(0): 0x00621000-0x0062afff: HW cursors (40 kB, 0x000000003fe21000 physical
)
(II) intel(0): 0x0062b000-0x00632fff: logical 3D context (32 kB)
(II) intel(0): 0x00633000-0x00633fff: overlay registers (4 kB, 0x000000003fe33000 physical
)
(II) intel(0): 0x00640000-0x02e3ffff: front buffer (40960 kB)
(II) intel(0): 0x007bf000:            end of stolen memory
(II) intel(0): 0x02e40000-0x05e3ffff: exa offscreen (49152 kB)
(II) intel(0): 0x10000000:            end of aperture
(II) intel(0): Selecting standard 18 bit TMDS pixel format.
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is off
(II) intel(0):   Display plane B is now disabled and connected to pipe B.
(II) intel(0):   Pipe B is on
(II) intel(0):   Display plane A is now enabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe none
(II) intel(0):   Output LVDS is connected to pipe B
(II) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
(II) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
(--) AlpsPS/2 ALPS GlidePoint touchpad found
(II) Macintosh mouse button emulation: Device reopened after 10 attempts.
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) PS/2 Mouse: Device reopened after 10 attempts.
(**) PS/2 Mouse: YAxisMapping: buttons 4 and 5
(**) PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) AT Translated Set 2 keyboard: Device reopened after 10 attempts.
(II) Video Bus: Device reopened after 10 attempts.
(II) intel(0): xf86UnbindGARTMemory: unbind key 0
(II) intel(0): xf86UnbindGARTMemory: unbind key 1
(II) Open ACPI successful (/var/run/acpid.socket)
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x007bf000 (pgoffset 1983)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x02e40000 (pgoffset 11840)
(II) intel(0): Fixed memory allocation layout:
(II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)
(II) intel(0): 0x00020000-0x0061ffff: compressed frame buffer (6144 kB, 0x000000003f820000 physical
)
(II) intel(0): 0x00620000-0x00620fff: compressed ll buffer (4 kB, 0x000000003fe20000 physical
)
(II) intel(0): 0x00621000-0x0062afff: HW cursors (40 kB, 0x000000003fe21000 physical
)
(II) intel(0): 0x0062b000-0x00632fff: logical 3D context (32 kB)
(II) intel(0): 0x00633000-0x00633fff: overlay registers (4 kB, 0x000000003fe33000 physical
)
(II) intel(0): 0x00640000-0x02e3ffff: front buffer (40960 kB)
(II) intel(0): 0x007bf000:            end of stolen memory
(II) intel(0): 0x02e40000-0x05e3ffff: exa offscreen (49152 kB)
(II) intel(0): 0x10000000:            end of aperture
(II) intel(0): Selecting standard 18 bit TMDS pixel format.
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is off
(II) intel(0):   Display plane B is now disabled and connected to pipe B.
(II) intel(0):   Pipe B is on
(II) intel(0):   Display plane A is now enabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe none
(II) intel(0):   Output LVDS is connected to pipe B
(II) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
(II) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
(--) AlpsPS/2 ALPS GlidePoint touchpad found
(II) Macintosh mouse button emulation: Device reopened after 10 attempts.
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) PS/2 Mouse: Device reopened after 10 attempts.
(**) PS/2 Mouse: YAxisMapping: buttons 4 and 5
(**) PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) AT Translated Set 2 keyboard: Device reopened after 10 attempts.
(II) Video Bus: Device reopened after 10 attempts. 
```

I do no want to go back to 8.04 as it will require too much work, however I plan on doing a complete reinstall once Jaunty comes out so that I can use the ext4 filesystem, and have a clean install.
Thanks for all you help guys/gals
ku

---

### Post by Yellow Pasque on 2009-02-18
> (EE) intel(0): Cannot support DRI with frame buffer width > 2048.

The problem appears to be in your xorg.conf file. My guess is that you upgraded from earlier versions of Ubuntu and it kept the same xorg.conf file, which may have worked with older versions of X.org, but doesn't work with the version in Intrepid.

Please post your /etc/X11/xorg.conf

---

### Post by soxs on 2009-02-19
My guess is that frambuffer option hunts your fps down, and temüjin is right, the error has to be in your xorg.conf

---

### Post by ku5165 on 2009-02-19
my etc/x11/xorg.conf file:
```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg
# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Generic Keyboard"
#	Driver		"kbd"
#	Option		"XkbRules"	"xorg"
#	Option		"XkbModel"	"pc105"
#	Option		"XkbLayout"	"us"
#EndSection
# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Configured Mouse"
#	Driver		"mouse"
#	Option		"CorePointer"
#EndSection
# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Synaptics Touchpad"
#	Driver		"synaptics"
#	Option		"SendCoreEvents"	"true"
#	Option		"Device"		"/dev/psaux"
#	Option		"Protocol"		"auto-dev"
#	Option		"HorizEdgeScroll"	"0"
#EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2560 1024
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection 
```
I was wondering, there are 3 more xorg.conf files there but they have what seem to be a bunch of numbers behind them, i guess they are backups?? Just out of curiosity is that right?
Thanks for all ur help.
Ku

---

### Post by Yellow Pasque on 2009-02-19
> there are 3 more xorg.conf files there but they have what seem to be a bunch of numbers behind them, i guess they are backups?
Correct.

> Virtual	2560 1024
This is the line causing the issue with direct rendering/DRI. Are you using (or have you ever used) an external display with your laptop? If not, remove this line from the file. You can edit it with:
```
gksudo gedit /etc/X11/xorg.conf
```
**EDIT**: I would also recommend adding this to the end of the file so you  don't run into permissions issues:
```

Section "DRI"
	Mode         0666
EndSection

```
After you do that, restart your system and check glxinfo again.

```
LIBGL_DEBUG=verbose glxinfo
```
Hopefully, the OpenGL renderer string will now report "Mesa DRI Intel.." and doing basic 2D tasks won't load your CPU and spin your fan so much.

---

### Post by ku5165 on 2009-02-19
It WORKED yay, now it shows OpenGL rendering as Mesa Intel
Now I was wondering, you said the delete the string for an external display, does that mean I cannot use an external display or I can still do it?
Thanks a LOT for your help, I dont think I would have been able to fix it without your help.
ku


Here is the output of that code :
```
name of display: :0.0
libGL: XF86DRIGetClientDriverName: 1.9.0 i915 (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/tls/i915_dri.so
libGL: OpenDriver: trying /usr/lib/dri/i915_dri.so
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 4, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 4, (OK)
drmOpenByBusid: drmOpenMinor returns 4
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
libGL error: 
Can't open configuration file /etc/drirc: No such file or directory.
libGL error: 
Can't open configuration file /home/ajmera/.drirc: No such file or directory.
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_swap_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_swap_control, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 945GM 20061102
OpenGL version string: 1.4 Mesa 7.2
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_point_parameters, GL_ARB_shadow, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_equation_separate, 
    GL_EXT_blend_func_separate, GL_EXT_blend_logic_op, GL_EXT_blend_minmax, 
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, GL_EXT_cull_vertex, 
    GL_EXT_compiled_vertex_array, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, 
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle, 
    GL_EXT_vertex_array, GL_3DFX_texture_compression_FXT1, 
    GL_APPLE_client_storage, GL_APPLE_packed_pixels, 
    GL_ATI_blend_equation_separate, GL_ATI_separate_stencil, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture, 
    GL_MESA_window_pos, GL_NV_blend_square, GL_NV_light_max_exponent, 
    GL_NV_point_sprite, GL_NV_texture_rectangle, GL_NV_texgen_reflection, 
    GL_NV_vertex_program, GL_NV_vertex_program1_1, GL_OES_read_format, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SUN_multi_draw_arrays

3 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x54 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None

36 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x55  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x56  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x57  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x58  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x59  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x5a  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x5b  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x5c  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x5d  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x5e  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x5f  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x60  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x61  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x62  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x63  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x64  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x65  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x66  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x67  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x68  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x69  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x6a  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x6b  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x6c  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x6d  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x6e  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x6f  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x70  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x71  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x72  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x73  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x74  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x75  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x76  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x77  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x78  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow

```

---

### Post by Yellow Pasque on 2009-02-20
> Now I was wondering, you said the delete the string for an external display, does that mean I cannot use an external display or I can still do it?
You can still use an external display, but you won't be able to use the laptop display and an external at the same time (dual-head mode) while still having direct rendering working. For technical explanation, see: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/146859](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/146859)
Hopefully, it will be fixed in time for Jaunty/9.04 as indicated in the bug report.

---

### Post by ku5165 on 2009-02-20
> **Temüjin said:**
> You can still use an external display, but you won't be able to use the laptop display and an external at the same time (dual-head mode) while still having direct rendering working. For technical explanation, see: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/146859](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/146859)
Hopefully, it will be fixed in time for Jaunty/9.04 as indicated in the bug report.

thanks a lot buddy, my standby started working now, the card reader seems ok, it seems like everything is fine now
thanks again for all your help
ku

---

