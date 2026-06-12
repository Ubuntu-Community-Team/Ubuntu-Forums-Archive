---
title: "Problem after installing NVPerfKit."
date: 2006-11-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by hecato on 2006-11-06
Hi there, I ask here, because I dont get answer in other place [Problem after installing NVPerfKit]("http://www.nvnews.net/vbulletin/showthread.php?t=79522") the thing is that I have installed the driver that come with [NVPerfKit]("http://developer.nvidia.com/object/nvperfkit_home.html") and after terminate X server and downloaded the headers for my kernel, I get a black screen, and the error showed in the attached (other post referenced) [nvidia-bug-report.log]("http://www.nvnews.net/vbulletin/attachment.php?attachmentid=21650&d=1162673942") the section of the errors I paste here for you (if you dont wanth to see the whole file)

> 
.....
(II) Loading /usr/lib/xorg/modules/libglx.so
dlopen: /usr/lib/libGLcore.so.1: undefined symbol: _nv000038gl
(EE) Failed to load /usr/lib/xorg/modules/libglx.so
(II) UnloadModule: "glx"
(EE) Failed to load module "glx" (loader failed, 7)
.....
(**) NVIDIA(0): Enabling RENDER acceleration
(==) NVIDIA(0): Video key set to default value of 0x101fe
(EE) NVIDIA(0): Failed to initialize the GLX module; please check in your X
(EE) NVIDIA(0):     log file that the GLX module has been loaded in your X
(EE) NVIDIA(0):     server, and that the module is the NVIDIA GLX module.  If
(EE) NVIDIA(0):     you continue to encounter problems, Please try
(EE) NVIDIA(0):     reinstalling the NVIDIA driver.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found


but
```

~: ls /usr/lib/xorg/modules/ |grep glx
libglx.so
libglx.so.1.0.8776

```
Then, there is glx, also is installed because synaptic say it is installed, the problem come because like I see now, NVPerfKit is 9640 and not 8776 like the drivers I have before and worked just fine (NVIDIA logo showing before GDM logon screen, 3D aceleration working).



I have tryigng deleting completely glx with synaptic and installed again, Im now using diver "vesa", so the question is, how to reinstall the whole thing and purge my system from NVPerfKit¿?¿? (Or where to get the 9640 drivers??).

---

### Post by hecato on 2006-11-06
Actually I have managed to get back the tne actual drivers 8776, if somebody is able to install NVPerfKit, please pot how to do it :) (what need to be upgraded before I guess).

---

