---
title: "Can not mix ATA &amp; SATA"
date: 2009-05-08
forum: x86 64-bit Users
---

### Post by jpaulb on 2009-05-08
Can not mix ATA & SATA
Installing Ubuntu 9.04 64 server
I am using a MSI K8n Neo F MB, 2 80g ATA & 1 500g SATA Drives
This is the same problem with 9.04 as with 8.04 nothing has been done with issue.

My MB BIOS orders the drives as ATA master, ATA slave , SATA master.
The partition manager on the other hand orders the SAT drive as (hd0)& the ATA as (hd1),(hd2)

This feature in Ubuntu causes the system to search on the wrong drive for the system. The bios looks at the first ATA which should be (hd0) for the boot, Ubuntu marks this as (hd1). The boot fails.


I removed the SATA drive with intentions of installing it manually later. The boot now fails with the warning 

boot from (hd0)
Powernow-k8 Bios error PSB or ACPI-PSS objects
No block device found
gave up waiting for root device
Alert /dev/disk/by-UUID.......

Any fixes for this??
There is not problem installing Debian so i

---

### Post by cariboo on 2009-05-08
I have an MSI K9NGM2 mother board, no matter how I set it the SATA drives are always the first drive. I have Jaunty and Karmic install on a 250Gb PATA drive. Both installations use the MBR on the SATA drive with zero problems.

---

### Post by dabl on 2009-05-08
On my Intel D975XBX motherboard, if there is an IDE drive connected, then Grub will ONLY go on that MBR -- there is no way to redirect the installer to put Grub anywhere else. This problem is not limited to *buntu, by the way -- other Linux installers behave the same.

However, this is only a problem during the installation of the OS.  So, you can disconnect the power connectors from the IDE drives, install Linux on your SATA drive, then reconnect the IDE drives. Of course the enumeration of drives will be wrong in /boot/grub/menu.lst and also in /etc/fstab, but these can be edited to straighten out the device IDs.

---

### Post by jpaulb on 2009-05-08
Looks like the MSI K9NGM2 mother board orders the drives one way and the Intel D975XBX motherboard the drives another.

I wanted the OS on the 80g  ATA drive and not on the 500g SATA drive which is one big partition with about 300g of videos. I had a choice either buy a new SATA or install Debian. Debian places the ATA's first which is what I want. 

I don't like the idea of upgrading the hardware when upgrading the OS. That sounds way too much like another company. 

Maybe by 10.04 this will get straightened out or my ATA's die.

---

### Post by caljohnsmith on 2009-05-08
Even though your BIOS may order your drives differently on start up (the BIOS boot order) so that Grub sees a different drive order than when you are in Ubuntu, most of the time it is not a problem if you just configure Grub to deal with whatever the drive order is. If you would like help doing that, how about downloading the **Boot Info Script** to your Ubuntu desktop (or can be any Live CD):

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

John

---

