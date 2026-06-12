---
title: "Problems with Graphical Drivers"
date: 2009-02-07
forum: x86 64-bit Users
---

### Post by Arnack on 2009-02-07
I have a Nvidia Geforce 8600 GTS and i'm trying to get the newest driver installed into my Ubuntu (newest version). When I go to the Hardware Drivers, I pick then newest driver, restart and Ubuntu says before startub that there is something wrong with my video card driver, and that I must start in default graphical configuration.
How do I select my drivers for my graphic card?

---

### Post by bicyclebarron on 2009-02-07
I upgraded my ATI drivers recently. Might check the NVDIA site for Linux instructions on installation. The ATI installation did not complete with a package manager. Installation was from .tar and required installation from terminal.

---

### Post by Arnack on 2009-02-07
I tried using their driver, but I got an error. Let me report back
When installing the driver with sh, it said:
  ERROR: You appear to be running an X server; please exit X before            
         installing.  For further details, please see the section INSTALLING   
         THE NVIDIA DRIVER in the README available on the Linux driver         
         download page at [www.nvidia.com](www.nvidia.com).

I fixed that and it says my Xen kernal cannot be used with my Nvidia driver.

---

### Post by Yellow Pasque on 2009-02-08
> I fixed that and it says my Xen kernel cannot be used with my Nvidia driver.
Aren't proprietary, closed-source drivers great?..

---

### Post by Raffles10 on 2009-02-08
I have the same graphics card as you, I installed the restricted driver that Ubuntu offers up after installation is complete, I think it's version 177, performance is excellent. would it really be that much better with the buggy nvidia offering ?

If it is let us know.

---

### Post by norwoods on 2009-02-12
you can install a newer driver (180.29) with synaptic from [https://launchpad.net/~anders-kaseorg/+archive/ppa](https://launchpad.net/~anders-kaseorg/+archive/ppa)

---

### Post by mad_max0204 on 2009-02-12
Why dont you install Nvidia drivers manually ??

Works everytime and its pretty easy when you do I once.
You can download both latest stable and latest beta from nvidia ftp.
Then just ctrl+alt+F1 (of F2-F6), login, type "sudo /etc/init.d/gdm stop",
cd to your downloaded drivers, run "sudo sh ./driver_name_version", follow steps and accept xorg.conf changes, then when you finish type "sudo /etc/init.d/gdm start" and woilla, nvidia drivers working.

I actually is that simple.
Later on you configure your xorg.conf manually as you wish or just run "sudo nvidia-settings" from terminal.

---

### Post by jet2230 on 2009-02-17
> **Raffles10 said:**
> I have the same graphics card as you, I installed the restricted driver that Ubuntu offers up after installation is complete, I think it's version 177, performance is excellent. would it really be that much better with the buggy nvidia offering ?

If it is let us know.

yes it is better. personally i think its a lot smoother, faster (compiz) and it has these benefits.

Added OpenGL 3.0 preliminary support;
· Added support for PureVideo-like features (via the VDPAU API);
· Added support for CUDA 2.1;
· Added performance optimizations for OpenGL workstations;
· Added SDI full-range color support;
· Improved stability and X pixmap placement on GeForce 8 series and newer GPUs;
· The glyph cache was enabled by default and it is now available on all supported GPUs;
· The shared memory X pixmaps option (AllowSHMPixmaps) is now disabled by default;
· Fixed an nvidia-settings issue. The application crashed if the xorg.conf file contained the Device and Screen sections but no ServerLayout section;
· Fixed an nvidia-settings issue with the SDI sync skew controls;
· Fixed a Compiz Fusion issue for Geforce 6 and 7 series GPUs;
· Fixed monitor sync range parsing issue in xorg.conf;
· Fixed crashing issues with some SDI applications;
· Fixed Linux OpenGL library issue. The library crashed when used inside the FreeBSD's Linux emulation layer.

the nvidia installer requires some patience, i think you will be lucky if everything goes ok on your 1st nvidia driver upgrade, but once you get it working you will not forget it!

this is what worked for me: [http://ubuntuforums.org/showthread.php?t=1071283](http://ubuntuforums.org/showthread.php?t=1071283)

---

