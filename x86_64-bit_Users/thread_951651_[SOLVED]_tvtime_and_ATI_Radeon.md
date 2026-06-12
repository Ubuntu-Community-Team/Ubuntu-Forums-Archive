---
title: "[SOLVED] tvtime and ATI Radeon"
date: 2008-10-18
forum: x86 64-bit Users
---

### Post by mfehr on 2008-10-18
I created a fresh computer using the ASUS M3A78 PRO motherboard with integrated ATI Radeon HD 3450 (aticonfig shows HD 3200). I installed Ubuntu 8.04.1 64 Bit and applied the Catalyst 8.10 video drivers. I also installed tvtime.

The live TV display is working ok in full screen mode. However, running tvtime in a window causes the display to flicker (tv signal is replaced by black and vice versa; multiple times per second). The TV tuner is a Haupage model. Any hints how I can get this to work properly?

---

### Post by soxs on 2008-10-18
> **mfehr said:**
> I created a fresh computer using the ASUS M3A78 PRO motherboard with integrated ATI Radeon HD 3450 (aticonfig shows HD 3200). I installed Ubuntu 8.04.1 64 Bit and applied the Catalyst 8.10 video drivers. I also installed tvtime.

The live TV display is working ok in full screen mode. However, running tvtime in a window causes the display to flicker (tv signal is replaced by black and vice versa; multiple times per second). The TV tuner is a Haupage model. Any hints how I can get this to work properly?

what drivers d you have installed?
fglrx

post the output from:
```
glxinfo
```
```
fglrxinfo
```
```
cat /etc/X11/xorg.conf
```
In code tags!

---

### Post by mfehr on 2008-10-19
Here we go:

**glxinfo:**

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
OpenGL version string: 2.1.8087 Release
OpenGL extensions:
    GL_AMD_performance_monitor, GL_ARB_color_buffer_float, 
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_draw_instanced, 
    GL_ARB_fragment_program, GL_ARB_fragment_shader, GL_ARB_half_float_pixel, 
    GL_ARB_half_float_vertex, GL_ARB_instanced_arrays, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shader_objects, 
    GL_ARB_shader_texture_lod, GL_ARB_shading_language_100, GL_ARB_shadow, 
    GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_float, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, 
    GL_ATI_draw_buffers, GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader, 
    GL_ATI_meminfo, GL_ATI_separate_stencil, GL_ATI_texture_compression_3dc, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_float, GL_EXT_abgr, 
    GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_equation_separate, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_compiled_vertex_array, GL_EXT_copy_texture, 
    GL_EXT_depth_buffer_float, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXT_framebuffer_object, GL_EXT_gpu_program_parameters, 
    GL_EXT_gpu_shader4, GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_float, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texgen_reflection, GL_EXT_texture3D, 
    GL_EXT_texture_compression_latc, GL_EXT_texture_compression_rgtc, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, 
    GL_EXT_texture_shared_exponent, GL_EXT_vertex_array, GL_KTX_buffer_region, 
    GL_NV_blend_square, GL_NV_texgen_reflection, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_WIN_swap_hint, 
    WGL_EXT_swap_control

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
0x89 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  4 1 Ncon

```

**fglrxinfo:**
```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3200 Graphics
OpenGL version string: 2.1.8087 Release

```

**/etc/X11/xorg.conf:**
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

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "ch"
	Option	    "XkbVariant" "de_mac"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:5:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection


```

---

### Post by soxs on 2008-10-20
Ok, add this inot the device section (perferably at the end of it) in your /etc/X11/xorg.conf

```
### Driver / Performance Options
	Option		"XAANoOffscreenPixmaps"	"1"
	Option		"TexturedVideo"		"1"
	Option		"TexturedVideoSync"	"1"
	Option		"Textured2D"		"1"
	Option		"TexturedXRender"	"1"
	Option		"DRI"			"1"
	Option		"UseInternalAGPGART"	"1"
	Option		"BackingStore"		"1"
	Option		"OpenGLOverlay"		"0"
	Option		"VideoOverlay"		"1"
```
You may try to play around with bakingstore, as it sometimes will render garbage and internal AGP gart though I never felt a real difference between those

---

### Post by mfehr on 2008-10-20
Hi,

thanks for your prompt response. I altered the xorg.conf file as menionned. I understood that the options become part of the device section. This section now looks as follows:

```
Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:5:0"
### Driver / Performance Options
	Option		"XAANoOffscreenPixmaps"	"1"
	Option		"TexturedVideo"		"1"
	Option		"TexturedVideoSync"	"1"
	Option		"Textured2D"		"1"
	Option		"TexturedXRender"	"1"
	Option		"DRI"			"1"
	Option		"UseInternalAGPGART"	"1"
	Option		"BackingStore"		"1"
	Option		"OpenGLOverlay"		"0"
	Option		"VideoOverlay"		"1"
EndSection

```

Starting the server with these settings causes 6 failed attempts to load X. You can see the login panel for half a second (in correct resolution), followed by a resolution change and various differnet colours (like in the good old CGA-resolution days) on the entire screen for another second. After this, the text-display is shown again. Finally, after 6 attempts, a text based message box is displayed, informing that it will try in 2 minutes. - I tried to reduce the parameters in different combinations with no success. All tested options did not allow a login from the X login panel.

The Xorg.0.log for all options enabled looks as follows:

