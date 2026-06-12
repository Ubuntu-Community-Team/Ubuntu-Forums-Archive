---
title: "dmesg ck804xrom_init_one(): . . kernel bug?"
date: 2007-12-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by Elle Stone on 2007-12-22
Hi, all

I am a long-time windows user (since 1985), switching to linux to take advantage of 64-bit computing, as vista seems entirely inappropriate (that whole drm, privacy-invading, resource-hog thing it seems to have going for itself).  

After some experimenting with different linux distributions, I recently installed Ubuntu Gutsy command line install, from a netCD ([https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)).  I added xorg, icewm, xfe, the nvidia driver, etc, to make a lightweight desktop environment (as few services as possible running in the background using up ram and cpu cycles).  

My system (now three years old, and built to be a number-cruncher for digital imaging) is:
Tyan k8we (s2895) dual opteron mainboard, with only one cpu, Opteron 252, installed
4 gb ram
2 wd raptors 74gb (not raided) + 1 seagate 120gb sata II
nvidia 7600gt graphics card

The k8we uses the nvidia nforce Professional 2200 chipset, which is the "CK804" that pops up repeatedly in dmesg.

My question:

The computer boots and seems to run normally.  However, (right after the part where the hard drives are detected) dmesg shows the following:

[  128.568191] ck804xrom ck804xrom_init_one(): Unable to register resource 0x00000000ffb00000-0x00000000ffffffff - kernel bug?
[  128.652353] CFI: Found no ck804xrom @ffc00000 device at location zero
[  128.692045] i2c-adapter i2c-0: nForce2 SMBus adapter at 0xa000
[  128.692068] i2c-adapter i2c-1: nForce2 SMBus adapter at 0xa040

after which the following lines are repeated over and over again:

[  128.773255] JEDEC: Found no ck804xrom @ffc00000 device at location zero
[  128.773313] CFI: Found no ck804xrom @ffc00000 device at location zero
. . .
[  128.829663] JEDEC: Found no ck804xrom @fff00000 device at location zero
[  128.829685] CFI: Found no ck804xrom @fff00000 device at location zero

and then finally it says 

[  128.829731] Found: SST 49LF080A
[  128.829739] ck804xrom @fff00000: Found 1 x8 devices at 0x0 in 8-bit bank
[  128.932070] number of JEDEC chips: 1
[  128.932073] cfi_cmdset_0002: Disabling erase-suspend-program due to code brokenness.
. . .

and finishes up booting.  The whole boot process doesn't take very long.  But I'm curious, and  I'm hoping that whatever is making the boot process unhappy doesn't affect performance (working with 500mb to 1gb size files).  

Should I file a bug report with Ubuntu? 

Perhaps it is maybe cd-dvdrom related? - I haven't tried to burn a CD yet.  

Or  related to drive IO speed?  sudo hdparm -tT /dev/sda (one of the raptors) shows

 Timing cached reads:   2324 MB in  2.00 seconds = 1161.56 MB/sec
 Timing buffered disk reads:  206 MB in  3.02 seconds =  68.25 MB/sec

which seems reasonable based on what I've found in the Ubuntu forums, but I don't really know for sure - I'd like IO speed to be as fast as possible of course!   

Or perhaps there's not even a problem here at all, just Ubuntu boot process catching up with itself, so to speak?

Thanks! for any input and advice as to whether there is a problem here that needs to be addressed.  

Elle

---

### Post by Ehtetur on 2007-12-24
It's a known issue with the nvidia nforce driver trying to initialize SATA drives on x64_86 servers with 4GB or more of memory. If updating Ubuntu doesn't also update nforce,  you may want to check out nvidia's website.

BTW. 3 yrs ain't old for a server... :twisted:
There's still a 5 yr old IBM x series at work running mission critical apps.

---

### Post by Elle Stone on 2007-12-29
Thanks very much for responding.  I am not sure what might need upgrading.  According to "uname -a", I am running "Linux rn 2.6.22-14-generic . . . x86_64 Gnu/Linux".  There is an upgrade available, but it is just to a later verion of 2.6.22-14.

The kernel is the one "geared toward desktop".  I'm not running a server, rather a stand-alone graphics desktop/workstation.  The only difference I could find between the two kernels, server or desktop, was the kind of prioritization given to I/O requests (see [http://www.serverwatch.com/tutorials/article.php/3715071](http://www.serverwatch.com/tutorials/article.php/3715071)).  So I chose the desktop kernel.

The other kind of update that I've run across that might make a difference is from Nvidia (see [http://www.nvidia.com/object/linux_nforce_1.21.html](http://www.nvidia.com/object/linux_nforce_1.21.html)).  The latest update to ethernet, audio, sata, etc is January 2007, and only "supported" for redhat and suse, though source is available.  But the Nvidia website says that for the various *nix installations, "all of the . . .  drivers are open-source and are included in most popular Linux distributions. In most cases, the Linux installer will select the appropriate driver for the detected nForce hardware."  So very likely Ubuntu 7.10 already has the latest drivers incorporated, unless they are adverse to including anything from Nvidia. but the drivers are all open-source.

Anyway, thanks again for letting me know that the issue is perhaps not so important.  

Elle

---

