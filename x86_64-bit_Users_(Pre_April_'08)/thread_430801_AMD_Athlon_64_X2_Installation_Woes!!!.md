---
title: "AMD Athlon 64 X2 Installation Woes!!!"
date: 2007-05-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by creolbuay on 2007-05-02
Hi all.  I have setup and ran several Linux boxes before. I currently built myself a dualcore amd64 am2 system to which I will post the specs for. I have tried all Ubuntu releases and get the same errors.

This is my problem:
During install I get the all familiar apic error. I use the "noaicp nolaicp acip=off aicp=off" option which gets the installation going, it completes and when it reboots it gives me the same error. I edited the /boot/grub/menu.lst file to add the options but it still hangs right after it loads fan monitoring stuff (I have that disabled in the bios). 

I kept reading posts that start with I imagine/bet you burned the image at 4x. Is there a special speed to burn the images at?

Here are my specs:
AMD Athlon 64 X2 3600+ Brisbane 1.9GHz 2 x 512KB L2 Cache Socket AM2 Processor
Western Digital Caviar SE16 WD4000KS 400GB 7200 RPM SATA 3.0Gb/s Hard Drive
ASUS M2N32-SLI Deluxe Wireless Edition Socket AM2 NVIDIA nForce 590 SLI MCP ATX AMD Motherboard
OCZ Gold 512MB 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400) total ram: 1.5 Gigs
BIOSTAR V6202EL16 GeForce 6200 LE 256MB TurboCache(128M VRAM on board) GDDR2 PCI Express x16

---

### Post by calraith on 2007-05-02
The only option you need is "acpi_use_timer_override," not the big long list of kernel arguments you have there.

I had the same problem on my Gigabyte GA-M57SLI-S4 board (another socket AM2 board with an NVidia chipset).  I pestered Gigabyte until they finally sent me a BIOS with HPET (high precision event timer) support, and I don't have to use any funky kernel strings anymore.

**A. If you are installing fresh...**

For now, though, whenever you perform a fresh installation of any Linux variant, *before the final reboot*, you should Ctrl-Alt-F1 or 2 or whatever you need to do to get to a virtual console.  Activate the console and modify /boot/grub/menu.lst.  Change four lines as indicated below.

[B]B. If you are trying to repair an installation...

[/B]You'll need to boot to your installation CD or to a rescue CD.  Perform the following steps:[LIST=1]
[*]Open a terminal window.
[*]sudo mount -t auto /dev/sda1 /target (or sda5 or sda6 or whatever, salt to taste)
[*]sudo chroot /target /bin/bash
[*]nano -w /boot/grub/menu.lst[/LIST][B]Continue here...

[/B]1. Find and modify the following "defoptions=" line appropriately.  Be sure to leave the defoptions= line commented out!
```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash acpi_use_timer_override
```2. Likewise, modify the "altoptions=" line.  As before, leave "altoptions=" commented out.
```
## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single acpi_use_timer_override
```3 and 4: append "acpi_use_timer_override" to your kernel lines at the bottom of menu.lst.

The reason for inserting that in steps 1 and 2 are because whenever a new kernel or modules are installed, Ubuntu runs update-grub.  The update-grub script parses those commented lines to append default options to kernel strings automatically.  Without them, you pretty much have to boot to a rescue CD to fix menu.lst every time update-grub is run.

Anyway, with menu.lst fixed, do:
```
grub-install /dev/sda
``` (or /dev/hda or /dev/sda1 or whatever is appropriate)

---

### Post by calraith on 2007-05-02
Incidentally, I think you might be confusing a couple of acronyms.  ACPI != APIC.  What's even more confusing is that APIC is a component of ACPI, crudely speaking.

From what I've been able to research about the problem with my Gigabyte board, the problem you are having comes from a bug in the ACPI tables from the nForce2 reference BIOS published by NVidia years ago.  Motherboard manufacturers, apparently including Asus and Gigabyte, have recycled these same buggy ACPI tables from generation to generation of NForce board.  The sad thing is that no reference BIOS published by NVidia since then has had this bug.  If you're interested in contacting ASUS to try to get the BIOS fixed, I think all that needs to happen is HPET needs to be enabled / activated / supported / whatever.

