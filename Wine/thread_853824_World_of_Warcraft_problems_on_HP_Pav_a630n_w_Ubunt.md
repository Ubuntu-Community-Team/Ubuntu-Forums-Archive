---
title: "World of Warcraft problems on HP Pav a630n w/ Ubuntu 8.04 Hardy Heron"
date: 2008-07-08
forum: Wine
---

### Post by gmunuh on 2008-07-08
Hello all,

I am new to Ubuntu.  I played a little with Debian about 2 years ago.  Mainly i work on XP, so i still consider myself a noob.

NEwaze, I installed Ubuntu on an HP Pavilion a630n.  Everthing works great and the installation was surprisingly easy (Many thanx to all you programmers out there!).

But when it came to my world of warcraft, i followed the directions of the posted howto and even the additional Entire Howto and still cannot find a solution to my problem.

here is my Config.wtf file:

SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET readTerminationWithoutNotice "-1"
SET locale "enUS"
SET coresDetected "2"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1024x768"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET videoOptionsVersion "1"
SET textureFilteringMode "0"
SET pixelShaders "1"
SET movie "0"
SET showToolsUI "1"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET Sound_OutputDriverName "System Default"
SET realmList "us.logon.worldofwarcraft.com"
SET patchlist "us.version.worldofwarcraft.com"
SET SmallCull "0.080000"
SET DistCull "350.000000"
SET farclip "400.000000"
SET specular "1"
SET particleDensity "1.000000"
SET spellEffectLevel "6"
SET cameraPitchMoveSpeed "90"
SET cameraPitchSmoothSpeed "45"
SET realmName "Rexxar"
SET gameTip "30"
SET accountName "scorpiomage"
SET ChatMusicVolume "0.30000001192093"
SET ChatSoundVolume "0.40000000596046"
SET ChatAmbienceVolume "0.30000001192093"
SET Sound_EnableMusic "0"
SET Sound_MasterVolume "1"
SET Sound_SFXVolume "0.80000001192093"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET cameraDistanceMaxFactor "2"
SET OutboundChatVolume "1"
SET InboundChatVolume "1"
SET VoiceActivationSensitivity "0.40000003576279"
SET minimapZoom "0"
SET minimapInsideZoom "0"
SET questFadingDisable "1"
SET displayFreeBagSlots "1"
SET autoSelfCast "1"
SET ShowTargetCastbar "1"
SET checkAddonVersion "0"
SET scriptErrors "1"
SET gxApi "opengl"
SET ffxDeath "0"
SET ffxGlow "0"
SET M2UseShaders "0"
SET Sound_SoundOutputSystem "1"
SET Sound_SoundBufferSize "150"
SET UIFaster "2"

I installed the WoW on a seperate hard drive (running XP), then rebooted to Ubuntu with the XP disk as a secondary drive.  after i ran the winecfg i copied the World of Warcraft contents from the Program Files (XP Hard Drive) over to: /home/gabriel/.wine/c-drive/ProgramFiles/WOW

After that, i edited the config.wtf by adding the lines:
SET gxApi "opengl"
SET ffxDeath "0"
SET ffxGlow "0"
SET M2UseShaders "0"
SET Sound_SoundOutputSystem "1"
SET Sound_SoundBufferSize "150"
SET UIFaster "2"

which fixed almost everything.  Now the game login and startup appear and sound fine, but once i actually enter the realm, 2 problems occur:

1.  the graphics are blank on some areas, and change when i enter or exit a building (to other blank areas; ex: map is pure white; or floor is 2 seperate textures instead of mixed)
2.  i created the suggested registry key (in ubuntu) and it seemed to speed up only the login part of the game.  once i enter the realm, it gets pretty choppy.

i will attach some screenshots.  the normal one is from when i booted to XP and ran the game (it runs fine in XP)

Any help would  be appreciated.  Thanx for taking the time to read my post.

--Gmunuh

---

### Post by beeldings on 2008-07-09
To me, this sounds like a problem with your graphics card drivers. Are you using an integrated graphics processor or are you using an actual graphics card (i.e an ATi or nVidia card)? Also, if you type "glxinfo" into a terminal (without the quotes), what information is returned?

---

### Post by gmunuh on 2008-07-09
> **beeldings said:**
> To me, this sounds like a problem with your graphics card drivers. Are you using an integrated graphics processor or are you using an actual graphics card (i.e an ATi or nVidia card)? Also, if you type "glxinfo" into a terminal (without the quotes), what information is returned?
Its integrated video. XP Device Manager shows as i915 (intel).  In XP the game plays good it's only in linux i have these problems.  Thanx for the quick reply!

Gmunuh

PS - heres the glxinfo:

name of display: :0.0
display: :0  screen: 0
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
OpenGL renderer string: Mesa DRI Intel(R) 915G 20061017 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 7.0.3-rc2
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_point_parameters, 
    GL_ARB_shadow, GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_cull_vertex, GL_EXT_compiled_vertex_array, GL_EXT_convolution, 
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_histogram, GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, 
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
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
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x54 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

THANX AGAIN!

---

### Post by beeldings on 2008-07-09
This one has me a bit stumped. The only thing that I can think of is to try running the game in Direct3D mode as opposed to OpenGL. Or possibly performing a fresh install of WoW on Linux through Wine. Do you have any add-ons running? If so, try disabling those and see what happens. Also, just for kicks, could you post your xorg.conf file (found in /etc/X11/)?

EDIT: Just thought of something else, are you running Compiz or some other form of an accelerated desktop when attempting to play the game?

Are you experiencing this problem with other games or does this apply just to WoW?

---

### Post by gmunuh on 2008-07-14
CENTRAL TIME:  10:37 am; July 14, 2008

I've been out of town so i'm sorry i couldnt reply sooner.

I decided to (re)start from scratch.  i reformatted my hd.  now i have a fresh install of ubuntu hardy heron 8.04 and the only thing i've done is download & install the updates (20 in all) using the Update Manager.  i will follow the WoW Howto thread instructions to the letter (using the online downloader option) and report my final result. Thanx for the help!

-- Gabriel

---

### Post by flytripper on 2008-07-14
with integrated video you've got no chance. the chip simply doesnt have the instructions to process the games visual output... this appears to you as not showing.

---

### Post by flytripper on 2008-07-14
you could however, try lowering all the effects and see what that turns up

---