```


This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux myserver 2.6.24-21-generic #1 SMP Mon Aug 25 16:57:51 UTC 2008 x86_64
Build Date: 13 June 2008  01:10:57AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Oct 20 20:04:37 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "aticonfig-Screen[0]-0" (0)
(**) |   |-->Monitor "aticonfig-Monitor[0]-0"
(**) |   |-->Device "aticonfig-Device[0]-0"
(==) Automatically adding devices
(==) Automatically enabling devices
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
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
	Using the first core pointer device.
(==) The core keyboard device wasn't specified explicitly in the layout.
	Using the first keyboard device.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7bd660
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1022,9600 card 1002,7910 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1022,9602 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:06:0: chip 1022,9606 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:11:0: chip 1002,4390 card 1043,82f1 rev 00 class 01,06,01 hdr 00
(II) PCI: 00:12:0: chip 1002,4397 card 1002,4397 rev 00 class 0c,03,10 hdr 80
(II) PCI: 00:12:1: chip 1002,4398 card 1002,4398 rev 00 class 0c,03,10 hdr 00
(II) PCI: 00:12:2: chip 1002,4396 card 1002,4397 rev 00 class 0c,03,20 hdr 00
(II) PCI: 00:13:0: chip 1002,4397 card 1002,4398 rev 00 class 0c,03,10 hdr 80
(II) PCI: 00:13:1: chip 1002,4398 card 1002,4399 rev 00 class 0c,03,10 hdr 00
(II) PCI: 00:13:2: chip 1002,4396 card 1002,4396 rev 00 class 0c,03,20 hdr 00
(II) PCI: 00:14:0: chip 1002,4385 card 1043,82f1 rev 3a class 0c,05,00 hdr 80
(II) PCI: 00:14:1: chip 1002,439c card 1043,82f1 rev 00 class 01,01,8a hdr 00
(II) PCI: 00:14:2: chip 1002,4383 card 1043,82fe rev 00 class 04,03,00 hdr 00
(II) PCI: 00:14:3: chip 1002,439d card 1002,4383 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:14:4: chip 1002,4384 card 0000,0000 rev 00 class 06,04,01 hdr 81
(II) PCI: 00:14:5: chip 1002,4399 card 1002,4396 rev 00 class 0c,03,10 hdr 00
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:05:0: chip 1002,9610 card 1043,82f1 rev 00 class 03,00,00 hdr 80
(II) PCI: 01:05:1: chip 1002,960f card 1002,960f rev 00 class 04,03,00 hdr 80
(II) PCI: 02:00:0: chip 10ec,8168 card 1043,82c6 rev 02 class 02,00,00 hdr 00
(II) PCI: 03:05:0: chip 109e,036e card 11bd,0012 rev 11 class 04,00,00 hdr 80
(II) PCI: 03:05:1: chip 109e,0878 card 11bd,0012 rev 11 class 04,80,00 hdr 80
(II) PCI: 03:06:0: chip 10ec,8169 card 10ec,8169 rev 10 class 02,00,00 hdr 00
(II) PCI: 03:07:0: chip 10ec,8139 card 10bd,0320 rev 10 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,3), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x001a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfe800000 - 0xfe9fffff (0x200000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:6:0), (0,2,2), BCTRL: 0x0003 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfea00000 - 0xfeafffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xfde00000 - 0xfdefffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:20:3), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:20:4), (0,3,3), BCTRL: 0x0003 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000e000 - 0x0000efff (0x1000) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xfeb00000 - 0xfebfffff (0x100000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0xfdf00000 - 0xfdffffff (0x100000) MX[B]
(--) PCI:*(1:5:0) ATI Technologies Inc unknown chipset (0x9610) rev 0, Mem @ 0xd0000000/28, 0xfe9f0000/16, 0xfe800000/20, I/O @ 0xc000/8
(--) PCI: (3:5:0) Brooktree Corporation Bt878 Video Capture rev 17, Mem @ 0xfdfff000/12
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xfebff800 - 0xfebff8ff (0x100) MX[B]
	[1] -1	0	0xfebffc00 - 0xfebffcff (0x100) MX[B]
	[2] -1	0	0xfdffe000 - 0xfdffefff (0x1000) MX[B]
	[3] -1	0	0xfdef0000 - 0xfdefffff (0x10000) MX[B]
	[4] -1	0	0xfeaff000 - 0xfeafffff (0x1000) MX[B]
	[5] -1	0	0xfe9e8000 - 0xfe9ebfff (0x4000) MX[B]
	[6] -1	0	0xfe7f9000 - 0xfe7f9fff (0x1000) MX[B]
	[7] -1	0	0xfe7f4000 - 0xfe7f7fff (0x4000) MX[B]
	[8] -1	0	0xfe7fa800 - 0xfe7fa8ff (0x100) MX[B]
	[9] -1	0	0xfe7fb000 - 0xfe7fbfff (0x1000) MX[B]
	[10] -1	0	0xfe7fc000 - 0xfe7fcfff (0x1000) MX[B]
	[11] -1	0	0xfe7ff000 - 0xfe7ff0ff (0x100) MX[B]
	[12] -1	0	0xfe7fd000 - 0xfe7fdfff (0x1000) MX[B]
	[13] -1	0	0xfe7fe000 - 0xfe7fefff (0x1000) MX[B]
	[14] -1	0	0xfe7ff800 - 0xfe7ffbff (0x400) MX[B]
	[15] -1	0	0xfdfff000 - 0xfdffffff (0x1000) MX[B](B)
	[16] -1	0	0xfe800000 - 0xfe8fffff (0x100000) MX[B](B)
	[17] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[18] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[19] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[20] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[22] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x00007000 - 0x0000700f (0x10) IX[B]
	[28] -1	0	0x00008000 - 0x00008003 (0x4) IX[B]
	[29] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[30] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[31] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[32] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfebff800 - 0xfebff8ff (0x100) MX[B]
	[1] -1	0	0xfebffc00 - 0xfebffcff (0x100) MX[B]
	[2] -1	0	0xfdffe000 - 0xfdffefff (0x1000) MX[B]
	[3] -1	0	0xfdef0000 - 0xfdefffff (0x10000) MX[B]
	[4] -1	0	0xfeaff000 - 0xfeafffff (0x1000) MX[B]
	[5] -1	0	0xfe9e8000 - 0xfe9ebfff (0x4000) MX[B]
	[6] -1	0	0xfe7f9000 - 0xfe7f9fff (0x1000) MX[B]
	[7] -1	0	0xfe7f4000 - 0xfe7f7fff (0x4000) MX[B]
	[8] -1	0	0xfe7fa800 - 0xfe7fa8ff (0x100) MX[B]
	[9] -1	0	0xfe7fb000 - 0xfe7fbfff (0x1000) MX[B]
	[10] -1	0	0xfe7fc000 - 0xfe7fcfff (0x1000) MX[B]
	[11] -1	0	0xfe7ff000 - 0xfe7ff0ff (0x100) MX[B]
	[12] -1	0	0xfe7fd000 - 0xfe7fdfff (0x1000) MX[B]
	[13] -1	0	0xfe7fe000 - 0xfe7fefff (0x1000) MX[B]
	[14] -1	0	0xfe7ff800 - 0xfe7ffbff (0x400) MX[B]
	[15] -1	0	0xfdfff000 - 0xfdffffff (0x1000) MX[B](B)
	[16] -1	0	0xfe800000 - 0xfe8fffff (0x100000) MX[B](B)
	[17] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[18] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[19] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[20] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[22] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x00007000 - 0x0000700f (0x10) IX[B]
	[28] -1	0	0x00008000 - 0x00008003 (0x4) IX[B]
	[29] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[30] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[31] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[32] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfebff800 - 0xfebff8ff (0x100) MX[B]
	[5] -1	0	0xfebffc00 - 0xfebffcff (0x100) MX[B]
	[6] -1	0	0xfdffe000 - 0xfdffefff (0x1000) MX[B]
	[7] -1	0	0xfdef0000 - 0xfdefffff (0x10000) MX[B]
	[8] -1	0	0xfeaff000 - 0xfeafffff (0x1000) MX[B]
	[9] -1	0	0xfe9e8000 - 0xfe9ebfff (0x4000) MX[B]
	[10] -1	0	0xfe7f9000 - 0xfe7f9fff (0x1000) MX[B]
	[11] -1	0	0xfe7f4000 - 0xfe7f7fff (0x4000) MX[B]
	[12] -1	0	0xfe7fa800 - 0xfe7fa8ff (0x100) MX[B]
	[13] -1	0	0xfe7fb000 - 0xfe7fbfff (0x1000) MX[B]
	[14] -1	0	0xfe7fc000 - 0xfe7fcfff (0x1000) MX[B]
	[15] -1	0	0xfe7ff000 - 0xfe7ff0ff (0x100) MX[B]
	[16] -1	0	0xfe7fd000 - 0xfe7fdfff (0x1000) MX[B]
	[17] -1	0	0xfe7fe000 - 0xfe7fefff (0x1000) MX[B]
	[18] -1	0	0xfe7ff800 - 0xfe7ffbff (0x400) MX[B]
	[19] -1	0	0xfdfff000 - 0xfdffffff (0x1000) MX[B](B)
	[20] -1	0	0xfe800000 - 0xfe8fffff (0x100000) MX[B](B)
	[21] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[22] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[25] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[26] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[27] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[28] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[33] -1	0	0x00007000 - 0x0000700f (0x10) IX[B]
	[34] -1	0	0x00008000 - 0x00008003 (0x4) IX[B]
	[35] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[36] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[37] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[38] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded by default.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
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
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.1.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.54.3
	Module class: X.Org Video Driver
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) Primary Device is: PCI 01:05:0
(II) ATI Proprietary Linux Driver Version Identifier:8.54.3
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.542                    
(II) ATI Proprietary Linux Driver Build Date: Oct  3 2008 17:42:58
(--) Chipset Supported AMD Graphics Processor (0x9610) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfebff800 - 0xfebff8ff (0x100) MX[B]
	[5] -1	0	0xfebffc00 - 0xfebffcff (0x100) MX[B]
	[6] -1	0	0xfdffe000 - 0xfdffefff (0x1000) MX[B]
	[7] -1	0	0xfdef0000 - 0xfdefffff (0x10000) MX[B]
	[8] -1	0	0xfeaff000 - 0xfeafffff (0x1000) MX[B]
	[9] -1	0	0xfe9e8000 - 0xfe9ebfff (0x4000) MX[B]
	[10] -1	0	0xfe7f9000 - 0xfe7f9fff (0x1000) MX[B]
	[11] -1	0	0xfe7f4000 - 0xfe7f7fff (0x4000) MX[B]
	[12] -1	0	0xfe7fa800 - 0xfe7fa8ff (0x100) MX[B]
	[13] -1	0	0xfe7fb000 - 0xfe7fbfff (0x1000) MX[B]
	[14] -1	0	0xfe7fc000 - 0xfe7fcfff (0x1000) MX[B]
	[15] -1	0	0xfe7ff000 - 0xfe7ff0ff (0x100) MX[B]
	[16] -1	0	0xfe7fd000 - 0xfe7fdfff (0x1000) MX[B]
	[17] -1	0	0xfe7fe000 - 0xfe7fefff (0x1000) MX[B]
	[18] -1	0	0xfe7ff800 - 0xfe7ffbff (0x400) MX[B]
	[19] -1	0	0xfdfff000 - 0xfdffffff (0x1000) MX[B](B)
	[20] -1	0	0xfe800000 - 0xfe8fffff (0x100000) MX[B](B)
	[21] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[22] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[25] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[26] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[27] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[28] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[33] -1	0	0x00007000 - 0x0000700f (0x10) IX[B]
	[34] -1	0	0x00008000 - 0x00008003 (0x4) IX[B]
	[35] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[36] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[37] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[38] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x7f84a0
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfebff800 - 0xfebff8ff (0x100) MX[B]
	[5] -1	0	0xfebffc00 - 0xfebffcff (0x100) MX[B]
	[6] -1	0	0xfdffe000 - 0xfdffefff (0x1000) MX[B]
	[7] -1	0	0xfdef0000 - 0xfdefffff (0x10000) MX[B]
	[8] -1	0	0xfeaff000 - 0xfeafffff (0x1000) MX[B]
	[9] -1	0	0xfe9e8000 - 0xfe9ebfff (0x4000) MX[B]
	[10] -1	0	0xfe7f9000 - 0xfe7f9fff (0x1000) MX[B]
	[11] -1	0	0xfe7f4000 - 0xfe7f7fff (0x4000) MX[B]
	[12] -1	0	0xfe7fa800 - 0xfe7fa8ff (0x100) MX[B]
	[13] -1	0	0xfe7fb000 - 0xfe7fbfff (0x1000) MX[B]
	[14] -1	0	0xfe7fc000 - 0xfe7fcfff (0x1000) MX[B]
	[15] -1	0	0xfe7ff000 - 0xfe7ff0ff (0x100) MX[B]
	[16] -1	0	0xfe7fd000 - 0xfe7fdfff (0x1000) MX[B]
	[17] -1	0	0xfe7fe000 - 0xfe7fefff (0x1000) MX[B]
	[18] -1	0	0xfe7ff800 - 0xfe7ffbff (0x400) MX[B]
	[19] -1	0	0xfdfff000 - 0xfdffffff (0x1000) MX[B](B)
	[20] -1	0	0xfe800000 - 0xfe8fffff (0x100000) MX[B](B)
	[21] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[22] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[23] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[24] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[25] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[26] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[27] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[28] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[29] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[30] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[31] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[34] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[35] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[36] -1	0	0x00007000 - 0x0000700f (0x10) IX[B]
	[37] -1	0	0x00008000 - 0x00008003 (0x4) IX[B]
	[38] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[39] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[40] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[41] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
	[42] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[43] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) fglrx(0): PCI bus 1 card 5 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "dri" "1"
(**) fglrx(0): Option "OpenGLOverlay" "0"
(**) fglrx(0): Option "VideoOverlay" "1"
(**) fglrx(0): Option "UseInternalAGPGART" "1"
(**) fglrx(0): Option "TexturedVideo" "1"
(**) fglrx(0): Option "TexturedVideoSync" "1"
(**) fglrx(0): Option "Textured2D" "1"
(**) fglrx(0): Option "TexturedXrender" "1"
(**) fglrx(0): Option "DPMS" "true"
(II) fglrx(0): Loading PCS database from /etc/ati/amdpcsdb
(II) fglrx(0): 10BitPixelFormat disabled by default
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(--) fglrx(0): Chipset: "ATI Radeon HD 3200 Graphics" (Chipset = 0x9610)
(--) fglrx(0): (PciSubVendor = 0x1043, PciSubDevice = 0x82f1)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xfe9f0000
(--) fglrx(0): I/O port at 0x0000c000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 10.94
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: RS780
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
(II) fglrx(0): Linear address override, using 0x220000000
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID PCI:1:5:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports PCI:1:5:0
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.54.3
	ABI class: X.Org Server Extension, version 0.3
(II) fglrx(0): Using adapter: 1:5.0.
(II) fglrx(0): [FB] Find the MC FB aperturs range(MCFBBase = 0xc0000000, MCFBSize = 0x10000000)
(--) fglrx(0): Video RAM: 262144 kByte, Type: DDR2
(II) fglrx(0): PCIE card detected
(--) fglrx(0): Using per-process page tables (PPPT) as GART.
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) fglrx(0): ***Display: ConnectedDisplayTypes=0x00000080, disabled=0x00000000
(II) fglrx(0): Connected Display1: DFP on secondary TMDS [tmds2i]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: FUS  Model: 594  Serial#: 99999999
(II) fglrx(0): Year: 2005  Week: 41
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 43  vert.: 26
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: Off; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.640 redY: 0.340   greenX: 0.295 greenY: 0.610
(II) fglrx(0): blueX: 0.145 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@67Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 832x624@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): 1152x870@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) fglrx(0): #1: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) fglrx(0): #2: hsize: 1280  vsize 720  refresh: 75  vid: 53121
(II) fglrx(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 106.5 MHz   Image Size:  410 x 256 mm
(II) fglrx(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904 h_border: 0
(II) fglrx(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 942 v_border: 0
(II) fglrx(0): Serial No: YEGU999999
(II) fglrx(0): Ranges: V min: 56  V max: 75 Hz, H min: 31  H max: 83 kHz, PixClock max 140 MHz
(II) fglrx(0): Monitor name: W19-1
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff001ab3940501010101
(II) fglrx(0): 	290f0103802b1a782ac905a3574b9c25
(II) fglrx(0): 	125054bfef80714f81c081cf81809500
(II) fglrx(0): 	0101010101019a29a0d051842a305098
(II) fglrx(0): 	36009a001100001c000000ff00594547
(II) fglrx(0): 	553033323631330a2020000000fd0038
(II) fglrx(0): 	4b1f530e000a202020202020000000fc
(II) fglrx(0): 	005731392d310a20202020202020008c
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(II) fglrx(0): Primary Controller - DFP on secondary TMDS
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(==) fglrx(0): Qbs is not supported in this release. Disabled.
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(**) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 34 modes found for primary display.
(--) fglrx(0): Virtual size is 1440x900 (pitch 0)
(**) fglrx(0): *Mode "1440x900": 106.5 MHz (scaled from 0.0 MHz), 55.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 +vsync (55.9 kHz)
(**) fglrx(0):  Default mode "1440x900": 106.5 MHz (scaled from 0.0 MHz), 55.9 kHz, 59.0 Hz
(II) fglrx(0): Modeline "1440x900"x59.0  106.50  1440 1520 1672 1904  900 903 909 942 +hsync (55.9 kHz)
(**) fglrx(0): *Mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 (80.0 kHz)
(**) fglrx(0):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1280x1024"x70.0  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync (74.6 kHz)
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 (64.0 kHz)
(**) fglrx(0): *Mode "1280x768": 79.5 MHz (scaled from 0.0 MHz), 47.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 +hsync (47.8 kHz)
(**) fglrx(0): *Mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 +hsync (44.8 kHz)
(**) fglrx(0): *Mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 (67.5 kHz)
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"x70.0   96.76  1152 1224 1344 1536  864 865 868 900 +hsync (63.0 kHz)
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 +hsync (53.7 kHz)
(**) fglrx(0): *Mode "1152x648": 59.9 MHz (scaled from 0.0 MHz), 40.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x648"x60.0   59.90  1152 1200 1320 1488  648 649 652 671 +hsync (40.3 kHz)
(**) fglrx(0): *Mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 (60.0 kHz)
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"x72.0   78.43  1024 1080 1192 1360  768 769 772 801 +hsync (57.7 kHz)
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync (56.5 kHz)
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync (48.4 kHz)
(**) fglrx(0): *Mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 (46.9 kHz)
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 (48.1 kHz)
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 +hsync (43.8 kHz)
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 (37.9 kHz)
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 (35.2 kHz)
(**) fglrx(0): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 +hsync (29.8 kHz)
(**) fglrx(0): *Mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 +hsync +vsync (37.5 kHz)
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"x72.0   31.50  640 664 704 832  480 489 492 520 +hsync +vsync (37.9 kHz)
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 +hsync +vsync (31.5 kHz)
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"x75.0   28.07  640 696 736 832  400 413 415 449 (33.7 kHz)
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 (31.5 kHz)
(**) fglrx(0):  Default mode "512x384": 19.7 MHz (scaled from 0.0 MHz), 31.1 kHz, 75.0 Hz
(II) fglrx(0): Modeline "512x384"x75.0   19.68  512 528 576 632  384 384 385 416 (31.1 kHz)
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 (29.8 kHz)
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x75.0   24.75  400 408 448 528  300 601 602 625 doublescan (46.9 kHz)
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan (45.0 kHz)
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x75.0   15.75  320 328 360 416  240 481 482 501 doublescan (37.9 kHz)
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan (31.5 kHz)
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x75.0   13.10  320 352 368 416  200 406 407 417 doublescan (31.5 kHz)
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan (31.5 kHz)
(--) fglrx(0): Display dimensions: (430, 260) mm
(--) fglrx(0): DPI set to (85, 87)
(--) fglrx(0): Virtual size is 1440x900 (pitch 1472)
(**) fglrx(0): *Mode "1440x900": 106.5 MHz (scaled from 0.0 MHz), 55.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 +vsync (55.9 kHz)
(**) fglrx(0):  Default mode "1440x900": 106.5 MHz (scaled from 0.0 MHz), 55.9 kHz, 59.0 Hz
(II) fglrx(0): Modeline "1440x900"x59.0  106.50  1440 1520 1672 1904  900 903 909 942 +hsync (55.9 kHz)
(**) fglrx(0): *Mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 (80.0 kHz)
(**) fglrx(0):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1280x1024"x70.0  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync (74.6 kHz)
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 (64.0 kHz)
(**) fglrx(0): *Mode "1280x768": 79.5 MHz (scaled from 0.0 MHz), 47.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 +hsync (47.8 kHz)
(**) fglrx(0): *Mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 +hsync (44.8 kHz)
(**) fglrx(0): *Mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 (67.5 kHz)
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"x70.0   96.76  1152 1224 1344 1536  864 865 868 900 +hsync (63.0 kHz)
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 +hsync (53.7 kHz)
(**) fglrx(0): *Mode "1152x648": 59.9 MHz (scaled from 0.0 MHz), 40.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x648"x60.0   59.90  1152 1200 1320 1488  648 649 652 671 +hsync (40.3 kHz)
(**) fglrx(0): *Mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 (60.0 kHz)
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"x72.0   78.43  1024 1080 1192 1360  768 769 772 801 +hsync (57.7 kHz)
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync (56.5 kHz)
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync (48.4 kHz)
(**) fglrx(0): *Mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 (46.9 kHz)
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 (48.1 kHz)
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 +hsync (43.8 kHz)
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 (37.9 kHz)
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 (35.2 kHz)
(**) fglrx(0): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 +hsync (29.8 kHz)
(**) fglrx(0): *Mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 +hsync +vsync (37.5 kHz)
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"x72.0   31.50  640 664 704 832  480 489 492 520 +hsync +vsync (37.9 kHz)
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 +hsync +vsync (31.5 kHz)
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"x75.0   28.07  640 696 736 832  400 413 415 449 (33.7 kHz)
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 (31.5 kHz)
(**) fglrx(0):  Default mode "512x384": 19.7 MHz (scaled from 0.0 MHz), 31.1 kHz, 75.0 Hz
(II) fglrx(0): Modeline "512x384"x75.0   19.68  512 528 576 632  384 384 385 416 (31.1 kHz)
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 (29.8 kHz)
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x75.0   24.75  400 408 448 528  300 601 602 625 doublescan (46.9 kHz)
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan (45.0 kHz)
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x75.0   15.75  320 328 360 416  240 481 482 501 doublescan (37.9 kHz)
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan (31.5 kHz)
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x75.0   13.10  320 352 368 416  200 406 407 417 doublescan (31.5 kHz)
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan (31.5 kHz)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.0
	ABI class: X.Org Video Driver, version 2.0
(**) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x4000000b
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 255 MB
(II) fglrx(0): [pcie] 261120 kB allocated
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(II) fglrx(0): Direct rendering enabled
(II) fglrx(0): Interrupt handler installed at IRQ 18.
(II) fglrx(0): Exposed events to the /proc interface
(II) fglrx(0): Finished Initialize PPLIB!
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xfe800000 - 0xfe8fffff (0x100000) MX[B]
	[1] 0	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B]
	[2] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xfebff800 - 0xfebff8ff (0x100) MX[B]
	[8] -1	0	0xfebffc00 - 0xfebffcff (0x100) MX[B]
	[9] -1	0	0xfdffe000 - 0xfdffefff (0x1000) MX[B]
	[10] -1	0	0xfdef0000 - 0xfdefffff (0x10000) MX[B]
	[11] -1	0	0xfeaff000 - 0xfeafffff (0x1000) MX[B]
	[12] -1	0	0xfe9e8000 - 0xfe9ebfff (0x4000) MX[B]
	[13] -1	0	0xfe7f9000 - 0xfe7f9fff (0x1000) MX[B]
	[14] -1	0	0xfe7f4000 - 0xfe7f7fff (0x4000) MX[B]
	[15] -1	0	0xfe7fa800 - 0xfe7fa8ff (0x100) MX[B]
	[16] -1	0	0xfe7fb000 - 0xfe7fbfff (0x1000) MX[B]
	[17] -1	0	0xfe7fc000 - 0xfe7fcfff (0x1000) MX[B]
	[18] -1	0	0xfe7ff000 - 0xfe7ff0ff (0x100) MX[B]
	[19] -1	0	0xfe7fd000 - 0xfe7fdfff (0x1000) MX[B]
	[20] -1	0	0xfe7fe000 - 0xfe7fefff (0x1000) MX[B]
	[21] -1	0	0xfe7ff800 - 0xfe7ffbff (0x400) MX[B]
	[22] -1	0	0xfdfff000 - 0xfdffffff (0x1000) MX[B](B)
	[23] -1	0	0xfe800000 - 0xfe8fffff (0x100000) MX[B](B)
	[24] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[25] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[26] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[27] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[28] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[29] 0	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[30] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[31] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[32] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[33] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[34] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[35] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[36] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[37] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[38] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[39] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[40] -1	0	0x00007000 - 0x0000700f (0x10) IX[B]
	[41] -1	0	0x00008000 - 0x00008003 (0x4) IX[B]
	[42] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[43] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[44] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[45] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
	[46] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[47] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(WW) fglrx(0): could not detect X server version (query_status=-1)
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
(II) fglrx(0): DRIScreenInit for fglrx driver
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID PCI:1:5:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports PCI:1:5:0
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:5:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x174000
(II) fglrx(0): [drm] mapped SAREA 0x174000 to 0x7f2c9470c000
(II) fglrx(0): [drm] framebuffer handle = 0x175000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.54.3
(II) fglrx(0):     Date: Oct  3 2008
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.24-21-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
(II) fglrx(0):     Build-Kernel __SMP__:            yes
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00176000
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x01000e00
(II) fglrx(0): FBMM initialized for area (0,0)-(1472,2850)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1472,900) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1472 x 1950
(**) fglrx(0): Option "BackingStore" "1"
(**) fglrx(0): Backing store enabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(**) fglrx(0): DPMS enabled
(**) fglrx(0): Textured Video is enabled.
(II) LoadModule: "glesx"
(II) Loading /usr/lib/xorg/modules//glesx.so
(II) Module glesx: vendor="X.Org Foundation"
	compiled for 7.1.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension GLESX
(II) fglrx(0): GLESX enableFlags = 30
(**) fglrx(0): Option "XaaNoOffscreenPixmaps" "1"
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid Horizontal and Vertical Lines
	Driver provided ScreenToScreenBitBlt replacement
	Driver provided FillSolidRects replacement
(II) fglrx(0): GLESX is enabled
(II) LoadModule: "amdxmm"
(II) Loading /usr/lib/xorg/modules//amdxmm.so
(II) Module amdxmm: vendor="X.Org Foundation"
	compiled for 7.1.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) fglrx(0): UVD2 feature is available 
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID PCI:1:5:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports PCI:1:5:0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(WW) AIGLX: 3D driver claims to not support visual 0x33
(WW) AIGLX: 3D driver claims to not support visual 0x34
(WW) AIGLX: 3D driver claims to not support visual 0x35
(WW) AIGLX: 3D driver claims to not support visual 0x36
(WW) AIGLX: 3D driver claims to not support visual 0x37
(WW) AIGLX: 3D driver claims to not support visual 0x38
(WW) AIGLX: 3D driver claims to not support visual 0x39
(WW) AIGLX: 3D driver claims to not support visual 0x3a
(WW) AIGLX: 3D driver claims to not support visual 0x3b
(WW) AIGLX: 3D driver claims to not support visual 0x3c
(WW) AIGLX: 3D driver claims to not support visual 0x3d
(WW) AIGLX: 3D driver claims to not support visual 0x3e
(WW) AIGLX: 3D driver claims to not support visual 0x3f
(WW) AIGLX: 3D driver claims to not support visual 0x40
(WW) AIGLX: 3D driver claims to not support visual 0x41
(WW) AIGLX: 3D driver claims to not support visual 0x42
(WW) AIGLX: 3D driver claims to not support visual 0x43
(WW) AIGLX: 3D driver claims to not support visual 0x44
(WW) AIGLX: 3D driver claims to not support visual 0x45
(WW) AIGLX: 3D driver claims to not support visual 0x46
(WW) AIGLX: 3D driver claims to not support visual 0x47
(WW) AIGLX: 3D driver claims to not support visual 0x48
(WW) AIGLX: 3D driver claims to not support visual 0x49
(WW) AIGLX: 3D driver claims to not support visual 0x4a
(WW) AIGLX: 3D driver claims to not support visual 0x4b
(WW) AIGLX: 3D driver claims to not support visual 0x4c
(WW) AIGLX: 3D driver claims to not support visual 0x4d
(WW) AIGLX: 3D driver claims to not support visual 0x4e
(WW) AIGLX: 3D driver claims to not support visual 0x4f
(WW) AIGLX: 3D driver claims to not support visual 0x50
(WW) AIGLX: 3D driver claims to not support visual 0x51
(WW) AIGLX: 3D driver claims to not support visual 0x52
(WW) AIGLX: 3D driver claims to not support visual 0x53
(WW) AIGLX: 3D driver claims to not support visual 0x54
(WW) AIGLX: 3D driver claims to not support visual 0x55
(WW) AIGLX: 3D driver claims to not support visual 0x56
(WW) AIGLX: 3D driver claims to not support visual 0x57
(WW) AIGLX: 3D driver claims to not support visual 0x58
(WW) AIGLX: 3D driver claims to not support visual 0x59
(WW) AIGLX: 3D driver claims to not support visual 0x5a
(WW) AIGLX: 3D driver claims to not support visual 0x5b
(WW) AIGLX: 3D driver claims to not support visual 0x5c
(WW) AIGLX: 3D driver claims to not support visual 0x5d
(WW) AIGLX: 3D driver claims to not support visual 0x5e
(WW) AIGLX: 3D driver claims to not support visual 0x5f
(WW) AIGLX: 3D driver claims to not support visual 0x60
(WW) AIGLX: 3D driver claims to not support visual 0x61
(WW) AIGLX: 3D driver claims to not support visual 0x62
(WW) AIGLX: 3D driver claims to not support visual 0x63
(WW) AIGLX: 3D driver claims to not support visual 0x64
(WW) AIGLX: 3D driver claims to not support visual 0x65
(WW) AIGLX: 3D driver claims to not support visual 0x66
(WW) AIGLX: 3D driver claims to not support visual 0x67
(WW) AIGLX: 3D driver claims to not support visual 0x68
(WW) AIGLX: 3D driver claims to not support visual 0x69
(WW) AIGLX: 3D driver claims to not support visual 0x6a
(WW) AIGLX: 3D driver claims to not support visual 0x6b
(WW) AIGLX: 3D driver claims to not support visual 0x6c
(WW) AIGLX: 3D driver claims to not support visual 0x6d
(WW) AIGLX: 3D driver claims to not support visual 0x6e
(WW) AIGLX: 3D driver claims to not support visual 0x6f
(WW) AIGLX: 3D driver claims to not support visual 0x70
(WW) AIGLX: 3D driver claims to not support visual 0x71
(WW) AIGLX: 3D driver claims to not support visual 0x72
(II) AIGLX: Loaded and initialized /usr/lib/dri/fglrx_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) fglrx(0): Enable the clock gating!
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "ch"
(**) Generic Keyboard: XkbLayout: "ch"
(**) Option "XkbVariant" "de_mac"
(**) Generic Keyboard: XkbVariant: "de_mac"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x6a) [0x48402a]
1: /lib/libc.so.6 [0x7f2c92c35100]
2: /usr/lib/xorg/modules/drivers//fglrx_drv.so(atiddxDisplayShadowIsShadowPixmap+0x16) [0x7f2c911bca86]
3: /usr/lib/xorg/modules//glesx.so [0x7f2c8e1c4723]
4: /usr/lib/xorg/modules//libxaa.so(XAAComposite+0x19b) [0x7f2c901148eb]
5: /usr/lib/xorg/modules//libxaa.so [0x7f2c9012ff1d]
6: /usr/bin/X [0x527ea2]
7: /usr/bin/X [0x515c3f]
8: /usr/bin/X(Dispatch+0x2ef) [0x44eaaf]
9: /usr/bin/X(main+0x47d) [0x436b9d]
10: /lib/libc.so.6(__libc_start_main+0xf4) [0x7f2c92c211c4]
11: /usr/bin/X(FontFileCompleteXLFD+0x279) [0x435ed9]

Fatal server error:
Caught signal 11.  Server aborting

(II) AIGLX: Suspending AIGLX clients for VT switch

```

