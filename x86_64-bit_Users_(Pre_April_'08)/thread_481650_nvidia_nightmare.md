---
title: "nvidia nightmare"
date: 2007-06-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by perky on 2007-06-22
G'day!

I'm running 64-bit feisty with a Nvidia 6800, and every time I boot, I am greeted with the text interface "gdm has failed....would you like to see diagnostic.." (something like that.... you probably all know what i'm talking about!).

Anyways, to be able to get into ubuntu, i have to sudo /etc/init.d/gdm stop, run the NVIDIA-Linux-x86_64-100.14.09-pkg2.run (from Nvidia's website), then start gdm.  Funnily enough, hardware acceleration works from this point onwards, and everything seems normal.  That is, until I reboot, I have to repeat the whole install process again.

Has anyone had a similar problem and come up with a fix?  The NVIDIA installer builds a new kernel every time (I think, i usually just quickly press OK to whatever comes up).

Any help greatly appreciated!

---

### Post by tux821 on 2007-06-22
Alway's use the Ubuntu Nvidia packages, see:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

It will take some effort at first, but will work so much better..

If you -exist- on using those nVidia driver package, check out your /etc/init.d/
I expect there some files like *nvidia* 
You have to disable those to prevent the startup nvidia configuration.

---

### Post by perky on 2007-06-23
The reason I am not using the ubuntu package is because i can not get it to work.  From what I've read, this is probably because I used envy with edgy, and did a dist-upgrade when feisty was released.

I tried moving nvidia-kernel (the only nvidia related thing i could see in /etc/init.d/), but same results.

Some more information, this appears in var/log/Xorg.0.log when x initially crashes and BEFORE I install the nvidia driver and boot into x:
```

(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"

```

```

lsmod | grep -i nvidia
nvidia               4577228  0 

```

Does this help?

---

### Post by perky on 2007-06-23
OK, after having a look at the nvidia file, there is a Q&A section that may be of use to someone who understands it!

Q. My X server fails to start, and my X log file contains the error:
   
   (EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
   
   
A. The X driver will abort with this error message if the NVIDIA kernel module
   fails to load. If you receive this error, you should check the output of
   `dmesg` for kernel error messages and/or attempt to load the kernel module
   explicitly with `modprobe nvidia`. If unresolved symbols are reported, then
   the kernel module was most likely built against a Linux kernel source tree
   (or kernel headers) for a kernel revision or configuration that doesn't
   match the running kernel.

   You can specify the location of the kernel source tree (or headers) when
   you install the NVIDIA driver using the --kernel-source-path command line
   option (see `sh NVIDIA-Linux-x86_64-100.14.09-pkg1.run --advanced-options`
   for details).

   Old versions of the module-init-tools include `modprobe` binaries that
   report an error when instructed to load a module that's already loaded into
   the kernel. Please upgrade your module-init-tools if you receive an error
   message to this effect.

   The X server reads '/proc/sys/kernel/modprobe' to determine the path to the
   `modprobe` utility and falls back to '/sbin/modprobe' if the file doesn't
   exist. Please make sure that this path is valid and refers to a `modprobe`
   binary compatible with the Linux kernel running on your system.

   The "LoadKernelModule" X driver option can be used to change the default
   behavior and disable kernel module auto-loading.


Output of dmesg | grep -i nvidia
```

[    0.000000] ACPI: RSDP (v000 Nvidia                                ) @ 0x00000000000f7560
[    0.000000] ACPI: RSDT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x000000003fff3040
[    0.000000] ACPI: FADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x000000003fff30c0
[    0.000000] ACPI: MCFG (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x000000003fff9880
[    0.000000] ACPI: MADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x000000003fff97c0
[    0.000000] ACPI: DSDT (v001 NVIDIA AWRDACPI 0x00001000 MSFT 0x0100000e) @ 0x0000000000000000
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[   50.326706] nvidia: module license 'NVIDIA' taints kernel.
[   50.332269] NVRM: loading NVIDIA Linux x86_64 Kernel Module  1.0-7184  Tue Aug  1 19:28:54 PDT 2006

```

modprobe nvidia does not have any output.

I dont understand what the Q&A is refering to about kernels.

---

### Post by nzadLithium on 2007-06-23
I had a similar problem. What i did to fix is i reinstalled ubuntu. Then i installed the nvidia drivers from synaptic package manager. worked perfectly after that. just go into package manager once u reinstalled and add nvidia-glx and nvidia-kernel-common. That should get it going.

---

### Post by Cappy on 2007-06-23
I've had that error before and it was because I was missing restricted modules
```
sudo apt-get install linux-restricted-modules-`uname -r`
```

This is the script I use every time I reinstall:
```

sudo apt-get --purge remove nvidia-glx* nvidia-kernel-common nvidia-settings
sudo rm /etc/init.d/nvidia-*
sudo update-rc.d nvidia-kernel remove
sudo apt-get install nvidia-glx-new linux-restricted-modules-`uname -r`

```

If you still want to compile here is the script I made for compiling:
```

sudo apt-get --purge remove nvidia-glx* nvidia-settings linux-restricted-modules*
sudo rm /etc/init.d/nvidia-*
sudo apt-get install build-essential linux-headers-amd64-generic linux-headers-generic gcc pkg-config xserver-xorg-dev linux-headers-`uname -r`
sudo sh NVIDIA-Linux-x86_64-100.14.09-pkg2.run
sudo nvidia-xconfig --no-composite

```

You MUST remove linux-restricted-modules to compile.

---

### Post by CREEPING DEATH on 2007-06-23
> **perky said:**
> G'day!
Anyways, to be able to get into ubuntu, i have to sudo /etc/init.d/gdm stop, run the NVIDIA-Linux-x86_64-100.14.09-pkg2.run (from Nvidia's website), then start gdm.  Funnily enough, hardware acceleration works from this point onwards, and everything seems normal.  That is, until I reboot, I have to repeat the whole install process again.

There's your problem, you shouldn't ever run the Nvidia .run file on a Debian-based distro.  And there is no reason to in Ubuntu since the drivers are precompiled in Synaptic!

CD

---

### Post by Cappy on 2007-06-23
Installing from the nvidia website is fine as long as you get the dependencies (like in the script above) or use Envy.
Infact, it's required if you run a 8500/8600 nvidia card.
The repos binaries are easier and I would use them instead, if I had a choice.

---

### Post by perky on 2007-06-23
> **Cappy said:**
> I've had that error before and it was because I was missing restricted modules

You MUST remove linux-restricted-modules to compile.

Thank-you!!!
Uninstalling the restricted drivers fixed my problem, and hardware acceleration still works, yay :D

---

### Post by darknightuk on 2007-06-23
> **CREEPING DEATH said:**
> There's your problem, you shouldn't ever run the Nvidia .run file on a Debian-based distro.  And there is no reason to in Ubuntu since the drivers are precompiled in Synaptic!

CD if you are using a card that is supported by the glx drivers it is EASIER to install this way but only if you card is supported and quite a number of new cards are not

---

### Post by tux821 on 2007-06-23
> **perky said:**
> Thank-you!!!
Uninstalling the restricted drivers fixed my problem, and hardware acceleration still works, yay :D

Ok thats important, you got it working. :D

Your nVidia 6800 is on the nvidia-glx package supported list:
/usr/share/doc/nvidia-glx/README.txt.gz

On my Debian AMD64 (x86_64) workstation,  with nVidia 6600 card, I have the best results using the Debian nvidia-kernel-source package + nvidia-glx. 
So I expect that on your Ubuntu x86_64 environment with 6800 card it should work too using the 'Ubuntu' nvidia packages.

---

### Post by Cappy on 2007-06-23
> **perky said:**
> Thank-you!!!
Uninstalling the restricted drivers fixed my problem, and hardware acceleration still works, yay :D

I'm glad you made sense of that mess =P

---

### Post by perky on 2007-06-23
> **tux821 said:**
> Ok thats important, you got it working. :D

Your nVidia 6800 is on the nvidia-glx package supported list:
/usr/share/doc/nvidia-glx/README.txt.gz

On my Debian AMD64 (x86_64) workstation,  with nVidia 6600 card, I have the best results using the Debian nvidia-kernel-source package + nvidia-glx. 
So I expect that on your Ubuntu x86_64 environment with 6800 card it should work too using the 'Ubuntu' nvidia packages.

I could not get the ubuntu version to work. I searched a lot and found that it was a common problem with people like me who used envy with edgy and dist-upgraded to feisty.  No biggie though, the nvidia one works for now (though that might change come next kernel release!)

Thanks anyway :)

---

### Post by alpinweiss88 on 2007-06-26
CAPPY!!!!!

Thank you, I owe you a beer!

I have never been able to get nvidia drivers to work so easily.  I have always had to recompile, and mess with it for hours on end.  Something about that 'purge' is what did it I think.

Here is how I got into my nightmare this time, it was unintentional (sort of).  I decided up do a dist-upgrade from edgy to feisty... launched Adept, did the Dist Upgrade.... it came back with some kind of error.  Oh well.

Cut to a couple of days later, and I went to install some other package... don't even remember what it was now.  Did 'sudo apt-get install <whatever it was>'... all of a sudden, lots of packages are updating.  I didn't want to kill it for fear of borking my system, but sure enough when I rebooted, I couldn't get into X.  

Still not sure what happened, but your method got me back up and running.  Going to save this as a script for future reference.  Thanks again!

---

