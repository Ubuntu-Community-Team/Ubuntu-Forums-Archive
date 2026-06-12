---
title: "64-bit karmic .. can't get webcam working..."
date: 2009-11-04
forum: x86 64-bit Users
---

### Post by xlberz on 2009-11-04
hi, this is my first time posting so please bear with me if I didn't follow a rule correctly.

I tried setting up a Logitech C500 webcam, which is registered at [http://www.quickcamteam.net/devices](http://www.quickcamteam.net/devices) as a supported Linux UVC device.

Plugged it in with the assumption that it would just work, but nope, didn't work. So I checked to see if it was being seen by lsusb:

Bus 004 Device 002: ID 046d:c526 Logitech, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 003: ID 413c:2010 Dell Computer Corp. 
**Bus 006 Device 004: ID 046d:0807 Logitech, Inc. **
Bus 006 Device 002: ID 413c:1003 Dell Computer Corp. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0917:0207 SmartDisk Corp. FireLite
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Yep. It's right there. I tried skype, cheese, ekiga ... no device found.

tried gstreamer-properties to see what I could see ... tried to test for v4l2 got the following error:

Video for Linux 2 (v4l2): Cannot identify device '/dev/video0'.

i've tried to follow all the tutorials and howtos... but this is something that I just cant figure out. tried to use easycam too, but can't isntall it because python-xml was removed from karmic. I'm completely stumped.

here's my lspci:

```

00:00.0 Host bridge: Intel Corporation X58 I/O Hub to ESI Port (rev 12)
00:01.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 1 (rev 12)
00:03.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 3 (rev 12)
00:07.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 7 (rev 12)
00:14.0 PIC: Intel Corporation 5520/5500/X58 I/O Hub System Management Registers (rev 12)
00:14.1 PIC: Intel Corporation 5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers (rev 12)
00:14.2 PIC: Intel Corporation 5520/5500/X58 I/O Hub Control Status and RAS Registers (rev 12)
00:14.3 PIC: Intel Corporation 5520/5500/X58 I/O Hub Throttle Registers (rev 12)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 1
00:1c.2 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 3
00:1c.3 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 4
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 5
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller
02:00.0 VGA compatible controller: ATI Technologies Inc RV730 PRO [Radeon HD 4650]
02:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]
04:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 AHCI Controller (rev 03)
04:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 AHCI Controller (rev 03)
05:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. Device 3403
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

```
if anyone has any insight on this I would very much appreciate it. thank you!

---

### Post by trpnblies7 on 2009-11-04
I'm having this exact same problem since upgrading to Karmic, but I've yet to find a solution. My camera will only run as root, and I don't know why. If I open cheese, nothing happens, but if I "sudo cheese" or sudo any other camera program, it works.

---

### Post by xlberz on 2009-11-05
yeah at this point I can't even sudo cheese ... nothing.

---

### Post by xlberz on 2009-11-05
this is what gstreamer-properties spits out at me:

```
 Cannot identify device '/dev/video0'. [v4l2_calls.c(482): gst_v4l2_open (): /GstPipeline:pipeline0/GstV4l2Src:v4l2src3:
system error: No such file or directory]
gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Device "/dev/video0" does not exist. [v4l_calls.c(168): gst_v4l_open (): /GstPipeline:pipeline1/GstV4lSrc:v4lsrc2]
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Cannot identify device '/dev/video0'. [v4l2_calls.c(482): gst_v4l2_open (): /GstPipeline:pipeline2/GstV4l2Src:v4l2src5:
system error: No such file or directory]

```

---

### Post by sanderj on 2009-11-05
Does (a live-boot of) Ubuntu 9.10 32-bit resolve this webcam issue?

Does (a live-boot of Ubuntu) 9.04 32/64-bit resolve this webcam issue?


If once or twice YES, I would register a bug on Launchpad.

---

### Post by xlberz on 2009-11-05
works now. I moved the camera to a different USB port. 

Oddly enough, the port I was trying to use the camera with now works with my USB mouse. strangeness.

---

