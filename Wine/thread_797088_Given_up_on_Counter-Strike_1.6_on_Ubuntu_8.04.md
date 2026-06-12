---
title: "Given up on Counter-Strike 1.6 on Ubuntu 8.04"
date: 2008-05-16
forum: Wine
---

### Post by Joshgo on 2008-05-16
Hi, I have officially given up on playing counter-strike 1.6 using wine on ubuntu 8.04. Why? Because I have spent useless hours on looking up guides, threads on this forum, and even posted for help on running counter-strike on wine. The thing is, performance has decreased a good amount (not as bad as some people are experiencing) but it has made me give up hope on ever gaming on ubuntu. Diablo 2 seems to work but steam games seem to be unfriendly with wine and will not cooperate. I have looked up many different guides on performance tweaks, video card settings, etc... Nothing works. Seems like wine just isn't perfect. Hopefully, my dad will buy me a windows xp cd so I can go back to windows. Despite the "hard to get steam games running" ordeal, I love ubuntu. It is worth the effort looking up things and learning more. Too bad I will be switching back to windows xp as soon as I get a hold of an installing cd of windows. Why have I posted this? To vent out my frustration, and maybe someone might help me change my mind.

---

### Post by Twitch6000 on 2008-05-17
Just a word of advice,post your exact problems so noone flames you for being a and I quote MICROSOFT LOVER or LINUX HATER unquote.

---

### Post by Joshgo on 2008-05-17
Problems are no matter what I do I can never get the same performance ingame running wine on ubuntu than back when I used Windows. I get fps drops where I usually get 99 fps constant, even using same config, same settings, resolution, etc.. My video card drivers are up-to-date, I am using metacity, I have gone over this many times and nothing seems to work. And I read the thread "Stuff I've Learned about Wine" and it also adds that wine is not perfect and will sometimes do things such as less performance. Also, steam is pretty glitchy running on wine using gecko. When I message friends on steam, nothing shows up in the chat box "empty" I have installed fonts correctly too. The words in the chat box appears after being on steam for about 20 minutes and the glitch is gone until I restart steam again. I would really prefer windows xp where I had to install steam easily, and get great performance on it.

---

### Post by cogadh on 2008-05-17
I'm sorry to hear about your bad experience, but honestly, what did you really expect? Wine is still **beta software** and you should not expect it to work perfectly. Yes, a release candidate is out now, but even that is no where near close to a final product that is flawlessly equal to Windows. It really sounds like you set your expectations for Wine way too high, which will almost always lead to disappointment.

Additionally, it also sounds like you hit way too many out of date how-tos for Steam and its games. With current versions of Wine, you really don't have to do that much to get it running:
[LIST=1]
[*]Install the restricted drivers for your video card
[*]Install the winbind package
[*]Install Wine and create your .wine directory
[*]In Wine, install Gecko and Flash player
[*]Install Steam
[*]Install games in Steam
[/LIST]
That's it, Steam should work now. You don't really need to mess with fonts or any special "tweak" configurations, but some functions of Steam will still not work fully, due to Wine's incomplete status (voice chat, some of the friend features, etc.). Getting the game to run its best may require a bit of tweaking, depending on your hardware (if you have an ATI or Intel video card, it might require a lot of tweaking), but no matter what you do, it will definitely not work at the same level that the game could work on Windows with the same hardware. 

> **Twitch6000 said:**
> Just a word of advice,post your exact problems so noone flames you for being a and I quote MICROSOFT LOVER or LINUX HATER unquote.
I'm not sure what forums you are talking about, but behavior like that is not tolerated on these forums. If someone were to flame a frustrated poster over something like this, the mods would squash it very quickly and decisively.

---

