---
title: "Lite-On SATA DVD burner"
date: 2007-05-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by professor_b on 2007-05-20
I have [this model](http://www.newegg.com/Product/ProductReview.aspx?Item=N82E16827106046) Lite-on SATA dvd burner installed under Ubuntu Feisty on AMD64. It worked perfectly when I bought it back in April -- it was literally plug and play. Now, lately, it doesn't work at all, as far as I can tell. I'm not sure what has changed on my system recently that would have caused this (i.e. no kernel upgrades, and it worked after I updated to Feisty). I'm running kernel 2.6.20-15-lowlatency.

I can see the drive in the BIOS, so I know the machine sees it. It works perfectly in Windows XP Pro, too (yech!). It just doesn't seem to work correctly when I boot into Ubuntu (which is my primary, everyday OS). 

When I insert a CD, it'll show up on the desktop, but the contents are completely empty (even for a CD that I know contains data). Audio CDs don't even read...they just kind of sit there and then eject automatically after a while. If I put in an audio CD and try to get tracks in GRIP, I get this:

"Error: Failed to read disc contents"

K3B reports not being able to see any device at all.

I'm baffled. Any ideas about how I can begin to track down this problem and get my once perfectly working burner perfectly working again (in Ubuntu!)? 

Thanks in advance.

---

### Post by Cappy on 2007-05-20
Maybe you should look in your system logs or "dmesg" to see if there are any kind of errors while you boot.
(System --> Administration --> System Log)

---

### Post by ronacc on 2007-05-20
also look at system>preferences>hardware info

---

### Post by professor_b on 2007-05-21
Thanks for the replies -- here's some more info:

> **Cappy said:**
> Maybe you should look in your system logs or "dmesg" to see if there are any kind of errors while you boot.
(System --> Administration --> System Log)
 
The only relevant error I see is this:

```

May 21 08:58:48 localhost kernel: [   24.912413] scsi1 : sata_nv
May 21 08:58:48 localhost kernel: [   25.215070] ata2: SATA link down (SStatus 0 SControl 300)
May 21 08:58:48 localhost kernel: [   25.216181] scsi 0:0:0:0: CD-ROM            LITE-ON  DVDRW SH-16A7S   WS04 PQ: 0 ANSI: 5

```

> **ronacc said:**
> also look at system>preferences>hardware info

Under CK804 Serial ATA controller, I see the device listed as a SCSI Device, including the model number (DVDRW SH-16A7S). The Device Tab says lists "unknown" for everything except status (which just says "status"). So, the system obviously "sees" the device....

This is really puzzling!

---

### Post by professor_b on 2007-05-21
I solved this, but not optimally.....

I found that booting into 2.6.17-10 made the SATA burner work properly, so I downgraded the kernel to 2.6.17-10 and everything is golden now. I couldn't get any of the newer kernels from feisty to work properly with it -- even though I could have sworn that I'd had this burner working properly in feisty previously.

Well ,whatever it is, the 2.6.17-10 makes it all work.

---

