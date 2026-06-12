---
title: "yaboot installation freezes"
date: 2006-01-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by Rovenhot on 2006-01-01
I haven't got any responses from my previous thread, so I'll restate my problem here:

I'm installing Breezy onto a 40 GB external hard drive for a dual-boot with Mac OS X.  I allotted a 3 MB bootstrap partition from some free space I had left over, and although this should be plenty for yaboot, it won't install.  The installer freezes at the yaboot step at 0% progress, although sometimes, it simply says that installing yaboot failed, and gives me the option to continue, but then it freezes at 50%, when it's "looking for other operating systems".

Has this been replicated?

---

### Post by Ptero-4 on 2006-01-01
Have you tried allotting 1 MB instead of three. In some older PowerPC based linux distros I tried I found yaboot to be very nitpicky about the size of the bootstrap partition it gets installed in, and setting it to 1 MB seemed to always fix it. Now I don't know if this is a yaboot bug or an odd spec rule (the partition where yaboot gets installed uses a special Apple defined type and may rely on odd block length parameters for correct operation), but I do know from prior PPC Linux distros (LinuxPPC 99, YDL 2.0 and SuSE 7.3 ppc) that yaboot has only been installed ok in 1MB bootstrap partitions.

---

### Post by Rovenhot on 2006-01-01
I'll try that...thanks for the help.

---

### Post by Rovenhot on 2006-01-01
Didn't work, although whenever I tried to set the partition size to 1 MB, it set it to 999.9 KB instead.  Is that the problem, or is that normal?  In the meantime, I just want to get it working at least once, so how do I launch the kernel it tells me to from the Open Firmware prompt?

---

### Post by linear on 2006-01-01
Yaboot installation on an external drive is problematic. See this thread for others' experience:

[http://www.ubuntuforums.org/showthread.php?p=498516](http://www.ubuntuforums.org/showthread.php?p=498516)

---

### Post by Rovenhot on 2006-01-02
[This tutorial]("http://macubuntu.blogspot.com/2005/11/nailed-howto-install-bootable-mac.html") seemed to be useful, but unfortunately, there were two fatal inconsistencies: there was no node@* folder inside the firewire@* folder, and my network connection, although the installer claimed was valid, was not able to fetch me the required tarzipped kernel, or anything, for that matter, after repeated attempts at downloading random webpages.  I guess I'll just have to install on an internal drive.

---

