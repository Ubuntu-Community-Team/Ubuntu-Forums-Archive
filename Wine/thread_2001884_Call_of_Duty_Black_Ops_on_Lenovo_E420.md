---
title: "Call of Duty Black Ops on Lenovo E420"
date: 2012-06-11
forum: Wine
---

### Post by Ranko Kohime on 2012-06-11
Now I know some are going to say it isn't possible, I need a desktop with a hefty graphics card blahblahblah...So let's get that out of the way first.

[http://www.youtube.com/watch?v=LLDNhzEr9go]("http://www.youtube.com/watch?v=LLDNhzEr9go")

The game does run, tolerably even, (albeit apparently under Windows), on the Intel HD3000 graphics that this laptop has.  ):P

But anyway.  I've installed it using PlayonLinux, and right now, if I start from the PoL window, I get the intro video at about 1 FPS, with the BlackOps.exe spiking a core.  (around 104%, typically).  No audio.

PoL created a desktop launcher icon, which calls itself (PoL) to start BO.  With PoL NOT running, if I click on this icon, I get the intro video at normal speed, with audio, in an 800x600 resolution.  After the intro video, I get a black screen, and BlackOps.exe spiking a core again.

So far the only thing I've tried tweaking is the "UseGLSL" option in the Wine Registry, which has the effect of the game not starting with the error "Shader Model 3.0 not available.", when disabled.  When enabled, I get the above.

For hardware, I've got a Lenovo E420, Core i3-2310M (2.10GHz), 8GB DDR3 running at 1333MHz, 80GB SSD as SDA, and 1TB HDD as SDB.  Running Ubuntu 12.04.

I can post any logs that Ubuntu, Wine, PoL or BO spits out, just tell me where they can be found.

---

### Post by Dlambert on 2012-06-12
I've ran it on my gaming rig @60+FPS. So I know it runs. 


