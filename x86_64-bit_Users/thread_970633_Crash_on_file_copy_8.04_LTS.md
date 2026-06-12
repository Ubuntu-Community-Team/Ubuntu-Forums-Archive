---
title: "Crash on file copy 8.04 LTS"
date: 2008-11-04
forum: x86 64-bit Users
---

### Post by daveraleri on 2008-11-04
Hi,

My system, after being mostly rock solid is locking up hard, no messages, when I copy some files.  I apologize for the length of the post, I just want to provide as much info as possible.

The system is an EVGA MB AMD x86_64 with 2Ghz AMD processor 4mb of RAM, it is my son's old gaming machine.  Video is an Nvidia 6200.  The first (original) drive is a WD 160 sata.  The uname says:
#uname -a
Linux dave-desktop 2.6.24-21-generic #1 SMP Tue Oct 21 23:09:30 UTC 2008 x86_64 GNU/Linux

I use the this to run VMWARE Server, but this behavior happens with or without a VM actually running.

The problems started on Saturday when the following actions were taken.

Second drive (Seagate 500 GB sata) installed.

All pending updates were applied via Update Manager.

I rebooted.

Release version of VMware 2.0 installed.

I rebooted.

I copied the Windows Server 2003 VM from the WD 160 to the Seagate 500 with no problem.  When I tried to copy the Win XP VM to the new drive, the system locked up.

I then screwed up and put the WinXP VM files in the trash, and it wouldn't move back, so I tried to copy it back out of the trash to where it was on original drive using drag and drop - system locked up.  

Then I tried to use rsync to get the GUI out of the way, locks up.  Took the second drive out, and tried again with rsync, locked up.  The WinXP VM files are 2GB or less.

I had work to do, so I just started the VM that copied properly, and left it be, and the system worked for 3 days, no problems.

Today it locked up when copying files within the Win2k3 Server, which it never did before, the VM had been up for 3 days, and working with no problems.

Is there some tweak I need to use to get the drives not to over-run, or whatever they are doing.

How can I get the gcc version of the kernel compile match the version of gcc installed.  Somehow they got out of sync, and gcc now says gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu3).  When I do the VMWare Server V2 install it complains that they don't match and this may cause problems.

I am familiar with several version of linux, and like Ubuntu, because it just lets you work, instead of constant fiddling.  If any further info is needed, please let me know.

---

