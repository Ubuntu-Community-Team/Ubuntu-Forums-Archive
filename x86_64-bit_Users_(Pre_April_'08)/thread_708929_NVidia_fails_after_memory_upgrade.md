---
title: "NVidia fails after memory upgrade?"
date: 2008-02-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by Tailkinker on 2008-02-26
So I had 7.10 running smooth, and then acquired a 2GB stick of RAM.  Popped it in, pulled out the 1GB I had in the box at the time, and started up.  The NVidia driver did not load, and I was stuck in crappy VESA mode.

I've tried everything short of pulling the RAM, and may yet try that.  Anyone got a better suggestion?

The machine is an AMD64 with DDR2 667 (currently 2GB, but the 1GB stick was otherwise identical), NVidia GeForce 7300.

---

### Post by dcstar on 2008-02-27
> **Tailkinker said:**
> So I had 7.10 running smooth, and then acquired a 2GB stick of RAM.  Popped it in, pulled out the 1GB I had in the box at the time, and started up.  The NVidia driver did not load, and I was stuck in crappy VESA mode.

I've tried everything short of pulling the RAM, and may yet try that.  Anyone got a better suggestion?

The machine is an AMD64 with DDR2 667 (currently 2GB, but the 1GB stick was otherwise identical), NVidia GeForce 7300.

Possibly your motherboard now uses "real" address space that the Nvidia card was configured to use in Linux, you should probably run the reconfigure procedure.

Also, if you had added an identical 1GB stick into the correct slot, your CPU would be accessing the DDR2 RAM in a faster mode than a mixed (or single) setup.

---

### Post by Tailkinker on 2008-02-27
Unfortunately, I've tried the nvidia-xconfig program (failed), re-installing the driver using Envy (refused to even try), re-installing the driver using the Restricted Drivers Manager (failed), manually re-installing the latest driver (found a new symptom - no text consoles at all, so I couldn't do this one), re-installing the driver from Synaptec (failed), running nvidia-settings (didn't detect the driver, possibly because it's not loading), manually inserting the kernel driver (couldn't find it!), selecting the nvidia driver from "Screens and Graphics Preferences" (alternates between failure, and killing X with no terminal fallback), running nvidia-glx-config (failed), and running an activation script I found elsewhere in the forums (failed).  Did I miss anything?

The Restricted Drivers Manager shows that the driver is selected but disabled.

Here's my lspci:
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc Unknown device 7913
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7300 GS] (rev a1)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 20)
03:00.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)
03:00.1 Input device controller: Creative Labs SB Live! Game Port (rev 08)
03:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
03:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

My /proc/version:
Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Tue Feb 12 05:41:34 UTC 2008


And, in case it matters, my /proc/cpuinfo:
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 95
model name      : AMD Athlon(tm) 64 Processor 4000+
stepping        : 3
cpu MHz         : 1000.000
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up pni cx16 lahf_lm svm cr8legacy ts fid vid ttp tm stc
bogomips        : 2044.46
clflush size    : 64

---

### Post by Yellow Pasque on 2008-02-27
Hmm, you could perhaps try using your integrated video and disabling your video card in the BIOS. Reboot. Then switch it back around and try again.

EDIT: You could also try clearing the CMOS or upgrading your BIOS if there's an update available.
EDIT2: What mobo do you have? Does it support 2GB sticks?

---

### Post by Tailkinker on 2008-02-27
I manually killed X and GDM, then ssh'ed in from another machine, since this machine was failing to provide terminals.  I manually installed the latest NVidia drivers, and poof!  It worked!

---

### Post by dcstar on 2008-03-05
> **Tailkinker said:**
> Unfortunately, I've tried the nvidia-xconfig program (failed), re-installing the driver using Envy (refused to even try), re-installing the driver using the Restricted Drivers Manager (failed), manually re-installing the latest driver (found a new symptom - no text consoles at all, so I couldn't do this one), re-installing the driver from Synaptec (failed), running nvidia-settings (didn't detect the driver, possibly because it's not loading), manually inserting the kernel driver (couldn't find it!), selecting the nvidia driver from "Screens and Graphics Preferences" (alternates between failure, and killing X with no terminal fallback), running nvidia-glx-config (failed), and running an activation script I found elsewhere in the forums (failed).  Did I miss anything?
........

I would have suggested **dpkg-reconfigure xserver-xorg** myself, but since that probably happened (one way or the other) after you solved it after installing the new driver, then it doesn't matter!

PS, please mark the thread as solved.

---

