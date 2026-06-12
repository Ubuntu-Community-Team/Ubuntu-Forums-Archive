---
title: "Jedi Academy Graphics"
date: 2008-01-03
forum: Wine
---

### Post by GOB1029 on 2008-01-03
Hey all,

I'm pretty new to Ubuntu, but managed to install Jedi Academy through Wine w/out any problems.  It installed fine, the game loads fine, but once I get in-game (SP), the cutscenes and actual gameplay graphics are horribly distorted.  I'm not sure where the issue lies.

I'm using Ubuntu 7.10, Gutsy.  My video card is ATI Radion X1200 series.  I have Wine 0.9.46.

If you need more info, let me know.

I'd really appreciate ANY ideas, I've attached a screenshot of what the game looks like.

---

### Post by kade on 2008-01-04
Can you please post what console output you get when the game is running?

Also, are you running with the default wine libraries, or have you installed some from a windows install?

---

### Post by GOB1029 on 2008-01-05
> JA: v1.0.1.0 win-x86 Oct 24 2003
Initialising zone memory .....
----- FS_Startup -----
Current search path:
C:\JK3\GameData\base\assets3.pk3 (16 files)
C:\JK3\GameData\base\assets2.pk3 (62 files)
C:\JK3\GameData\base\assets1.pk3 (8320 files)
C:\JK3\GameData\base\assets0.pk3 (15346 files)
C:\JK3\GameData/base

----------------------
23744 files in pk3 files
execing default.cfg
couldn't exec autoexec.cfg
...detecting CPU, found AMD w/ 3DNow!

------- Input Initialization -------
Skipping check for DirectInput
Joystick is not active.
------------------------------------
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
--- Common Initialization Complete ---
Working directory: C:\JK3\GameData
couldn't exec setlanguage.cfg
Initializing OpenGL subsystem
...initializing QGL
succeeded
...setting mode 4: 800 600 FS
...using desktop display depth of 24
...calling CDS: ok
...registered window class
...created window@0,0 (800x600)
Initializing OpenGL driver
...getting DC: succeeded
...GLW_ChoosePFD( 24, 24, 8 )
...0 PFDs found
...hardware acceleration found
...PIXELFORMAT 1 selected
...creating GL context: succeeded
...making context current: succeeded
Initializing OpenGL extensions
...no supported texture compression method found
.....ignoring texture compression
...using GL_EXT_texture_env_add
...GL_EXT_texture_filter_anisotropic not found
...using WGL_EXT_swap_control
...using GL_ARB_multitexture
...GL_EXT_compiled_vertex_array not found
...GL_EXT_point_parameters not found
...GL_NV_point_sprite not found
...GL_NV_register_combiners not found
...GL_ARB_vertex_program not found
...GL_ARB_fragment_program not found
execing low.cfg
Initializing OpenGL extensions
...no supported texture compression method found
.....ignoring texture compression
...using GL_EXT_texture_env_add
...GL_EXT_texture_filter_anisotropic not found
...using WGL_EXT_swap_control
...using GL_ARB_multitexture
...GL_EXT_compiled_vertex_array not found
...GL_EXT_point_parameters not found
...GL_NV_point_sprite not found
...GL_NV_register_combiners not found
...GL_ARB_vertex_program not found
...GL_ARB_fragment_program not found

GL_VENDOR: ATI Technologies Inc.
GL_RENDERER: ATI Radeon X1200 Series
GL_VERSION: 1.2 (2.0.6473 (8.37.6))
GL_EXTENSIONS:  GL_ARB_multitexture GL_ARB_texture_border_clamp
GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine
GL_ARB_texture_env_dot3 GL_ARB_transpose_matrix GL_EXT_abgr
GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract
GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3
GL_EXT_texture_lod_bias
GL_MAX_TEXTURE_SIZE: 2048
GL_MAX_ACTIVE_TEXTURES_ARB: 8

PIXELFORMAT: color(32-bits) Z(24-bit) stencil(8-bits)
MODE: 3, 800 x 600 fullscreen hz:60
GAMMA: software w/ 0 overbright bits
CPU: AMD w/ 3DNow!
rendering primitives: multiple glArrayElement
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 2
texture bits: 16
lightmap texture bits: 0
multitexture: enabled
compiled vertex arrays: disabled
texenv add: enabled
compressed textures: disabled
compressed lightmaps: disabled
texture compression method: None
anisotropic filtering: disabled  (0.000000 of 0.000000)
Dynamic Glow: disabled

------- sound initialization -------
Initializing DirectSound
locked hardware.  ok
s_khz will be changed upon restarting.
r_detailtextures will be changed upon restarting.
r_subdivisions will be changed upon restarting.
r_depthbits will be changed upon restarting.
r_noportals is cheat protected.
------ Server Initialization ------
JA: v1.0.1.0 win-x86 Oct 24 2003
Server: yavin1
Loading shader text .....
..... 3391 shader definitions loaded
------- Game Initialization -------
gamename: base
gamedate: Oct 24 2003
Warning: cvar "g_spskill" given initial values: "1" and "0"
-----------------------------------
-----------------------------------
...loaded 1877 faces, 58 meshes, 134 trisurfs, 0 flares
------ Server Initialization ------
JA: v1.0.1.0 win-x86 Oct 24 2003
Server: yavin1b
------- Game Initialization -------
gamename: base
gamedate: Oct 24 2003
Warning: cvar "g_spskill" given initial values: "1" and "0"
-----------------------------------
-----------------------------------
Skipping cinematic...
...loaded 818 faces, 26 meshes, 150 trisurfs, 0 flares
Skipping cinematic...
Saving game "auto"...
Done.
]condump winerror.txt
Dumped console text to winerror.txt.


I'm running default Wine, at least I believe so, as I just downloaded it from the repositories and installed it. (Again, I'm completely new to all of this)

---

### Post by kade on 2008-01-09
Thanks for posting that output, however, I actually meant for you to post the console output from wine.  In other words, when you run JA from the command line using wine, what is the command line output from wine?  This is the the information that can help solve your problem.

Also, have you tried looking up JA in the Wine AppDB?  Here's a link to JA entry on the website:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=2315]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=2315")

It's an excellent resource for compatibility and instructions for helping run many games and apps in wine.  JA has been awarded the highest award for compatibility, so I think you have a good chance of finding a solution to you problem.

---

### Post by intel on 2008-01-19
You may ask the support group for ATI Radeon X1200 series at

https://groups.google.com/group/x1250

other users there who have faced a similar problem will help you out.

---

### Post by mikedep333 on 2008-01-19
What graphics driver are you using? The one from the restricted drivers manager?

It may help to install the very latest ati driver.
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-117effcb5f0fbe8e10f40881bff1dbf7824a77b0](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-117effcb5f0fbe8e10f40881bff1dbf7824a77b0)

---