The issue seems to be a segmentation fault (signal 11) eventually cause with the loading of fonts? The log does not show any errors before the Fatal server error. Can you see something promising to identify the issue or do you have another hint?

---

### Post by soxs on 2008-10-20
> **mfehr said:**
> Hi,

thanks for your prompt response. I altered the xorg.conf file as menionned. I understood that the options become part of the device section. This section now looks as follows:

```
Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:5:0"
### Driver / Performance Options
	Option		"XAANoOffscreenPixmaps"	"1"
	Option		"TexturedVideo"		"1"
	Option		"TexturedVideoSync"	"1"
	Option		"Textured2D"		"1"
	Option		"TexturedXRender"	"1"
	Option		"DRI"			"1"
	Option		"UseInternalAGPGART"	"1"
	Option		"BackingStore"		"1"
	Option		"OpenGLOverlay"		"0"
	Option		"VideoOverlay"		"1"
EndSection

```

Starting the server with these settings causes 6 failed attempts to load X. You can see the login panel for half a second (in correct resolution), followed by a resolution change and various differnet colours (like in the good old CGA-resolution days) on the entire screen for another second. After this, the text-display is shown again. Finally, after 6 attempts, a text based message box is displayed, informing that it will try in 2 minutes. - I tried to reduce the parameters in different combinations with no success. All tested options did not allow a login from the X login panel.

