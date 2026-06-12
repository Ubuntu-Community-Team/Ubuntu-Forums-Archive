---
title: "28-Jan-2009 updates broke X ?"
date: 2009-01-28
forum: x86 64-bit Users
---

### Post by asynchronous13 on 2009-01-28
This morning I let the automatic updates run. After working for a couple hours I noticed that a reboot was recommended. Upon reboot, I could only boot in low-resolution mode. It appears that my /etc/X11/xorg.conf was overwritten?

I struggled with various configuration files, and eventually just re-installed nvidia drivers, updated my xorg.conf and now I'm back at 1920x1200 resolution. 

I've got everything back to normal, just wondering if anyone else had a problem.

---

### Post by sune_cph on 2009-01-28
No problems here...I also run 1920x1200 on nvidia gtx 260 (using the nvidia proprietary driver...)

/Sune

---

### Post by em4r1z on 2009-01-28
The most recent updates affected my system too, but my X server doesn't start with any kernel (in normal or recovery modes.) I guess the NVIDIA drivers didn't compile properly after the update.
After loading any kernel, the system stops and states there's a problem with the X server, making that terminal unusable. I try a different terminal, load aptitude (to reinstall the NVIDIA driver) and the systems states is running in read-only mode.
Any ideas on how to reinstall the drivers or solve this problem?

---

### Post by drlmg on 2009-01-29
I have the same problem. If I find out any useful info. I will post a link here.

---

### Post by davubu on 2009-02-06
X only let me use low graphics mode with a resolution of 480 by some other number.  After downloading the new proprietary driver and installer from nvidia I restarted into recovery mode.  

Selecting "Fix X Server" did not work.

Selecting the option that let me log in as root did.
I tried to run the nvidia-xconfig installer which told me that it wouldn't work in runlevel 1 and to try again after entering "initrd 3" (I think).  I tried running the nvidia-xconfig installer again and now everything works fine again.

---

### Post by Yashiro on 2009-02-06
It's because you need to rebuild the nvidia kernel module after a kernel update (usually). Your driver should do this automatically but it seems not work on some nvidia installations.

---

