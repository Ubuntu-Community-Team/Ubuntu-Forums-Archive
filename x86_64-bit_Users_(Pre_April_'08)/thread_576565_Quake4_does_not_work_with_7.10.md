---
title: "Quake4 does not work with 7.10"
date: 2007-10-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by xt600 on 2007-10-15
Quake4 works fine with Sabayon on my pc but I can not get it to work with Ubuntu Gutsy!

:(    Any ideas or help?

Loading guides.... 64 loaded
242ms to load 1125k of material
77ms to load 43k of skin
188ms to load 723k of sound
5ms to load 1k of materialType
443ms to load 2889k of lipSync
74ms to load 105k of playback
1024ms to load 1690k of effect
---------------------------------------------
-------- Initializing renderSystem ----------
using ARB renderSystem
renderSystem initialized.
---------------------------------------------
Found default language English with VO
.... found additional language 'french' without VO
.... found additional language 'italian' without VO
.... found additional language 'spanish' with VO
696 strings read from strings/english_code.lang
1794 strings read from strings/english_guis.lang
5756 strings read from strings/english_lips.lang
5759 strings read from strings/english_mappack.lang
6235 strings read from strings/english_maps.lang
3 strings read from strings/french_mappack.lang
3 strings read from strings/italian_mappack.lang
632 strings read from strings/spanish_code.lang
1654 strings read from strings/spanish_guis.lang
5616 strings read from strings/spanish_lips.lang
5619 strings read from strings/spanish_mappack.lang
6088 strings read from strings/spanish_maps.lang
Couldn't open journal files
execing default.cfg
"ALT" isn't a valid key
"CTRL" isn't a valid key
couldn't exec editor.cfg
couldn't exec Quake4Config.cfg
couldn't exec autoexec.cfg
-------- Initializing Sound System ----------
sound system initialized.
---------------------------------------------
--------------- R_InitOpenGL ----------------
Initializing SDL subsystem
Loading GL driver 'libGL.so.1' through SDL
SDL_ListModes:
1024x768 SDL_ListModes are currently ignored for resolution filtering. Set r_useSDLModes to 1 if you want it
8/8/8/8 RGBA bits, 24 depth bits, 8 stencil bits
1 pixels multisampling
dlopen(libasound.so.2)
asoundlib version: 1.0.14a
Alsa is available
------ Alsa Sound Initialization -----
opened Alsa PCM device default for playback
device buffer size: 5644 frames ( 22576 bytes )
allocated a mix buffer of 16384 bytes
--------------------------------------
...using GL_ARB_multitexture
...using GL_ARB_texture_env_combine
...using GL_ARB_texture_cube_map
...using GL_ARB_texture_env_dot3
...using GL_ARB_texture_env_add
X..GL_ARB_texture_non_power_of_two not found
X..GL_NV_blend_square not found
X..GL_ARB_texture_compression not found
Fatal Error: Texture compression unavailable
Shutting down SDL subsystem
--------------- BSE Shutdown ----------------
---------------------------------------------
Shutting down sound hardware
----------- Alsa Shutdown ------------
close pcm
dlclose
--------------------------------------
idRenderSystem::Shutdown()
Sys_Error: Texture compression unavailable


P3 1 gig ram Radeon 9600 Pro agp

---

### Post by pcoyote on 2007-10-31
Same problem here. I tried using Envy to update my nvidia driver with no luck. I entered glxinfo in a terminal and interestingly it said that opengl was version 1.2, which does not support texture compression.

The only other thing I knew to try next was to disable xgl and it worked. To disable it, add a directory under ~/.config named xserver-xgl and run the follwing in a terminal:

touch ~/.config/xserver-xgl/disable

That just adds an empty file named disable to disable xgl. You have to log out and log back in for it to take effect. You can delete the file to enable xgl.

Now if someone would figure out how to run Quake 4 with xgl enabled, I would be very grateful.

---

### Post by tekhawk on 2007-10-31
most likly wont happen most opengl games wont run with xgl running however i have had some luck running opengl with using the nvidia system to replace xgl ive only done that on beryl though and im not sure if that can be done easly with gutsy

---

### Post by bdamon on 2007-11-03
Quake4 runs ok for me on a fresh install Gutsy 64bit Nvidia 8600GT. I have garbled sound though

Edit

Ok Sound was an easy fix. I have Q4 running fine here with compiz enabled.

---

### Post by saintlostone on 2007-11-04
I tried to dl the .run file from id, but it only opens in the same window as code.  I need something that runs or instructions for how to manually install.  Any ideas?](*,):confused::-x

---

### Post by orange2k on 2007-11-05
[http://zerowing.idsoftware.com/linux/quake4/](http://zerowing.idsoftware.com/linux/quake4/)

I had to run the installer like this: sudo sh quake4-linux-1.4.2.x86.run

Then I copied the requiered .pk4 files via terminal with cudo cp to the install directory (nautilus won`t work because of permissions)...

The game itself must be run as: sudo quake4

Another problem was that the game menus were in spanish, so I had to change the configuration file which will be located in your home directory, but in the  hidden folder .quake4

---

### Post by bdamon on 2007-11-05
> **saintlostone said:**
> I tried to dl the .run file from id, but it only opens in the same window as code.  I need something that runs or instructions for how to manually install.  Any ideas?](*,):confused::-x

I had that happen too. If I recall you can right click in the window and save it as a file. Also if you change the permissions on the pk4 files to 755 you can run the game as a regular user.

---

### Post by Ranime on 2007-11-26
> **bdamon said:**
> I had that happen too. If I recall you can right click in the window and save it as a file. Also if you change the permissions on the pk4 files to 755 you can run the game as a regular user.

Or richtclick on the link and choose save target as... ;)

---

### Post by cv_zero on 2007-12-27
i'm having problems with it too, but a different error, terminal output..

cvzero@severus:~$ sudo quake4
[sudo] password for cvzero:
./quake4.x86: error while loading shared libraries: libSDL-1.2.so.0: cannot open shared object file: No such file or directory


is there a way i can find out where quake is looking for the lib, libSDL......   IS installed on my system, i think a simlink might be missing somewhere....any help aleays appreciated

---

### Post by Rhubarb on 2007-12-27
You shouldn't have to install Quake 4 with administrator priviliges (sudo).
Unfortunatly I'm currently away from my 64bit PC at the moment, so I can't test this.

I do know in ubuntu 7.04 I was able to easily install it without admin rights.

---

