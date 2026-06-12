---
title: "Unplayably slow starcraft in WINE"
date: 2007-12-24
forum: Wine
---

### Post by thefirstM on 2007-12-24
I am attempting to play Starcraft Broodwar on my gutsy system using wine 0.9.50.  It is unbearably and unplayably slow.  I have read about how to enable opengl rendering of directdraw, but when I enable this, wine crashes right away.  My system is a 1000mHz PIII with a GeForce 6600gt AGP.  (Yes, I know it is old.)  (Yes, I know the videocard is way overpowered for the CPU.)  I do not think my old PC is the problem, because this same box runs Counter-Strike 1.6 just fine with wine.  I have also tried running starcraft in wine on a system that had a 1.8gHz Core Duo, and it ran just as slowly.  Can anyone help me?

---

### Post by soviet911 on 2007-12-24
i got the same problem,tryied opengl command but also crashes, so im trying to setup its own server but having problems with starting it, will post more detail later gotto go.

---

### Post by thefirstM on 2007-12-25
Hopefully, a helpful expert will BUMP into this thread...

---

### Post by thefirstM on 2007-12-26
I seem to have run into a speedBUMP in solving my problem...:-({|=

---

### Post by thefirstM on 2007-12-27
Sorry, evidently this post just BUMPed into a brick wall...

---

### Post by soviet911 on 2007-12-27
hmm try useing wine 9.15 it might work, didnt help me though the problem seems to be
 fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8

wich means that the game is trying to run in 32 bit color and not 8 bit so it lags, start yours from terminal and see if you get the same error,( you will need to scrole through the termial messages)

---

### Post by thefirstM on 2007-12-27
I am using the winehq apt repository, so attempting to install an old package would hose things up.  Also,  I was unable to get Counter-Strike 1.6 (the other game I absolutely must have working in Linux) to work with the older version.  Thanks for the suggestion though.  By the way, I have tried launching it in a seperate xserver running at 8-bit color, but this did not change anything.

---

### Post by dfreer on 2007-12-27
Have you installed your nvidia drivers correctly, so direct rendering is enabled?
What's the output of these commands?
```
glxgears
glxinfo | grep rendering
glxinfo | head
```

---

### Post by soviet911 on 2007-12-28
soviet911@Soviet911portable:~$ glxgears
2093 frames in 5.1 seconds = 411.648 FPS
2040 frames in 5.1 seconds = 401.129 FPS
5146 frames in 5.0 seconds = 1029.117 FPS
9880 frames in 5.0 seconds = 1966.848 FPS
10232 frames in 5.0 seconds = 2040.149 FPS
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 65768 requests (64121 known processed) with 0 events remaining.
soviet911@Soviet911portable:~$ glxinfo | grep rendering
direct rendering: No
soviet911@Soviet911portable:~$ glxinfo | head
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group



I got an old ATI graphics card, so im not sure if i have any drivers installed, and as i can see direct rendering is off, so what am i suppose to do,oh and its an ATI Radeon Mobility graphics with 16MB of SDRAM

something tells me its the drivers, i will try to google on how to get them, but help would be apreciated 

P.S i installed steam on 9.51 and run CS1.6 flawlessly on my this laptop (In video i set the option to Softwear so it looks like **** but doesnt lag considering how old the laptop is anyhow, still starcraft should have no problem running so it got to be eather the drivers or somethign in wine)

---

### Post by thefirstM on 2007-12-28
Here is the output for me:  (The framerate for glxgears is locked to 60fps because I am a complete vsync whore.)

michael@MichaelsPC:~$ glxgears
302 frames in 5.0 seconds = 60.231 FPS
300 frames in 5.0 seconds = 59.968 FPS
298 frames in 5.0 seconds = 59.566 FPS
X connection to :0.0 broken (explicit kill or server shutdown).
michael@MichaelsPC:~$ glxinfo | grep rendering
direct rendering: Yes
michael@MichaelsPC:~$ glxinfo | head
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer,
    GLX_ARB_fbconfig_float
michael@MichaelsPC:~$

As for running CS 1.6 in the old version of Wine, it would not work for me in OpenGL mode.  The software rendering has simply too poor quality for me.
As for your ATi drivers, which version of Ubuntu are you running?  I should think that the included ati opensource driver would work with your card.

---

### Post by soviet911 on 2007-12-28
Feisty 7.04 and yes i looked in the xorg.conf and it said its useing ATI driver, but i also play4ed around with the setup and tried Radeon drivers but it didnt load them (x server crashes on start up) and i heard it might work better with the radeon drivers, also i set the defult depth to 16  got this from those commands 
soviet911@Soviet911portable:~$ glxgears
3293 frames in 5.1 seconds = 645.771 FPS
3234 frames in 5.1 seconds = 628.262 FPS
3240 frames in 5.0 seconds = 646.925 FPS
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 21730 requests (12334 known processed) with 0 events remaining.
soviet911@Soviet911portable:~$ glxinfo | grep rendering
direct rendering: No
soviet911@Soviet911portable:~$ glxinfo | head
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
soviet911@Soviet911portable:~$ 
soviet911@Soviet911portable:~$ 

The FPS went up and the starcraft seems to be less lagy but still to laggy, so i think it might be that my direct rending is off and the the reason why its laggy. and if i set the defult depth to 8 (wich is what starcraft runs at) i get barly 240 fps, so i donno whats going on.

---

### Post by YokoZar on 2007-12-31
> **soviet911 said:**
> Feisty 7.04 and yes i looked in the xorg.conf and it said its useing ATI driver, but i also play4ed around with the setup and tried Radeon drivers but it didnt load them (x server crashes on start up) and i heard it might work better with the radeon drivers, also i set the defult depth to 16  got this from those commands 
soviet911@Soviet911portable:~$ glxgears
3293 frames in 5.1 seconds = 645.771 FPS
3234 frames in 5.1 seconds = 628.262 FPS
3240 frames in 5.0 seconds = 646.925 FPS
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 21730 requests (12334 known processed) with 0 events remaining.
soviet911@Soviet911portable:~$ glxinfo | grep rendering
direct rendering: No
soviet911@Soviet911portable:~$ glxinfo | head
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
soviet911@Soviet911portable:~$ 
soviet911@Soviet911portable:~$ 

The FPS went up and the starcraft seems to be less lagy but still to laggy, so i think it might be that my direct rending is off and the the reason why its laggy. and if i set the defult depth to 8 (wich is what starcraft runs at) i get barly 240 fps, so i donno whats going on.
Direct Rendering: No means that hardware accelerated OpenGL is not working on your computer.  Since Wine renders Direct3D (and DirectDraw like Starcraft) via OpenGL, this will be extremely slow until you fix the drivers.

---

### Post by prince.buster on 2009-07-15
Hey there,
I had this problem, and fixed it. A bit obscure, but hey, maybe the same thing's happened to someone else, so here goes:

IBM Thinkpad X31 (an old'un but a good'un)
Pentium M 1.4 GHz
512MB RAM
ATI Radeon Mobility graphics 16MB of SDRAM
Open source "radeon" driver
Jaunty
wine-1.0.1

Starcraft ran, but was hellishly slow.

I inspected xorg.conf and found that, for some bizarre reason, the screen resolution was set to 2048x768, instead of (the slightly more sane) 1024x786. So basically, every pixel was being drawn twice. Corrected it, restarted the computer, and StarCraft ran slick as a pole dancer's pole.

I don't know why it was set to 2048x768, it certainly wasn't done intentionally. The desktop looked exactly the same as it does now at 1024x768. In retrospect, it possibly may have happened automatically when I attempted to plug in a second external monitor.

Even if this solution doesn't work, one thing to take out of this is the knowledge that **IT IS POSSIBLE to run StarCraft perfectly** through wine on this hardware.

Sound works through PulseAudio/ALSA and OSS. Switching between sound drivers and disabling sound altogether (in Starcraft and/or Wine) has no noticeable effect on performance for me.

The rest of gnome continues as normal; beagle and pidgin and even firefox running in the background has no noticeable effect on gameplay.

Wine gives me the following messages:
```
jerry@X31:~$ wine .wine/drive_c/Program\ Files/Starcraft/StarCraft.exe 
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x32f420,0x00000000), stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8

```

so safe to conclude that the BPP problem **does not** have a profound effect on performance

For your interest:
```
jerry@X31:~$ glxgears
1143 frames in 5.0 seconds = 228.529 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 4860 requests (2975 known processed) with 0 events remaining.
jerry@X31:~$ glxinfo | grep rendering
direct rendering: Yes
jerry@X31:~$ glxinfo | head
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
jerry@X31:~$ 
```

---

