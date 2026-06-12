---
title: "Best Hardware SATA-II Controller"
date: 2006-06-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by TJInc. on 2006-06-23
Hi All,

I'm going to return my Highpoint RocketRaid 2300 controller, as I've just found out it's really a semi-software based product. Hence, all the frustration over the past 7-10 days in trying to install Ubuntu 64bit and getting the OS to recognise all the drives as one. Contemplating Raid-0 or Raid-10 configuration at this point in time, but will start with Raid-0, just to get it working.

As a consequence, I was wondering what will actually work with all the later major distributions including Ubuntu 6.06 64 bit edition.

I was thinking about the following pure hardware solutions:

1. 3Ware 9590SE-8ML (8 Ports)
2. LSI Logic MegaRAID SATA 300-8X
3. Areca ARC-1210/1220/1230/1260 Controller

The computer hardware the controller will be used on is as follows:
 
- ASUS M2N32-SLI motherboard
- AMD 64 X2 4200+ CPU
- NVidia 7600GS video card with DDR 256 MB of Ram
- 2 or 4 x Seagate 300 MB SATA-II (7200.9) Hard drives
- 2 GB of PQI 667Mhz DDR-2 RAM

I've been trying desperatly to get any version of Linux including Fedora Core 5, SusE 10.1 & Ubuntu 32 and 64 Bit 6.06 working with the HighPoint RocketRaid 2300, but have failed miserably.

I REALLY WANT TO END THIS PAIN WITH THE RAID CONTROLLER, ONCE AND FOR ALL.

Thanks to all that reply

---

### Post by TJInc. on 2006-06-23
Oops, sorry about the title, It's a SATA-II Raid Controller, I'm interested in.

I'm also open to SATA-II raid controllers, other than the ones mentioned. 

Thanks

---

### Post by dbenhur on 2006-06-24
Why are you so set on a hardware controller? :-k 

For Raid 0,1,10 the computational overhead is trivial and software works great.  Ubuntu comes with this ability out of the box with mdadm.

Here's a HowTo for debian & ubuntu: [http://www.howtoforge.com/linux_software_raid](http://www.howtoforge.com/linux_software_raid)

---

### Post by TJInc. on 2006-06-24
thanks,

I may try that and post the verdict. 
I guess i'm more interested in users who have mnaged to get 6.06 6bit working with ANY sort of SATA RAID controller

---

### Post by JoWilly on 2006-06-24
Hardware raid is not really worth the money, unless you are running servers that are accessing the disks while running at max CPU usage non stop. 

As dbenhur said, linux software raid is very good; It supports more capabilities than any hardware raid.I have been running it for years on my different machines, always in raid0 on several disks (just put your controller in IDE mode and install dapper with the alternate CD, set your partitions to software raid, and then create the raid. Don't forget that you will need a boot partition if /root is on raid).

But if you really want to go the "hardware" raid route, 3ware has imho the best reputation for quality products.

---