### Post by Joshgo on 2008-05-17
Thanks for the advice cogadh, but to begin with on windows since I am using a Nvidia Geforce 5200 fx video card with 128 mb memory (pretty bad *** vid card in a negative way), I decided to find tweaks and play on lowest settings for best performance (I'm not too crazy about looks, just gameplay) and I played in lowest resolution, with lowest graphical settings. In windows, with those settings, I manage to get pretty good fps. Constant 99 fps in medium-small maps and with not too many people in the server. In ubuntu, My fps constantly drops here and there (it stays 99 pretty much until 1 person is in server, drops to 70) I am also using block models (really ugly models which look like lego character) and that didn't help much either. I rather not play cs than play it with constant fps drops ruining gameplay. You were also right about my expectations, I expected "better" performance on ubuntu because that's what I heard is better about linux than windows. But I forgot to realize that I should be grateful for wine because without it, I would never even have steam on linux.

---

### Post by cogadh on 2008-05-17
You did hear correctly, Linux will perform better than Windows, but that is really only true when you are talking about games that can be run natively in Linux (Doom 3, Neverwinter Nights, the UT games, etc.). When running non-native games through Wine, you can usually only expect adequate to nearly equal performance, depending on the game and your hardware.

---

### Post by hyperair on 2008-05-17
Hmm? Nvidia Geforce 5200 FX huh? I'm running on an Nvidia Geforce4 MX 440, and CS 1.6's performance on my computer is wonderful. Medium settings. Also, can you really notice any difference in gameplay with FPS above 60Hz? I highly doubt it. The human eye's limit is somewhere around 60Hz. Some may differ, but it's quite a small range. Unless you can visually see the difference without a FPS counter, I think you really shold avoid complaining about the FPS. Even for fast action movies, the FPS is around 30 only.

---

### Post by Cresho on 2008-05-17
I don't have a single problem what so ever.  Very easy to install and very easy to run.  FPS is the same on my system than on windows.  I'm lucky I guess.

> **Joshgo said:**
> Hi, I have officially given up on playing counter-strike 1.6 using wine on ubuntu 8.04. Why? Because I have spent useless hours on looking up guides, threads on this forum, and even posted for help on running counter-strike on wine. The thing is, performance has decreased a good amount (not as bad as some people are experiencing) but it has made me give up hope on ever gaming on ubuntu. Diablo 2 seems to work but steam games seem to be unfriendly with wine and will not cooperate. I have looked up many different guides on performance tweaks, video card settings, etc... Nothing works. Seems like wine just isn't perfect. Hopefully, my dad will buy me a windows xp cd so I can go back to windows. Despite the "hard to get steam games running" ordeal, I love ubuntu. It is worth the effort looking up things and learning more. Too bad I will be switching back to windows xp as soon as I get a hold of an installing cd of windows. Why have I posted this? To vent out my frustration, and maybe someone might help me change my mind.

listen...if you really want to get this running!  ASK!  Don't post stuff Here of stuff you don't understand.  Please list your...

OS
Wine version
graphics card
cpu
etc.

and we can tell you what you need.

if you launch it from terminal, what does it say?

---

### Post by YokoZar on 2008-05-17
Hey, I make the Wine packages for Ubuntu.

You're absolutely right that things can be frustrating as hell when they don't just work.

Wine is much better than it used to be, but we still run the user through completely arduous tasks just to do something as simple-seeming as playing counterstrike.  You have to learn about Wine.  Then install the Wine package.  Then you can't just double click the steam .msi file - you have to open a scary terminal and learn how to navigate to wherever you put the file and do wine msiexec /i.

Worse, it might not even work then.  You have to install Gecko, which needs to be downloaded. The automatic download might mysteriously fail.  Then after downloading your games, they might not just work.

So you go looking for help.  You find that you need to enable restricted drivers, and maybe you run across about 100 tutorials on Google aimed for obsolete versions of Wine running on 3 year old versions of Ubuntu.  It's all quite annoying.


All I can tell you is that I'm aware of it, and working on it.  Wine will be making its first ever actual non-beta release in a few weeks, and that version should become the "default" in a few ways (such as being in the Ubuntu-backports repository).  Installing the [winbind](apt://winbind) package like codagh recommends will be automatic (as Wine will "depend" on it).  There will still be bugs, but all known regressions from previous versions, including performance-related ones, should be fixed by then.

Diagnosing performance issues like the ones you've been getting are the toughest.  So many different things affect performance - drivers, bugs in the window manager, bugs in Wine, even seemingly unrelated features like desktop search can slow things down.  It should be no surprise that we receive a lot of mixed reports - a good chunk of users even report that Ubuntu+Wine runs substantially *better* than actual Windows.


So, I don't know what to tell you other than that I'm sorry it's so aggravating and I'm doing my best to make things easy.  As for immediate advice so you can play your games, you could give the latest 1.0 release candidate a try; or alternatively just enable the backports repository and wait a few weeks to try the actual 1.0 release.  If you do give up, though, there's a good chance things will be fixed by the next Ubuntu release, and I hope a few bugs in unfinished software don't scare you off Ubuntu for good.

---

### Post by Sleaka J on 2008-05-17
Steam client friends chat not working is a known bug in Wine.

[http://bugs.winehq.org/show_bug.cgi?id=9771](http://bugs.winehq.org/show_bug.cgi?id=9771)

---

### Post by cogadh on 2008-05-17
> **hyperair said:**
> Hmm? Nvidia Geforce 5200 FX huh? I'm running on an Nvidia Geforce4 MX 440, and CS 1.6's performance on my computer is wonderful. Medium settings. Also, can you really notice any difference in gameplay with FPS above 60Hz? I highly doubt it. The human eye's limit is somewhere around 60Hz. Some may differ, but it's quite a small range. Unless you can visually see the difference without a FPS counter, I think you really shold avoid complaining about the FPS. Even for fast action movies, the FPS is around 30 only.

That is actually a fallacy, there is no limit to the frames per second that the human eye can detect, since the human eye does not actually see by processing individual images like that. The higher the FPS, the smother and more fluid the animations in the game will appear. However, on a standard definition monitor, you probably won't really notice much of a difference between 60 to 100 FPS, the difference only really becomes noticeable on a high definition monitor, with HD quality graphics.

---

### Post by Frak on 2008-05-17
> **cogadh said:**
> That is actually a fallacy, there is no limit to the frames per second that the human eye can detect, since the human eye does not actually see by processing individual images like that. The higher the FPS, the smother and more fluid the animations in the game will appear. However, on a standard definition monitor, you probably won't really notice much of a difference between 60 to 100 FPS, the difference only really becomes noticeable on a high definition monitor, with HD quality graphics.
?

30FPS is the borderline to where your brain can notice fast moving images to  fluid motion. 40 fps is considered a *safe* bet. Anything over 90 is rediculous (and you are right, the eye can see improvements in framerate, but not much).

In terms of Hz of a monitor. 60 is the minimum to where the eye can no longer see refreshes on a small LCD monitor (17" or below) and 100 on larger ones (17" or above).

With HD, the Hz range has to be increased to accomodate the large amount of information of the screen, but only by about 15Hz.

---

### Post by Joshgo on 2008-05-17
There is a HUGE difference between 30-99 fps and 60-99 fps, other then the smooth and fluent screen, when I get stabbed in cs (I play in the CKL counter-strike knife league not gunning) with 60 fps or lower, I get stunned like crazy, the same with other players with lowers fps. Also, I can definitely tell the difference between hz. It hurts your eyes more when using 60 than 120. Back on windows, I could use 120 hz when I used 1024 x 768 or lower resolution (for 1152 x 868 - 1280 x 960 I could use 100 hz) but now I can only use 85 hz on ubuntu, despite the resolution I use (even using 320 x 175). Does anyone know the problem? This is another thing I've tried to solve, but I can't seem to figure it out. I remember back in windows if I used Plug and Play setting, I would only get a max hz of 85 like on ubuntu. If I am using plug and play, how do I change that? Also, I have posted 3 threads before on different problems giving specifications, and details on the issue. Few tried to solve my problem, but after that, the thread was not getting any replies. I also hope the next release of wine will fix my problem as Yokozar said.

If you guys can help, here is some information:
OS: Ubuntu 8.04
Processor: Pentium 4 2.6 Ghz
Display: Dell P991 CRT Screen
Video Card: Nvidia GeForce 5200 fx 128 mb memory
Wine Version: 1.0-rc1

Any help is greatly appreciated, also thanks for everyone who replied on this thread.
And, what is the winbind package? I installed it from the link Yokozar posted.

Note: I'm talking about refresh rate not FPS.

---

### Post by Frak on 2008-05-17
> **Joshgo said:**
> There is a HUGE difference between 30-99 fps and 60-99 fps, other then the smooth and fluent screen, when I get stabbed in cs (I play in the CKL counter-strike knife league not gunning) with 60 fps or lower, I get stunned like crazy, the same with other players with lowers fps. Also, I can definitely tell the difference between hz. It hurts your eyes more when using 60 than 120. Back on windows, I could use 120 hz when I used 1024 x 768 or lower resolution (for 1152 x 868 - 1280 x 960 I could use 100 hz) but now I can only use 85 hz on ubuntu, despite the resolution I use (even using 320 x 175). Does anyone know the problem? This is another thing I've tried to solve, but I can't seem to figure it out. I remember back in windows if I used Plug and Play setting, I would only get a max hz of 85 like on ubuntu. If I am using plug and play, how do I change that? Also, I have posted 3 threads before on different problems giving specifications, and details on the issue. Few tried to solve my problem, but after that, the thread was not getting any replies. I also hope the next release of wine will fix my problem as Yokozar said.

If you guys can help, here is some information:
OS: Ubuntu 8.04
Processor: Pentium 4 2.6 Ghz
Display: Dell P991 CRT Screen
Video Card: Nvidia GeForce 5200 fx 128 mb memory
Wine Version: 1.0-rc1

Any help is greatly appreciated, also thanks for everyone who replied on this thread.
And, what is the winbind package? I installed it from the link Yokozar posted.

Note: I'm talking about refresh rate not FPS.
Be aware that higher FPS can strain your system more. I have a 6800 in the one I'm on now, and its noticeable that I keep more decent framerates while running around 40-50 than 90 hard.

---

### Post by cogadh on 2008-05-17
> **Joshgo said:**
> There is a HUGE difference between 30-99 fps and 60-99 fps, other then the smooth and fluent screen, when I get stabbed in cs (I play in the CKL counter-strike knife league not gunning) with 60 fps or lower, I get stunned like crazy, the same with other players with lowers fps. Also, I can definitely tell the difference between hz. It hurts your eyes more when using 60 than 120. Back on windows, I could use 120 hz when I used 1024 x 768 or lower resolution (for 1152 x 868 - 1280 x 960 I could use 100 hz) but now I can only use 85 hz on ubuntu, despite the resolution I use (even using 320 x 175). Does anyone know the problem? This is another thing I've tried to solve, but I can't seem to figure it out. I remember back in windows if I used Plug and Play setting, I would only get a max hz of 85 like on ubuntu. If I am using plug and play, how do I change that? Also, I have posted 3 threads before on different problems giving specifications, and details on the issue. Few tried to solve my problem, but after that, the thread was not getting any replies. I also hope the next release of wine will fix my problem as Yokozar said.

If you guys can help, here is some information:
OS: Ubuntu 8.04
Processor: Pentium 4 2.6 Ghz
Display: Dell P991 CRT Screen
Video Card: Nvidia GeForce 5200 fx 128 mb memory
Wine Version: 1.0-rc1

Any help is greatly appreciated, also thanks for everyone who replied on this thread.
And, what is the winbind package? I installed it from the link Yokozar posted.

Note: I'm talking about refresh rate not FPS.

You monitor is probably not configured correctly in your xorg.conf. As long as your vertical and horizontal refresh rates are entered correctly in the xorg.conf, it should be able to do the same exact thing it does in Windows. However, the Nvidia driver does do a really weird thing to accommodate Nvidia's Dynamic Twin View functions. Basically it creates custom monitor configurations that report the wrong refresh rate to the OS, even though it is actually running at the correct refresh rate. For example, on my monitor, if it says it is running at 54Hz, that actually means 85Hz. You can make it report the correct refresh rate by editing your xorg.conf and adding this under the display adapter section:
```
Option	DynamicTwinView	"False"
```
Make sure you log out and restart the X server after making the change.

---

### Post by Joshgo on 2008-05-17
I'm not great with computers, especially with ubuntu because I'm a beginner, but how do I edit xorg.confg file? Do I use the command "sudo gedit xorg.conf" or something? I only know how to change the display settings using "gksudo nvidia-settings" I don't know about the other stuff. What is the command, or how do I edit the file? Thanks.

---

### Post by Cresho on 2008-05-17
I did not look back or read anytyhing but can you paste the output of your

type "glxinfo" without quotes into the terminal and hit enter.  then run "glxgears -info"  and then paste what you get as well.

---

### Post by Joshgo on 2008-05-17
glxinfo:

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_framebuffer_sRGB
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce FX 5200/AGP/SSE2
OpenGL version string: 2.1.2 NVIDIA 169.12
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, 
    GL_ARB_half_float_pixel, GL_ARB_imaging, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shadow, 
    GL_ARB_shader_objects, GL_ARB_shading_language_100, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, 
    GL_S3_s3tc, GL_EXT_texture_env_add, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_func_separate, GL_EXT_blend_minmax, 
    GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, GL_EXT_Cg_shader, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_blit, 
    GL_EXT_framebuffer_multisample, GL_EXT_framebuffer_object, 
    GL_EXT_gpu_program_parameters, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, 
    GL_EXT_paletted_texture, GL_EXT_pixel_buffer_object, 
    GL_EXT_point_parameters, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_shared_texture_palette, GL_EXT_stencil_two_side, 
    GL_EXT_stencil_wrap, GL_EXT_texture3D, GL_EXT_texture_compression_s3tc, 
    GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_sRGB, 
    GL_EXT_timer_query, GL_EXT_vertex_array, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_KTX_buffer_region, GL_NV_blend_square, 
    GL_NV_copy_depth_to_color, GL_NV_depth_clamp, GL_NV_fence, 
    GL_NV_float_buffer, GL_NV_fog_distance, GL_NV_fragment_program, 
    GL_NV_fragment_program_option, GL_NV_framebuffer_multisample_coverage, 
    GL_NV_half_float, GL_NV_light_max_exponent, GL_NV_multisample_filter_hint, 
    GL_NV_occlusion_query, GL_NV_packed_depth_stencil, GL_NV_pixel_data_range, 
    GL_NV_point_sprite, GL_NV_primitive_restart, GL_NV_register_combiners, 
    GL_NV_register_combiners2, GL_NV_texgen_reflection, 
    GL_NV_texture_compression_vtc, GL_NV_texture_env_combine4, 
    GL_NV_texture_expand_normal, GL_NV_texture_rectangle, 
    GL_NV_texture_shader, GL_NV_texture_shader2, GL_NV_texture_shader3, 
    GL_NV_vertex_array_range, GL_NV_vertex_array_range2, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_NV_vertex_program2, 
    GL_NV_vertex_program2_option, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SGIX_shadow, 
    GL_SUN_slice_accum

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x28 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x30 24 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x31 24 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x33 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x34 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x35 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x36 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x37 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x38 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x39 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x3a 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x3b 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x3c 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x3d 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x3e 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x3f 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x40 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x41 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x42 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x43 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x44 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x45 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x46 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0x47 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x48 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x49 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x4a 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0x4b 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x4c 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x4d 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x4e 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x4f 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x50 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x51 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x52 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x53 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x54 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x55 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x56 24 dc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x57 24 dc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x59 24 dc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x5a 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x5b 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x5c 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x5d 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x5e 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x5f 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x60 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x61 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x62 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x63 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x64 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x65 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x66 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x67 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x68 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x69 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x6a 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x6b 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x6c 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x6d 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0x6e 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x6f 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x70 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x71 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0x23 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x72 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x73 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x74 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x75 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x76 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x77 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x78 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x79 32 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x7a 32 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x7b 32 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x7c 32 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x7d 32 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x7e 32 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x7f 32 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x80 32 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x81 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x82 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x83 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x84 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x85 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x86 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x87 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x88 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x89 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x8a 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x8b 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x8c 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x8d 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x8e 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x8f 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x90 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x91 32 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x92 32 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x93 32 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x94 32 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0x95 32 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x96 32 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x97 32 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x98 32 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon






And glxgears -info:

GL_RENDERER   = GeForce FX 5200/AGP/SSE2
GL_VERSION    = 2.1.2 NVIDIA 169.12
GL_VENDOR     = NVIDIA Corporation
GL_EXTENSIONS = GL_ARB_depth_texture GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_half_float_pixel GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_framebuffer_object GL_EXT_gpu_program_parameters GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_paletted_texture GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_shared_texture_palette GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_sRGB GL_EXT_timer_query GL_EXT_vertex_array GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_copy_depth_to_color GL_NV_depth_clamp GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_framebuffer_multisample_coverage GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_texgen_reflection GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum 



P.S: Can anyone tell me what to check off and what to not check off in Nvidia X Server Settings if I want best performance? Examples: Sync to Vblank, Sync to Vblank on display device, Allow Flipping.

I am guessing one of those are Vsync.

---

### Post by Cresho on 2008-05-17
open up terminal and type nvidia-settings

under openGL settings, change image settings to High Performance.  come back and let me know how it went.  Under antialiasing settings, make sure you override antiliasing and keep off.  In  anisotropic filter, leave alone.

One questions?  are you running compiz?  if so, turn it off before starting counterstrike.  If this is your problem, ill show you how to create a easy script that will auto start game while disabling the compiz and reenabling it with no problems.

---

### Post by Joshgo on 2008-05-17
Is the correct way to edit xorg.conf using the command "nano /etc/X11/xorg.conf" as root? Or is there another way? And when I used the command "nano /etc/X11/xorg.conf" I didn't see the section named display adapter, but I saw "Screen", "Device", "Input Device", "Monitor", "ServerLayout", "Files", "Module", "ServerFlags". 

Note: There were multiple sections of the same name (there were 2 Input Device sections and 2 Device sections)

---

### Post by Joshgo on 2008-05-17
Like I mentioned, I uninstalled compiz (I don't want fancy smancy) and I am running on metacity. As for the things you told me to do, I already have done. High performance, and etc.. The other settings I'm not sure about is VBlank to Sync and those others.

---

### Post by cogadh on 2008-05-17
> **Joshgo said:**
> I'm not great with computers, especially with ubuntu because I'm a beginner, but how do I edit xorg.confg file? Do I use the command "sudo gedit xorg.conf" or something? I only know how to change the display settings using "gksudo nvidia-settings" I don't know about the other stuff. What is the command, or how do I edit the file? Thanks.
Make a backup copy of your exisitng xorg.conf:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg_backup
```
Open the original for editing:
```
sudo gedit /etc/X11/xorg.conf
```
Scroll down to the "Device" section. It should look something like this (NOTE: mine has been modified from the default):
```
Section "Device"
	Identifier	"Generic Video Card"
	Boardname	"NVIDIA GeForce 7 Series"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"DynamicTwinView"	"False"
	Vendorname	"NVIDIA"
EndSection
```
Add the Dynamic Twin View line as it appears above. Now scroll down to the "Monitor" section, it should look something like this (NOTE: again, mine is modified from the default):
```
Section "Monitor"
	Identifier	"Generic Monitor"
	Vendorname	"Samsung"
	Modelname	"Samsung SyncMaster 753DF(X)/703DF(X)/783DF(X)/CD173A(T)"
	Option		"DPMS"
	Horizsync	30-70
	Vertrefresh	50-160
	Gamma	1.0
EndSection
```
Verify that the "Horizsync" and "Vertrefresh" lines are correct for your monitor. You will need to get that info from the monitor's specs, either in an owner's manual or from the manufacturer's website. Once you have made any necessary modifications, save the file, log out and restart the X server (CTRL-ALT-BKSPC). 

If, for some reason, the Xserver doesn't start, reboot the PC, hit escape to get into the boot menu and select recovery. After it boots up to the command line, run this to restore the original working xorg.conf:
```
cp /etc/X11/xorg_backup /etc/X11/xorg.conf
```
Then reboot the PC (CTRL-ALT-DEL).

---

### Post by Cresho on 2008-05-17
post what you have in there here and well have a look at it.

do a

sudo gedit /etc/X11/xorg.conf

dont change anything because one small change will totally kill your system



How much ram are you running?  pc wize?  This question is important because if your running 256, you will have problems.  I'm not asking for video card memory.

---

### Post by cogadh on 2008-05-17
> **Cresho said:**
> dont change anything because one small change will totally kill your system
This is why I told him to make a backup of his xorg.conf right in the beginning (and how to restore it). The only change I suggested that might break xorg is the refresh rates, but as long as he has the right information, it won't.

---

### Post by Joshgo on 2008-05-17
I have 1gb of ram (1024 MB)

The problem is I have 2 Sections that say Section Device:


```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
EndSection
```

---

### Post by Cresho on 2008-05-17
> **cogadh said:**
> This is why I told him to make a backup of his xorg.conf right in the beginning (and how to restore it). The only change I suggested that might break xorg is the refresh rates, but as long as he has the right information, it won't.

thanks...it seems we posted at the same time!

---

### Post by Cresho on 2008-05-17
> **Joshgo said:**
> I have 1gb of ram (1024 MB)

The problem is I have 2 Sections that say Section Device:


```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
EndSection
```

this is interesting.  Ill look around.

My system tells me

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option         "NoLogo" "true"
EndSection

looks like conflicting stuff but I never encountered this before. This is a bumb!  just out of curiosity, does it have a tv tuner?

---

### Post by Joshgo on 2008-05-17
I have no clue what a tv turner is or whether it has one or not.

---

### Post by cogadh on 2008-05-17
> **Joshgo said:**
> I have 1gb of ram (1024 MB)

The problem is I have 2 Sections that say Section Device:


```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
EndSection
```

Scroll down to the "Screen" section, that will tell you which one of those (Device0 or Videocard0) xorg is actually using. Here's what mine looks like:
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
EndSection
```
Again, yours will be different, but it should very clearly indicate which "Device" entry is really being used.

---

### Post by Joshgo on 2008-05-17
```
Section "Screen"

# Removed Option "metamodes" "1600x1200_85 +0+0"
# Removed Option "metamodes" "1600x1200_85 +0+0; 1600x1200 +0+0"
# Removed Option "metamodes" "1600x1200 +0+0; 1600x1200_85 +0+0"
# Removed Option "metamodes" "1600x1200_85 +0+0; 1600x1200 +0+0"
# Removed Option "metamodes" "1280x1024 +0+0"
# Removed Option "metamodes" "1600x1200_85 +0+0"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1600x1200_85 +0+0; 1600x1200 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

So I'm guessing it's videocard0 right?

---

### Post by Joshgo on 2008-05-17
Well, I googled "Dell P991 CRT Sync Info" and got this:

[http://support.dell.com/support/edocs/monitors/p991/en/spec.htm](http://support.dell.com/support/edocs/monitors/p991/en/spec.htm)

And according to it, what I have down below is correct.

```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL P991"
    HorizSync       30.0 - 107.0
    VertRefresh     48.0 - 120.0
    Option         "DPMS"
EndSection

```

---

### Post by cogadh on 2008-05-17
Yep, that looks right and based on what you posted, xorg is using "Videocard0". You can probably just delete the other device entry, but just to be safe, you should comment it out (put "#" in front of each line).

---

### Post by Joshgo on 2008-05-17
I finished adding in the refresh rate display fix and it works! I didn't really need it (Cause I changed resolution from using "gksudo nvidia-settings" and saving the settings) but now I can fix it from System-Preference-Screen Resolution without having it say the wrong refresh rate! Thanks a lot! One problem down. Also, thanks a lot for the detailed step by step information, usually people instruct things as if I knew how to do the things (didn't show me how to do this, etc...)

---

### Post by Joshgo on 2008-05-17
> **cogadh said:**
> Yep, that looks right and based on what you posted, xorg is using "Videocard0". You can probably just delete the other device entry, but just to be safe, you should comment it out (put "#" in front of each line).

Like this?:

```
#Section "Device"
    #Identifier     "Device0"
    #Driver         "nvidia"
    #VendorName     "NVIDIA Corporation"
#EndSection

```


And I'm guessing windows displayed it wrong? Because it seems on windows using 85 refresh rate was a lot less smooth than on ubuntu. Maybe because it turns out I've been running 85 all along when I thought it was 120?

---

### Post by cogadh on 2008-05-17
Yep, that's exactly right.

I would guess  that Windows is somehow wrong, since that info page you linked shows your monitor has a max refresh of 85Hz.

---

