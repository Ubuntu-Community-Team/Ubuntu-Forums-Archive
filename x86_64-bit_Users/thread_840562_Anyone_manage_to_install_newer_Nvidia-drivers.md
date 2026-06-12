---
title: "Anyone manage to install newer Nvidia-drivers?"
date: 2008-06-25
forum: x86 64-bit Users
---

### Post by isecore on 2008-06-25
I'm trying to install the newer Nvidia-drivers. Currently I'm running an older beta-version (171.06) which is stable. I've found that there's less than completely smooth running experiences with newer ones. Especially 173.14.05 has some funky issues.

So I found that Nvidia has release a slightly newer version, 173.14.09 and also a beta, 177.13.

However, neither of these will install. Both installs fail with the message about how the kernel module couldn't be compiled, and the logfile only shows a few sudden errors without much to go on as far as troubleshooting.

I've googled my brains out but have found no solution to this at all. The only thing I've found is that apparently some people with -rt kernels have these issues. I run the -rt kernel since I depend on maximum performance in video/audio applications. I might try rebooting into the generic kernel later and see if the problem persists. I've found no help in [the documentation for the driver]("http://us.download.nvidia.com/XFree86/Linux-x86_64/177.13/README/chapter-08.html").

My uname -a is

```
Linux superbeast 2.6.24-19-rt #1 SMP PREEMPT RT Wed Jun 18 15:36:32 UTC 2008 x86_64 GNU/Linux
```

and I have a Geforce 9600GT graphics card.

UPDATE: My reason for wanting a newer driver even though the 171.06 is "stable" is that there's some very annoying freezes when using multiple monitors or TV-out. I was hoping these issues would be resolved in a newer driver.

---

### Post by philinux on 2008-06-25
Yes.

