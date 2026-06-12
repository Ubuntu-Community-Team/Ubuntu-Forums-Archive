---
title: "Activating C-State management in BIOS causes random segfaults"
date: 2009-08-09
forum: x86 64-bit Users
---

### Post by mbirth on 2009-08-09
I just built a new desktop PC using a Intel Q9440 Core2 Quad together with a MSI P45 Platinum mainboard.

The mainboard has 5 LEDs to show the current C-State of the CPU. Also there is an option to automatically manage the C-State in the BIOS.

When this option is enabled, I can see that only one of the 5 LEDs is lit and the second one flashes a bit when there's load on the CPU. But in this state, several applications give random segmentation faults. Even a successful "apt-get update" went wrong in the way that there were some "8" characters in the file /var/lib/dpkg/available where a ":" should be, e.g.:

```

Package: qt
Version8 1.0-1

```

Now after turning off the C-state management, all 5 LEDs are lit (i.e. the CPU is running full speed) and everything works as expected.


Is there anybody else with these symptoms?


Cheers,
  -mARKUS

**EDIT:** I searched around and found+installed the BIOS 1.7 BETA 5 for my board. Now the C-state management seems to work fine. I'll play around a bit more, but if you don't read anything more here, it still works. ;-)

---

### Post by Yellow Pasque on 2009-08-10
Make sure your BIOS is updated. I believe this is your board? [http://www.msi.com/index.php?func=downloaddetail&type=bios&maincat_no=1&prod_no=1479](http://www.msi.com/index.php?func=downloaddetail&type=bios&maincat_no=1&prod_no=1479)

The easiest way to update an AMI BIOS with only Linux is to save the file to a FAT16-formatted USB flash drive and use the motherboard's built-in flasher (hit the F12 key when you turn on the system).

If you don't have a USB flash drive, I highly recommend getting a cheap/small one. It's a good investment. Here's the one I use to flash my BIOS: [http://www.newegg.com/Product/Product.aspx?Item=N82E16820178223](http://www.newegg.com/Product/Product.aspx?Item=N82E16820178223)

---

### Post by mbirth on 2009-08-10
> **Temüjin said:**
> Make sure your BIOS is updated. I believe this is your board? [http://www.msi.com/index.php?func=downloaddetail&type=bios&maincat_no=1&prod_no=1479](http://www.msi.com/index.php?func=downloaddetail&type=bios&maincat_no=1&prod_no=1479)

I already have the latest AMI BIOS installed. There's a newer EFI available at [http://global.msi.eu/html/popup/MB/uefi/download.html](http://global.msi.eu/html/popup/MB/uefi/download.html), but this makes my PC occasionally hang before the EFI kicks in so that I have to power-cycle it once or twice before it boots correctly.

Since I want to use Wake-on-LAN, this is a no-go for me.


Cheers,
  -mARKUS


P.S.: I noticed that I sometimes get a similar effect with my current settings (no C-State management!) every once in a while: aptitude segfaults directly after boot, but doesn't create garbage in its files. After a reboot, everything works fine again. I can't find a reason for this strange effects...

---