The Xorg.0.log for all options enabled looks as follows:

```


This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux myserver 2.6.24-21-generic #1 SMP Mon Aug 25 16:57:51 UTC 2008 x86_64
Build Date: 13 June 2008  01:10:57AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Oct 20 20:04:37 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "aticonfig-Screen[0]-0" (0)
(**) |   |-->Monitor "aticonfig-Monitor[0]-0"
(**) |   |-->Device "aticonfig-Device[0]-0"
(==) Automatically adding devices
(==) Automatically enabling devices
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
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
	Using the first core pointer device.
(==) The core keyboard device wasn't specified explicitly in the layout.
	Using the first keyboard device.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7bd660
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1022,9600 card 1002,7910 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1022,9602 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:06:0: chip 1022,9606 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:11:0: chip 1002,4390 card 1043,82f1 rev 00 class 01,06,01 hdr 00
(II) PCI: 00:12:0: chip 1002,4397 card 1002,4397 rev 00 class 0c,03,10 hdr 80
(II) PCI: 00:12:1: chip 1002,4398 card 1002,4398 rev 00 class 0c,03,10 hdr 00
(II) PCI: 00:12:2: chip 1002,4396 card 1002,4397 rev 00 class 0c,03,20 hdr 00
(II) PCI: 00:13:0: chip 1002,4397 card 1002,4398 rev 00 class 0c,03,10 hdr 80
(II) PCI: 00:13:1: chip 1002,4398 card 1002,4399 rev 00 class 0c,03,10 hdr 00
(II) PCI: 00:13:2: chip 1002,4396 card 1002,4396 rev 00 class 0c,03,20 hdr 00
(II) PCI: 00:14:0: chip 1002,4385 card 1043,82f1 rev 3a class 0c,05,00 hdr 80
(II) PCI: 00:14:1: chip 1002,439c card 1043,82f1 rev 00 class 01,01,8a hdr 00
(II) PCI: 00:14:2: chip 1002,4383 card 1043,82fe rev 00 class 04,03,00 hdr 00
(II) PCI: 00:14:3: chip 1002,439d card 1002,4383 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:14:4: chip 1002,4384 card 0000,0000 rev 00 class 06,04,01 hdr 81
(II) PCI: 00:14:5: chip 1002,4399 card 1002,4396 rev 00 class 0c,03,10 hdr 00
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:05:0: chip 1002,9610 card 1043,82f1 rev 00 class 03,00,00 hdr 80
(II) PCI: 01:05:1: chip 1002,960f card 1002,960f rev 00 class 04,03,00 hdr 80
(II) PCI: 02:00:0: chip 10ec,8168 card 1043,82c6 rev 02 class 02,00,00 hdr 00
(II) PCI: 03:05:0: chip 109e,036e card 11bd,0012 rev 11 class 04,00,00 hdr 80
(II) PCI: 03:05:1: chip 109e,0878 card 11bd,0012 rev 11 class 04,80,00 hdr 80
(II) PCI: 03:06:0: chip 10ec,8169 card 10ec,8169 rev 10 class 02,00,00 hdr 00
(II) PCI: 03:07:0: chip 10ec,8139 card 10bd,0320 rev 10 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,3), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x001a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfe800000 - 0xfe9fffff (0x200000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:6:0), (0,2,2), BCTRL: 0x0003 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfea00000 - 0xfeafffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xfde00000 - 0xfdefffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:20:3), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:20:4), (0,3,3), BCTRL: 0x0003 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000e000 - 0x0000efff (0x1000) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xfeb00000 - 0xfebfffff (0x100000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0xfdf00000 - 0xfdffffff (0x100000) MX[B]
(--) PCI:*(1:5:0) ATI Technologies Inc unknown chipset (0x9610) rev 0, Mem @ 0xd0000000/28, 0xfe9f0000/16, 0xfe800000/20, I/O @ 0xc000/8
(--) PCI: (3:5:0) Brooktree Corporation Bt878 Video Capture rev 17, Mem @ 0xfdfff000/12
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xfebff800 - 0xfebff8ff (0x100) MX[B]
	[1] -1	0	0xfebffc00 - 0xfebffcff (0x100) MX[B]
	[2] -1	0	0xfdffe000 - 0xfdffefff (0x1000) MX[B]
	[3] -1	0	0xfdef0000 - 0xfdefffff (0x10000) MX[B]
	[4] -1	0	0xfeaff000 - 0xfeafffff (0x1000) MX[B]
	[5] -1	0	0xfe9e8000 - 0xfe9ebfff (0x4000) MX[B]
	[6] -1	0	0xfe7f9000 - 0xfe7f9fff (0x1000) MX[B]
	[7] -1	0	0xfe7f4000 - 0xfe7f7fff (0x4000) MX[B]
	[8] -1	0	0xfe7fa800 - 0xfe7fa8ff (0x100) MX[B]
	[9] -1	0	0xfe7fb000 - 0xfe7fbfff (0x1000) MX[B]
	[10] -1	0	0xfe7fc000 - 0xfe7fcfff (0x1000) MX[B]
	[11] -1	0	0xfe7ff000 - 0xfe7ff0ff (0x100) MX[B]
	[12] -1	0	0xfe7fd000 - 0xfe7fdfff (0x1000) MX[B]
	[13] -1	0	0xfe7fe000 - 0xfe7fefff (0x1000) MX[B]
	[14] -1	0	0xfe7ff800 - 0xfe7ffbff (0x400) MX[B]
	[15] -1	0	0xfdfff000 - 0xfdffffff (0x1000) MX[B](B)
	[16] -1	0	0xfe800000 - 0xfe8fffff (0x100000) MX[B](B)
	[17] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[18] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[19] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[20] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[22] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x00007000 - 0x0000700f (0x10) IX[B]
	[28] -1	0	0x00008000 - 0x00008003 (0x4) IX[B]
	[29] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[30] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[31] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[32] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfebff800 - 0xfebff8ff (0x100) MX[B]
	[1] -1	0	0xfebffc00 - 0xfebffcff (0x100) MX[B]
	[2] -1	0	0xfdffe000 - 0xfdffefff (0x1000) MX[B]
	[3] -1	0	0xfdef0000 - 0xfdefffff (0x10000) MX[B]
	[4] -1	0	0xfeaff000 - 0xfeafffff (0x1000) MX[B]
	[5] -1	0	0xfe9e8000 - 0xfe9ebfff (0x4000) MX[B]
	[6] -1	0	0xfe7f9000 - 0xfe7f9fff (0x1000) MX[B]
	[7] -1	0	0xfe7f4000 - 0xfe7f7fff (0x4000) MX[B]
	[8] -1	0	0xfe7fa800 - 0xfe7fa8ff (0x100) MX[B]
	[9] -1	0	0xfe7fb000 - 0xfe7fbfff (0x1000) MX[B]
	[10] -1	0	0xfe7fc000 - 0xfe7fcfff (0x1000) MX[B]
	[11] -1	0	0xfe7ff000 - 0xfe7ff0ff (0x100) MX[B]
	[12] -1	0	0xfe7fd000 - 0xfe7fdfff (0x1000) MX[B]
	[13] -1	0	0xfe7fe000 - 0xfe7fefff (0x1000) MX[B]
	[14] -1	0	0xfe7ff800 - 0xfe7ffbff (0x400) MX[B]
	[15] -1	0	0xfdfff000 - 0xfdffffff (0x1000) MX[B](B)
	[16] -1	0	0xfe800000 - 0xfe8fffff (0x100000) MX[B](B)
	[17] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[18] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[19] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[20] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[22] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x00007000 - 0x0000700f (0x10) IX[B]
	[28] -1	0	0x00008000 - 0x00008003 (0x4) IX[B]
	[29] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[30] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[31] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[32] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfebff800 - 0xfebff8ff (0x100) MX[B]
	[5] -1	0	0xfebffc00 - 0xfebffcff (0x100) MX[B]
	[6] -1	0	0xfdffe000 - 0xfdffefff (0x1000) MX[B]
	[7] -1	0	0xfdef0000 - 0xfdefffff (0x10000) MX[B]
	[8] -1	0	0xfeaff000 - 0xfeafffff (0x1000) MX[B]
	[9] -1	0	0xfe9e8000 - 0xfe9ebfff (0x4000) MX[B]
	[10] -1	0	0xfe7f9000 - 0xfe7f9fff (0x1000) MX[B]
	[11] -1	0	0xfe7f4000 - 0xfe7f7fff (0x4000) MX[B]
	[12] -1	0	0xfe7fa800 - 0xfe7fa8ff (0x100) MX[B]
	[13] -1	0	0xfe7fb000 - 0xfe7fbfff (0x1000) MX[B]
	[14] -1	0	0xfe7fc000 - 0xfe7fcfff (0x1000) MX[B]
	[15] -1	0	0xfe7ff000 - 0xfe7ff0ff (0x100) MX[B]
	[16] -1	0	0xfe7fd000 - 0xfe7fdfff (0x1000) MX[B]
	[17] -1	0	0xfe7fe000 - 0xfe7fefff (0x1000) MX[B]
	[18] -1	0	0xfe7ff800 - 0xfe7ffbff (0x400) MX[B]
	[19] -1	0	0xfdfff000 - 0xfdffffff (0x1000) MX[B](B)
	[20] -1	0	0xfe800000 - 0xfe8fffff (0x100000) MX[B](B)
	[21] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[22] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[25] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[26] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[27] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[28] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[33] -1	0	0x00007000 - 0x0000700f (0x10) IX[B]
	[34] -1	0	0x00008000 - 0x00008003 (0x4) IX[B]
	[35] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[36] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[37] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[38] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded by default.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
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
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.1.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.54.3
	Module class: X.Org Video Driver
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) Primary Device is: PCI 01:05:0
(II) ATI Proprietary Linux Driver Version Identifier:8.54.3
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.542                    
(II) ATI Proprietary Linux Driver Build Date: Oct  3 2008 17:42:58
(--) Chipset Supported AMD Graphics Processor (0x9610) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfebff800 - 0xfebff8ff (0x100) MX[B]
	[5] -1	0	0xfebffc00 - 0xfebffcff (0x100) MX[B]
	[6] -1	0	0xfdffe000 - 0xfdffefff (0x1000) MX[B]
	[7] -1	0	0xfdef0000 - 0xfdefffff (0x10000) MX[B]
	[8] -1	0	0xfeaff000 - 0xfeafffff (0x1000) MX[B]
	[9] -1	0	0xfe9e8000 - 0xfe9ebfff (0x4000) MX[B]
	[10] -1	0	0xfe7f9000 - 0xfe7f9fff (0x1000) MX[B]
	[11] -1	0	0xfe7f4000 - 0xfe7f7fff (0x4000) MX[B]
	[12] -1	0	0xfe7fa800 - 0xfe7fa8ff (0x100) MX[B]
	[13] -1	0	0xfe7fb000 - 0xfe7fbfff (0x1000) MX[B]
	[14] -1	0	0xfe7fc000 - 0xfe7fcfff (0x1000) MX[B]
	[15] -1	0	0xfe7ff000 - 0xfe7ff0ff (0x100) MX[B]
	[16] -1	0	0xfe7fd000 - 0xfe7fdfff (0x1000) MX[B]
	[17] -1	0	0xfe7fe000 - 0xfe7fefff (0x1000) MX[B]
	[18] -1	0	0xfe7ff800 - 0xfe7ffbff (0x400) MX[B]
	[19] -1	0	0xfdfff000 - 0xfdffffff (0x1000) MX[B](B)
	[20] -1	0	0xfe800000 - 0xfe8fffff (0x100000) MX[B](B)
	[21] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[22] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[25] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[26] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[27] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[28] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[33] -1	0	0x00007000 - 0x0000700f (0x10) IX[B]
	[34] -1	0	0x00008000 - 0x00008003 (0x4) IX[B]
	[35] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[36] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[37] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[38] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x7f84a0
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfebff800 - 0xfebff8ff (0x100) MX[B]
	[5] -1	0	0xfebffc00 - 0xfebffcff (0x100) MX[B]
	[6] -1	0	0xfdffe000 - 0xfdffefff (0x1000) MX[B]
	[7] -1	0	0xfdef0000 - 0xfdefffff (0x10000) MX[B]
	[8] -1	0	0xfeaff000 - 0xfeafffff (0x1000) MX[B]
	[9] -1	0	0xfe9e8000 - 0xfe9ebfff (0x4000) MX[B]
	[10] -1	0	0xfe7f9000 - 0xfe7f9fff (0x1000) MX[B]
	[11] -1	0	0xfe7f4000 - 0xfe7f7fff (0x4000) MX[B]
	[12] -1	0	0xfe7fa800 - 0xfe7fa8ff (0x100) MX[B]
	[13] -1	0	0xfe7fb000 - 0xfe7fbfff (0x1000) MX[B]
	[14] -1	0	0xfe7fc000 - 0xfe7fcfff (0x1000) MX[B]
	[15] -1	0	0xfe7ff000 - 0xfe7ff0ff (0x100) MX[B]
	[16] -1	0	0xfe7fd000 - 0xfe7fdfff (0x1000) MX[B]
	[17] -1	0	0xfe7fe000 - 0xfe7fefff (0x1000) MX[B]
	[18] -1	0	0xfe7ff800 - 0xfe7ffbff (0x400) MX[B]
	[19] -1	0	0xfdfff000 - 0xfdffffff (0x1000) MX[B](B)
	[20] -1	0	0xfe800000 - 0xfe8fffff (0x100000) MX[B](B)
	[21] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[22] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[23] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[24] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[25] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[26] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[27] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[28] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[29] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[30] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[31] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[34] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[35] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[36] -1	0	0x00007000 - 0x0000700f (0x10) IX[B]
	[37] -1	0	0x00008000 - 0x00008003 (0x4) IX[B]
	[38] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[39] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[40] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[41] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
	[42] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[43] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) fglrx(0): PCI bus 1 card 5 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "dri" "1"
(**) fglrx(0): Option "OpenGLOverlay" "0"
(**) fglrx(0): Option "VideoOverlay" "1"
(**) fglrx(0): Option "UseInternalAGPGART" "1"
(**) fglrx(0): Option "TexturedVideo" "1"
(**) fglrx(0): Option "TexturedVideoSync" "1"
(**) fglrx(0): Option "Textured2D" "1"
(**) fglrx(0): Option "TexturedXrender" "1"
(**) fglrx(0): Option "DPMS" "true"
(II) fglrx(0): Loading PCS database from /etc/ati/amdpcsdb
(II) fglrx(0): 10BitPixelFormat disabled by default
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(--) fglrx(0): Chipset: "ATI Radeon HD 3200 Graphics" (Chipset = 0x9610)
(--) fglrx(0): (PciSubVendor = 0x1043, PciSubDevice = 0x82f1)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xfe9f0000
(--) fglrx(0): I/O port at 0x0000c000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 10.94
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: RS780
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
(II) fglrx(0): Linear address override, using 0x220000000
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID PCI:1:5:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports PCI:1:5:0
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.54.3
	ABI class: X.Org Server Extension, version 0.3
(II) fglrx(0): Using adapter: 1:5.0.
(II) fglrx(0): [FB] Find the MC FB aperturs range(MCFBBase = 0xc0000000, MCFBSize = 0x10000000)
(--) fglrx(0): Video RAM: 262144 kByte, Type: DDR2
(II) fglrx(0): PCIE card detected
(--) fglrx(0): Using per-process page tables (PPPT) as GART.
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) fglrx(0): ***Display: ConnectedDisplayTypes=0x00000080, disabled=0x00000000
(II) fglrx(0): Connected Display1: DFP on secondary TMDS [tmds2i]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: FUS  Model: 594  Serial#: 99999999
(II) fglrx(0): Year: 2005  Week: 41
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 43  vert.: 26
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: Off; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.640 redY: 0.340   greenX: 0.295 greenY: 0.610
(II) fglrx(0): blueX: 0.145 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@67Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 832x624@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): 1152x870@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) fglrx(0): #1: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) fglrx(0): #2: hsize: 1280  vsize 720  refresh: 75  vid: 53121
(II) fglrx(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 106.5 MHz   Image Size:  410 x 256 mm
(II) fglrx(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904 h_border: 0
(II) fglrx(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 942 v_border: 0
(II) fglrx(0): Serial No: YEGU999999
(II) fglrx(0): Ranges: V min: 56  V max: 75 Hz, H min: 31  H max: 83 kHz, PixClock max 140 MHz
(II) fglrx(0): Monitor name: W19-1
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff001ab3940501010101
(II) fglrx(0): 	290f0103802b1a782ac905a3574b9c25
(II) fglrx(0): 	125054bfef80714f81c081cf81809500
(II) fglrx(0): 	0101010101019a29a0d051842a305098
(II) fglrx(0): 	36009a001100001c000000ff00594547
(II) fglrx(0): 	553033323631330a2020000000fd0038
(II) fglrx(0): 	4b1f530e000a202020202020000000fc
(II) fglrx(0): 	005731392d310a20202020202020008c
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(II) fglrx(0): Primary Controller - DFP on secondary TMDS
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(==) fglrx(0): Qbs is not supported in this release. Disabled.
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(**) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 34 modes found for primary display.
(--) fglrx(0): Virtual size is 1440x900 (pitch 0)
(**) fglrx(0): *Mode "1440x900": 106.5 MHz (scaled from 0.0 MHz), 55.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 +vsync (55.9 kHz)
(**) fglrx(0):  Default mode "1440x900": 106.5 MHz (scaled from 0.0 MHz), 55.9 kHz, 59.0 Hz
(II) fglrx(0): Modeline "1440x900"x59.0  106.50  1440 1520 1672 1904  900 903 909 942 +hsync (55.9 kHz)
(**) fglrx(0): *Mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 (80.0 kHz)
(**) fglrx(0):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1280x1024"x70.0  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync (74.6 kHz)
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 (64.0 kHz)
(**) fglrx(0): *Mode "1280x768": 79.5 MHz (scaled from 0.0 MHz), 47.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 +hsync (47.8 kHz)
(**) fglrx(0): *Mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 +hsync (44.8 kHz)
(**) fglrx(0): *Mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 (67.5 kHz)
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"x70.0   96.76  1152 1224 1344 1536  864 865 868 900 +hsync (63.0 kHz)
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 +hsync (53.7 kHz)
(**) fglrx(0): *Mode "1152x648": 59.9 MHz (scaled from 0.0 MHz), 40.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x648"x60.0   59.90  1152 1200 1320 1488  648 649 652 671 +hsync (40.3 kHz)
(**) fglrx(0): *Mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 (60.0 kHz)
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"x72.0   78.43  1024 1080 1192 1360  768 769 772 801 +hsync (57.7 kHz)
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync (56.5 kHz)
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync (48.4 kHz)
(**) fglrx(0): *Mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 (46.9 kHz)
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 (48.1 kHz)
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 +hsync (43.8 kHz)
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 (37.9 kHz)
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 (35.2 kHz)
(**) fglrx(0): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 +hsync (29.8 kHz)
(**) fglrx(0): *Mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 +hsync +vsync (37.5 kHz)
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"x72.0   31.50  640 664 704 832  480 489 492 520 +hsync +vsync (37.9 kHz)
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 +hsync +vsync (31.5 kHz)
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"x75.0   28.07  640 696 736 832  400 413 415 449 (33.7 kHz)
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 (31.5 kHz)
(**) fglrx(0):  Default mode "512x384": 19.7 MHz (scaled from 0.0 MHz), 31.1 kHz, 75.0 Hz
(II) fglrx(0): Modeline "512x384"x75.0   19.68  512 528 576 632  384 384 385 416 (31.1 kHz)
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 (29.8 kHz)
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x75.0   24.75  400 408 448 528  300 601 602 625 doublescan (46.9 kHz)
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan (45.0 kHz)
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x75.0   15.75  320 328 360 416  240 481 482 501 doublescan (37.9 kHz)
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan (31.5 kHz)
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x75.0   13.10  320 352 368 416  200 406 407 417 doublescan (31.5 kHz)
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan (31.5 kHz)
(--) fglrx(0): Display dimensions: (430, 260) mm
(--) fglrx(0): DPI set to (85, 87)
(--) fglrx(0): Virtual size is 1440x900 (pitch 1472)
(**) fglrx(0): *Mode "1440x900": 106.5 MHz (scaled from 0.0 MHz), 55.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 +vsync (55.9 kHz)
(**) fglrx(0):  Default mode "1440x900": 106.5 MHz (scaled from 0.0 MHz), 55.9 kHz, 59.0 Hz
(II) fglrx(0): Modeline "1440x900"x59.0  106.50  1440 1520 1672 1904  900 903 909 942 +hsync (55.9 kHz)
(**) fglrx(0): *Mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 (80.0 kHz)
(**) fglrx(0):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1280x1024"x70.0  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync (74.6 kHz)
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 (64.0 kHz)
(**) fglrx(0): *Mode "1280x768": 79.5 MHz (scaled from 0.0 MHz), 47.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 +hsync (47.8 kHz)
(**) fglrx(0): *Mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 +hsync (44.8 kHz)
(**) fglrx(0): *Mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 (67.5 kHz)
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"x70.0   96.76  1152 1224 1344 1536  864 865 868 900 +hsync (63.0 kHz)
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 +hsync (53.7 kHz)
(**) fglrx(0): *Mode "1152x648": 59.9 MHz (scaled from 0.0 MHz), 40.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x648"x60.0   59.90  1152 1200 1320 1488  648 649 652 671 +hsync (40.3 kHz)
(**) fglrx(0): *Mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 (60.0 kHz)
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"x72.0   78.43  1024 1080 1192 1360  768 769 772 801 +hsync (57.7 kHz)
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync (56.5 kHz)
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync (48.4 kHz)
(**) fglrx(0): *Mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 (46.9 kHz)
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 (48.1 kHz)
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 +hsync (43.8 kHz)
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 (37.9 kHz)
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 (35.2 kHz)
(**) fglrx(0): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 +hsync (29.8 kHz)
(**) fglrx(0): *Mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 +hsync +vsync (37.5 kHz)
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"x72.0   31.50  640 664 704 832  480 489 492 520 +hsync +vsync (37.9 kHz)
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 +hsync +vsync (31.5 kHz)
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"x75.0   28.07  640 696 736 832  400 413 415 449 (33.7 kHz)
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 (31.5 kHz)
(**) fglrx(0):  Default mode "512x384": 19.7 MHz (scaled from 0.0 MHz), 31.1 kHz, 75.0 Hz
(II) fglrx(0): Modeline "512x384"x75.0   19.68  512 528 576 632  384 384 385 416 (31.1 kHz)
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 (29.8 kHz)
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x75.0   24.75  400 408 448 528  300 601 602 625 doublescan (46.9 kHz)
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan (45.0 kHz)
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x75.0   15.75  320 328 360 416  240 481 482 501 doublescan (37.9 kHz)
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan (31.5 kHz)
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x75.0   13.10  320 352 368 416  200 406 407 417 doublescan (31.5 kHz)
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan (31.5 kHz)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.0
	ABI class: X.Org Video Driver, version 2.0
(**) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x4000000b
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 255 MB
(II) fglrx(0): [pcie] 261120 kB allocated
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(II) fglrx(0): Direct rendering enabled
(II) fglrx(0): Interrupt handler installed at IRQ 18.
(II) fglrx(0): Exposed events to the /proc interface
(II) fglrx(0): Finished Initialize PPLIB!
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xfe800000 - 0xfe8fffff (0x100000) MX[B]
	[1] 0	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B]
	[2] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xfebff800 - 0xfebff8ff (0x100) MX[B]
	[8] -1	0	0xfebffc00 - 0xfebffcff (0x100) MX[B]
	[9] -1	0	0xfdffe000 - 0xfdffefff (0x1000) MX[B]
	[10] -1	0	0xfdef0000 - 0xfdefffff (0x10000) MX[B]
	[11] -1	0	0xfeaff000 - 0xfeafffff (0x1000) MX[B]
	[12] -1	0	0xfe9e8000 - 0xfe9ebfff (0x4000) MX[B]
	[13] -1	0	0xfe7f9000 - 0xfe7f9fff (0x1000) MX[B]
	[14] -1	0	0xfe7f4000 - 0xfe7f7fff (0x4000) MX[B]
	[15] -1	0	0xfe7fa800 - 0xfe7fa8ff (0x100) MX[B]
	[16] -1	0	0xfe7fb000 - 0xfe7fbfff (0x1000) MX[B]
	[17] -1	0	0xfe7fc000 - 0xfe7fcfff (0x1000) MX[B]
	[18] -1	0	0xfe7ff000 - 0xfe7ff0ff (0x100) MX[B]
	[19] -1	0	0xfe7fd000 - 0xfe7fdfff (0x1000) MX[B]
	[20] -1	0	0xfe7fe000 - 0xfe7fefff (0x1000) MX[B]
	[21] -1	0	0xfe7ff800 - 0xfe7ffbff (0x400) MX[B]
	[22] -1	0	0xfdfff000 - 0xfdffffff (0x1000) MX[B](B)
	[23] -1	0	0xfe800000 - 0xfe8fffff (0x100000) MX[B](B)
	[24] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[25] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[26] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[27] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[28] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[29] 0	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[30] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[31] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[32] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[33] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[34] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[35] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[36] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[37] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[38] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[39] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[40] -1	0	0x00007000 - 0x0000700f (0x10) IX[B]
	[41] -1	0	0x00008000 - 0x00008003 (0x4) IX[B]
	[42] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[43] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[44] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[45] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
	[46] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[47] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(WW) fglrx(0): could not detect X server version (query_status=-1)
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
(II) fglrx(0): DRIScreenInit for fglrx driver
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID PCI:1:5:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports PCI:1:5:0
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:5:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x174000
(II) fglrx(0): [drm] mapped SAREA 0x174000 to 0x7f2c9470c000
(II) fglrx(0): [drm] framebuffer handle = 0x175000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.54.3
(II) fglrx(0):     Date: Oct  3 2008
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.24-21-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
(II) fglrx(0):     Build-Kernel __SMP__:            yes
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00176000
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x01000e00
(II) fglrx(0): FBMM initialized for area (0,0)-(1472,2850)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1472,900) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1472 x 1950
(**) fglrx(0): Option "BackingStore" "1"
(**) fglrx(0): Backing store enabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(**) fglrx(0): DPMS enabled
(**) fglrx(0): Textured Video is enabled.
(II) LoadModule: "glesx"
(II) Loading /usr/lib/xorg/modules//glesx.so
(II) Module glesx: vendor="X.Org Foundation"
	compiled for 7.1.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension GLESX
(II) fglrx(0): GLESX enableFlags = 30
(**) fglrx(0): Option "XaaNoOffscreenPixmaps" "1"
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid Horizontal and Vertical Lines
	Driver provided ScreenToScreenBitBlt replacement
	Driver provided FillSolidRects replacement
(II) fglrx(0): GLESX is enabled
(II) LoadModule: "amdxmm"
(II) Loading /usr/lib/xorg/modules//amdxmm.so
(II) Module amdxmm: vendor="X.Org Foundation"
	compiled for 7.1.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) fglrx(0): UVD2 feature is available 
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID PCI:1:5:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports PCI:1:5:0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(WW) AIGLX: 3D driver claims to not support visual 0x33
(WW) AIGLX: 3D driver claims to not support visual 0x34
(WW) AIGLX: 3D driver claims to not support visual 0x35
(WW) AIGLX: 3D driver claims to not support visual 0x36
(WW) AIGLX: 3D driver claims to not support visual 0x37
(WW) AIGLX: 3D driver claims to not support visual 0x38
(WW) AIGLX: 3D driver claims to not support visual 0x39
(WW) AIGLX: 3D driver claims to not support visual 0x3a
(WW) AIGLX: 3D driver claims to not support visual 0x3b
(WW) AIGLX: 3D driver claims to not support visual 0x3c
(WW) AIGLX: 3D driver claims to not support visual 0x3d
(WW) AIGLX: 3D driver claims to not support visual 0x3e
(WW) AIGLX: 3D driver claims to not support visual 0x3f
(WW) AIGLX: 3D driver claims to not support visual 0x40
(WW) AIGLX: 3D driver claims to not support visual 0x41
(WW) AIGLX: 3D driver claims to not support visual 0x42
(WW) AIGLX: 3D driver claims to not support visual 0x43
(WW) AIGLX: 3D driver claims to not support visual 0x44
(WW) AIGLX: 3D driver claims to not support visual 0x45
(WW) AIGLX: 3D driver claims to not support visual 0x46
(WW) AIGLX: 3D driver claims to not support visual 0x47
(WW) AIGLX: 3D driver claims to not support visual 0x48
(WW) AIGLX: 3D driver claims to not support visual 0x49
(WW) AIGLX: 3D driver claims to not support visual 0x4a
(WW) AIGLX: 3D driver claims to not support visual 0x4b
(WW) AIGLX: 3D driver claims to not support visual 0x4c
(WW) AIGLX: 3D driver claims to not support visual 0x4d
(WW) AIGLX: 3D driver claims to not support visual 0x4e
(WW) AIGLX: 3D driver claims to not support visual 0x4f
(WW) AIGLX: 3D driver claims to not support visual 0x50
(WW) AIGLX: 3D driver claims to not support visual 0x51
(WW) AIGLX: 3D driver claims to not support visual 0x52
(WW) AIGLX: 3D driver claims to not support visual 0x53
(WW) AIGLX: 3D driver claims to not support visual 0x54
(WW) AIGLX: 3D driver claims to not support visual 0x55
(WW) AIGLX: 3D driver claims to not support visual 0x56
(WW) AIGLX: 3D driver claims to not support visual 0x57
(WW) AIGLX: 3D driver claims to not support visual 0x58
(WW) AIGLX: 3D driver claims to not support visual 0x59
(WW) AIGLX: 3D driver claims to not support visual 0x5a
(WW) AIGLX: 3D driver claims to not support visual 0x5b
(WW) AIGLX: 3D driver claims to not support visual 0x5c
(WW) AIGLX: 3D driver claims to not support visual 0x5d
(WW) AIGLX: 3D driver claims to not support visual 0x5e
(WW) AIGLX: 3D driver claims to not support visual 0x5f
(WW) AIGLX: 3D driver claims to not support visual 0x60
(WW) AIGLX: 3D driver claims to not support visual 0x61
(WW) AIGLX: 3D driver claims to not support visual 0x62
(WW) AIGLX: 3D driver claims to not support visual 0x63
(WW) AIGLX: 3D driver claims to not support visual 0x64
(WW) AIGLX: 3D driver claims to not support visual 0x65
(WW) AIGLX: 3D driver claims to not support visual 0x66
(WW) AIGLX: 3D driver claims to not support visual 0x67
(WW) AIGLX: 3D driver claims to not support visual 0x68
(WW) AIGLX: 3D driver claims to not support visual 0x69
(WW) AIGLX: 3D driver claims to not support visual 0x6a
(WW) AIGLX: 3D driver claims to not support visual 0x6b
(WW) AIGLX: 3D driver claims to not support visual 0x6c
(WW) AIGLX: 3D driver claims to not support visual 0x6d
(WW) AIGLX: 3D driver claims to not support visual 0x6e
(WW) AIGLX: 3D driver claims to not support visual 0x6f
(WW) AIGLX: 3D driver claims to not support visual 0x70
(WW) AIGLX: 3D driver claims to not support visual 0x71
(WW) AIGLX: 3D driver claims to not support visual 0x72
(II) AIGLX: Loaded and initialized /usr/lib/dri/fglrx_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) fglrx(0): Enable the clock gating!
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "ch"
(**) Generic Keyboard: XkbLayout: "ch"
(**) Option "XkbVariant" "de_mac"
(**) Generic Keyboard: XkbVariant: "de_mac"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x6a) [0x48402a]
1: /lib/libc.so.6 [0x7f2c92c35100]
2: /usr/lib/xorg/modules/drivers//fglrx_drv.so(atiddxDisplayShadowIsShadowPixmap+0x16) [0x7f2c911bca86]
3: /usr/lib/xorg/modules//glesx.so [0x7f2c8e1c4723]
4: /usr/lib/xorg/modules//libxaa.so(XAAComposite+0x19b) [0x7f2c901148eb]
5: /usr/lib/xorg/modules//libxaa.so [0x7f2c9012ff1d]
6: /usr/bin/X [0x527ea2]
7: /usr/bin/X [0x515c3f]
8: /usr/bin/X(Dispatch+0x2ef) [0x44eaaf]
9: /usr/bin/X(main+0x47d) [0x436b9d]
10: /lib/libc.so.6(__libc_start_main+0xf4) [0x7f2c92c211c4]
11: /usr/bin/X(FontFileCompleteXLFD+0x279) [0x435ed9]

Fatal server error:
Caught signal 11.  Server aborting

(II) AIGLX: Suspending AIGLX clients for VT switch

```

