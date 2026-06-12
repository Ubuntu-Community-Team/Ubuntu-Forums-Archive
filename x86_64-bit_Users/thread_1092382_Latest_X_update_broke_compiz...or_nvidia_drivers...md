---
title: "Latest X update broke compiz...or nvidia drivers...?"
date: 2009-03-10
forum: x86 64-bit Users
---

### Post by mikespug on 2009-03-10
I ran some updates today, among which were two updates to X, and now compiz won't load.  Typically I see the same thing happen when the kernel is upgraded.  The solution is usually to "re-install" nvidia's drivers and things go back to normal but this doesn't seem to be the case in this scenario.  I'll provide below some of the relevant information to help diagnose:

Ubuntu Intrepid 64
Nvidia 180.29 drivers
Compiz 0.7.8
Xorg 7.4

Here is a section from the xorg.o.log file pretaining to the nvidia video card drivers loading.  There is one line of interest highlighted in bold in which it is stated that 2D acceleration is in use, although two lines before it states that 3D acceleration has been initialized:

```
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 7350 LE (G72) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 05.72.22.51.15
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7350 LE at PCI:1:0:0:
(--) NVIDIA(0):     SAMSUNG (DFP-0)
(--) NVIDIA(0): SAMSUNG (DFP-0): 165.0 MHz maximum pixel clock
(--) NVIDIA(0): SAMSUNG (DFP-0): Internal Single Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(==) NVIDIA(0): 
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) NVIDIA(0):     will be used as the requested mode.
(==) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
(++) NVIDIA(0): DPI set to (96, 96); computed from -dpi X commandline option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(0): Disabling shared memory pixmaps
**(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture**
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
```

Again, reinstalling nvidia's drivers don't resolve the issue.  Any ideas as to my next course of action?  Thanks.

**update:**  Opening a terminal and loading compiz manually results in compiz turning on but it still does not load on reboot.  Here's the output when loading compiz manually"

```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1920x1080) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Starting gtk-window-decorator
```

---

### Post by Yellow Pasque on 2009-03-10
I don't see anything "wrong" with the info you provided.

Try looking through your system messages.  dmesg will show you everything. Some suggestions to narrow things down:
```
dmesg | grep compiz
dmesg | -tail 50
```

---

### Post by mikespug on 2009-03-10
"dmesg | grep compiz" outputs nothing.  Just reading through dmesg nothing seems to stand out.  Again, I can start compiz manually (either though terminal or a run dialog).  What handles the loading of compiz at boot?  A session?

---

### Post by ab636 on 2009-03-11
I got the same problem about same time ago. 

first I noticed that Avant Windows Navigator is not working (later I realise that any window I open compozited wrong - I cannot work with them). So I run AWN in Terminal

anton@anton-laptop:~$ sudo avant-window-navigator
[sudo] password for anton:
Error: Screen isn't composited. Please run compiz (-fusion) or another compositing manager.

So I run this command 

anton@anton-laptop:~$ sudo compiz
[sudo] password for anton:
Checking for Xgl: not present.
Detected PCI ID for VGA: 01:00.0 0300: 10de:0429 (rev a1) (prog-if 00
[VGA controller])
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1680x1050) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present.
Checking for FBConfig: present.
Checking for Xgl: not present.
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format,
disabling YV12 image format

After running this command I can work but NOT everything is working properly (for example, Advance Desktop Effects are not working, some settings of my desktop are different - 2 workspaces instead of 4). And after a restart of a laptop everything go back to where I was. So each time I want to work on my laptop I have to run sudo compiz...

---

### Post by mikespug on 2009-03-11
You can load compiz automatically by creating a session (instead of running sudo compiz) in Menu > Preferences > Sessions and creating a new session.  Name it compiz and the command to start it is compiz.  That will load compiz at boot but is not the normal way ubuntu handles the start of the program.  You'll still see an error for a second or two at boot but it goes away quickly and Awn/screenlets load as normal.  I'm still trying to figure out how ubuntu normally handles the start of compiz to eliminate the error all together.

---

### Post by ab636 on 2009-03-12
could you please tell the name of the command i shall write in the command line?

---

### Post by mikespug on 2009-03-12
"compiz"  (without quotes)

---

### Post by ab636 on 2009-03-15
do you think upgrading ubuntu 8.04 to 8.10 will solve the issue?

---

### Post by ab636 on 2009-04-04
the problem was caused by Avant Window Navigator. 

I used this guide and return all the settings to default [http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/](http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/)

I no longer use AWN.

---