I followed this
[http://ubuntuforums.org/showthread.php?t=813931&highlight=nvidia](http://ubuntuforums.org/showthread.php?t=813931&highlight=nvidia)

Post 6

---

### Post by philinux on 2008-06-25
Once you do this there is no going back to the synaptic version.


Every time there is a kernel upgrade you need to recompile the driver.

Pretty easy only takes 2 mins.

---

### Post by isecore on 2008-06-25
At the risk of sounding like a complete dick, but I know all that already. The Nvidia-driver in Restricted Drivers don't support the 9xxx-series of Nvidia-cards, so installing the driver manually is the only recourse. I'm fine with that. I also know that for each kernel upgrade I'll have to reinstall it. No problems, it's perfectly logical.

What I'm wondering is why the 173.14.05 installs fine, but 173.14.09 and later won't compile (and thus not install).

---

### Post by philinux on 2008-06-25
If you've got 173.14.05 already installed then maybe try.

sudo nvidia-installer --update

---

### Post by isecore on 2008-06-25
> **philinux said:**
> If you've got 173.14.05 already installed then maybe try.

sudo nvidia-installer --update

All that did was give me a message that 173.14.05 is already the newest available. Besides, the only thing that command does is download the file and then run it. Nothing special about that.

I tried following those instructions you pointed out earlier, thinking that it might be any Nvidia-related packages in APT who was screwing things up. However, when I tried doing apt-get remove --purge nvidia* it wanted to also remove my kernels (!) which of course is less than optimal. It also wanted to remove the ubuntu-desktop metapackage which if removed will cause problems when upgrading. So no go there.

However, I tried doing the 177.13 install and here's the nvidia-installer.log for anyone interested to peruse.

```

tenvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Wed Jun 25 22:07:48 2008
installer version: 1.0.7

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
  no cc version check     : false
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
-> Installing NVIDIA driver version 177.13.
-> There appears to already be a driver installed on your system (version: 173.
   14.05).  As part of installing this driver (version: 177.13), the existing d
   river will be uninstalled.  Are you sure you want to continue? ('no' will ab
   ort installation) (Answer: Yes)
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.24-19-rt/build'
-> Kernel output path: '/lib/modules/2.6.24-19-rt/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/lib/modules/2.6.24-19-rt/bu
   ild SYSOUT=/lib/modules/2.6.24-19-rt/build'...
   NVIDIA: calling KBUILD...
   make CC=cc  KBUILD_VERBOSE=1 -C /lib/modules/2.6.24-19-rt/build SUBDIRS=/tmp
   /selfgz18997/NVIDIA-Linux-x86_64-177.13-pkg2/usr/src/nv modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;								\
   	/bin/false)
   mkdir -p /tmp/selfgz18997/NVIDIA-Linux-x86_64-177.13-pkg2/usr/src/nv/.tmp_ve
   rsions ; rm -f /tmp/selfgz18997/NVIDIA-Linux-x86_64-177.13-pkg2/usr/src/nv/.
   tmp_versions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz18997/NVIDIA-Linux-x86_64-177.
   13-pkg2/usr/src/nv
     cc -Wp,-MD,/tmp/selfgz18997/NVIDIA-Linux-x86_64-177.13-pkg2/usr/src/nv/.nv
   .o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.2.3/include -D__KER
   NEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-p
   rototypes -Wno-trigraphs -fn
   o-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2  -mt
   une=generic -m64 -mno-red-zone -mcmodel=kernel -pipe -Wno-sign-compare -fno-
   asynchronous-unwind-tables -funit-at-a-time -mno-sse -mno-mmx -mno-sse2 -mno
   -3dnow -maccumulate-outgoing-args   -fstack-protector -fomit-frame-pointer -
   g  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign   -I
   /tmp/selfgz18997/NVIDIA-Linux-x86_64-177.13-pkg2/usr/src/nv -Wall -Wimplicit
   -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-ar
   ith -Wno-multichar -Werror -mcmodel=kernel -mno-red-zone -MD   -Wsign-compar
   e -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING
   =\"177.13\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUI
   LD_BASENAME=KBUILD_STR(nv)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tm
   p/selfgz18997/NVIDIA-Linux-x86_64-177.13-pkg2/usr/src/nv/.tmp_nv.o /tmp/self
   gz18997/NVIDIA-Linux-x86_64-177.13-pkg2/usr/src/nv/nv.c
   In file included from include/asm/dma-mapping_64.h:9,
                    from include/asm/dma-mapping.h:4,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz18997/NVIDIA-Linux-x86_64-177.13-pkg2/usr/s
   rc/nv/nv-linux.h:86,
                    from /tmp/selfgz18997/NVIDIA-Linux-x86_64-177.13-pkg2/usr/s
   rc/nv/nv.c:14:
   include/linux/scatterlist.h: In function â&#128;&#152;sg_virtâ&#128;&#153;:
   include/linux/scatterlist.h:293: warning: pointer of type â&#128;&#152;void *â&#128;&#153; used 
   in arithmetic
   In file included from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz18997/NVIDIA-Linux-x86_64-177.13-pkg2/usr/s
   rc/nv/nv-linux.h:86,
                    from /tmp/selfgz18997/NVIDIA-Linux-x86_64-177.13-pkg2/usr/s
   rc/nv/nv.c:14:
   include/asm-generic/pci-dma-compat.h: In function â&#128;&#152;pci_map_pageâ&#128;&#153;:
   include/asm-generic/pci-dma-compat.h:49: warning: pointer of type â&#128;&#152;void *â
   &#128;&#153; used in arithmetic
   In file included from include/linux/compat.h:14,
                    from include/asm/mtrr.h:131,
                    from /tmp/selfgz18997/NVIDIA-Linux-x86_64-177.13-pkg2/usr/s
   rc/nv/nv-linux.h:121,
                    from /tmp/selfgz18997/NVIDIA-Linux-x86_64-177.13-pkg2/usr/s
   rc/nv/nv.c:14:
   include/asm/compat.h: In function â&#128;&#152;compat_alloc_user_spaceâ&#128;&#153;:
   include/asm/compat.h:210: warning: pointer of type â&#128;&#152;void *â&#128;&#153; used in arit
   hmetic
   /tmp/selfgz18997/NVIDIA-Linux-x86_64-177.13-pkg2/usr/src/nv/nv.c: In functio
   n â&#128;&#152;nv_alloc_file_privateâ&#128;&#153;:
   /tmp/selfgz18997/NVIDIA-Linux-x86_64-177.13-pkg2/usr/src/nv/nv.c:1887: error
   : implicit declaration of function â&#128;&#152;__SEMAPHORE_INITIALIZERâ&#128;&#153;
   /tmp/selfgz18997/NVIDIA-Linux-x86_64-177.13-pkg2/usr/src/nv/nv.c:1887: error
   : invalid initializer
   /tmp/selfgz18997/NVIDIA-Linux-x86_64-177.13-pkg2/usr/src/nv/nv.c: In functio
   n â&#128;&#152;nv_lock_init_locksâ&#128;&#153;:
   /tmp/selfgz18997/NVIDIA-Linux-x86_64-177.13-pkg2/usr/src/nv/nv.c:3808: error
   : invalid initializer
   /tmp/selfgz18997/NVIDIA-Linux-x86_64-177.13-pkg2/usr/src/nv/nv.c:3809: error
   : invalid initializer
   make[3]: *** [/tmp/selfgz18997/NVIDIA-Linux-x86_64-177.13-pkg2/usr/src/nv/nv
   .o] Error 1
   make[2]: *** [_module_/tmp/selfgz18997/NVIDIA-Linux-x86_64-177.13-pkg2/usr/s
   rc/nv] Error 2
   NVIDIA: left KBUILD.
   nvidia.ko failed to build!
   make[1]: *** [module] Error 1
   make: *** [module] Error 2
-> Error.
ERROR: Unable to build the NVIDIA kernel module.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.
```

Sorry about the formatting, for some reason it gets mangled.

---

### Post by |{urse on 2008-06-25
or go to nvidia's website and download the appropriate driver for your card. Install kernel development headers, then sudo init 4 and chmod +X nameofthenvidiadriver.run then ./nameofthenvidiadriver.run

---

### Post by OmegaBLK on 2008-06-25
> **isecore said:**
> At the risk of sounding like a complete dick, but I know all that already. The Nvidia-driver in Restricted Drivers don't support the 9xxx-series of Nvidia-cards, so installing the driver manually is the only recourse. I'm fine with that. I also know that for each kernel upgrade I'll have to reinstall it. No problems, it's perfectly logical.

What I'm wondering is why the 173.14.05 installs fine, but 173.14.09 and later won't compile (and thus not install).

I have a 9600GT also.  When I first moved to 64-bit recently I had trouble installing the 173.14.05, but I eventually was able to get it working along with 173.14.09.  I haven't tried the newer beta driver that has support for the GT200, 177.13, but I'm sure it will install with no problems also.  I don't really recall step by step of what I did to get it working, but I know I blacklisted the restricted module and the nv module in /etc/default/linux-restricted-modules-common.  I also was compiling against /lib/modules/$(uname -r)/build instead of /lib64/modules/$(uname -r)/build a few times which caused me to have problems--old habit I guess.

Best bet is to remove everything nvidia, and try recompiling against the generic kernel as you mentioned. Never used the realtime kernel so I can't really help with that.  If you are still having problems you may want to go over to [NVNews](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14) for further advice/help.

---

### Post by isecore on 2008-06-25
> **|{urse said:**
> or go to nvidia's website and download the appropriate driver for your card. Install kernel development headers, then sudo init 4 and chmod +X nameofthenvidiadriver.run then ./nameofthenvidiadriver.run

Yeah, I kinda figured that wouldn't make any difference. But I tried it, and as it turns out... it doesn't make any difference. 

I don't see what the runlevel affects so profoundly that the 173.14.05 installs fine but 173.14.09 doesn't.

---

### Post by Neo0351 on 2008-06-26
i just installed the 173.14.09 with no problems.  im running a 9600gt also.  here's my uname -a
```
Linux neo-desktop 2.6.24-19-generic #1 SMP Wed Jun 18 14:15:37 UTC 2008 x86_64 GNU/Linux

```

---

### Post by isecore on 2008-06-27
Well sportsfans, it's official. If you're running a real-time kernel (one that ends in -rt) then any Nvidia driver newer than 173.14.05 won't compile. I tried it with the same identical kernel version, but the "generic" flavor, and it compiled just fine.

Also, the issues I've experienced in every recent driver is still present, even in the 177-beta driver. This means my next graphicscard will be from AMD/ATI.

---

### Post by Neo0351 on 2008-06-27
> **isecore said:**
> 
Also, the issues I've experienced in every recent driver is still present, even in the 177-beta driver.

i agree, the drivers really suck so far.

---

### Post by lordViN on 2008-06-27
well, Yesterday I managed to install Nvidia 173.14.09 driver on Ubuntu 8.04 server amd64, my gpu is a nvidia 7600GT, and my CPU is an amd athlon 64 x2 3800+.

there are two ways, 

one is to install the linux-restricted-modules-server, then install the nvidia-glx-new from ubuntu repositories. *I haven't tried this yet but from what I've read this method should work.

the second one, is to follow the manual installation method.



1. Download the NVIDIA-Linux-x86_64-173.14.09-pkg2.run from nvidia's website.

2. in a terminal, 

```
sudo apt-get remove --purge nvidia*
```

3. install the neccesary for the installation
```
sudo apt-get install build-essential linux-headers-$(uname-r) pkg-config  xserver-xorg-dev
```

4. Delete unnecesary and conflictive files
```
sudo rm /etc/init.d/nvidia-kernel
```

5.modify the modules to disable the use of restricted drivers to avoid conflicts.
```
sudo nano -w /etc/default/linux-restricted-modules-common 
```
and modify the following line. 
it should look like this:
     
     DISABLED_MODULES="nv nvidia_new"


6. go to your desktop or to the location where the installer is located.

```
sudo chmod +x NVIDIA-Linux-x86_64-173.14.09-pkg2.run
```

7. back up your x configuration file

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

```
8. ctrl-alt-F1 to open a shell.

9.in ubuntu, (for kde is kdm instead of gdm) 
```
sudo /etc/init.d/gdm stop
``` 

10. install the driver
  
       ```
sudo sh NVIDIA-Linux-x86_64-173.14.09-pkg2.run
```


answer yes to all the questions, in the end it will ask something about installing opengl 32-bit libraries answer yes to this question too. (it will fail to check a opengl file, but it will succeed the installation). 


```

sudo /etc/init.d/gdm start
```
to start the x server

in the end try 

    ```
glxinfo | grep direct
```
    
direct rendering should be set to "yes".

check out glxgears to confirm harware acceleration

```
sudo apt-get install mesa-utils

```
```
glxgears
```

---

### Post by isecore on 2008-06-27
> **lordViN said:**
> A really long entry that I edited out

Yes of course. But had you actually read the thread you would know that this method does not work if you have a 9xxx-series card since there's no support in the nvidia-glx-new package.

Also, the manual install, like I already concluded, will fail for no apparent reason if you're running a real-time kernel. But had you read the thread you would know this.

---

### Post by bigpoppa on 2008-07-07
hey guys im quite new with linux. i have the 64bit version and yes i do have the 9600gt as well... all the codes you guys been posting made me dizzy.. is there anyway that i can install the driver, the one that i downloaded from the nvidia site? i always get an error message..

thanks!

---

### Post by isecore on 2008-07-07
> **bigpoppa said:**
> hey guys im quite new with linux. i have the 64bit version and yes i do have the 9600gt as well... all the codes you guys been posting made me dizzy.. is there anyway that i can install the driver, the one that i downloaded from the nvidia site? i always get an error message..

thanks!

And as always it helps immensely if you tell us WHAT that error message is :)

---

### Post by blazercist on 2008-07-07
Can you please elaborate on what "issues" you have with the newer NVIDIA drivers? I also, like you, used to use the 171.06 drivers because I read on Phoronix of people complaining, but since then I have tried the newer drivers and I find almost no difference, however, I'm not a very technical user.  I had no problems installing them either (generic kernel + 9600GT).

---

### Post by isecore on 2008-07-07
Issues I experience:

* Screen randomly "blinks" and then freezes.

This happens even in 171.06 but it's much more rare than in higher versions. It's a random event, doesn't matter if I'm using a 3D app or just puttering around the desktop. Suddenly the display "jerks" and everything gets stuck. Drivers higher than 171.06 exhibit this behavior regularly.

* Twinview is a dead end. 

Sets up fine but as soon as you drag a window between monitors or use a Compiz-effect such as the Expo it freezes in mid-render, then "sticks" like that for several minutes. This happens in EVERY driver I've tried, even 171.06

* Noisy display

With drivers higher than 171.06 I sometimes get a very strange phenomenon. The display suddely gets filled with random noise. Pixels randomly changing color. It's happened once with 171.06 but never again.

Attached is a cropped screenshot displaying this. This is just when it's beginning, the longer you do this without a reboot the more noise accumulates. Restarting X does not make it go away, only a reboot does that.

---

### Post by blazercist on 2008-07-07
Thats really weird dude, I have the same card and I have none of those problems... are you running a 64-bit kernel by any chance?

How did you install the driver?  What does you xorg.conf look like?

I use twinview, compiz, emerald at my max resolution with no problems at all.

---

### Post by isecore on 2008-07-07
My uname -a:

```
Linux superbeast 2.6.24-19-generic #1 SMP Wed Jun 18 14:15:37 UTC 2008 x86_64 GNU/Linux
```

Installation in brief:

Installed the driver via the Nvidia-installer. Ctrl-alt-f1 to get to a terminal. Shut down X via /etc/init.d/gdm stop then install required headers and build-essential using apt. Run the installer, blacklist the "nv" module, have the installer write a new xorg.conf for me. Load "nvidia" kernel module. Check xorg.conf and setup mouse/keyboard etc. Restart gdm via /etc/init.d/gdm start

xorg.conf as it looks right now:

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder62)  Mon May 19 00:29:52 PDT 2008

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "MX1000"
EndSection

Section "Files"
    RgbPath         "/usr/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"
	Identifier "MX1000"
	Driver  "evdev"
	Option "Device" "/dev/input/event2"
#	Option "Device" "/dev/input/by-id/usb-Logitech_USB_Receiver-event-mouse"
#	Option  "Name"  "Logitech USB Receiver"
	Option "RelHWHEELOptions" "invert"
#	Option  "HWHEELRelativeAxisButtons" "7 6"
EndSection

#Section "InputDevice"
    # generated from default
#    Identifier     "Mouse0"
#    Driver         "mouse"
#    Option         "Protocol" "auto"
#    Option         "Device" "/dev/psaux"
#    Option         "Emulate3Buttons" "no"
#    Option         "ZAxisMapping" "4 5"
#EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option	   "NoLogo"
    Option 	   "Coolbits" "1"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

---

### Post by blazercist on 2008-07-07
Wow thats weird, seems to be the normal install procedure/kernel/xorg.conf I can't tell you what is wrong, but the behavior you are describing is NOT normal.

Perhaps you are running some type of software that interferes with the display driver or perhaps some hardware conflicts?  Or maybe even a bad GPU altogether?

See if disabling compiz fixes this?
Try changing the VGA/DVI cable that connects your monitor?

---

### Post by bigpoppa on 2008-07-14
this is the error message that i get:

"Could not open the file /home/mark/Desktop/NVIDI…x86_64-173.14.09-pkg2.run."

what im doing is im double clicking on the .run file or drag and drop it on the terminal...

---

### Post by Ducksgoquak on 2008-07-14
in order to install that file you have to do something a little different.

First hit alt + cntl + f1 to open a black screened terminal.

Then you have to stop gnome:
```

sudo /etc/init.d/gdm stop

```

now change to the desktop directory(have to capitalize Desktop)

```
cd Desktop
```

Now install run the install file (hit tab after you have the ./NVIDIA it will fill in the rest of the file name for you) :)

```
sudo sh ./NVIDIA...
```

after this you can restart gnome

```
sudo /etc/init.d/gdm restart
```


NOTE: this is just to install the new driver, i don't know if you need to remove anything else before hand to get it to work. Definitely not an expert... this is just how you run that file.

---

### Post by sunny_nwho on 2008-07-14
if you still have a problem try using the envy script. It now has the latest drivers

---

### Post by Artemis3 on 2008-07-15
> **isecore said:**
> Issues I experience:

* Screen randomly "blinks" and then freezes.

This happens even in 171.06 but it's much more rare than in higher versions. It's a random event, doesn't matter if I'm using a 3D app or just puttering around the desktop. Suddenly the display "jerks" and everything gets stuck. Drivers higher than 171.06 exhibit this behavior regularly.

* Twinview is a dead end. 

Sets up fine but as soon as you drag a window between monitors or use a Compiz-effect such as the Expo it freezes in mid-render, then "sticks" like that for several minutes. This happens in EVERY driver I've tried, even 171.06

* Noisy display

With drivers higher than 171.06 I sometimes get a very strange phenomenon. The display suddely gets filled with random noise. Pixels randomly changing color. It's happened once with 171.06 but never again.

This sounds like a hardware issue to me, either bad memory or gpu / some component malfunctioning. Make sure your gpu is not running too hot, install nvclock and in a terminal type: nvclock -i and check the gpu temp. See if you have problems in windows, and tell us if you bought an overclocked card.

I have found with my 8800gt that i need to run nvclock -f -F auto or else i get very high temps.

Regarding the initial post: I say either stay with the old driver, or don't use a -rt kernel. Because Nvidia is a closed proprietary driver, only Nvidia can fix these issues; and its very unlikely that they will try each possible kernel variant/platform out there.

Do note that -rt kernels trade overall performance for low latency, (ie. your system as a whole will be slower) so be very sure that you absolutely need low latency (for audio / video editing, you don't).

---

### Post by flip314 on 2008-07-17
> **sunny_nwho said:**
> if you still have a problem try using the envy script. It now has the latest drivers

I installed the latest envy script from hardy-proposed, but it's only offering to install v169.x and not the new versions.  I installed the newest nvidia-glx-new-envy (v173.14.09), but that didn't seem to actually do anything.  I don't have hardware acceleration and can't see the driver anywhere

---

### Post by darkknight045 on 2008-07-18
I installed Envy two days ago and it had the latest drivers available, are you sure your getting the right package?

```
sudo apt-get install envyng-gtk
```

---

### Post by screaminj3sus on 2008-07-18
I currently have 173.14.09 installed, but it seems like nvidia has pulled it and now the latest it shows is 173.14.05. Strange.

---

