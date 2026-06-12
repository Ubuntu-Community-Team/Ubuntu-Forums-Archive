---
title: "Newbie Questions: Dual boot Ubuntu/OSX off FireWire drive using iBook G4"
date: 2006-04-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by arkabas on 2006-04-30
Hi everyone,

I am more or less a Linux newbie, especially with regards to Linux on Mac/OpenFirmware.  I have a ton of questions about installing Ubuntu.  I would appreciate it very much if I could be some advice on what to do and/or where to look for solutions.  A link to a tutorial would be great.

My Mac system:

iBook G4 1.33 MHz (one generation ago, not the current generation)
FireWire HD with Oxford Chipset (250 GB)

What I want with linux:

To dual boot Ubuntu and Mac OS X from the external HD using my iBook G4.  

My problem:

I formated the FW HD using Mac OS X's "Disk Utility" to HFS+ with Mac OS 9 drivers.  Next I ran the Ubuntu CD installer and allowed it to do "Guided Partition" of the entire 250 GB drive (apparently this creates 3 partitions: boot, ext3 for all files, and swap for the OS??).  Everything was looking good until the installer got to Yaboot.  The installer crashed and said that Yaboot could not be installed.  I decided to continue anyway and skip Yaboot installation.  At the end of the installation I was told to manually boot Ubuntu from "/boot/vmlinux kernel" on the partition "/dev/sda3" with "root=/dev/sda3". On a side note, I ran the installer without internet connection (I only have wireless access via AirPort Extreme until next week).

Any suggestions?  Is dual booting Ubuntu and OS X off an external FW drive possible?  Any recommendations on partitioning or bootloaders?  I found one website ([http://macubuntu.blogspot.com/2005/11/nailed-howto-install-bootable-mac.html](http://macubuntu.blogspot.com/2005/11/nailed-howto-install-bootable-mac.html)) that seemed to address this problem, but it requires ethernet connection to work.  I'm ok with Linux on PC BIOS, but I am totally lost with Linux on Mac OpenFirmware using a FW drive.

Thanks in advance and my deepest apologies for these incredibly newbie-ish questions.  I simply don't know where else to go.  Google and searching these forums hasn't helped me much.

Thanks again.

---

### Post by Rxke on 2006-04-30
from the HOWTO, it looks like you'll need connectivity anyway... I'm not following up too well on Airport exteme (because I don't have one) but Dapper seems to goot it working, so you might consider downloading the beta instead if that's an option? (I've been running Dapper for awhile and it's working quite well)
Again: I'm not sure how good the AE works under Dapper, you might have to look around a bit to get the latest news about it...

---

### Post by keyshawn on 2006-05-25
Hey,

Sorry if I don't understand, but what are you running on your internal ibook drive, Tiger, I presume ? Do you want to partition this external drive so that it has extra space so you can access files on OS X and have the entire ubuntu install on it ? 

If that's the case, then from what I've found, on this thread [http://www.ubuntuforums.org/showthread.php?t=89960](http://www.ubuntuforums.org/showthread.php?t=89960)
you might be able to do the same as described, and instead use the name for your external drive instead of 'Macintosh HD.' 

Also, check out these threads as well:
[http://www.ubuntuforums.org/showpost.php?p=498516&postcount=5](http://www.ubuntuforums.org/showpost.php?p=498516&postcount=5)
[http://ubuntuforums.org/archive/index.php/t-3952.html](http://ubuntuforums.org/archive/index.php/t-3952.html)

Good luck and keep us updated on how it's working for you !
regards,
skora.

---

