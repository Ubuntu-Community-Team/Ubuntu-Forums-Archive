---
title: "Having problems with setting up triple-boot"
date: 2007-06-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by azteech on 2007-06-09
Hello,
 
Please bear with me, as I attempt to layout my issue, as it could get a little long.
 
Am attempting to set up a triple boot on a new system and experiencing problems with Fiesty 64-bit overwritting Fiesty 32-bit OS files. Have looked in forums, but not finding answer to my issue.
 
Specs for new system are: 64-bit AMD Sempron 3000+ CPU, 2G DDR2, with two SATA drives (200GB and 300GB) (set up as non-raid), and nvida GeForce 5200 (128 mb) AGP video card.
 
Used gparted (32-bit version) from live CD to set up SATA drives as follows:
 
sda1 - Partition 1 - 40GB - for XP   (format - NTFS)
Partition 2 - 40GB - Shared data   (format - fat32)
Partition 3 - 90GB - / (root) - used for Fiesty 32-Bit   (format - ext3)
Partition 4 - 4GB - Linux Swap
11.31GB left unpartitioned for future expansion
 
sdb1 - Partition 1 - 100GB - /(root) - used for Fiesty 64-bit    (format - ext3) 
Partition 2 - 5GB - Linux Swap for Fiesty 64-bit   (format - ext3)
Partition 3 - 10GB - /tmp (shared between Fiesty 32- and 64-bit)   (format - ext3)
Partition 4 - 160GB - extended partition
Logical Partition 5 - 75GB - /home32 (Fiesty 32-bit)   (format - ext3)
Logical Partition 6 - 75GB - /home64 (Fiesty 64-bit)   (format - ext3)
15GB left unpartitioned for future expansion
 
Installed XP 1st, followed by installing Fiesty 32-bit from Live CD, to sda1. Both installs went smoothly.  Use and run both from GRUB with no problems. Loaded up Nvida drivers for Fiesty 32-bit with no problems.
 
Ran 64-bit Fiesty from Live CD before installing to ensure I would not have any problems - none noted after using it for a day. Installed Fiesty 64-bit from Live CD to sdb1. Install went without a hitch; no error messages noted. 
 
After installing 64-bit Fiesty, I rebooted. Grub seemed to be set-up okay - though seemed odd that Fiesty 32-bit would be listed down in the "Other OS" section. Checked grub to ensure all command lines were set up correctly. They were.
 
Booted into Fiesty 64-bit. Grub worked fine, and system started to boot. 
Here is where things got a little strange. During the boot process, got several errors stating various programs could not be loaded, and grub halted. Grub presented me with only a command line and option to press any key to continue. 
Pressed enter and Feisty-64 continued to load. I was subsequently presented with Ubuntu's logon splash screen. I was successful in logging onto Fiesty and see the desktop and browse the computer.
 
Where I am noticing problems (other than the strange error messages during loading, is it appears that both Fiesty 32-bit and Fiesty 64-bit installed itself into /home directory, rather than the /home32 and /home64 directories I told them to use during setup. 
Confirmed this as both the /home32 and /home64 bit directories are empty, and have a new /home setup which appears to be used by both OS's.
 
Here is my questions.
 
1. Do I have the partitions set up properly, or am I missing something?
I saw in the forum where it was suggested to set up a /boot partition for both. Is this totally necessary, and could it be that I have botched my partition setup and this is really the cause of my problem(s)?
 
2. How do I get both OS's to use the /home32 and /home64 directories respectively, instead of setting up their own /home directory?
 
3. If this is not possible, how do i ensure that Fiesty 32-bit files are not overwritten when i install Fiesty 64-bit?
 
4. Do I have to hide Fiesty 32-bit partitions before I install Fiesty 64-bit?
 
Any suggestions are welcome, including recommendations for setting up a different partitioning scheme.
 
Thanks in advance.

---

### Post by azteech on 2007-06-10
Anyone have any ideas, or suggestions on correcting this?

---

### Post by Cappy on 2007-06-10
If they are sharing a /home/ partition then they have to be writing to the same partition. You need to compare your /etc/fstab on each of your Ubuntu "/" partitions to the list of partitions on your hard drive from ```
sudo fdisk -l
``` 
Something isn't being mounted correctly in the /etc/fstab

I think the need for a /boot/ partition is only when you have a Windows partition at the front of the disk that is larger than roughly 8.4GB and you want to boot Linux on the same disk.

---

