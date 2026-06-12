---
title: "Hard Freeze in Ubuntu Breezy on AMD 64"
date: 2006-05-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by Jonathan Knowles on 2006-05-07
Hi everyone

I've been using Ubuntu Breezy AMD64 on both my work and home desktops for several months now. I've set up both machines identically.

However, my home desktop often (and unpredictably) enters into a hard freeze, where the only way of fixing the problem is to do a hard reset. The time between each hard freeze can vary dramatically, so sometimes the machine can go several days without freezing, and then sometimes it freezes several times a day.

For some reason, the freezes happen more often, while I'm using Mozilla Firefox. My Firefox installation is within a 32-bit chroot environment. However this is not the only thing causing a freeze because the freezes also happen when I'm using normal 64-bit apps too.

I've done several things to try and diagnose the freezing:

[LIST]
[*]I've run memtest for over 48 hours, but this shows up no problems.
[*]I've checked through some of the log files in /var/log, but I can't see anything unusual that might be causing the lockups (but I'm really not expert enough to know what to look for).
[*]I've periodically checked the processor's temperature, which at full load is about 45-50 degrees centigrade.
[*]I've left the case running open in case there are any other temperature related issues.
[/LIST]

The problem is that nothing I do seems to fix the problem. Could anyone point me in the right direction about how to make a diagnosis?

Many thanks!

Jonathan

---

### Post by gborzi on 2006-05-07
I've had the same problems with an amd64 processor + MB ASrock 939M-56 + Videocard nvidia GeForce 6200 TurboCache + 4 memory combinations:
2 x 512 MB;
3 x 1GB;
2 x 1GB;
4 x 1GB;
The worst behavoiur was with 3 x 1GB, with hard freezes and boot problems. The best one is the 4 x 1GB. The 2 x configurations were stable too, but not as stable as 4 x 1GB. Check in the BIOS if there is some option to put the CPU on sleep/wait etc and disable it. On my amd64 there isn't such option, or I didn't find it, but on another system this solved the problem.
On the software side, I improved the stability by:
updating the kernel to 2.6.15 from the default breezy 2.6.12 kernel;
disabling composite extensions and RenderAccel in xorg.conf;
The freeze I fixed modifying xorg.conf were not hard freezes, I was able to login from another PC. It was an X window freeze (damned closed source nvidia drivers problem).

Regards.

---

### Post by tseliot on 2006-05-07
[QUOTE=Jonathan Knowles]Hi everyone

I've been using Ubuntu Breezy AMD64 on both my work and home desktops for several months now. I've set up both machines identically.

However, my home desktop often (and unpredictably) enters into a hard freeze, where the only way of fixing the problem is to do a hard reset. The time between each hard freeze can vary dramatically, so sometimes the machine can go several days without freezing, and then sometimes it freezes several times a day.

For some reason, the freezes happen more often, while I'm using Mozilla Firefox. My Firefox installation is within a 32-bit chroot environment. However this is not the only thing causing a freeze because the freezes also happen when I'm using normal 64-bit apps too.

I've done several things to try and diagnose the freezing:

[LIST]
[*]I've run memtest for over 48 hours, but this shows up no problems.
[*]I've checked through some of the log files in /var/log, but I can't see anything unusual that might be causing the lockups (but I'm really not expert enough to know what to look for).
[*]I've periodically checked the processor's temperature, which at full load is about 45-50 degrees centigrade.
[*]I've left the case running open in case there are any other temperature related issues.
[/LIST]

The problem is that nothing I do seems to fix the problem. Could anyone point me in the right direction about how to make a diagnosis?

Many thanks!

Jonathan[/QUOTE]
That might be a kernel issue, i.e. incompatibility.

Can you post the model of your motherboard and graphic card?

---

### Post by Jonathan Knowles on 2006-05-07
Hello again.

My motherboard is a MSI K8T Neo-FIS2R Version 1.0.
My graphics card is a nVidia Geforce 3.

In case it helps, here is the output of lspci:

```

0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8385 [K8T800 AGP] Host Bridge (rev 01)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800 South]
0000:00:08.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
0000:00:08.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 07)
0000:00:0a.0 Multimedia controller: Philips Semiconductors SAA7146 (rev 01)
0000:00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
0000:00:0e.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
0000:00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
0000:00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [K8T800 South]
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:00.0 VGA compatible controller: nVidia Corporation NV20 [GeForce3] (rev a3)

```

Cheers

Jonathan

---

### Post by Clock Sabre on 2006-05-07
That's exactly the problem I've been having with my own desktop with an AMD64 processor. Jon, do you also get lines that appear randomly inside the firefox window?

---

### Post by Jonathan Knowles on 2006-05-13
[QUOTE=Clock Sabre]That's exactly the problem I've been having with my own desktop with an AMD64 processor. Jon, do you also get lines that appear randomly inside the firefox window?[/QUOTE]

Hi Clock Sabre

No, I've not had lines appearing inside the Firefox window.

Though I *have* noticed that the machines crashes more frequently when using firefox - which is installed as a 32-bit app within a 32-bit chroot environment. (I do this because its very easy to install 32-bit firefox plugins this way).

Does anyone have any ideas as to why this might happen?

Thanks again
Jonathan

---

### Post by brt on 2006-06-11
[QUOTE=Jonathan Knowles]
0000:00:0a.0 Multimedia controller: Philips Semiconductors SAA7146 (rev 01)
[/QUOTE]


i have the same dvb-s card and i was told that i need at least kernel 2.6.16 to make this card work. 

i followed this Howto :

[http://ubuntuforums.org/showthread.php?t=157560&highlight=2.6.16]("http://ubuntuforums.org/showthread.php?t=157560&highlight=2.6.16")

now all the modules for this card get loaded at startup (budget_av,... etc.) but dmesg still gives me:
```
[4294684.590000] videodev: "SAA7146A" has no release callback. Please fix your driver for proper sysfs support, see http://lwn.net/Articles/36850/

```

but the dvb-device-files are missing and even when i make dem manually, i get: cat: /dev/dvb/adapter0/dvr0: No such device (the devicefile /dev/dvb/adapter0/dvr0 exists)

still messing around with this, but its solid without any lockups.

---

### Post by brt on 2006-06-18
i got it to work, i only had to blacklist the module stradis, i don't know why its been loaded or what it's for, but it works great now :D
all the needed modules are being loaded and the devicefiles are created automatically

---

### Post by Jonathan Knowles on 2006-08-06
Thanks for your help everyone.

I recently upgraded to Dapper Drake - as a result it seems the hard freezing has disappeared... :-? 

However, I'm going to look further into incompatibilities with the DVD-B card.

Cheers

Jonathan

---

