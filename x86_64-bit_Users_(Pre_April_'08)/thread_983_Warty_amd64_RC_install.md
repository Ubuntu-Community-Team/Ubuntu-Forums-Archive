---
title: "Warty amd64 RC install"
date: 2004-10-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by dmatrix on 2004-10-17
Some experiences and bugs.

Hardware:
Asus K8V SE deluxe
1 gig ddr
nvidia geforce ti4200
orinoco_pci wireless
3com 100mbit wired
onboard sound

- On install parted said one of my ext3 partition was ext2 and couldn't resize it. Selecting 'Do not touch partition' made it through.

- On install with an orinoco_pci card when downloading software from internet on install complains over and over 'Error -110 writing Tx descriptor to BAP'. 'New link status: AP Out of Range (0004)' 'AP In Range (0005)'. This happened in the preview release of Warty on my system and spammed the console while installing. One time while installing Warty this actually got stuck in a loop effectivley disabling the console and forcing a reset.

- On bootup Hardware clock cannot be set. Complains to try with --debug. Warty X86 preview set the clock fine. But Warty AMD64 preview or RC says that it cannot. This can be seen on the initial bootup.

- Uses 'nv' driver by default with my Nvidia hardware. I have TV output on my card using S-Video. The 'nv' driver does not like this and makes a mess of the screen. Disconnecting the S-Video cable brings up the 'nv' driver fine with settings I used on install.

- 'nv' driver defaults my system to 1024x768 @60hz. Which is awful and flickery. The Screen Resolution application has no more options for my system. With the nvidia driver I use 1024x768 @85hz Why is the nvidia driver not installed and setup by default? as well monitor detection seems buggered.

- Had to CTRL-ALT-F1 to console. apt-get install linux-amd64-k8 linux-restricted-modules-amd64-k8 nvidia-glx nvidia-settings. I probably could have installed the amd64-generic restricted-modules but I wanted the amd64-k8 kernel anyways.

- Edited /boot/grub/menu.lst as noted in another thread. I have an ASUS K8V SE Deluxe motherboard that appears to require these options in the menu.lst to avoid DMA hangup issues. At the end of the kernel line I placed these options 'noapic pci=usepirqmask'. Reboot.

- Looks like after a reboot the nvidia driver was not setup properly. I had to edit /etc/X11/XF86Config-4 and add in the usual nvidia glx driver stuff. I also had to add the nvidia driver to the /etc/modules file. Screen Refresh still @60hz and awful. Copied my old XF86Config-4 into place and restarted GDM.

- Annoying bug. /usr/X11R6/lib32 libGL and libGLU were still using Mesa libs. This can be seen easily by running a 32 bit game like Neverwinter Nights or Doom3. Textures will be corrupted and messed up, as well GL will seem slower than it should.

---

### Post by code on 2004-10-18
I've run into a few problems testing out Warty on a dual Opteron system:

Tyan S2885 Thunder K8W
2x AMD Opteron 250
4 GB DDR
IBM 40 GB IDE disk
3Ware SATA-RAID (3w_9xxx)
2x 120 GB SATA disks (as seperate volumes, no RAID)
NVidia Quadro 980 XGL
Broadcom GigE onboard

1. When grub tries to load a kernel into memory, it will claim that there is not enough memory free (obviously this is not the case.) If I manually specify "uppermem" with some number (like 1024000 kB) it will boot fine. I've been told this doesn't happen on this machine with Fedora Core 2 or SUSE 9, but haven't tried myself.

2. The kernel included with the installer (2.6.8.1-2-amd64-generic) doesn't seem to be in the warty package archive. The newest is 2.6.7-5ubuntu3--which doesn't support my 3Ware controller. The generic 2.6.8.1 kernel doesn't have SMP enabled. I couldn't even find the kernel as a deb package anywhere on the install CD (Edit: I didn't realize the kernel packages were linux-amd64... rather than kernel-image-...)

3. Fancy USB storage device auto-mounting doesn't work (It's not mounted and no icon shows up on the desktop like the i386 release, but dmesg shows that the device is recognized when I plug it in.)

And of course, I got weird looks in my office when GDM started up with the default theme. ;)

---

### Post by Solar Hydro on 2004-10-31
Hello,

Install failed, with the following message:

"Debootstrap exited with an error (return value 1). Check /var/log/messages or see virtual console 3".

Didn't find any messages. Retried several times to no avail.

System:

AMD Athlon FX-53
MSI K8N Neo2-54G (WiFi card not installed)
ATi X800XT 256 Mb
1 Gb DDR
WD Raptor (used for WinXP)
Seagate ST (used for Linux)
nForce 3 and RealTek GigE
onboard sound 

Suggestions are welcome. I'm a Linux noob (but did run the Ubuntu LiveCD successfully on my other computers)

Solar Hydro

---

### Post by mistic on 2005-01-01
[QUOTE=dmatrix]Some experiences and bugs.

Hardware:
Asus K8V SE deluxe
1 gig ddr
nvidia geforce ti4200
orinoco_pci wireless
3com 100mbit wired
onboard sound
[/QUOTE]

can you please post your menu.lst from grub or explain how exactly you fixed the grub problem ?

would be really helpfull....

grtz
mistic

---

### Post by dmatrix on 2005-01-21
I am running Hoary now and last time I checked with the 2.6.9 kernel this bug was still present with my motherboard. I have not tested it on 2.6.10 yet. Quite an annoying bug and makes the system unusable under even somewhat heavy loads.

Here is the line for the latest Hoary kernel in my menu.lst:

title           Ubuntu, kernel 2.6.10-2-amd64-k8 Default
root            (hd0,2)
kernel          /boot/vmlinuz root=/dev/hda3 ro console=tty0 quiet splash noapic pci=usepirqmask
initrd          /boot/initrd.img
savedefault
boot


The options I need to apply are 'noapic pci=usepirqmask' at the end of the kernel line. You can make this stick through kernel upgrades in this section in the menu.lst.


## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash noapic pci=usepirqmask

---