Although I don't think that entirely fixes all hardware issues for me.  qemu + kqemu works for me now, but didn't before HPET was enabled.  However, kvm and VirtualBox both freeze when a VM is initialized, I'm guessing when the VM tries to access the physical processor's specialized instruction set for virtualization.  I've got a ticket open with the InnoTek guys for VirtualBox, but I'm not terribly optimistic of resolution on the software side.

---

### Post by creolbuay on 2007-05-02
Hi, 

Thanks for the reply. I added the line like you said for the initial install process but it got stuck after it did a floppy drive search.  I finally got it installed but same problem. I contacted ASUS and was told that they do have a bios upgrade that specifically targeted the problems with linux as well as other issues (M2N32-SLI Deluxe BIOS 0706) . I am installing it as I write.. :-\"  Will let you know how that went..

---

### Post by creolbuay on 2007-05-02
:guitar: \\:D/   The ASUS bios update worked.

---

### Post by popeyeray on 2007-07-12
Can you tell us what it was? I have the ga-m57sli-s4 bios update F9. I was able to get the 7.04 using the 
acpi_use_timer_override

as soon as I boot with the CD, but if gigabyte is issuing a different update, other than the regular old bios flash updates I' d like to know so I can get in on it.

Thanks

---

### Post by vikramgulati88 on 2007-08-03
Hey!

I have an AMD Turion 64 X2 laptop and installing ubuntu x86 (64 bit version) is proving to be a HUGE problem.

When I select the "Start or Install Ubuntu" option two files load followed by a kernel message. Then everything just STOPS. The screen goes blank until I reset the machine. My ISO file is perfect and I don't think there are any problems with the CD as well. 

Is there anything I can do to set this right? Help will be really appreciated....

My system config is :
AMD Turion 64 X2 (TL - 52)
ATI Xpress 1100
1 GB RAM (DDR2)

Vikram.

---

### Post by Lonthong on 2007-08-03
> **vikramgulati88 said:**
> Hey!

I have an AMD Turion 64 X2 laptop and installing ubuntu x86 (64 bit version) is proving to be a HUGE problem.

When I select the "Start or Install Ubuntu" option two files load followed by a kernel message. Then everything just STOPS. The screen goes blank until I reset the machine. My ISO file is perfect and I don't think there are any problems with the CD as well. 

Is there anything I can do to set this right? Help will be really appreciated....

My system config is :
AMD Turion 64 X2 (TL - 52)
ATI Xpress 1100
1 GB RAM (DDR2)

Vikram.

I have a similar laptop as yours.
BenQ P41
Turion X2 TL - 50
Ati Xpress 1100
512 MB RAM

Never ever have any install problem with Dapper, Edgy, & now Feisty - all in 64 bit version.
Could it be just a bad CD? Maybe you can also try the alternate CD

---

### Post by vikramgulati88 on 2007-08-03
nope
I have already tried two different CD's
The same problem happened with Fedora Core 7. (Error : Kernel panic)
Did you use the Ship It CD's or did you download and write the iso file?
Maybe it is a problem with my Wifi or Bluetooth cards.. Do you have that on your PC as well?
Vikram.

---

### Post by vikramgulati88 on 2007-08-03
and I also verified my iso file before writing it...

---

### Post by Lonthong on 2007-08-03
YEs, I have both bluetooth & wireless (atheros ar5006eg) as well.
Dapper & Edgy failed to recognized the atheros card properly. It works out of the box with Feisty.
So far I have no bluetooth device to test.

I got Dapper & Feisty live CD through shipit. Whereas Edgy, I downloaded the alternate install iso.
In case you only tried the live CD version, try to download alternate CD,
Otherwise you should try with all those parameters as suggested by others.

---

### Post by erico on 2007-08-03
I also have an ASUS and X2 CPU. The difference is that mine is s939 with the nForce4 X16SLI chipset. The only difficulty I have ever run into was attempting to use the Alternate Feisty Desktop CD. All other installs have been reasonably smooth, excepting the Wifi networking problem which almost seems to be a norm. When I download the CD or DVD I use the burner programs built into LINUX and not from my Windows partition.

The advise that was given seems solid. ACPI has given me grief on other MOBOS and Linux installs.

---

### Post by vikramgulati88 on 2007-08-03
thanks
I just ordered the Ship It CD's. It should work with that. I'll also download the alternate iso once I'm back at college...
meanwhile, should I try boot parameters like "noacpi" or "nosplash"?
Vikram.

---

