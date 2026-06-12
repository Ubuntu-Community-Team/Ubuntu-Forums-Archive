---
title: "Call of duty game or any game that uses OpenGL dont start"
date: 2012-08-17
forum: Wine
---

### Post by doo2doo2 on 2012-08-17
i have just downloaded and installed call of duty 1 , it was done perfectly but when i try to start it it show me this error console ::
```
COD 1.0 build win-x86 Oct  5 2003
----- FS_Startup -----
Current language: english
Current search path:
D:\PROGRA~1\CALLOF~1\main\pak6.pk3 (3 files)
D:\PROGRA~1\CALLOF~1\main\pak5.pk3 (4858 files)
D:\PROGRA~1\CALLOF~1\main\pak4.pk3 (1668 files)
D:\PROGRA~1\CALLOF~1\main\pak3.pk3 (1992 files)
D:\PROGRA~1\CALLOF~1\main\pak2.pk3 (694 files)
D:\PROGRA~1\CALLOF~1\main\pak1.pk3 (2642 files)
D:\PROGRA~1\CALLOF~1\main\pak0.pk3 (12828 files)
D:\PROGRA~1\CALLOF~1/main
D:\PROGRA~1\CALLOF~1\main\localized_english_pak1.pk3 (3736 files)
    localized assets pak file for english
D:\PROGRA~1\CALLOF~1\main\localized_english_pak0.pk3 (1204 files)
    localized assets pak file for english

File Handles:
----------------------
29625 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec config.cfg
couldn't exec autoexec.cfg
========= autoconfigure
configure.csv: using configuration 1200 cpu MHz 512 sys MB 64 vid MB
execing configure.cfg
fs_basepath is write protected.
fs_homepath is write protected.
Hunk_Clear: reset the hunk ok
...detecting CPU, found Intel Pentium III
Measured CPU speed is 1.60 GHz
System memory is 1024 MB (capped at 1 GB)
Video card memory is 64 MB
Streaming SIMD Extensions (SSE) supported

----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
Initializing OpenGL subsystem
...initializing QGL
...calling LoadLibrary( 'C:\Windows\system32\opengl32.dll' ): succeeded
...setting mode 4: 800 600 FS
...using colorbits of 32
...calling CDS: ok
...registered window class
...created window@0,0 (800x600)
Initializing OpenGL driver
...getting DC: succeeded
...GLW_ChoosePFD( 32, 24, 8 )
...35 PFDs found
...GLW_ChoosePFD failed
...GLW_ChoosePFD( 32, 24, 0 )
...35 PFDs found
...GLW_ChoosePFD failed
...failed to find an appropriate PIXELFORMAT
...restoring display settings
...WARNING: could not set the given mode (4)
...shutting down QGL
...unloading OpenGL DLL
Forcing 640x480 resolution to allow OpenGL to run in fullscreen
...initializing QGL
...calling LoadLibrary( 'C:\Windows\system32\opengl32.dll' ): succeeded
...setting mode 3: 640 480 FS
...using colorbits of 32
...calling CDS: ok
...created window@0,0 (640x480)
Initializing OpenGL driver
...getting DC: succeeded
...GLW_ChoosePFD( 32, 24, 8 )
...35 PFDs found
...GLW_ChoosePFD failed
...GLW_ChoosePFD( 32, 24, 0 )
...35 PFDs found
...GLW_ChoosePFD failed
...failed to find an appropriate PIXELFORMAT
...restoring display settings
...WARNING: could not set the given mode (3)
...shutting down QGL
...unloading OpenGL DLL
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
Hunk_Clear: reset the hunk ok
Could not load OpenGL.  Make sure that you have the latest drivers for your video card from the manufacturer's web site.

```
here are my laptop (( dell inspiron 1300 )) specs ::
Computer name: ABDO-GOGO-PC
User name: Abdo-Gogo

Operating System: Windows NT
Operating system version 5.0
Operating system build: 0.0.2195
OS-Info: 
Processor: Intel(R) Celeron(R) M processor         1.60GHz
Clock speed: ~1593MHz
Processor type: Original OEM

Total physical memory: 1527Mb
Available physical memory: 897Mb
Total page file size: 2527Mb
Total available page file size: 1847Mb
Total virtual memory: 2047Mb
Available virtual memory: 1983Mb

CPUID: Yes
RDTSC: Yes
CMOV: Yes
MMX: Yes
SSE: Yes
SSE2: Yes
3DNow!: No
Extended 3DNow!: No
CPU Feature bits: 0xafe9fbff
Ext. CPU Feature bits: 0x0

