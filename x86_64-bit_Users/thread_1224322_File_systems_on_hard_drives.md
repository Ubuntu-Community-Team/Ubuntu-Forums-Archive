---
title: "File systems on hard drives"
date: 2009-07-27
forum: x86 64-bit Users
---

### Post by niw_uk1964 on 2009-07-27
Relating to my other post...my system has 5 1TB drives and 1 160GB IDE drive in it.

9.04 64-bit is installed on the 160GB IDE drive as a trial. The 5 1TB drives are all NTFS (this was a Win 7 installation) contianing my data.

I've decided to stick with Ubuntu and dump Windows. What's the best thing to do with these drives? Get all the data off, reformat with a Linux file system or just leave them as it?

---

### Post by sarfarazkazi on 2009-07-27
Best option would be to reformat them with linux filesystem.

---

### Post by niw_uk1964 on 2009-07-27
I was afraid that I might hear that! What would you recommend? ext2/3/4?

With 8GB of RAM I don't think swapping is likely to occur, but presumably it might be a good idea (when I come to do a full rebuild) to put the swap partition on a separate drive?

---

### Post by wojox on 2009-07-27
ext3
[http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)
ext4
[http://en.wikipedia.org/wiki/Ext4](http://en.wikipedia.org/wiki/Ext4)

---

### Post by niw_uk1964 on 2009-07-27
I was hoping for some real-world experience reocmmendations though. I'm aware of some of ext4's advantages.

---

### Post by hotbit on 2009-07-27
> **niw_uk1964 said:**
> I was hoping for some real-world experience reocmmendations though. I'm aware of some of ext4's advantages.

I was using part of my 250G drive formatted / used earlier under windows - thus NTFS formatted - for like 3 years - had no problems. But maybe moving to ext3/4 is better solution...

---

### Post by Rizlaw on 2009-07-27
> **niw_uk1964 said:**
> I was hoping for some real-world experience reocmmendations though. I'm aware of some of ext4's advantages.

On my system, I've been running Ubuntu 9.04 64 bit since it was released with no problems (i.e, no data loss or file corruption) using ext4 fs on all my drives. I also use an APC Smart 1500 UPS to make sure my system doesn't crash if there is a power line problem. In addition, I have 5 additional connected 750GB drives formatted as ext4, which I use for storage via an Addonics port multiplier/ Addonics Sil 3132 PCI Express controller card .  I've had the OS totally lock up  2-3 times (last time because of a documented bug in 9.04's AHCI mode) forcing me to do a hard power-off and reboot. Each time, the system rebooted and the auto fsck fixed any file system errors without any issues. I'm pretty satisfied that ext4, at this point, is safe enough to use.  I'm sure there are others who have had a less positive experience and would counsel that you use the "safer" ext3 fs. You could always wait until this October when 9.10 will have ext4 as the default fs on new installations.

Unless you plan on using a Windows OS regularly, I certainly recommend reformatting your ntfs drives to either ext3 or ext4 which are, IMHO, better file systems. I also would point out that if you do change to ext3/ext4, no Windows OS's will be able to natively read/write to the data on your linux formatted drives. There is a freeware Windows driver ([http://www.fs-driver.org/](http://www.fs-driver.org/)) that can read/write to ext2 and ext3 fs, but I've found that since the last XP service pack, M$ seems to have borked this drivers ext3 capabilities.

---

### Post by niw_uk1964 on 2009-07-28
> **Rizlaw said:**
> 
I also would point out that if you do change to ext3/ext4, no Windows OS's will be able to natively read/write to the data on your linux formatted drives. There is a freeware Windows driver ([http://www.fs-driver.org/](http://www.fs-driver.org/)) that can read/write to ext2 and ext3 fs, but I've found that since the last XP service pack, M$ seems to have borked this drivers ext3 capabilities.

Ah. That's a problem. A big problem as I have Windows systems that need access to files on my Linux box.

---

### Post by vanadium on 2009-07-28
That is not a problem. For Windows machines accessing your Ubuntu box over the network, the file system on the Ubuntu box does not matter. 

On drives that cannot be directly accessed by a Windows system, you should not be using ntfs. Linux lacks the tools to maintain and repair ntfs file systems, although basic functionality is available with ntfsfix. Save you the headache and performance hit of ntfs under linux and use a native linux file system, typically ext3. ext4 is emerging, but not (yet) standard.

To take a long story short, I certainly would reformat these partitions to ext3 in your case.

---

### Post by theremper on 2009-07-29
I have been using ext4 and have noticed an increase in performance. I have not had any negative side effects. go for it. ext4 will be the default in 9.10

---

