---
title: "Advanced? Cant' find 32bits OpenGL libraries &amp; Direct3D9 is not available w/o OpenGL."
date: 2012-12-09
forum: Wine
---

### Post by NoCyberDom on 2012-12-09
Hi all,

First, I've researched this half to death and have already tried the common solutions... no joy on any of them. I really don't want to have to put WinXP on another drive but I'm nearing the end of my rope.

Symptoms:

POL starts with saying it's unable to find 32 bit OpenGL libs despite the fact that they are definitely installed. I start Guild Wars 2 and get the downloading screen but from the internet activity it's clear that the dat file is fully downloaded. 

For more info, I restarted GW2 via command line and after it initializes I get this error repeated, scrolling down the terminal window: [I]"Direct3D9 is not available without OpenGL."

[/I]General Info:

Ubuntu 12.04
ia32-libs is installed.
CPU: AMD FX6100 (6 core bulldozer)... CPU activity is low (under 35%) on all 6 CPU's. 
RAM: 16G, not even using 20% of it per resources analyser.

Graphics Info:
Nvidia GT640
Driver: NVIDIA-Linux-x86_64-310.19.run (Downloaded today, 12/9/12)
32 bit libs during install? YES

me@mycoputer:~$ glxinfo | grep -i render
direct rendering: Yes
OpenGL renderer string: GeForce GT 640/PCIe/SSE2
    GL_NV_conditional_render, GL_NV_copy_depth_to_color, GL_NV_copy_image, 
    GL_NV_parameter_buffer_object2, GL_NV_path_rendering, 
    GL_NVX_conditional_render, GL_NVX_gpu_memory_info, 
    GL_OES_depth_texture, GL_OES_element_index_uint, GL_OES_fbo_render_mipmap, 

POL Info:
POL Version 4.1.8
Wine Version for this virtual drive: 1.5.18
** I suspect this is a 32 bit wine version as POL does not allow me to select any 64 bit versions when installing GW2.

GW2 Info:
Argument when called: -dxsingle
Registry keys already created:
     "HKEY_CURRENT_USER/Software/wine/Direct3D" ... "UseGLSL" ... "disabled"
                                                            and
     ""HKEY_CURRENT_USER/Software/wine/Direct3D" ... "Multisampling" ... "enabled"

Any constructive ideas are greatly appreciated.

Thanks,
NCD

---

### Post by NoCyberDom on 2012-12-09
Color coding is intended to make this easier to follow... During my attempts I noticed this:

*[COLOR=DarkOrange]p11-kit: couldn't load module:  /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so:  /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open  shared object file: [/COLOR][COLOR=Red]No such file or directory[/COLOR]*

Googling that took me to this suggestion about getting the libs and making links:
*[http://askubuntu.com/questions/127848/wine-cant-find-gnome-keyring-pkcs11-so](http://askubuntu.com/questions/127848/wine-cant-find-gnome-keyring-pkcs11-so)*

Along the way I learned that:
[COLOR=SeaGreen]*ia32-libs is already the newest version.*[/COLOR]

But I had not yet made the links... and this is where it got weird... pasted terminal output is color coded to make it easier to notice what I see.

[I][COLOR=SeaGreen]me@mymachine:~$ sudo mkdir -p /usr/lib/i386-linux-gnu/pkcs11/ 
[/COLOR][/I]**[COLOR=SeaGreen][COLOR=Black]It appears to have made the dir, as expected.[/COLOR][/COLOR]**[I][COLOR=SeaGreen]
[/COLOR]
[COLOR=DarkOrange]me@mymachine:~$ sudo ln -s /usr/lib32/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so[/COLOR]
[COLOR=Red]ln: failed to create symbolic link `/usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so': File exists[/COLOR][/I]
**Huh?? How can it exist if I just made the dir? **

So I ran GW2 in the same terminal window... here is the OP:
[I]
[COLOR=SeaGreen]me@mymachine:~$ /usr/share/playonlinux/playonlinux --run "Guild Wars 2" %F
[main] Message: PlayOnLinux (4.1.8) is starting
[clean_tmp] Message: Cleaning temp directory
Script started /home/ncd/.PlayOnLinux/shortcuts/Guild Wars 2
[POL_System_CheckFS] Message: Checking filesystem for Gw2.exe
[POL_Wine] Message: Running wine-1.5.12-GuildWars2 Gw2.exe -dx9single %F (Working directory : /home/ncd/.PlayOnLinux/wineprefix/GuildWars2/drive_c/Program Files (x86)/ArenaNet/Guild Wars 2)
[POL_Wine] Message: Notice: PlayOnLinux deliberately disables winemenubuilder. See [http://www.playonlinux.com/fr/page-26-Winemenubuilder.html](http://www.playonlinux.com/fr/page-26-Winemenubuilder.html)[/COLOR]
[COLOR=DarkOrange]p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file:[/COLOR] [COLOR=Red]No such file or directory[/COLOR]
Direct3D9 is not available without OpenGL.
Direct3D9 is not available without OpenGL.
Direct3D9 is not available without OpenGL.[/I]

---

### Post by NoCyberDom on 2012-12-09
Sigh... tracing things hand over hand like a string revealed that the link is there, but it's broken.

/usr/lib32/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so

cant' be linked to because the dir

/usr/lib32/i386-linux-gnu/

doesn't exist.

Yes, I had the nvidia installer install the 32bit libs... four times. 

Taking a break to ease the headache... any help is appreciated.

Thanks

---

### Post by NoCyberDom on 2012-12-09
> **NoCyberDom said:**
> 

/usr/lib32/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so

cant' be linked to because the dir

/usr/lib32/i386-linux-gnu/

doesn't exist.


After a break I installed the keyring, which I apparently did not have... but it didn't create that dir either. 

Instead it installed *[COLOR=DarkOrange]gnome-keyring-pkcs11.so[/COLOR]* to:
/usr/lib/x86_64-linux-gnu/pkcs11/

So I deleted the old link, created a new one to redirect to the actual location of the .so and upon starting GW2 I once again that same old scrolling line:
[I]
Direct3D9 is not available without OpenGL[/I]
[I]Direct3D9 is not available without OpenGL
.
.
.

[/I]I have officially lost my sense of humour with this issue.

---

### Post by NoCyberDom on 2012-12-21
This remains unsolved but I found a workaround... I installed 12.04 32 bit in another partition and ran the program off that.

---

