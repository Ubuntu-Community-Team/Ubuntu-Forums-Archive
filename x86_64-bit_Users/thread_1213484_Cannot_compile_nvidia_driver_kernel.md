---
title: "Cannot compile nvidia driver kernel"
date: 2009-07-14
forum: x86 64-bit Users
---

### Post by bestsword on 2009-07-14
I have a Core i7 system and try to install nvidia GTX 280. I am following the instruction 
[http://ubuntuforums.org/showthread.php?t=1125400](http://ubuntuforums.org/showthread.php?t=1125400)
for installing the nvidia driver.
My ubuntu is 8.04.
However, when I am running the driver installer, an error message always shows up:

"
[FONT=PrimaSans BT,Verdana,sans-serif]ERROR: Unable to load the kernel module 'nvidia.ko'.  This happens most
       frequently when this kernel module was built against the wrong or
       improperly configured kernel sources, with a version of gcc that differs
       from the one used to build the target kernel, or if a driver such as
       rivafb/nvidiafb is present and prevents the NVIDIA kernel module from
       obtaining ownership of the NVIDIA graphics device(s), or NVIDIA GPU
       installed in this system is not supported by this NVIDIA Linux graphics
       driver release.

       Please see the log entries 'Kernel module load error' and 'Kernel
       messages' at the end of the file '/var/log/nvidia-installer.log' for
       more information.
-> Kernel module load error: insmod: error inserting './usr/src/nv/nvidia.ko':
   -1 No such device
"


Does it mean that ubuntu cannot find the device? 
Where can I find the nvidia.ko file?
Any suggestions of how to resolver this problem?

Thanks in advance.

The whole error message is as following:
[/FONT][FONT='PrimaSans BT,Verdana,sans-serif']-> Kernel messages:
   [  139.506015] ACPI: PCI Interrupt 0000:0a:00.0[A] -> GSI 16 (level, low) ->
   IRQ 16
   [  139.506023] NVRM: request_mem_region failed for 16M @ 0xfb000000. This
   can
   [  139.506024] NVRM: occur when a driver such as rivatv is loaded and claims
   [  139.506025] NVRM: ownership of the device's registers.
   [  139.506029] nvidia: probe of 0000:0a:00.0 failed with error -1
   [  139.506043] NVRM: The NVIDIA probe routine failed for 1 device(s).
   [  139.506045] NVRM: None of the NVIDIA graphics adapters were initialized!
   [  198.628283] mtrr: type mismatch for f9c00000,200000 old: write-back new:
   write-combining
   [  198.628293] mtrr: type mismatch for f9800000,400000 old: write-back new:
   write-combining
   [  198.628299] mtrr: type mismatch for f9000000,800000 old: write-back new:
   write-combining
   [  453.278900] NVRM: request_mem_region failed for 16M @ 0xfb000000. This
   can
   [  453.278901] NVRM: occur when a driver such as rivatv is loaded and claims
   [  453.278902] NVRM: ownership of the device's registers.
   [  453.279085] nvidia: probe of 0000:0a:00.0 failed with error -1
   [  453.279128] NVRM: The NVIDIA probe routine failed for 1 device(s).
   [  453.279129] NVRM: None of the NVIDIA graphics adapters were initialized!
   [  469.233689] mtrr: type mismatch for f9c00000,200000 old: write-back new:
   write-combining
   [  469.233698] mtrr: type mismatch for f9800000,400000 old: write-back new:
   write-combining
   [  469.233705] mtrr: type mismatch for f9000000,800000 old: write-back new:
   write-combining
   [  816.111257] NVRM: request_mem_region failed for 16M @ 0xfb000000. This
   can
   [  816.111259] NVRM: occur when a driver such as rivatv is loaded and claims
   [  816.111264] NVRM: ownership of the device's registers.
   [  816.111269] nvidia: probe of 0000:0a:00.0 failed with error -1
   [  816.111275] NVRM: The NVIDIA probe routine failed for 1 device(s).
   [  816.111276] NVRM: None of the NVIDIA graphics adapters were initialized!
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

[/FONT]

---

### Post by mgranet on 2009-07-15
Those are some pretty confusing directions.

To make it simple: Search for and uninstall anything named 'nvidia' in your package manager. Now, download the latest .run if you don't have it already from the Nvidia website: 
[http://us.download.nvidia.com/XFree86/Linux-x86_64/185.18.14/NVIDIA-Linux-x86_64-185.18.14-pkg2.run](http://us.download.nvidia.com/XFree86/Linux-x86_64/185.18.14/NVIDIA-Linux-x86_64-185.18.14-pkg2.run)

Next, move the .run into your home directory. Reboot. At the login screen, Press CTRL-ALT-F1. This will take you to the console. Log in, then: ```
sudo sh NVIDIA-Linux-x86_64-185.18.14-pkg2.run

```

Reboot.

---

### Post by bestsword on 2009-07-15
Hi Mgranet,

Thank you very much for your response.
I have tried removing all nvidia* packages, and reinstall the newest nvidia driver.
However, the problem is still there.
According to the error message, I think there is something missing, the 
nvidia.ko file is not found. I even doubt whether ubuntu has successfully 
identify the nvidia card. Is there any way to check whether ubuntu successfully 
identify the card?
Thanks.

---

### Post by philinux on 2009-07-15
It could be 8.04, the kernel it uses and the version of gcc.

Is the nvidia-glx-... driver in 8.04 not working?

---

### Post by oldos2er on 2009-07-15
Do you have source repositories enabled?

---

### Post by dabl on 2009-07-15
Did you

```
sudo apt-get update && sudo apt-get install linux-headers-`uname -r` build-essential
```

?

---

### Post by bestsword on 2009-07-15
To philinux: Yes, I have tried nvidia-glx-new. It can be installed. However, it will result in the problem that the system complains about it needs to be run under lower resolution mode. So I think I still need to install the newest nvidia driver.


To oldos2er: What do you mean by having source repositories enable__d? I am running the command by sudo, so I think I can have the authority of any directories and any files.

To dabl: Yes. I have installed the headers with the correct distribution version.

---

### Post by punkybouy on 2009-07-15
Install EnvyNG which I think is in the repositories.  After install run it and it will do all the "heavy lifting".  Mine was in Applications\System Tools.

---

### Post by JDShu on 2009-07-16
So you get that error message while you run: sudo sh NVIDIA-Linux-x86_64-185.18.14-pkg2.run ?

---

### Post by huntzire on 2009-07-16
I used to get that error when I was starting out compling kernels, I found out you must have the most recent version of the Nvidia installer script for the kernel and have it match the GCC.

---

### Post by oldos2er on 2009-07-16
> **bestsword said:**
> 
To oldos2er: What do you mean by having source repositories enabled? I am running the command by sudo, so I think I can have the authority of any directories and any files.
 

 Check System, Administration, Software Sources, make certain the box next to 'Source code' is checked.

---

### Post by bestsword on 2009-07-16
To punkybouy: EnvyNG will install nvidia-glx version 173. It is not the latest release of the nvidia driver. Thanks anyway.

To JDShu: Yes. You are right. 

To huntzire: I have tried both gcc4.1 and gcc4.2. None of them work.

To oldos2er: Thanks. The boxed is not checked. But after I checked it, the error is still there.

When I google the error message, some people said that this kind of error message means that my motherboard cannot access the nvidia card correctly. Any feedback on this comment?
Thanks.


__

---

### Post by GeekGirl1 on 2009-07-16
GTX 280 here also. Have you tried to install the PPA repository 185.18.14 drivers? There could be some subtle problems that the script can't handle. I had lots of problems until I used Synaptic to install the drivers. It even enabled the proprietary driver support and got Open GL running. Try this: [http://ubuntuforums.org/showpost.php?p=7590748&postcount=917](http://ubuntuforums.org/showpost.php?p=7590748&postcount=917)

---

