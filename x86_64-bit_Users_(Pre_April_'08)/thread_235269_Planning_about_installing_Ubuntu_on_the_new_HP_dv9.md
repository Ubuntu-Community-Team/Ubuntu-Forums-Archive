---
title: "Planning about installing Ubuntu on the new HP dv9000z"
date: 2006-08-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by elizleisndahizle on 2006-08-12
So I have not bought this yet because I am waiting to get the extra money that I borrowed with my student loans.  I know that an OS like Windows is not worthy of being ran on a piece of hardware this beautiful.  Here is a link to it []("http://www.shopping.hp.com/webapp/shopping/computer_series.do?series_name=dv9000z_series&catLevel=3&category=notebooks/hp_pavilion/dv9000_series&storeName=computer_store")
I am planning on getting the Turion X2 MT60 and I was wondering about some things.  I want to get the most performance out of my laptop(doesn't everybody). I was just wondering what kernel I need to use to get 64 bit and dual core working and will i be able to get it with apt get or will i have to custom compile it.  I have the 64 bit disks of both Ubuntu and Kubuntu.  Any advice about this would be great.  Just let me know.  Also are there any known issues with the new hp laptops or the geforce go 7600.  Thats about it.  Thanks in advance.

---

### Post by Kilz on 2006-08-12
> **elizleisndahizle said:**
> So I have not bought this yet because I am waiting to get the extra money that I borrowed with my student loans.  I know that an OS like Windows is not worthy of being ran on a piece of hardware this beautiful.  Here is a link to it []("http://www.shopping.hp.com/webapp/shopping/computer_series.do?series_name=dv9000z_series&catLevel=3&category=notebooks/hp_pavilion/dv9000_series&storeName=computer_store")
I am planning on getting the Turion X2 MT60 and I was wondering about some things.  I want to get the most performance out of my laptop(doesn't everybody). I was just wondering what kernel I need to use to get 64 bit and dual core working and will i be able to get it with apt get or will i have to custom compile it.  I have the 64 bit disks of both Ubuntu and Kubuntu.  Any advice about this would be great.  Just let me know.  Also are there any known issues with the new hp laptops or the geforce go 7600.  Thats about it.  Thanks in advance.

If you have the live CD's , just pop one in to test it to see what one you like. Gonome(Ubuntu) or KDE(Kubuntu) are both good, its just personal preference. Im not to sure on the Kernel but there are quite a few and all amd64 kernels are smp from what I have read.

---

### Post by elizleisndahizle on 2006-09-23
Ok so I finally got my laptop(thank you student loans).  So I put in the 64 bit version of ubuntu or kubuntu(I tried both) and It gets to the part where it starts setting up the hardware or whatever and just stays there.  Occassionally I will get an error something about bcm firmware some wireless crap(crap being that it's not Atheros).  Are there any solutions to this?  I was just wondering.

---

### Post by xstaticxgpx on 2006-09-23
linux has always had problems with wireless, i never heard of it preventing you to load the liveCD... try 32bit ubuntu/kubuntu

---

### Post by elizleisndahizle on 2006-09-29
it wasn't the wireless.  I had to boot with acpi=off.  Wireless should work with ndiswrapper need to test it out and reboot.

---

### Post by Agapo on 2006-10-06
How it working? I will be getting the same machine probably next week or so and I’m interested in installing ubuntu but I’m concern with drivers for the multimedia card reader, web cam and wireless/Bluetooth. Thank you!

---

### Post by kester111 on 2006-10-06
Hi,

I have the dv6000, and have problems with the installation
with partitioning the disk. Maybe you won't if you want to just delete WinXP

The freezing during install problem I also had (or similar)
and got around by using noapic nolapic boot options. 

- Kester

PS pls let me know if you understand how to partition the disk.

---

### Post by Agapo on 2006-10-09
I plan to partition and keep the existing xp media installation. I understand how to partition the disk there are also a couple of write-ups on the web.  
Like this one:
[http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html](http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html)
If you have more advice or options on the how to they are welcome since I don’t have my laptop yet.
How is your hardware working?

---

### Post by dalesyk on 2006-10-25
I installed edubuntu amd64 on my dv9000 with xp.  I basically booted with knoppix and used ntfsresize to shrink xp from 120G to 20G.  Then I used fdisk on knoppix to resize the partition to 25G, rebooted and resized again growing ntfs to 25G.  Later I installed edubuntu on another 25G partition and used the remainder as a fat32 data partition to share files between OS's.

---

