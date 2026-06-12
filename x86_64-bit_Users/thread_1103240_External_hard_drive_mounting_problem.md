---
title: "External hard drive mounting problem"
date: 2009-03-22
forum: x86 64-bit Users
---

### Post by kvasanthkumar on 2009-03-22
Hi,

I have a Seagate external hard drive which was working fine, automatically mounting the drive once I plug the USB.

Now when i mount the drive I get this error :
$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdc1': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.

It is not just this drive, I couldn't mount my other NTFS partitions as well, from the Places -> (drive). But, am able to mount local NTFS partitions from command line.

ntfs-3g is already installed. So, what could be the problem ?

---

### Post by cariboo on 2009-03-23
You could install ntfsprogs and then run ntfsfix on the drive to see if you repair the problem. Ntfsprogs is in the repositories, you can use Synaptic Package Manager to install it.

Jim

---

### Post by Yashiro on 2009-03-24
> $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdc1': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. [B]In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important![/B] If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.  .

---

### Post by kvasanthkumar on 2009-03-24
I have run chkdsk from windows and it has started working now.
The external drive access acts bit odd by autumatically unmounting and mounting every now and then.

Will get back based if the problem continues.

Thanks.

---

### Post by Yashiro on 2009-03-24
It happens when you disconnect from a file system when it is still open. ie Pulling the plug on an external usb drive without unmounting or ejecting it.

On Linux you can use a handy tray app called Ejecter to help. You should find it on getdeb.net

---

### Post by kvasanthkumar on 2009-03-24
I mean it happens automatically. The cables are all fine.
The drive icon is displayed twice in the desktop.

---