The issue seems to be a segmentation fault (signal 11) eventually cause with the loading of fonts? The log does not show any errors before the Fatal server error. Can you see something promising to identify the issue or do you have another hint?

Remove it again! I am sorry, I just found it myself the hard way. I installed intrepid and I got stuck with a blackscreen at that stage though 8.04 worked flawlessly with these options. Don't ask me why they render your system unusable. I'm so sorry...

---

### Post by cariboo on 2008-10-20
You might be better off asking your question here:

[http://ubuntuforums.org/forumdisplay.php?f=346](http://ubuntuforums.org/forumdisplay.php?f=346)

as the above forum is specific to Intrepid testing.

Jim

---

### Post by mfehr on 2008-10-27
I made some progress. I installed EnvyNG which configured a different ATI driver for me. As a result, tvtime now runs better than with the other drivers I tried before: When tvtime is launched in window mode, it flickers about every second (before it was much more nervous video refresh). If I overlap a window over the tvtime window or move the mouse (without clicking), the video flickering increases immediately. - This looks like interrupt issues in the old Windows 3.x times.

EnvyNG configured xorg.conf with 2 Options:
VideoOverlay "on"
OpenGLOverlay "off"
There is no difference whether these parameters are active, commented or even configured with opposite content. I also tried with all the Options soxs brought up with the same result.

---

### Post by markbuntu on 2008-10-29
You can just run off the desktop visual effects and that will eliminate the flickering. The only other option that seems to work somewhat for some cards is

TexturedVideo "off"

You can also look here, which is the only place I ever saw that mentioned tvtime and flgrx at the same time:


[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

---

### Post by 080818jk on 2008-10-30
&#25216;&#26415;&#20248;&#21183;&#65306;&#20445;&#25345;&#34892;&#19994;&#25216;&#26415;&#39046;&#20808;&#12289;&#24341;&#23548;&#21943;&#27849;&#28040;&#36153;&#29702;&#24565;&#12289;&#20381;&#25176;&#25216;&#26415;&#35851;&#21457;&#23637;&#12289;&#20381;&#38752;&#25216;&#26415;&#36194;&#24066;&#22330;&#65292;&#26159;&#20844;&#21496;&#25104;&#31435;&#20043;&#21021;&#21046;&#23450;&#20844;&#21496;&#21457;&#23637;&#30340;&#22522;&#26412;&#26041;&#38024;&#65292;[**&#23460;&#20869;&#21943;&#27849;**](http://www.music-water.com/snpq.htm)&#20844;&#21496;&#25237;&#20837;&#22823;&#37327;&#20154;&#21147;&#12289;&#36130;&#21147;&#24320;&#21457;&#21943;&#27849;&#19987;&#29992;&#25216;&#26415;&#65292;&#29616;&#24050;&#25104;&#21151;&#24320;&#21457;&#20102;&#38899;&#20048;&#21943;&#27849;&#35745;&#31639;&#26426;&#25511;&#21046;&#31995;&#32479;&#12289;&#36828;&#31243;&#25511;&#21046;&#22411;&#36305;&#27849;&#25511;&#21046;&#22871;&#20214;&#12289;&#24452;&#21521;&#25671;&#25670;&#31995;&#32479;&#22871;&#20214;&#12289;&#25913;&#36827;&#22411;&#40509;&#24335;&#25671;&#25670;&#22871;&#20214;&#12289;[**&#21943;&#27849;&#35774;&#22791;**](http://www.music-water.com/shebei.asp?id=59)&#28418;&#28014;&#24335;&#21943;&#27849;&#27785;&#28014;&#26426;&#26500;&#22871;&#20214;&#12289;&#20809;&#20142;&#21943;&#27849;&#22871;&#20214;&#12289;&#30334;&#31859;&#21943;&#27849;&#24635;&#25104;&#22871;&#20214;&#12289;&#24494;&#30005;&#33041;&#25511;&#21046;&#32418;&#22806;&#24863;&#24212;&#22411;&#25103;&#27700;&#21943;&#27849;&#22871;&#20214;&#12289;&#26097;&#22320;&#22411;&#36277;&#31361;&#27849;&#22871;&#20214;&#12289;&#25671;&#25670;&#26426;&#26500;&#23450;&#20301;&#31995;&#32479;&#22871;&#20214;&#31561;&#25968;&#21313;&#31181;&#21943;&#27849;&#23454;&#29992;&#22411;&#25216;&#26415;&#12290;&#12288;&#12288;&#20154;&#25165;&#20248;&#21183;&#65306;&#20154;&#25165;&#26159;&#25216;&#26415;&#30340;&#36733;&#20307;&#65292;[**&#21943;&#27849;&#25511;&#21046;**](http://www.music-water.com/products.asp?id=1)&#25216;&#26415;&#26159;&#20154;&#25165;&#30340;&#20215;&#20540;&#12290;&#26368;&#22823;&#38480;&#24230;&#30340;&#21457;&#29616;&#20154;&#25165;&#12289;&#24341;&#36827;&#20154;&#25165;&#12289;&#22521;&#20859;&#20154;&#25165;&#65292;[**&#21943;&#27849;&#24037;&#31243;**](http://www.music-water.com/gc.asp?id=64)&#20026;&#20844;&#21496;&#30340;&#21457;&#23637;&#22880;&#23450;&#20102;&#22362;&#23454;&#30340;&#22522;&#30784;&#12290;&#20844;&#21496;&#24341;&#36827;&#20102;&#33258;&#21160;&#21270;&#25511;&#21046;&#12289;&#33402;&#26415;&#31574;&#21010;&#12289;&#25928;&#26524;&#35774;&#35745;&#12289;&#26426;&#26800;&#35774;&#35745;&#12289;&#26045;&#24037;&#31649;&#29702;&#31561;&#19968;&#25209;&#39640;&#32423;&#20154;&#25165;&#65292;&#20182;&#20204;&#19981;&#20165;&#22312;&#26412;&#19987;&#19994;&#26377;&#36739;&#28145;&#30340;&#36896;&#35811;&#65292;[**&#21943;&#27849;&#20844;&#21496;**](http://www.music-water.com/pqgs.htm)&#32780;&#19988;&#37117;&#26377;&#22810;&#24180;&#20174;&#20107;&#21943;&#27849;&#34892;&#19994;&#30340;&#32463;&#21382;&#65292;&#22312;&#21508;&#33258;&#19987;&#19994;&#22312;&#21943;&#27849;&#34892;&#19994;&#30340;&#24212;&#29992;&#26041;&#38754;&#20316;&#20986;&#20102;&#24040;&#22823;&#30340;&#25104;&#23601;&#12290;

---

### Post by mfehr on 2008-11-06
Heureka! I found the solution: Turning visual effects off solved the problem. I currently use the ati drivers installed and configured by envy-ng. NO changes to /etc/X11/xorg.conf required. 

Just right-click on your desktop and select "Change Desktop Background" - "Visual Effects" - "None"

I was close to evaluate an alternate graphics card... but this approach saved further frustration...

---

