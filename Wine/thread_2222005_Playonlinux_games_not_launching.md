---
title: "Playonlinux games not launching"
date: 2014-05-04
forum: Wine
---

### Post by DidierDrigbi on 2014-05-04
Hi.
I am on Ubuntu 14.04 (Thrusty Tahr).

Today I experienced problem with PlayOnLinux. 

I installed two games: GTA San Andreas (officially supported) and Far Cry (following [THIS]("http://www.gamersonlinux.com/forum/threads/far-cry-guide.172/") guide). Both games seem to be installed properly, but when I try to launch them, nothing happens (no errors, just everything stays as I didn't click the 'Play' button). It's a strange behaviour, as GTA San Andreas worked like a charm before (Ubuntu 12.04). I have no idea how to make them work. 

One other game (Heretic 2) installed on PlayOnLinux works, so it is probably not a problem with whole PlayOnLinux installation.

Thanks in advance for any help.

---

### Post by jbaerboc on 2014-05-06
It could be a simple problem but without more information it would be hard to diagnose and help you out. I would recommend running playonlinux from the terminal, then after attempting to launch one of those game copy and past [or screenshot] what the terminal shows. This should give us a better idea of what is failing and where.

---

### Post by DidierDrigbi on 2014-05-09
[ATTACH=CONFIG]253021[/ATTACH]

Sure, I will provide any info, but I don't know what to provide. This is the result of Lanuching Grand Theft Auto San Andreas and Far Cry. With GTA San Andreas it says somethign about the graphics, but I think my graphics drivers are installed (system recognised the card as Gallium 0.4). I am running 32bit system.

---

### Post by vanquishedangel on 2014-05-09
Gallium is the opensourced driver and the opensourced driver is 1/10th of the performance of the proprietary ones. The information needed would be:

type of computer: make  and model
Processor
Ram amount
Video card
OS

Play on Linux has a debug option to launch a game as well, when you open play on Linux, highlight the game and then click debug on the lower right. copy and paste the output of the debug window that will open.

To see if your video card can use the proprietary drivers you need to open software sources and go to the additional drivers tab, if anything is listed for video that means you may use those drivers. This is optional however and sometimes can cause its own problems with some games.

---

### Post by DidierDrigbi on 2014-05-09
My card can't use the drives provided by the AMD, checked this before.

Pentium 4 2,8 Ghz
RAM: 2,5 Gb
Video Card: ATI Radeon HD4670 AGP
OS: Ubuntu 14.04

For GTA San Andreas:

> [05/09/14 20:12:40] - Running wine-1.3.26 gta_sa.exe (Working directory : /home/jasiek/.PlayOnLinux/wineprefix/GTASA/drive_c/Program Files/Rockstar Games/GTA San Andreas)
err:wgl:has_opengl Failed to load libGL: /usr/lib/i386-linux-gnu/libxcb-dri3.so.0: undefined symbol: xcb_send_fd
err:wgl:has_opengl OpenGL support is disabled.
err:d3d_caps:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat.
err:d3d:InitAdapters Failed to get a gl context for default adapter
err:d3d_caps:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat.
err:d3d:InitAdapters Failed to get a gl context for default adapter
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 32 channels, pretending there's only 2 channels
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 8 channels, pretending there's only 2 channels
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 16 channels, pretending there's only 2 channels
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 32 channels, pretending there's only 2 channels
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 16 channels, pretending there's only 2 channels
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x144008,0x136da0): stub
err:d3d_caps:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat.
err:d3d:InitAdapters Failed to get a gl context for default adapter
Direct3D9 is not available without OpenGL.

For Far Cry:

> [05/09/14 20:13:45] - Running wine-1.4.1 FarCry.exe (Working directory : /home/jasiek/.PlayOnLinux/wineprefix/fracra/drive_c/Program Files/Kolekcja Klasyki/Far Cry)
Direct3D9 is not available without OpenGL.

---

### Post by vanquishedangel on 2014-05-09
**Direct3D9 is not available without OpenGL **<------ this is your problem, I have had this before but many things could cause it. It would also help to know if you are running 64 bit or not.

I would make sure that Playonlinux is set to use openGL by opening playonlinux -----> configure (gear button) -----> display (tab) and set these in the boxes (also place the correct amount of ram for/on your video card):

"DirectDrawRenderer"="opengl"

**(these are optional but I found they help, however they don't work with all games)**

"Multisampling"="enabled"
"OffscreenRenderingMode"="fbo"
"RenderTargetModeLock"="readtex"
"StrictDrawOrdering"="enabled"
"UseGLSL"="enabled"
 
Also it looks like this game is written with openGL by the guide you linked to. Did you do the part where it said to replace ** r_Driver = "Direct3D9"** with **r_Driver = "openGL"** in the system.cfg file?

---

### Post by DidierDrigbi on 2014-05-09
Yes, everything is set as you described, but it doesn't help. I am curious what causes these problems, because as I said it used to work on Ubuntu 12.04.

Of course I replaced the line in system.cfg to support openGL. But Far Cry is a minor problem, because it may not work. But GTA should as it did.

---

