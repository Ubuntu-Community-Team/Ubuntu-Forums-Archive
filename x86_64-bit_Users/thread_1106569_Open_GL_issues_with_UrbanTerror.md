---
title: "Open GL issues with UrbanTerror"
date: 2009-03-25
forum: x86 64-bit Users
---

### Post by nathanhillinbl on 2009-03-25
I'm trying to run UrbanTerror, and are using the 177 version Nvidia proprietary drivers for the 3d acceleration, and get what seems to be a OpenGL error.  

```
nate@nateneedsalaptop:~/UrbanTerror$ ./ioUrbanTerror.x86_64
ioQ3 1.35urt linux-x86_64 Dec 21 2007
----- FS_Startup -----
Going through search path...

----------------------
8032 files in pk3 files
execing default.cfg
execing q3config.cfg
execing autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
Couldn't read q3history.
----- Initializing Renderer ----
-------------------------------
QKEY found.
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1:
Calling SDL_Init(SDL_INIT_VIDEO)...
SDL_Init(SDL_INIT_VIDEO) passed.
Initializing OpenGL display
...setting mode 4: 800 600
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
Couldn't get a visual
...WARNING: could not set the given mode (4)
Initializing OpenGL display
...setting mode 3: 640 480
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
Couldn't get a visual
...WARNING: could not set the given mode (3)
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem

nate@nateneedsalaptop:~/UrbanTerror$ 

``` 


Any help at all would, as always, be greatly appreciated!

---

