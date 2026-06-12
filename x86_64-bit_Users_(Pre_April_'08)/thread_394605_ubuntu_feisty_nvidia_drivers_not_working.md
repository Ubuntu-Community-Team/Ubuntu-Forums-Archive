---
title: "ubuntu feisty nvidia drivers not working"
date: 2007-03-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by survient on 2007-03-27
ok, I was using the nvidia-glx drivers up until recently, in my xorg.conf, I had the driver set to "nvidia" and not "nv", but now I'm getting an error where it's saying my x server's kernel is version 9755 and my nvidia kernel version is 9749, and the xserver won't start. If I switch the "nvidia" to "nv" the x server wills start, but only one monitor will show up(I have Dual Monitor Display). I've tried installing the official nvidia driver, but it's forcing me to build my own kernel, and when I try using it, the x server says the kernel fails to load. How can I fix this? I just want DMD.

---

### Post by Colonel Kilkenny on 2007-03-27
Check out the feisty discussion. There are few threads about this.

---

### Post by kleeman on 2007-03-27
I had an issue like this a while back on both an amd64 and i386 systems. I solved it in both cases by reinstalling the appropriate linux-restricted-modules-*** and nvidia-glx packages. Why that worked I'm not sure....

sudo apt-get install --reinstall PACKAGE

---

### Post by cmost on 2007-03-27
I find the easiest way to install the nvidia drivers is to manually compile and install the official driver from nvidia's website.  To do this, you will need to uninstall the nvidia glx related packages from Synaptic (including the restricted modules.)  Next, download the official nvidia package from the nvidia website and save it to your home folder (remember where you saved it.)  Next, in a terminal, type: "sudo apt-get install build-essential gcc".  Go into Synaptic and install your kernel headers (for your running kernel.  You can figure out what kernel you're running by typing "uname -r" in a terminal.  Finally, install the nvidia driver after first killing your X server.  To do this, simply open a terminal and type "sudo /etc/init.d/gdm stop"; without the quotes to kill the xserver.  Next, type:  sudo sh /path/to/nvidia/download/NVIDIA-Linux-x86_64-1.0-9755-pkg2.run  Follow the prompts.  I recommend you DON'T let the nvidia package modify your /etc/X11/xorg.conf.  Do this yourself.  Type:  sudo nano /etc/X11/xorg.conf.  Simply change "nv" to "nvidia" in xorg.conf, save the file and reboot.

---

### Post by survient on 2007-03-27
if that worked, I would have had it working by now. I've had both build-essential and gcc and the proper headers installed. Is there any way to clear the propietary driver installation out, or where can I find some precompiled nvidia kernels? Thanks again

---

