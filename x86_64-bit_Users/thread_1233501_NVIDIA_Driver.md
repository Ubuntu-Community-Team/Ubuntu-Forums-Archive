---
title: "NVIDIA Driver"
date: 2009-08-06
forum: x86 64-bit Users
---

### Post by adempewolff on 2009-08-06
Hello, I just upgraded to 64-bit and am slightly confused as to what to do about my video card.  I have an NVIDIA Quadro NVS 135M and used the proprietary driver with 32-bit Ubuntu.

I am trying to install the 64-bit driver but not sure what the easiest way to do this is and am having trouble with what I have tried so far.
So far I:

Went to [http://www.nvidia.com/Download/Find.aspx?lang=en-us](http://www.nvidia.com/Download/Find.aspx?lang=en-us) and searched for Quadro - NVS - Notebooks - 135M - Linux 64 bit - English - All and it returned these three drivers:

Linux Display Driver Version 169.04 (beta)
Linux Display Driver Version 100.14.23 (beta)
Linux Display Driver Version 100.14.11

Not sure which to use I just downloaded the latest one, stopped the x-server and tried to install it.  It said:

```
No precompiled kernel interface was found to match your kernel; would you like the installer to attempt to download a kernel interface for your kernel from the NVIDIA ftp site (ftp://download.nvidia.com)
```
I said yes, it said these messages in succession (plus extra things I didn't see at the time, I'm just copying this out of the logfile):

```
ERROR: Unable to connect to download.nvidia.com (unknown host)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.28-14-generic/build'
-> Kernel output path: '/lib/modules/2.6.28-14-generic/build'
ERROR: If you are using a Linux 2.4 kernel, please make sure
       you either have configured kernel sources matching your
       kernel or the correct set of kernel headers installed
       on your system.
       
       If you are using a Linux 2.6 kernel, please make sure
       you have configured kernel sources matching your kernel
       installed on your system. If you specified a separate
       output directory using either the "KBUILD_OUTPUT" or
       the "O" KBUILD parameter, make sure to specify this
       directory with the SYSOUT environment variable or with
       the equivalent nvidia-installer command line option.
       
       Depending on where and how the kernel sources (or the
       kernel headers) were installed, you may need to specify
       their location with the SYSSRC environment variable or
       the equivalent nvidia-installer command line option.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.
```


After this I looked around a little bit and found this manual: [https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

Which I followed (the main difference being that I downloaded the build essential headers

```
sudo apt-get install build-essential linux-headers-`uname -r`
```

However when I ran the installer again I got exactly the same errors.

I wonder if I need to download the entire source for the linux kernel as suggested as a last resort:

```
This next step is optional. Most people will not need it, and it takes a fair amount of bandwidth and diskspace. It installs the Linux kernel source. If later steps fail, consider this a last resort.

sudo apt-get install linux-source-`uname -r`
cd /usr/src
sudo tar xvjf linux-source-`uname -r`
sudo ln -s linux-source-`uname -r` /usr/src/linux

The above command might print an error similar to the following:

E: Couldn't find package linux-source-2.6.20-16-386

In such case you could try following

sudo apt-get install linux-source
```


So the things I can see myself possibly needing to do are:

-download the linux kernel source
-figure out how to turn on wireless from single user mode so the installer can download a preconfigured kernel
-download a different version of the driver from NVIDIA
or -find out if there is a simpler way of doing this.

If anyone has any suggestions on where I should go from here they would be very much appreciated!

Here is the installer log:
```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Thu Aug  6 18:00:35 2009

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
  no X server check       : false
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
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: Yes)
ERROR: Unable to connect to download.nvidia.com (unknown host)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.28-14-generic/build'
-> Kernel output path: '/lib/modules/2.6.28-14-generic/build'
ERROR: If you are using a Linux 2.4 kernel, please make sure
       you either have configured kernel sources matching your
       kernel or the correct set of kernel headers installed
       on your system.
       
       If you are using a Linux 2.6 kernel, please make sure
       you have configured kernel sources matching your kernel
       installed on your system. If you specified a separate
       output directory using either the "KBUILD_OUTPUT" or
       the "O" KBUILD parameter, make sure to specify this
       directory with the SYSOUT environment variable or with
       the equivalent nvidia-installer command line option.
       
       Depending on where and how the kernel sources (or the
       kernel headers) were installed, you may need to specify
       their location with the SYSSRC environment variable or
       the equivalent nvidia-installer command line option.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.
```

---

### Post by Arup on 2009-08-06
Have you removed linux restricted modules?

---

### Post by adempewolff on 2009-08-06
No, although something wierd has been happening with it.  When I tested with the livecd both the drivers for my wireless card and video card showed up.  When I first installed however only the driver for the wireless card was available.  Then I upgraded to 2.6.30 for the ext4 support and the video card showed up but not the wireless card. I then booted into the 2.6.28-14 and both the video and wireless were there.  So I am currently using the one in the restricted modules but I would imagine it is a 32-bit driver and wonder if it would be better to use the 64 it driver?

---

### Post by 3rdalbum on 2009-08-06
If it's a driver from the repositories (Hardware Drivers program) then it matches the architecture of your computer. So, if you are running the 64-bit Ubuntu, then the driver you install from Hardware Drivers is 64-bit too.

---

### Post by Arup on 2009-08-07
Don't know why you upgraded the kernel for ext 4 support when the stock kernel supports it right out of the box.

---

### Post by adempewolff on 2009-08-07
3rdalbum - thanks, I had been hoping that was the case but it was exactly the same version as I used with 32 bit.

Arup - Someone told me that while the current kernel has support for it pre-2.6.30 kernels have occasional issues.  As all my data is on another partition which is not ext4 I'm not too worried about it

---

### Post by Arup on 2009-08-08
> **adempewolff said:**
> 3rdalbum - thanks, I had been hoping that was the case but it was exactly the same version as I used with 32 bit.

Arup - Someone told me that while the current kernel has support for it pre-2.6.30 kernels have occasional issues.  As all my data is on another partition which is not ext4 I'm not too worried about it

Been using ext4 for my boot and data partitions since day one of Jaunty and so far haven't lost any data, had a power failure as well.

---

