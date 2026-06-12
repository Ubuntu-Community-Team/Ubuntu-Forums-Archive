---
title: "GFX Driver Problem?"
date: 2006-09-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by arcasa@Alchemy on 2006-09-20
Hi all.

I run Kubuntu 2.6.15-27-amd64-generic. I installed WINE (With difficulty) and I'm glad to say it works. Well at least it works for most applications.

I get an error when I try to run Tibia.
```

arcasa@Alchemy:~/c/Program Files/Tibia$ wine Tibia.exe engine 0
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:process_attach Could not create default context.
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

```

Tibia is the only thing I miss about Windows.. 

Please help me.

Thanks in advance, 

Arcasa.

---

### Post by Kilz on 2006-09-20
> **arcasa@Alchemy said:**
> Hi all.

I run Kubuntu 2.6.15-27-amd64-generic. I installed WINE (With difficulty) and I'm glad to say it works. Well at least it works for most applications.

I get an error when I try to run Tibia.
```

arcasa@Alchemy:~/c/Program Files/Tibia$ wine Tibia.exe engine 0
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:process_attach Could not create default context.
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

```

Tibia is the only thing I miss about Windows.. 

Please help me.

Thanks in advance, 

Arcasa.

You need to install or update your graphics drivers.

---

### Post by arcasa@Alchemy on 2006-09-20
Well I would do... 

But that has a problem too.

I get "Unable to find kernel source tree" or something of the like.

I have installed kernel source AND kernel source code tree from Adept.


So why it's not getting them, I do not know.

---

### Post by arcasa@Alchemy on 2006-09-20
I don't know if this helps much... But still:


nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Thu Sep 21 01:36:00 2006

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  compat32 install chroot : (not specified)
  compat32 install prefix : (not specified)
  compat32 install libdir : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
ERROR: Unable to find the kernel source tree for the currently running kernel. 
       Please make sure you have installed the kernel source files for your
       kernel and that they are properly configured; on Red Hat Linux systems,
       for example, be sure you have the 'kernel-source' RPM installed.  If you
       know the correct kernel source files are installed, you may specify the
       kernel source path with the '--kernel-source-path' command line option.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

---

### Post by RAOF on 2006-09-20
The correct way to install the nvidia drivers is (from the terminal):
```

sudo aptitude install linux-amd64 nvidia-glx
sudo nvidia-xconfig

```
If you have an old nVidia card (TNT2/Geforce 1 era) you need to install **nvidia-glx-legacy** rather than **nvidia-glx**.  The "linux-amd64" in the install line is to make sure that you've got 1) the most recent kernel, and 2) the appropriate linux-restricted-modules package.

---

### Post by arcasa@Alchemy on 2006-09-21
My GFX card is a BFG Tech nVidia GeForce 7300 GS OC.

I'm installing ALL the linux-restricted-drivers I can find in Adept and I'm updating my kernel... Just hope this works this time.

---

