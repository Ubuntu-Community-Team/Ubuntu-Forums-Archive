---
title: "Diablo II: LOD Problems"
date: 2007-06-08
forum: Wine
---

### Post by Incarnadine on 2007-06-08
I just recently attempted to update Diablo II to LOD, but when I tried to start the setup.exe file with Wine it tells me that I have to install Diablo II first. I already have it installed though. I can play it and everything, but yet it says it's not installed and I can't update to the Expansion:( What's going on?

Another problem I have is that when I do play Diablo II it's at 3 FPS with my Radeon 9800. My guy is lagging all over the screen and it's unplayable. Does anyone have a solution to these problems? If you need more information please let me know. Oh and I am using the latest version of Wine with Ubuntu 7.04. Thanks for stopping by to read my problem.

---

### Post by Incarnadine on 2007-06-08
Ok i solved one problem. I enabled my ATI driver under the "Restricted Drivers Manger" and everything worked. I got a FPS of 130 and the game was looking smoother as ever. Looks even better then on Windows:popcorn: I just still can't install LOD because it says the game still isn't installed. Strange.

---

### Post by Incarnadine on 2007-06-08
I ran into another bug, but maybe this problem is just with me. When I am playing the game and I hold down Alt to see what's on the floor I can't pick up the items. In Windows you can hold Alt down and then pick stuff up, but not with Linux. Maybe Wine just doesn't allow it for some odd reason? Please try to do this yourself and see if you have the same problem. I switched the button to Tab and then I can properly pick stuff up, but Tab is horrible to use compared to Alt. If anyone has this problem please reply back. Most of all if you have a solution please tell;) Thanks.

---

### Post by lavs23 on 2007-06-08
I had the same problem you did.  I reinstalled Diablo II and before upgrading I installed LOD.  That seemed to work.  I also can't use Alt to view items because if you hold down Alt you move the windows.  I'm not sure if you can change that or not.

---

### Post by Incarnadine on 2007-06-08
Thanks for confirming that. Now I know it's just not me. I also noticed another thing though when I was playing. I can't enable the 3D EAX sound effects in the options. I have a Sound Audigy card and I used to play it the EAX enabled all the time with Windows, but i guess Wine doesn't use the EAX sounds. Maybe later? Or am I once again doing something wrong? What about you lavs23? You have the same problem?

Oh by the way I took your advice and reinstalled the game. Works perfectly now. Just the EAX thing and the Alt button now. Solving one issue at a time I guess. Hahahaha.....

---

### Post by Dritzen on 2007-06-08
I too had the ALT key problem. The solution for me was:

Go into a terminal and run winecfg
Click on Graphics at the top
Take the checkmark out of "Allow the window manager to manage created windows"

Click ok, then run Diablo2 and you can now use the Alt key to highlight and click items.  The catch is that you can no longer alt tab.  You can try but you'll lose keyboard control of the game.

Let me know if anyone figures out a better solution.

---

### Post by Incarnadine on 2007-06-08
Thanks it worked for me. I hope it worked for you too lavs23:popcorn:

What about the EAX problem? I think I am going to need a special driver for that or something. I saw that Ubuntu installed my Sound Audigy card, but I don't think it installed the features for the EAX sound. Or maybe it did, but Wine just doesn't utilize it. It has to be one of those.

---

### Post by Cappy on 2007-06-08
I don't think Linux has EAX support. I think Creative said they will add it on their release of their closed source X-Fi Linux Drivers.

---

### Post by Enverex on 2007-06-08
EAX: Wont work till the Linux sound drivers support it, which as you can tell is going to be some time if ever.

Alt-Click issue: Go into your window managers settings (Gnome or KDE) and find out how to turn off the "Hold Alt and click to drag" option. It's under "System >> Preferences >> Windows" in Gnome. Change it from Alt to something like Super Key (the Windows key).

---

### Post by lavs23 on 2007-06-08
I just went ahead and mapped the Alt key to a different key in Diablo II.  As for sound make sure the ALSA driver is enabled in winecfg.  Or maybe it's OSS I forget, either way one of them works one of them doesn't.

---

### Post by Enverex on 2007-06-08
> **lavs23 said:**
> I just went ahead and mapped the Alt key to a different key in Diablo II.  As for sound make sure the ALSA driver is enabled in winecfg.  Or maybe it's OSS I forget, either way one of them works one of them doesn't.

They both work.

---

### Post by jso2897 on 2007-06-10
I have a weird problem - I screwed up part of the instal, and aborted and deleted D2. Now when I try to install, when i input my CD key, it just freezes on that screen.  What did I do?:(

---

### Post by Enverex on 2007-06-10
> **jso2897 said:**
> I have a weird problem - I screwed up part of the instal, and aborted and deleted D2. Now when I try to install, when i input my CD key, it just freezes on that screen.  What did I do?:(

Try running in a virtual desktop (can't remember if that fixes it) or move the Diablo 2 installing Window BEFORE hand as it doesn't freeze, it asks for for the other disc, but the requester is actually behind the other windows.

---

### Post by Incarnadine on 2007-06-10
Ya jso2987 the prompt telling you to switch CD's during the install is hiding behind the menu. I had that problem too, but then I changed my Wine configuration and then it went away. Here is what I changed. Hope the screen shot helps.

---

### Post by Cappy on 2007-06-10
Except he would need to check "Virtual Desktop"

---

### Post by Incarnadine on 2007-06-10
This is the way I have it set up and I don't have any problems. The prompt comes up the way it's suppose to so I don't even have to move the windows looking for it. It sucks using the Virtual Desktop setting though because you can't play the game full screen. This isn't something I would suggest enabling.

---

### Post by Cappy on 2007-06-10
He only needs to enable it for the install. He IS having this problem (as I did) so he does need to enable it if he doesn't use the "move all the windows to the side before clicking okay on them" method.

---

### Post by jso2897 on 2007-06-10
I got around it by using another CD key. It just wouldn't accept the same one twice. I have finally gotten Diablo2 and LOD loaded and playing (in No-cd mode). It plays pretty well - as well as it played on this machine when it was running windows. I have heard some rare and intermittant sound chop - but nothing serious. I don't listen to the music anyway.
As far as the "insert CD: screen hiding - it wasn't there at all - I had to deduce which disks to put in when based on when the loading stopped and the drive stopped spinning - but, hey, if it works...:p

---

### Post by Incarnadine on 2007-06-11
Diablo II loads flawlessly now for me thanks to you guys, but for some reason I get these really hard video lag spikes. When a bunch of people get on my screen everything gets choppy as hell and I almost die. I know this isn't a problem with my hardware because on Windows I never experienced anything like this before. Maybe my video card has to be updated? I went to the ATI website and noticed that they don't offer updates for Ubuntu. So then I did a update, but it said my computer was up to date. What could be wrong? Oh and I did also activate my Restricted Drivers already. That already made a improvement for me, but still choppy for some reason](*,)

---

### Post by Enverex on 2007-06-11
ATi DOES have Linux drivers on their Website. The ones in Fiesty are very outdated to be honest. What version of Wine are you using anyway?

---

### Post by Incarnadine on 2007-06-11
I'm currently using Wine 0.9.33. Yes I seen the Linux ATI drivers on there website, but they aren't for Ubuntu. They are for a Linux OS called X or something like that. I see that on your signature there is a newer version of Wine then what I have, but yet when I run my updates I don't get a newer version.  Am I missing something?  Thanks for the help:popcorn:

---

### Post by Incarnadine on 2007-06-13
Ok I managed to solve some of these problems myself. About the Wine update I got the latest Wine from [www.winehq.com](www.winehq.com). I added the respiratory to my list and downloaded the latest version. About my video card driver I did some research and found that "fglrx" is what I need for my video card. It turns out though that I already have it installed so I'm still wondering why Diablo II doesn't play as smooth as it did on Windows for me. When I do a shout with my Barbarian even that looks choppy. Any ideas anyone?

---

### Post by Enverex on 2007-06-13
> **Incarnadine said:**
> I'm currently using Wine 0.9.33. Yes I seen the Linux ATI drivers on there website, but they aren't for Ubuntu. They are for a Linux OS called X or something like that

*falls out of his chair laughing*

---

### Post by Incarnadine on 2007-06-13
I guess that shows just how much I know about Linux. Since you laughed at me I looked into this X Free 86 and found out it isn't a distribution of Linux, but just a part of the OS.  Big ooops on my part, but I guess the more I deal with Linux the more I know. Apart from laughing at me though did any ideas popup in your head on why my game is so laggy? Any help would be great.

---

### Post by Enverex on 2007-06-13
> **Incarnadine said:**
> I guess that shows just how much I know about Linux. Since you laughed at me I looked into this X Free 86 and found out it isn't a distribution of Linux, but just a part of the OS.  Big ooops on my part, but I guess the more I deal with Linux the more I know. Apart from laughing at me though did any ideas popup in your head on why my game is so laggy? Any help would be great.

Paste the output of "glxinfo" and that should tell us what's going on with your graphics card.

---

### Post by yosser on 2007-06-13
> **Enverex said:**
> *falls out of his chair laughing*

way to be helpful.

---

### Post by Citizin on 2007-06-13
I had the same problem, then I started using Crossover (For Linux, not OSX) and I can run almost any windows game/app and better then WINE does.

---

### Post by Enverex on 2007-06-13
> **Citizin said:**
> I had the same problem, then I started using Crossover (For Linux, not OSX) and I can run almost any windows game/app and better then WINE does.

The only reason that would be true would be if you're using an old version of Wine. Crossover is Wine + Hacks to make certain things work and commercial support.

> **yosser said:**
> way to be helpful.

I've already posted what he needs to do to get help now. Way to not contribute to the thread at all.

---

### Post by Incarnadine on 2007-06-14
Post my "glxinfo" info!? You have got to be kidding me. Hahahahaha....I can't make anything out of this information:( I hope you can see what the problem is. Thanks for taking the time.

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
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample, 
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro
OpenGL version string: 2.0.6334 (8.34.8)
OpenGL extensions:
    GL_ARB_multitexture, GL_EXT_texture_env_add, GL_EXT_compiled_vertex_array, 
    GL_S3_s3tc, GL_ARB_depth_texture, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, 
    GL_ARB_multisample, GL_ARB_occlusion_query, GL_ARB_point_parameters, 
    GL_ARB_point_sprite, GL_ARB_shader_objects, GL_ARB_shading_language_100, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_float, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_blend, 
    GL_ARB_vertex_buffer_object, GL_ARB_pixel_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, 
    GL_ARB_draw_buffers, GL_ATI_draw_buffers, GL_ATI_element_array, 
    GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader, GL_ATI_map_object_buffer, 
    GL_ATI_separate_stencil, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_float, GL_ATI_texture_mirror_once, 
    GL_ATI_vertex_array_object, GL_ATI_vertex_attrib_array_object, 
    GL_ATI_vertex_streams, GL_ATIX_texture_env_combine3, 
    GL_ATIX_texture_env_route, GL_ATIX_vertex_shader_output_point_size, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_texgen_reflection, GL_EXT_texture3D, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_EXT_vertex_shader, GL_HP_occlusion_test, GL_NV_blend_square, 
    GL_NV_occlusion_query, GL_NV_texgen_reflection, GL_SGI_color_matrix, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

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
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x31 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x33 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x34 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x35 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x36 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x37 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x38 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x39 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x3a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x3b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x40 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x41 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x42 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x43 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x44 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x45 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x46 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x47 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x48 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x49 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x4a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
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
0x57 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x59 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x5a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x5b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x60 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x61 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x62 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None

---

### Post by Enverex on 2007-06-14
That basically tells us that your graphics card is working and that 3D OpenGL hardware accelleration is turned on. Do you have Diablo 2 set up to use DirectDraw or Direct3D? (it's the d2vidtest.exe or something in the Diablo 2 folder).

---

### Post by Incarnadine on 2007-06-14
Hhhhhmmmm..........this is interesting. I had it set on Direct3D, but that's what I used when I had Windows XP installed and I had no lag, but now that I switched it over to DirectDraw it seems to run fine with no lag. Why is that you think? Does Direct3D not run good on Wine? If that's the case no problems here. I'm fine on DirectDraw:p

Here's a little something else to add. When I first installed the game I didn't get the option to even select DirectDraw when I did the Video Test for Diablo II. Why does it appear now?

---

### Post by Citizin on 2007-06-15
Well I installed D2 on Crossover and it seemed to ask me, I think I did it in WINE as well and same thing there. Well, at least you fixed the problem :) Maybe we can play sometime, whenever I get my video card problem fixed -_-

---

### Post by Enverex on 2007-06-15
> **Incarnadine said:**
> Hhhhhmmmm..........this is interesting. I had it set on Direct3D, but that's what I used when I had Windows XP installed and I had no lag, but now that I switched it over to DirectDraw it seems to run fine with no lag. Why is that you think? Does Direct3D not run good on Wine? If that's the case no problems here. I'm fine on DirectDraw:p

Here's a little something else to add. When I first installed the game I didn't get the option to even select DirectDraw when I did the Video Test for Diablo II. Why does it appear now?

Actually I was expecting the opposite but ah well. Wine is still quirky as are Linux graphics drivers.

---

### Post by ljonesj on 2007-07-01
okay i got wine installed how do i go about installing diablo 2 on my machine running feisty
never mind i got wine running but when diablo2 goes threw were to install were do i put it and if i just chose a place it just sits at the install screen and does nothing cd rom stops spinning and no light and it locks that screen up and it cannot be got off unless i restart i would love to get everything changed over from windows to ubuntu but my games are what i am worried about

---

### Post by Diabolis on 2009-02-14
For the **alt** problem:
gconf-editor
then:
apps / metacity / general / mouse_button_modifier

I change mine to **<super>** and then **restarted** D2, now I can pick up items with **alt**.

---

