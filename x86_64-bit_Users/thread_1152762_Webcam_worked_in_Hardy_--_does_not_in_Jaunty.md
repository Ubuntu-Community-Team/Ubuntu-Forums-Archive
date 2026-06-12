---
title: "Webcam worked in Hardy -- does not in Jaunty"
date: 2009-05-08
forum: x86 64-bit Users
---

### Post by ScottyPDX on 2009-05-08
I have a Creative Webcam that worked when I plugged it in using Hardy Herron AMD64. Now I tried the same webcam with Jaunty and it doesn't work. It doesn't even acknowledge a webcam exists. It thinks it's an Omnivision in the lsusb printout, but I've tried installing the OV511 package, still nothing. I've tried using MAKEDEV, but I get an error:
.udevdb or .udev presence implies active udev.  Aborting MAKEDEV invocation.
I'm going nuts trying to get this thing working. Anyone have a suggestion? My lsusb is:
Bus 001 Device 008: ID 15a9:0004  
Bus 001 Device 007: ID 1058:0705 Western Digital Technologies, Inc. 
Bus 001 Device 006: ID 0bda:0111 Realtek Semiconductor Corp. Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 005: ID 03f0:0711 Hewlett-Packard OfficeJet K80
Bus 002 Device 004: ID 1784:0006 TopSeed Technology Corp. 
Bus 002 Device 003: ID 05a9:a511 OmniVision Technologies, Inc. OV511+ WebCam
Bus 002 Device 002: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Thank you.

---

### Post by cariboo on 2009-05-08
Things have changed since Hardy as far as webcam drivers are concerned. Have you checked to see if the driver for your webcam is already loaded? Open a terminal and type:

```
lsmod | grep ov511
```

if you don't get any results from the above command, try and load the module manually:

```
sudo modprobe ov511
```

You could also check dmesg to see if your webcam is detected on boot:

```
dmesg | grep ov511
```

---

### Post by dotdot on 2009-05-08
yeah i know looks like jaunty is non working wrt webcam.

when you plug it in it fails to create /dev/video etc..

think it's been bugged already.

..mm thinking jaunty naff for webcams - anyone got one working...
if so how did you get dev video... ?

---

### Post by Anubis on 2009-05-08
[https://bugs.launchpad.net/ubuntu/+source/libv4l/+bug/260918]("https://bugs.launchpad.net/ubuntu/+source/libv4l/+bug/260918"):(

---

