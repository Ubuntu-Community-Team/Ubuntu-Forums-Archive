---
title: "Ubuntu 7.1 / Lineage II / Wine 9.54 HELP"
date: 2008-02-15
forum: Wine
---

### Post by carnivore1 on 2008-02-15
Hey All,

I am trying to get Lineage II working on Ubuntu 7.1 with Wine 9.54. eveything seemed to install fine and i even got the patcher up and patched to game. however, when i try to execute the game itself the window just disapears.

I tried this with the Terminal and i recieve the following errors when loading the game:

[COLOR="Navy"][B]fixme:reg:GetNativeSystemInfo (0x10a6b0b1) using GetSystemInfo()
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0x260298d): Stub!
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0x10ad20d2): Stub!
fixme:process:GetProcessWorkingSetSize (0xffffffff,0x34f028,0x34f024): stub
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
err:d3d:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat
err:d3d:InitAdapters Failed to get a gl context for default adapter
[/B][/COLOR]

Any suggestions on how to make this work??

---

### Post by Beren Camlost on 2008-02-15
Do you have Direct Rendering enabled?

To check this, type the following in a terminal:

```

[COLOR=Blue]glxinfo | grep -i direct
[/COLOR]
```[COLOR=Blue]

[COLOR=Black] As the error you get is rendering related, you may want to start with that.[/COLOR]
[/COLOR]

---

### Post by Sammi on 2008-02-15
What graphics card do you have and what driver is installed for it?

---

### Post by Sugi on 2008-02-15
I am pretty sure Lineage II broken after wine 0.9.50.  I know for myself, I am currently running it under 0.9.50 at the moment.  My error was within Lineage II, saying something about directx wasn't up to date.  Even though, I was update for my Lineage II directory.

Try uninstalling wine and reinstalling 0.9.50 and see if that helps at all.  There documents reporting that 0.9.49 works flawlessly as well.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=59726&stc=1&d=1203093997[/IMG]
Don't mind the man show, lineage 2 is on the right side.


Sugi

---

### Post by carnivore1 on 2008-02-15
> **Beren Camlost said:**
> Do you have Direct Rendering enabled?

To check this, type the following in a terminal:

```

[COLOR=Blue]glxinfo | grep -i direct
[/COLOR]
```[COLOR=Blue]

[COLOR=Black] As the error you get is rendering related, you may want to start with that.[/COLOR]
[/COLOR]

running the command you gave me returns the following:

[COLOR="Navy"]direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
[/COLOR]

to follow up with this i also ran glxinfo and that returned the following:

[COLOR="Navy"]name of display: :1.0
display: :1  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_framebuffer_sRGB
GLX version: 1.2
GLX extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_SGIX_fbconfig, 
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce Go 7300/PCI/SSE2
OpenGL version string: 1.2 (2.1.1 NVIDIA 100.14.19)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_imaging, GL_ARB_multitexture, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shadow, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_window_pos, GL_ARB_texture_non_power_of_two, GL_ARB_vertex_program, 
    GL_ARB_fragment_program, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_texture3D, GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, GL_EXT_texture_lod, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_vertex_array, 
    GL_ATI_texture_mirror_once, GL_IBM_texture_mirrored_repeat, 
    GL_NV_blend_square, GL_NV_texgen_reflection, GL_NV_texture_rectangle, 
    GL_NV_texture_env_combine4, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, 
    GL_SGIX_depth_texture, GL_SGIX_shadow
[/COLOR]

as you can see from above i am using the NVIDIA  GeForce Go 7300/PCI/SSE2 Card on a DELL Inspiron E1505 Laptop.

---

### Post by Beren Camlost on 2008-02-15
As I suspected, you don't have Direct Rendering enabled, which means you won't be able to play 3D games at all.

This is not my area of expertise, but try reconfiguring xorg:```

sudo dpkg-reconfigure xserver-xorg
```

If that doesn't help, I assume you will have to reinstall your nvidia driver.

---

### Post by carnivore1 on 2008-02-15
> **Beren Camlost said:**
> As I suspected, you don't have Direct Rendering enabled, which means you won't be able to play 3D games at all.

This is not my area of expertise, but try reconfiguring xorg:```

sudo dpkg-reconfigure xserver-xorg
```

If that doesn't help, I assume you will have to reinstall your nvidia driver.

Hey Beren, 

Thanks for the reply, unfortunately its still giving me the same results. i tried both your suggestions and its a no go :(

---

### Post by carnivore1 on 2008-02-15
GOT IT!! :guitar:

this was a brand new install of ubuntu 7.1 so i had nothing to lose by trying a re-install and starting from scratch.

doing so and then loading appropriate updates seems to have fixed at the very least my issue with not being able to get Direct Rendering Enabled.

not sure if Lineage is going to run yet but i will post back when I'm done reinstalling it and have more info.

---

