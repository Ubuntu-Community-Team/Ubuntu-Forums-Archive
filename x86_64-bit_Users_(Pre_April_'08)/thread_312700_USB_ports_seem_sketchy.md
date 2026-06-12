---
title: "USB ports seem sketchy"
date: 2006-12-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by Nachtengel on 2006-12-04
Running 64 bit Dapper on an Asus A8N SLI Deluxe, and the usb ports seem rather fineky... my digital camera will work, but my mp3 player and my usb sticks do not seem to work.  Commands like ```
lsusb
``` seem to hang the system.  As I am still rather new to the magic of hardware compatibility in linux, does anyone have any advice they can offer to get my peripherals working?

(All these peripherals ran on another PC running Breezy, so it's not the perhipheral's fault it would seem)

---

### Post by kuja on 2006-12-05
Sounds like a kernel-related issue to me. Perhaps you should try edgy, the problem might not be present in Edgy's newer kernel.

Then again, the problem could be related to your computer's motherboard, possibly.

---

### Post by handband2 on 2006-12-05
> **Nachtengel said:**
> Running 64 bit Dapper on an Asus A8N SLI Deluxe, and the usb ports seem rather fineky... my digital camera will work, but my mp3 player and my usb sticks do not seem to work.  Commands like ```
lsusb
``` seem to hang the system.  As I am still rather new to the magic of hardware compatibility in linux, does anyone have any advice they can offer to get my peripherals working?

(All these peripherals ran on another PC running Breezy, so it's not the perhipheral's fault it would seem)

Nachtengel,

I have a A8N-VM and ran into the same problem with the usb ports.  I finally to everything working when I changed from **HiSpeed** to **FullSpeed** in the BIOS.

```
Advanced -> USB Configuration -> USB 2.0 Controller Mode -> FullSpeed
```

---

### Post by Nachtengel on 2006-12-25
Well the bios fix hasn't worked exactly.  Still kind of a hit or miss proposition when I connect a USB device.  

lsusb works now... but only shows 2 of a possible 6 ports from my motherboard.  Anyone with the A8N-SLI Deluxe have any experience with this?

---

### Post by Jcarr_toonist on 2007-03-24
I am using an A8N-SLI motherboard with edgy and I am having the exact same problem. lsusb hangs and my usb ports seem to be hit and miss for the most part. 

My usb flash drive seems to work but nothing else does(camera, scanner, webcam, etc) despite all these device working wonderfully on my old motherboard. 

Also the entire system wouldn't boot up at all when I have my Logitech communicate STX webcam plugged in.  

I was unable to try the bios fix because I have a different bios which doesn't provide the fullspeed/hi-speed options. Instead I have a choice between legacy and usb2.0 enabled or disabled.

---

