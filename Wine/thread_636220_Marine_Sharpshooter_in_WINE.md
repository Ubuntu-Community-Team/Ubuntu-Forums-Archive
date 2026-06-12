---
title: "Marine Sharpshooter in WINE"
date: 2007-12-09
forum: Wine
---

### Post by thehandyman on 2007-12-09
I was able to install Marine Sharpshooter on my machine using WINE, but I cannot get it to run no matter what I try, however I have most likely missed something as I am new to this. I welcome all suggestions and comments. Thanx

---

### Post by cogadh on 2007-12-09
Telling us little more than "it doesn't work" doesn't help us help you at all. You need to provide a little detail. See this post for the kinds of things we need to know:
[http://ubuntuforums.org/showthread.php?t=624424](http://ubuntuforums.org/showthread.php?t=624424)

---

### Post by thehandyman on 2007-12-09
I cannot get any error messages in the terminal, however I just downloaded this yesterday and am just trying to learn it. I just installed wine a couple of hours ago it WINE 0.9.46. 

wine: cannot find 'c:/program files/groove games/marine sharpshooter/ctums.exe]'
wine: could not load L"c:\\windows\\system32\\[c:program.exe": Module not found

WINE Config
OS=XP
Library Overrides=0
Audio=OSS Driver; Full Acceleration; Default Bits 16
Video= Allow the window manager to control the window; allow pixel shader (hardware); DPI 96
 I hope this is enough to get started

---

### Post by thehandyman on 2007-12-09
Also this is all I ahev in the wine dir except for notepad

---

### Post by cogadh on 2007-12-09
First off, update to the newest version of Wine, 0.9.50, it works much better than 0.9.46. Instructions on updating can be found here:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Next, you might want to read up on how to actually use Wine. Click on the "Stuff I've learned about Wine" link in my sig, its a basic beginner's Wine usage doc.

As for the specific problem you are having, the error you posted usually means that you need to change directories to wherever the executable is, then run it in Wine:
```
cd path/to/executable
wine executable.exe
```

---

### Post by thehandyman on 2007-12-09
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\Program Files\\Groove Games\\Marine Sharpshooter\\CTUMS.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Groove Games\\Marine Sharpshooter\\CTUMS.exe" failed, status c0000135

This is what I got when I finally got the correct dir path

---

### Post by cogadh on 2007-12-09
You are going to need to copy the MFC42.DLL file from a Windows machine into the .wine/drive_c/windows/system32 directory. If you don't have a Windows machine to copy it from, just Google it, there are plenty of places you can download it from. After you copy it into that directory, run winecfg, go to the Libraries tab and add an override for the DLL file. Try running the game again and that error should go away.

---

### Post by thehandyman on 2007-12-09
Already got the .dll, Thank you. Will try the winecfg now thanx
Game starts now but starts to load the mission the logs me out of the system

---

### Post by thehandyman on 2007-12-09
Well now, Here we go with the FIXme's, but I will hold off on posting them all right now. Might make someone crazy. Here are just a few:

fixme:winmm:MMDRV_Exit Closing while ll-driver open

fixme:winmm:MMDRV_Exit Closing while ll-driver open

[email]steve@steve:~/.wine[/email]/drive_c/Program Files/Groove Games/Marine Sharpshooter$ err:dmloader:IDirectMusicLoaderImpl_IDirectMusicLoader_SetObject : could not attach stream to file

fixme:dmime:IDirectMusicPerformance8Impl_InitAudio (0xa9cb28, (nil), (nil), (nil), 8, 128, 3f, (nil)): to check

fixme:dmime:IDirectMusicPerformance8Impl_InitAudio return dsound(0xb198b8,0)

fixme:dmime:IDirectMusicPerformance8Impl_Init (iface = 0xa9cb28, dmusic = (nil), dsound = 0xb198b8, hwnd = (nil))

fixme:dmime:IDirectMusicPerformance8Impl_CreateStandardAudioPath (0xa9cb28)->(8, 128, 0, 0xa9ccf4): semi-stub

fixme:dmime:IDirectMusicAudioPathImpl_IDirectMusicAudioPath_Activate (0xb19cf0, 0): stub

fixme:dmime:IDirectMusicPerformance8Impl_GetDefaultAudioPath (0xa9cb28, 0x34f9dc): semi-stub (0xb19cf4)

fixme:dmime:IDirectMusicAudioPathImpl_IDirectMusicAudioPath_SetVolume (0xb19cf0, 0, 0): stub

fixme:win:EnumDisplayDevicesW ((null),0,0x34ef24,0x00000000), stub!


HELP, LOL I might have got in way over my head on this

---

### Post by cogadh on 2007-12-09
I'm sorry, it logged you out of Ubuntu? Applications run in Wine should not be able to do that...

Unless it caused the X server to restart, which would put you back at the login screen. What do you have for a graphics card?

You can mostly ignore the "fixme" messages, they are just developer notes about incomplete or unimplemented functions in Wine. They usually mean nothing to a normal user, and most games run fine in spite of them (the ones that actually work in Wine, that is).

---

### Post by thehandyman on 2007-12-09
Don't know what graphics card. Not sure where to find that. It is onboard. Had to take my ATI Radeon 7000 32 mb ddr tvo out

---

### Post by thehandyman on 2007-12-09
Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter

---

### Post by cogadh on 2007-12-09
Run this in a terminal:
```
glxinfo | grep direct
```
and post the results.

BTW - Why did you have to take out the ATI card?

---

### Post by thehandyman on 2007-12-09
steve@steve:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_EXT_texture_from_pixmap
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)
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
0x22 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x3d 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon


Nothing for grep direct yet

---

### Post by cogadh on 2007-12-09
That's supposed to be a single command "glxinfo | grep direct", it just produces a single part of the glxinfo output, instead of all that mess. Doesn't matter though, the part I wanted is in there:
**direct rendering: No**

This means that you do not have 3D acceleration available. After doing a little digging on my own, it appears that there aren't any 3D accelerated drivers available for the SiS chipsets on Linux. Since this game was trying to run 3D graphics and your video hardware can't do it, that's why the X server crashed and brought you back to a login prompt.

Your best bet for getting the game to work is to either re-install that ATI card, or get an Nvidia card. I personally recommend getting an Nvidia card, their Linux driver support is fantastic.

---

### Post by thehandyman on 2007-12-09
Thank you for your help, but I can't get an Nvidia so what do I do with the ATI. It won't boot with the ATI in there

---

### Post by thehandyman on 2007-12-09
I guess the two could be causing a conflict with UBUNTU. I will try to disable the SiS in CMOS. and reinstall the ATI

---

