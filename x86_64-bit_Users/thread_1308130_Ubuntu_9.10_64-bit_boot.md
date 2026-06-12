---
title: "Ubuntu 9.10 64-bit boot"
date: 2009-10-31
forum: x86 64-bit Users
---

### Post by Richard Carlson on 2009-10-31
I've installed and reinstalled both Ubuntu 9.10 and Kubuntu 9.10 64-bit. The system boots initially once then when the system is completely shutdown and restarted the system stops during  the grub boot. When I run the boot  in recovery mode the software shows the grub process line by line and stops on a line that says:

clocksource tsc unstable (delta=xxxxxxxxx ns).

This is where it seems to hang up and stop  indefinitely. Initially both programs worked for a short while but upon renewed startup this has happeded.  I can't figure out what is causing this mess. I've re-installed both programs from start with a frest format to hard drive. 

Any help would be appreciated. This has got me really baffled. Never had this problem with 9.04. 

Rich

---

### Post by nikgare on 2009-10-31
This might help:
[http://ubuntuforums.org/showthread.php?t=698211&page=2](http://ubuntuforums.org/showthread.php?t=698211&page=2)

---

### Post by sanderj on 2009-10-31
Have you Googled for it? Because the first hits give explanation and a workaround: disable ACPI.

[http://www.google.com/search?q=clocksource+tsc+unstable+delta](http://www.google.com/search?q=clocksource+tsc+unstable+delta)

---