### Post by yetanothersteve on 2009-03-25
You may be better off asking in the Urban Terror Linux Related Support Forum at the Urban Terror web site. [http://forums.urbanterror.net/]("http://forums.urbanterror.net/")

Thanks for pointing this game out to me, though, looks a lot like a modern version of Enemy Territory.

---

### Post by evilaim on 2009-03-25
It means that you don't have your video drivers installed for your ati video card.   Install your card properly, maybe the restricted drivers might help.

---

### Post by Yellow Pasque on 2009-03-26
Can you post the output of:
```
LIBGL_DEBUG=verbose glxinfo
```

---

### Post by talvez on 2009-03-27
I also am seeing a regression in NVIDIA drivers in the latest IBEX updates, on 3/27/09.

The following GLX apps were working fine until yesterday:

glxgears
Blender
Google Earth
Urban Terror

Xorg.0.log shows:

(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "0"
(**) NVIDIA(0): Option "MetaModes" "CRT: 1280x1024_75 +0+0; CRT: nvidia-auto-select +0+0"
(**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "CRT-0"
(**) NVIDIA(0): Enabling RENDER acceleration
(EE) NVIDIA(0): Failed to initialize the GLX module; please check in your X
(EE) NVIDIA(0):     log file that the GLX module has been loaded in your X
(EE) NVIDIA(0):     server, and that the module is the NVIDIA GLX module.  If
(EE) NVIDIA(0):     you continue to encounter problems, Please try
(EE) NVIDIA(0):     reinstalling the NVIDIA driver.
(II) NVIDIA(0): NVIDIA GPU GeForce 6200 (NV44) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.44.a2.10.01
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6200 at PCI:1:0:0:
(--) NVIDIA(0):     Proview CY765 (CRT-0)
(--) NVIDIA(0):     NVIDIA TV Encoder (TV-0)
(--) NVIDIA(0): Proview CY765 (CRT-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(0): NVIDIA TV Encoder (TV-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(0): TV encoder: NVIDIA
(II) NVIDIA(0): Display Device found referenced in MetaMode: CRT-0
(WW) NVIDIA(0): The EDID for Proview CY765 (CRT-0) contradicts itself: mode
(WW) NVIDIA(0):     "640x360" is specified in the EDID; however, the EDID's
(WW) NVIDIA(0):     valid HorizSync range (30.000-80.000 kHz) would exclude
(WW) NVIDIA(0):     this mode's HorizSync (26.2 kHz); ignoring HorizSync check
(WW) NVIDIA(0):     for mode "640x360".
(WW) NVIDIA(0): The EDID for Proview CY765 (CRT-0) contradicts itself: mode
(WW) NVIDIA(0):     "720x405" is specified in the EDID; however, the EDID's
(WW) NVIDIA(0):     valid HorizSync range (30.000-80.000 kHz) would exclude
(WW) NVIDIA(0):     this mode's HorizSync (29.5 kHz); ignoring HorizSync check
(WW) NVIDIA(0):     for mode "720x405".
(WW) NVIDIA(0): The EDID for Proview CY765 (CRT-0) contradicts itself: mode
(WW) NVIDIA(0):     "800x600" is specified in the EDID; however, the EDID's
(WW) NVIDIA(0):     valid VertRefresh range (60.000-75.000 Hz) would exclude
(WW) NVIDIA(0):     this mode's VertRefresh (56.2 Hz); ignoring VertRefresh
(WW) NVIDIA(0):     check for mode "800x600".
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "CRT:1280x1024_75+0+0"
(II) NVIDIA(0):     "CRT:nvidia-auto-select+0+0"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(0): DPI set to (95, 96); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(1): RGB weight 888
(==) NVIDIA(1): Default visual is TrueColor
(==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(1): Option "TwinView" "0"
(**) NVIDIA(1): Option "MetaModes" "TV: nvidia-auto-select +0+0"
(**) NVIDIA(1): Enabling RENDER acceleration
(II) NVIDIA(1): NVIDIA GPU GeForce 6200 (NV44) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(1): Memory: 262144 kBytes
(--) NVIDIA(1): VideoBIOS: 05.44.a2.10.01
(II) NVIDIA(1): Detected AGP rate: 4X
(--) NVIDIA(1): Interlaced video modes are supported on this GPU
(--) NVIDIA(1): Connected display device(s) on GeForce 6200 at PCI:1:0:0:
(--) NVIDIA(1):     Proview CY765 (CRT-0)
(--) NVIDIA(1):     NVIDIA TV Encoder (TV-0)
(--) NVIDIA(1): Proview CY765 (CRT-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(1): NVIDIA TV Encoder (TV-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(1): TV encoder: NVIDIA
(II) NVIDIA(1): Display Device found referenced in MetaMode: TV-0
(II) NVIDIA(1): Assigned Display Device: TV-0
(II) NVIDIA(1): Validated modes:
(II) NVIDIA(1):     "TV:nvidia-auto-select+0+0"
(II) NVIDIA(1): Virtual screen size determined to be 1024 x 768
(==) NVIDIA(1): DPI set to (75, 75); computed from built-in default
(==) NVIDIA(1): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  Yes, I do.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Unable to connect to the ACPI daemon; the ACPI daemon may not
(II) NVIDIA(0):     be running or the "AcpidSocketPath" X configuration option
(II) NVIDIA(0):     may not be set correctly.  When the ACPI daemon is
(II) NVIDIA(0):     available, the NVIDIA X driver can use it to receive ACPI
(II) NVIDIA(0):     events.  For details, please see the "ConnectToAcpid" and
(II) NVIDIA(0):     "AcpidSocketPath" X configuration options in Appendix B: X
(II) NVIDIA(0):     Config Options in the README.
(II) NVIDIA(0): Setting mode "CRT:1280x1024_75+0+0"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) NVIDIA(1): Initialized AGP GART.
(II) NVIDIA(1): Unable to connect to the ACPI daemon; the ACPI daemon may not
(II) NVIDIA(1):     be running or the "AcpidSocketPath" X configuration option
(II) NVIDIA(1):     may not be set correctly.  When the ACPI daemon is
(II) NVIDIA(1):     available, the NVIDIA X driver can use it to receive ACPI
(II) NVIDIA(1):     events.  For details, please see the "ConnectToAcpid" and
(II) NVIDIA(1):     "AcpidSocketPath" X configuration options in Appendix B: X
(II) NVIDIA(1):     Config Options in the README.
(II) NVIDIA(1): Setting mode "TV:nvidia-auto-select+0+0"
(II) NVIDIA(1): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(1): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(1): Backing store disabled
(==) NVIDIA(1): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(1): DPMS enabled
(WW) NVIDIA(1): Option "AGPMode" is not used
(WW) NVIDIA(1): Option "AGPFastWrite" is not used
(WW) NVIDIA(1): Option "EnablePageFlip" is not used
(WW) NVIDIA(1): Option "AccelMethod" is not used
(WW) NVIDIA(1): Option "MigrationHeuristic" is not used
(==) RandR enabled

---

### Post by nathanhillinbl on 2009-03-27
```
nate@nateneedsalaptop:~$ LIBGL_DEBUG=verbose glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
3 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Segmentation fault

```

---