L1 Data Cache: None
L1 Instruction Cache: None
L1 Instruction Trace Cache: None
L2 cache: None

Video Card: Mobile Intel(R) 915GM/GMS,910GML Express Chipset Family
Driver: ialmrnt5.dll
Product=6, Version=14, SubVersion=10, Build=4609
Video Card Chip Vendor: Intel
Type of chip: Unknown Intel Device
Vendor id: 0x8086
Device id: 0x2592
SubSys id: 0x1c91028
Revision: 3
GUID = {0xd7b78e66, 0x66d2, 0x11cf}, {0x99, 0x61, 0xc3, 0x21, 0xa2, 0xc2, 0xcb, 0x35}
Hardware T&L support: No
NPatch support: No
ZBias support: Yes
Gamma support: Yes
Anisotropic filtering support: Yes
Supports texture format: A8R8G8B8
Supports texture format: X8R8G8B8
Supports texture format: R5G6B5
Supports texture format: A1R5G5B5
Supports texture format: A4R4G4B4
Supports texture format: A8
Supports texture format: L8
Supports texture format: A8L8
Supports texture format: A4L4
Supports texture format: U8V8
Supports texture format: L6V5U5
Supports texture format: X8L8V8U8
Supports texture format: DXT1
Supports texture format: DXT2
Supports texture format: DXT3
Supports texture format: DXT4
Supports texture format: DXT5
Supports render-to-texture format: A8R8G8B8
Supports render-to-texture format: X8R8G8B8
Supports render-to-texture format: R5G6B5
Supports render-to-texture format: A1R5G5B5
Supports render-to-texture format: A4R4G4B4
Texture compression support: Yes
Bumpmap support: Yes
Bumpmap luminance support: Yes
Vertex shader version: 3.0, pixel shader version: 2.0
Driver version status: Good
Max textures per pass: 8
Multisample Anti-Aliasing setting: None
VSync enabled: 1
Shaders enabled: 1
High quality shadows enabled: 1

Compact tab-delimited version:
-120    WIN2K    2195    Intel    1593    1528    afe9fbff    0    Intel    Unknown Intel Device    4609    100    100    0    0    0    0    2    0    0    0    1    640    480    16    0    0.0    
Dynamic LOD budget: 100
Static LOD budget: 100
Shadow Mode: None
Dynamic Shadows: Off
Static Shadows: Off
Prelit Mode: Vertex
Texture Resolution: 2
Surface Effects (0-2): 0
Particle Detail(0-2): 0
Texture Filter Mode: Bilinear
Screen UV Bias: Enabled
NPatch level: Not supported
Display mode: 640 * 480, 16 bits Fullscreen

Sound device: 
Sound effects: Enabled
Sound effects volume: 0.37
Music: Enabled
Music volume: 0.31





will be very thankfull if someone told me a solution , i cant play any medal of honor game also :/ , it gives me exactly the same error .

---

### Post by doorknob60 on 2012-08-17
Wait are you using Linux+Wine or Windows 2000? Normally I'd assume you're using Wine, but based on what you posted, it really looks like Windows to me, you really should specify these things when posting on a Linux forum :P Anyways, go download the latest drivers for your graphics card, this should be them (assuming you're using Windows and not Wine): [http://downloadcenter.intel.com/SearchResult.aspx?lang=eng&ProductFamily=Graphics&ProductLine=Laptop+graphics+drivers&ProductProduct=Mobile+Intel%C2%AE+915GM%2fGMS%2c+910GML+Express+Chipset+Family](http://downloadcenter.intel.com/SearchResult.aspx?lang=eng&ProductFamily=Graphics&ProductLine=Laptop+graphics+drivers&ProductProduct=Mobile+Intel%C2%AE+915GM%2fGMS%2c+910GML+Express+Chipset+Family)

Also, those computer specs are not gaming quality specs, good luck getting any good gaming performance out of it, even with old games like COD 1.

---

### Post by doo2doo2 on 2012-08-17
thanks for replying fast , i got windows 7 home basic , and i allready tring getting latest drivers and reinstalling the game , still the same error :/

---

### Post by doo2doo2 on 2012-08-19
please reply XD

---

### Post by thatguruguy on 2012-08-19
> **doo2doo2 said:**
> thanks for replying fast , i got windows 7 home basic , and i allready tring getting latest drivers and reinstalling the game , still the same error :/

Perhaps you've misunderstood where you are.  This is a forum for gaming on Linux. If you are using Windows, you should try to find an appropriate forum somewhere else.

---

### Post by doo2doo2 on 2012-08-20
lmao , lol sorry for that :/

---