> Try a clean WINE prefix (I think it's not necessary)

Install Directx from the CoD:BO game directory.

Set winever to XP.

Set dsound to builtin.

I use ALSA with full hardware aceleration. 

Set Direct Draw to opengl. And maybe Off screen to Fbo or backbuffer. You have drivers correct?

---

### Post by Ranko Kohime on 2012-06-12
> **Dlambert said:**
> Set Direct Draw to opengl. And maybe Off screen to Fbo or backbuffer. You have drivers correct?
Where might those two options be?

And, I have not loaded any drivers specially for my configuration, I let Ubuntu handle the display.  Are there some drivers I should attempt to load?

ETA: I believe PoL does the first thing on the list you quoted, and everything else I've checked off.

---

### Post by Dlambert on 2012-06-12
Alright, SO in POL Hit configure the go over to display and you will see those options. 

Update: Try playing in a small windowed session and post results.

---

### Post by Dlambert on 2012-06-12
Never mind about the drivers: You have 3000 Intel graphics if I'm not mistaken. It will be difficult for this game to run, But I was able to run COD4 on my GM4500 Back in the day. So it should work.

---

### Post by Ranko Kohime on 2012-06-12
> **Dlambert said:**
> Alright, SO in POL Hit configure the go over to display and you will see those options. 

Update: Try playing in a small windowed session and post results.
Oh.  I didn't realize that button did something that wasn't available in the right-click menu.  :oops:

Anyway, I set DD to opengl, and Off Screen to Fbo and backbuffer, but neither had any effect.

Running in a windowed session produces the same results.

Multi-Player, for some reason, (I can't recall changing anything to cause this to happen), now skips the intro and goes straight to a menu, I would assume, as I hear what sounds like menu music.  If I press Esc, I get a game menu sound effect.  However, the window is still pitch black, and so I have no way of controlling anything in it.  It will quit by clicking the X on the Wine window, whereas single player requires I kill BlackOps.exe manually.

---

### Post by Dlambert on 2012-06-13
Set everything to LOW?

---

### Post by Ranko Kohime on 2012-06-13
> **Dlambert said:**
> Set everything to LOW?
In-game, I assume?  That's not doable, as I'm unable to interact with the in-game menus.

Out of game, I'm afraid I'd have to ask again where.  :oops:

---

### Post by Dlambert on 2012-06-13
> Call of Duty: Black Ops looks set to be another massive hit for Activision, even allowing for the company’s slightly reduced expectations for sales. Even so, on release the multiplayer performance has been less than stunning.
Many report poor frame rates and keyboard-pummelling lag. We’ve experienced similar frustrations ourselves, so here’s the PC Format quick guide for getting smoother frame rates out of your machine.
First, take your graphics settings out of the equation by setting everything to fugly. You’ll be able to dial all those settings up again later, but when it comes to trying to sort out your connection and general performance settings, it’s worth easing back on the ol’ GPU first.
Turn ANTI_ALIASING OFF.
Set SYNC EVERY FRAME is set to NO.
Set TEXTURE FILTERING to BILINEAR.
TEXTURE QUALITY to LOW.
Turn SHADOWS OFF.
Turn BULLET IMPACTS OFF.
Well done, you’ve just made Call of Duty: Black Ops looks ten years old. It should, however, now spin along at silly frame rates. Give it a go, and see if it runs any smoother.

The next stage is to get your hands dirty and throw yourself, hands flailing, at the configuration file, where you’ll find far more juicy sounding settings. The jury is still out on which settings actually have any real effect on your performance, but try the following and cross your fingers.
You’ll find the config file in your Steam folder (by default “C:\Program Files (x86)\Steam”) inside the “steamapps\common\call of duty black ops\players” folder.
Open the config_mp.cfg up in Wordpad and scroll down until you find the line:
seta r_multiGpu “1”
Change the “1” to “0”.
IF, and only if you only have one video card. If you have multiple video cards (SLI mode), setting it to 0 will reduce performance.
Directly underneath it you’ll find:
seta r_multithreaded_device “0”
Change the “0” to “1”.
Again, this is if, and only if you have a multi-core CPU.
There are plenty of other settings in here worth messing around with, including the all-important net code parameters – although with a rumoured overhaul in the netcode in the works, it’s not worth losing too much sleep over this.
The main value you need to mess around with is cl_maxpackets, which you should try setting to “100” to see if it makes any difference.
Also on PC Format:
Poll – Are you happy with Black Op’s multiplayer performance at launch?
QuickFix: Split screen Left 4 Dead 2
The Good, the Bad and the Plain Ugly of Black Ops Multiplayer by the PCF Clan

Try those!

---

### Post by Ranko Kohime on 2012-06-16
> **Dlambert said:**
> Try those!
Well, the first half I still cannot access...  (can't get into the game to modify those settings), and the second half is already set exactly like your quote.

---

### Post by Dlambert on 2012-06-16
Ah..maybe look up where those settings are in the file.

---

### Post by Ranko Kohime on 2012-06-23
Here's an update.  I ran with debugging enabled, twice, and got the following log files.  In both cases, the game had to be force quit.

```
ranko@yggdrasil:~/.PlayOnLinux/wineprefix/CoDBlackOps/drive_c/Program Files (x86)/Activision/Call of Duty - Black Ops$ playonlinux BlackOps.exe 
[install_plugins] Message: Checking plugin: Offline PlayOnLinux...
[install_plugins] Message: Checking plugin: Capture...
[Check_OpenGL] Message: 32bits direct rendering is enabled
[install_plugins] Message: Checking plugin: Transgaming Cedega...
[install_plugins] Message: Checking plugin: WineImport...
[Check_OpenGL] Message: 64bits direct rendering is enabled
[install_plugins] Message: Checking plugin: Wine Look...
[main] Message: Filesystem is compatible
[install_plugins] Message: Checking plugin: ScreenCap...
[install_plugins] Message: Checking plugin: PlayOnLinux Vault...
[main] Message: Running into a virtual drive : 
[POL_Wine_SelectPrefix] Message: Selecting prefix: CoDBlackOps
[POL_System_CheckFS] Message: Checking filesystem for /home/ranko/.PlayOnLinux/wineprefix/CoDBlackOps/drive_c/Program Files (x86)/Activision/Call of Duty - Black Ops/BlackOps.exe
[POL_Wine_SetVersionEnv] Message: Setting wine version path: 1.4, amd64
[POL_Wine_SetVersionEnv] Message: "/home/ranko/.PlayOnLinux//wine/linux-amd64/1.4" exists
[POL_Wine] Message: Running wine-1.4 /home/ranko/.PlayOnLinux/wineprefix/CoDBlackOps/drive_c/Program Files (x86)/Activision/Call of Duty - Black Ops/BlackOps.exe 
[POL_Wine] Message: Notice: PlayOnLinux deliberately disables winemenubuilder. See http://www.playonlinux.com/fr/page-26-Winemenubuilder.html
[maj_check] Message: Web version : 1340409614
[maj_check] Message: Current local version : 1340311501
[maj_check] Message: Updating list
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory
fixme:thread:SetThreadIdealProcessor (0x80): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x33f3cc,0x00000000), stub!
fixme:thread:SetThreadIdealProcessor (0x9c): stub
fixme:thread:SetThreadIdealProcessor (0xb4): stub
fixme:thread:SetThreadIdealProcessor (0x17c): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x823e0b0,0x00000000), stub!
fixme:d3d:debug_d3dformat Unrecognized 0x5a534552 (as fourcc: RESZ) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x5a534552) in the format lookup table
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:win:EnumDisplayDevicesW ((null),0,0x823e38c,0x00000000), stub!
fixme:thread:SetThreadIdealProcessor (0x19c): stub
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
ALSA lib conf.c:3314:(snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib dlmisc.c:254:(snd1_dlobj_cache_get) Cannot open shared library /usr/lib/i386-linux-gnu/alsa-lib/libasound_module_pcm_pulse.so
ALSA lib dlmisc.c:254:(snd1_dlobj_cache_get) Cannot open shared library /usr/lib/i386-linux-gnu/alsa-lib/libasound_module_pcm_pulse.so
ALSA lib dlmisc.c:254:(snd1_dlobj_cache_get) Cannot open shared library /usr/lib/i386-linux-gnu/alsa-lib/libasound_module_pcm_pulse.so
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
fixme:win:EnumDisplayDevicesW ((null),0,0x823e3b4,0x00000000), stub!
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>/usr/share/playonlinux/lib/wine.lib: line 427:  4975 Killed                  $(POL_Config_Read BEFORE_WINE) wine "$@" 2> >(grep -v menubuilder | tee -a "$WINEPREFIX/playonlinux.log" >&2) > >(tee -a "$WINEPREFIX/playonlinux.log")
[POL_Wine] Error: Wine seems to have crashed

If your program is running, just ignore this message
[POL_Wine] Message: Wine return: 137
>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2566
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2352
```

```
st_x86.exe /q
fixme:clusapi:GetNodeClusterState ((null),0x33ec04) stub!
fixme:advapi:DecryptFileA "c:\\d949cd9138bf7d6695cd\\" 00000000
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directoryfixme:heap:HeapSetInformation (nil) 1 (nil) 0
err:winediag:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path. Usually, you can find it in the winbind package of your distribution.
fixme:advapi:LsaOpenPolicy ((null),0x33f304,0x00000001,0x33f32c) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:storage:create_storagefile Storage share mode not implemented.
fixme:sxs:cache_QueryAssemblyInfo 0x1c47f8, 0x00000002, L"Microsoft.VC90.ATL,version=\"9.0.30729.1\",publicKeyToken=\"1fc8b3b9a1e18e3b\",processorArchitecture=\"x86\",type=\"win32\"", 0x7ae500
fixme:sxs:cache_QueryAssemblyInfo 0x1c47f8, 0x00000002, L"policy.9.0.Microsoft.VC90.ATL,version=\"9.0.30729.1\",publicKeyToken=\"1fc8b3b9a1e18e3b\",processorArchitecture=\"x86\",type=\"win32-policy\""fixme:sxs:cache_QueryAssemblyInfo 0x1c47f8, 0x00000002, L"Microsoft.VC90.CRT,version=\"9.0.30729.1\",publicKeyToken=\"1fc8b3b9a1e18e3b\",processorArchitecture=\"x86\",type=\"win32\"", 0x7ae500
fixme:sxs:cache_QueryAssemblyInfo 0x1c47f8, 0x00000002, L"policy.9.0.Microsoft.VC90.CRT,version=\"9.0.30729.1\",publicKeyToken=\"1fc8b3b9a1e18e3b\",processorArchitecture=\"x86\",type=\"win32-policy\""fixme:sxs:cache_QueryAssemblyInfo 0x1c47f8, 0x00000002, L"Microsoft.VC90.MFC,version=\"9.0.30729.1\",publicKeyToken=\"1fc8b3b9a1e18e3b\",processorArchitecture=\"x86\",type=\"win32\"", 0x7ae500
fixme:sxs:cache_QueryAssemblyInfo 0x1c47f8, 0x00000002, L"policy.9.0.Microsoft.VC90.MFC,version=\"9.0.30729.1\",publicKeyToken=\"1fc8b3b9a1e18e3b\",processorArchitecture=\"x86\",type=\"win32-policy\""fixme:sxs:cache_QueryAssemblyInfo 0x1c47f8, 0x00000002, L"Microsoft.VC90.MFCLOC,version=\"9.0.30729.1\",publicKeyToken=\"1fc8b3b9a1e18e3b\",processorArchitecture=\"x86\",type=\"win32\"", 0x7ae500
fixme:sxs:cache_QueryAssemblyInfo 0x1c47f8, 0x00000002, L"policy.9.0.Microsoft.VC90.MFCLOC,version=\"9.0.30729.1\",publicKeyToken=\"1fc8b3b9a1e18e3b\",processorArchitecture=\"x86\",type=\"win32-policyfixme:sxs:cache_QueryAssemblyInfo 0x1c47f8, 0x00000002, L"Microsoft.VC90.OpenMP,version=\"9.0.21022.8\",publicKeyToken=\"1fc8b3b9a1e18e3b\",processorArchitecture=\"x86\",type=\"win32\"", 0x7ae500
fixme:sxs:cache_QueryAssemblyInfo 0x1c47f8, 0x00000002, L"policy.9.0.Microsoft.VC90.OpenMP,version=\"9.0.21022.8\",publicKeyToken=\"1fc8b3b9a1e18e3b\",processorArchitecture=\"x86\",type=\"win32-policy[06/23/12 01:21:19] - Running wine-1.3.34 regedit /home/ranko/.PlayOnLinux//tmp/override-dll.reg
[06/23/12 01:21:19] - Content of /home/ranko/.PlayOnLinux//tmp/override-dll.reg
-----------
REGEDIT4
 
[HKEY_CURRENT_USER\Software\Wine\DllOverrides]
"*msvcr90"="native,builtin"
-----------
[06/23/12 01:21:42] - Running wine-1.3.34 start /unix vcredist_x64.exe /q
fixme:advapi:DecryptFileA "C:\\users\\ranko\\Temp\\IXP000.TMP\\" 00000000
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directoryfixme:advapi:DecryptFileA "C:\\users\\ranko\\Temp\\IXP001.TMP\\" 00000000
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directoryfixme:storage:create_storagefile Storage share mode not implemented.
fixme:sxs:cache_QueryAssemblyInfo 0x3d4238, 0x00000002, L"Microsoft.VC80.ATL,type=\"win32\",version=\"8.0.50727.762\",publicKeyToken=\"1fc8b3b9a1e18e3b\",processorArchitecture=\"amd64\"", 0x33f938
fixme:sxs:cache_QueryAssemblyInfo 0x3d4238, 0x00000002, L"Microsoft.VC80.CRT,type=\"win32\",version=\"8.0.50727.762\",publicKeyToken=\"1fc8b3b9a1e18e3b\",processorArchitecture=\"amd64\"", 0x33f938
fixme:sxs:cache_QueryAssemblyInfo 0x3d4238, 0x00000002, L"Microsoft.VC80.MFC,type=\"win32\",version=\"8.0.50727.762\",publicKeyToken=\"1fc8b3b9a1e18e3b\",processorArchitecture=\"amd64\"", 0x33f938
fixme:sxs:cache_QueryAssemblyInfo 0x3d4238, 0x00000002, L"Microsoft.VC80.MFCLOC,type=\"win32\",version=\"8.0.50727.762\",publicKeyToken=\"1fc8b3b9a1e18e3b\",processorArchitecture=\"amd64\"", 0x33f938
fixme:sxs:cache_QueryAssemblyInfo 0x3d4238, 0x00000002, L"Microsoft.VC80.OpenMP,type=\"win32\",version=\"8.0.50727.762\",publicKeyToken=\"1fc8b3b9a1e18e3b\",processorArchitecture=\"amd64\"", 0x33f938
fixme:sxs:cache_QueryAssemblyInfo 0x3d4238, 0x00000002, L"policy.8.0.Microsoft.VC80.ATL,type=\"win32-policy\",version=\"8.0.50727.762\",publicKeyToken=\"1fc8b3b9a1e18e3b\",processorArchitecture=\"amd6fixme:sxs:cache_QueryAssemblyInfo 0x3d4238, 0x00000002, L"policy.8.0.Microsoft.VC80.CRT,type=\"win32-policy\",version=\"8.0.50727.762\",publicKeyToken=\"1fc8b3b9a1e18e3b\",processorArchitecture=\"amd6fixme:sxs:cache_QueryAssemblyInfo 0x3d4238, 0x00000002, L"policy.8.0.Microsoft.VC80.MFC,type=\"win32-policy\",version=\"8.0.50727.762\",publicKeyToken=\"1fc8b3b9a1e18e3b\",processorArchitecture=\"amd6fixme:sxs:cache_QueryAssemblyInfo 0x3d4238, 0x00000002, L"policy.8.0.Microsoft.VC80.MFCLOC,type=\"win32-policy\",version=\"8.0.50727.762\",publicKeyToken=\"1fc8b3b9a1e18e3b\",processorArchitecture=\"afixme:sxs:cache_QueryAssemblyInfo 0x3d4238, 0x00000002, L"policy.8.0.Microsoft.VC80.OpenMP,type=\"win32-policy\",version=\"8.0.50727.762\",publicKeyToken=\"1fc8b3b9a1e18e3b\",processorArchitecture=\"a[06/23/12 01:21:49] - Running wine-1.3.34 start /unix vcredist_x86.exe /q
fixme:advapi:DecryptFileA "C:\\users\\ranko\\Temp\\IXP000.TMP\\" 00000000
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directoryfixme:advapi:DecryptFileA "C:\\users\\ranko\\Temp\\IXP001.TMP\\" 00000000
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directoryfixme:storage:create_storagefile Storage share mode not implemented.
fixme:sxs:cache_QueryAssemblyInfo 0x3d5870, 0x00000002, L"Microsoft.VC80.ATL,type=\"win32\",version=\"8.0.50727.762\",publicKeyToken=\"1fc8b3b9a1e18e3b\",processorArchitecture=\"x86\"", 0x33f938
fixme:sxs:cache_QueryAssemblyInfo 0x3d5870, 0x00000002, L"Microsoft.VC80.CRT,type=\"win32\",version=\"8.0.50727.762\",publicKeyToken=\"1fc8b3b9a1e18e3b\",processorArchitecture=\"x86\"", 0x33f938
fixme:sxs:cache_QueryAssemblyInfo 0x3d5870, 0x00000002, L"Microsoft.VC80.MFC,type=\"win32\",version=\"8.0.50727.762\",publicKeyToken=\"1fc8b3b9a1e18e3b\",processorArchitecture=\"x86\"", 0x33f938
fixme:sxs:cache_QueryAssemblyInfo 0x3d5870, 0x00000002, L"Microsoft.VC80.MFCLOC,type=\"win32\",version=\"8.0.50727.762\",publicKeyToken=\"1fc8b3b9a1e18e3b\",processorArchitecture=\"x86\"", 0x33f938
fixme:sxs:cache_QueryAssemblyInfo 0x3d5870, 0x00000002, L"Microsoft.VC80.OpenMP,type=\"win32\",version=\"8.0.50727.762\",publicKeyToken=\"1fc8b3b9a1e18e3b\",processorArchitecture=\"x86\"", 0x33f938
fixme:sxs:cache_QueryAssemblyInfo 0x3d5870, 0x00000002, L"policy.8.0.Microsoft.VC80.ATL,type=\"win32-policy\",version=\"8.0.50727.762\",publicKeyToken=\"1fc8b3b9a1e18e3b\",processorArchitecture=\"x86\fixme:sxs:cache_QueryAssemblyInfo 0x3d5870, 0x00000002, L"policy.8.0.Microsoft.VC80.CRT,type=\"win32-policy\",version=\"8.0.50727.762\",publicKeyToken=\"1fc8b3b9a1e18e3b\",processorArchitecture=\"x86\fixme:sxs:cache_QueryAssemblyInfo 0x3d5870, 0x00000002, L"policy.8.0.Microsoft.VC80.MFC,type=\"win32-policy\",version=\"8.0.50727.762\",publicKeyToken=\"1fc8b3b9a1e18e3b\",processorArchitecture=\"x86\fixme:sxs:cache_QueryAssemblyInfo 0x3d5870, 0x00000002, L"policy.8.0.Microsoft.VC80.MFCLOC,type=\"win32-policy\",version=\"8.0.50727.762\",publicKeyToken=\"1fc8b3b9a1e18e3b\",processorArchitecture=\"xfixme:sxs:cache_QueryAssemblyInfo 0x3d5870, 0x00000002, L"policy.8.0.Microsoft.VC80.OpenMP,type=\"win32-policy\",version=\"8.0.50727.762\",publicKeyToken=\"1fc8b3b9a1e18e3b\",processorArchitecture=\"xfixme:msi:ITERATE_RemoveExistingProducts remove L"0"
[06/23/12 01:21:56] - Running wine-1.3.34 regedit /home/ranko/.PlayOnLinux//tmp/override-dll.reg
[06/23/12 01:21:56] - Content of /home/ranko/.PlayOnLinux//tmp/override-dll.reg
-----------
REGEDIT4
 
[HKEY_CURRENT_USER\Software\Wine\DllOverrides]
"*msvcr80"="native,builtin"
-----------
[06/23/12 01:24:56] - Running wine-1.3.34 BlackOps.exe
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directoryALSA lib conf.c:3314:(snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib dlmisc.c:254:(snd1_dlobj_cache_get) Cannot open shared library /usr/lib/i386-linux-gnu/alsa-lib/libasound_module_pcm_pulse.so
ALSA lib dlmisc.c:254:(snd1_dlobj_cache_get) Cannot open shared library /usr/lib/i386-linux-gnu/alsa-lib/libasound_module_pcm_pulse.so
ALSA lib dlmisc.c:254:(snd1_dlobj_cache_get) Cannot open shared library /usr/lib/i386-linux-gnu/alsa-lib/libasound_module_pcm_pulse.so
[06/23/12 01:26:11] - Running wine-1.3.34 winecfg
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory[06/23/12 01:26:38] - Running wine-1.3.34 BlackOps.exe
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directoryfixme:thread:SetThreadIdealProcessor (0x80): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x32f3cc,0x00000000), stub!
fixme:thread:SetThreadIdealProcessor (0x9c): stub
fixme:thread:SetThreadIdealProcessor (0xb4): stub
fixme:thread:SetThreadIdealProcessor (0x17c): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x823e0b0,0x00000000), stub!
fixme:d3d:debug_d3dformat Unrecognized 0x5a534552 (as fourcc: RESZ) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x5a534552) in the format lookup table
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:win:EnumDisplayDevicesW ((null),0,0x823e38c,0x00000000), stub!
fixme:thread:SetThreadIdealProcessor (0x19c): stub
ALSA lib conf.c:3314:(snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib dlmisc.c:254:(snd1_dlobj_cache_get) Cannot open shared library /usr/lib/i386-linux-gnu/alsa-lib/libasound_module_pcm_pulse.so
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 10000 channels, pretending there's only 2 channels
ALSA lib dlmisc.c:254:(snd1_dlobj_cache_get) Cannot open shared library /usr/lib/i386-linux-gnu/alsa-lib/libasound_module_pcm_pulse.so
ALSA lib dlmisc.c:254:(snd1_dlobj_cache_get) Cannot open shared library /usr/lib/i386-linux-gnu/alsa-lib/libasound_module_pcm_pulse.so
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 10000 channels, pretending there's only 2 channels
fixme:win:EnumDisplayDevicesW ((null),0,0x823e3b4,0x00000000), stub!
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ ../../../dlls/wined3d/surface.c / 2572
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexSubImage2D @ ../../../dlls/wined3d/surface.c / 2359
```

---

