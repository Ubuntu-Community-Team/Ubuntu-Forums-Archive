---
title: "Xorg/OpenGL/Wine issues"
date: 2007-02-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by genewitch on 2007-02-22
Ok... i have to say that ubuntu that it is a lot nicer than SUSE, so far.

With that being said, i'd like to state that the main reason i have never used linux for more than a few weeks after being installed... i am still having THAT issue.

Yes, that's right. xwindows, xorg.conf, aticonfig, beryl, etc etc etc. Why can't they play nice?
Without futher ado, here is my issue.
Beryl is working. Sorta. it crashes to login screen randomly, coming back up with metacity selected.
That means that XGL is working, i'd assume.
here's my problem:
genewitch@UBUSIT:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string:  [B]Generic
[/B]OpenGL version string: 2.0.6286 (8.33.6)

I can not, for the life of me, get that to not be "generic". The reason it shouldn't be generic is:
root@UBUSIT:/mnt/wait/World of Warcraft# wine wow.exe -opengl
err:module:load_builtin_dll failed to load .so lib for builtin L"OPENGL32.dll": libXext.so.6: cannot open shared object file: No such file or directory
err:module:import_dll Loading library OPENGL32.dll (which is needed by L"Z:\\mnt\\wait\\World of Warcraft\\wow.exe") failed (error c000007a).
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\mnt\\wait\\World of Warcraft\\wow.exe" failed, status c0000135

See? Nothing is noticing that i have a real video card installed. (except beryl, which is nice).

I followed the directions here [http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)
First, then i did what i did on SUSE, do everything by hand. and pretty much the same thing happened, Xorg.conf gets borked by something during reboot... on SUSE it was sax2, on ubuntu i think it is dexconf? anyhow...

Basically, i need to know how to get opengl up and running on 64 bit Ubuntu.
oh... more output
root@UBUSIT:/mnt/wait/World of Warcraft# glxinfo
name of display: :1.0
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
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
OpenGL renderer string:  Generic
OpenGL version string: 1.2 (2.0.6286 (8.33.6))
OpenGL extensions:
    GL_ARB_multitexture, GL_ARB_texture_border_clamp, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_dot3, GL_ARB_transpose_matrix, GL_EXT_abgr, 
    GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

----
root@UBUSIT:/mnt/wait/World of Warcraft# uname -a
Linux UBUSIT 2.6.17-11-generic #2 SMP Thu Feb 1 18:03:05 UTC 2007 x86_64 GNU/Linux
----

root@UBUSIT:/mnt/wait/World of Warcraft# glxgears -printfps
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
45155 frames in 5.0 seconds = 9030.942 FPS
48596 frames in 5.0 seconds = 9719.200 FPS
48213 frames in 5.0 seconds = 9631.723 FPS
48187 frames in 5.0 seconds = 9630.609 FPS

It appears that GL is working, but lots of little things are happening that lead me to believe that it isn't, like that whole wine thing.

Also, i have a dual core amd... Is it in my best interest to continue using ubuntu x64? or should i switch to 32? or should i really be using another operating system (like 32 bit suse or something)?

My level of linux expertise is (can recompile a kernel and boot off of it without help + full commandline junkie)

Thanks! 

PS -  as far as wine goes, i've tried doing the --force method (forcing i386), i've tried compiling from source (which worked, but gave the same error as above) and tried using the one that was linked elsewhere in these forums called: wine_0.9.30-1_amd64.deb

All three give the same error, that opengl32.dll is not found. whatever.

thanks again!

---

### Post by genewitch on 2007-02-22
Just to prove that stuff is working... and to add another question (see below the pic for question, please!)
[IMG]http://i31.photobucket.com/albums/c389/genewitch/Screenshot.png[/IMG]

<br>
anyhow... when i hit shift backspace... XGL logs me out and asks for username and password... where do i disable that? because i have been doing it a lot on accident.

Also, the login screen looks like it is set at 1600X1200 (the login bit is waaaay over on the right hand side, and i can't see the options button anywhere....) where do i set this?

---

### Post by Nameless_one on 2007-02-22
As for the shortcut you keep pressing, have you checked in System > Preferences > Keyboard shortcuts?

---

### Post by RAOF on 2007-02-22
All that output seems normal.  You don't get Direct Rendering with XGL (because XGL is already using the direct-rendering hardware).

Since your problem seems to be Wine, I'd suggest that you make sure that you have the **ia32-libs** package installed, which has the 32bit version of the *libXext.so.6* library wine is complaining about.

---

### Post by genewitch on 2007-02-25
ok so how do i disable XGL temporarily so i can run direct rendering?
i want to see if bf2142 and WOW work, if so i won't use windows anymore.

---

### Post by RAOF on 2007-02-25
You don't really need to - OpenGL should work in XGL, just slightly slower.

Alternatively, you can just select a non-XGL session, if that's the way you've got it set up, or try running the program on DISPLAY=:0

---

### Post by 4KvRMU7Nnv on 2007-02-25
shift backspace problem is fixed:

make a script.  paste the following in it:

#!/bin/bash
xmodmap -e "keycode 22 = BackSpace Delete"

save as whatever you like then make it executable

sudo chmod 755 <your file>

then put the script inside the sessions startup area and restart X.  It will be fixed.

---

### Post by genewitch on 2007-02-26
> **d3br074 said:**
> shift backspace problem is fixed:

make a script.  paste the following in it:

#!/bin/bash
xmodmap -e "keycode 22 = BackSpace Delete"

save as whatever you like then make it executable

sudo chmod 755 <your file>

then put the script inside the sessions startup area and restart X.  It will be fixed.

Thanks for this.
I fixed the wine issue, $LD_LIBRARY_PATH, and also ld.so.conf added:
/emul/ia32-linux/usr/lib
as a path... wine starts perfectly now.

Only problem is... it's really slow.
On Suse i was able to pump 40FPS through a fullscreen WOW.exe -opengl session...
Now it seems to be running about 3fps.
I am in a gnome session, rather than XGL..
and i am still showing:
Xlib:  extension "XFree86-DRI" missing on display "localhost:1.0".
On certain things.
I downloaded Scorched3d from synaptic, and it looks like crap, cause rather than the right text and little color bars it just shows gibberish, like FFFFFFFFFFFFFOoooooo instead of a horizontal bar. the islands look ok, and i can see the enemies, etc, so the WHOLE graphics subsystem isn't borked, just parts of it.
Maybe the DRI?
I wish i knew what it was.

---

### Post by revellion on 2007-02-28
> **genewitch said:**
> Thanks for this.
I fixed the wine issue, $LD_LIBRARY_PATH, and also ld.so.conf added:
/emul/ia32-linux/usr/lib
as a path... wine starts perfectly now.

Only problem is... it's really slow.
On Suse i was able to pump 40FPS through a fullscreen WOW.exe -opengl session...
Now it seems to be running about 3fps.
I am in a gnome session, rather than XGL..
and i am still showing:
Xlib:  extension "XFree86-DRI" missing on display "localhost:1.0".
On certain things.
I downloaded Scorched3d from synaptic, and it looks like crap, cause rather than the right text and little color bars it just shows gibberish, like FFFFFFFFFFFFFOoooooo instead of a horizontal bar. the islands look ok, and i can see the enemies, etc, so the WHOLE graphics subsystem isn't borked, just parts of it.
Maybe the DRI?
I wish i knew what it was.

Try to run WoW on the underlying Xorg instead. with something like DISPLAY=:93 wine WoW.exe -opengl

or whatever the :X you get if you do ps aux|grep X

---

