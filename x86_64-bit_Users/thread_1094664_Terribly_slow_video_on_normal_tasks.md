---
title: "Terribly slow video on normal tasks"
date: 2009-03-12
forum: x86 64-bit Users
---

### Post by mattyb515 on 2009-03-12
Some basics:

AMD Athlon 64 3700+
2GB Ram
nVidia GeForce 5200 128MB
  - driver 169.12
Ubuntu Studio 64
  - real time kernel

Since my install, this system seems to lag something awful when performing normal tasks.  When doing things like switching between windows, I can count the seconds it takes to do this.  The same goes for things like scrolling down web pages.  The more graphics on a page the worse it is.  I had Compiz installed at one point but that seemed to make it worse.  I'm surprised at the difference I've seen between XP and Studio 64.  Is the video card really to blame on this one?  I've run htop and with only Firefox running I'm using 3% CPU and my system is only using about 400MB of RAM.  Any help anyone can provide would be greatly appreciated.  

Thanks!

---

### Post by Arup on 2009-03-13
Have you installed the video drivers from the repos? If so I suggest you remove them and install latest ones from nvidia site. They make a big difference.

---

### Post by mattyb515 on 2009-03-13
They are installed from the repos.  I'll snag them from nVidia and give that a try.

Thanks.

---

### Post by Arup on 2009-03-13
> **mattyb515 said:**
> They are installed from the repos.  I'll snag them from nVidia and give that a try.

Thanks.

Make sure you remove the ones you installed from the repos.

---

### Post by 3Miro on 2009-03-13
I am not familiar with Studio and its desktop, but drvers before 1.80 work horribly with KDE. There might be other issues for other desktops. Get the latest video driver and see what happens.

---

### Post by mattyb515 on 2009-03-16
I've downloaded the drivers from nVidia and was following this install:

[http://ubuntuguide.org/wiki/Ubuntu:Intrepid#Installation_of_ATI_and_nVidia_Graphics_drivers]("http://ubuntuguide.org/wiki/Ubuntu:Intrepid#Installation_of_ATI_and_nVidia_Graphics_drivers")

but I get the following error messages.  Any thoughts/help would be appreciated.  The one part of those instructions I'm just not getting is where they say to "just connect to the internet."  

```
-> Installing NVIDIA driver version 173.14.18.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
ERROR: Unable to find the kernel source tree for the currently running kernel. 
       Please make sure you have installed the kernel source files for your
       kernel and that they are properly configured; on Red Hat Linux systems,
       for example, be sure you have the 'kernel-source' or 'kernel-devel' RPM
       installed.  If you know the correct kernel source files are installed,
       you may specify the kernel source path with the '--kernel-source-path'
       command line option.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.
```

---

### Post by mattyb515 on 2009-03-16
I should've also mentioned that I checked in the /usr/src directory for the kernel tree and it is there.  So I'm at a loss as to what to do next.

---

### Post by Arup on 2009-03-18
sudo apt-get install envy

Click on envy and follow instructions.

---

