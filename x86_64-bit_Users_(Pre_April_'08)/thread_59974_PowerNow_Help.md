---
title: "PowerNow Help"
date: 2005-08-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by da_buddha on 2005-08-26
So I have an A64 processor and am running Ubuntu and am trying to just run the Live CD for the time being...

I *know* there are PowerNow threads already and probably even HOW TOs, however my question is more specific and I am unfortunately a bit new to Ubuntu/Linux... I am wondering if there are any PowerNow (like powernowd, etc.) installs so that they can be installed and ran *without* rebuilding the kernel? I need to try and install strictly off of my LiveCD (and even try and get a script to auto do that every time I boot from it). 

Please let me know if you know of any versions or ways to enable PowerNow for the A64 without rebuilding the kernel and requiring a "reboot" to reload the new kernel (unless I am mistaken as to that requirement). Thanks!  :)

---

### Post by da_buddha on 2005-08-27
Any help at all with this?? I haven't heard anything back and am still stuck waiting  :(

---

### Post by FluffyElmo on 2005-08-28
I'm not sure I see your problem. I'm no expert but powernowd seems to be enabled on my desktop install and I just booted from the LiveCD and it seems to be enabled with it as well?
```

ubuntu@blk-xxx-xxx-xxx:~$ sudo cat /var/log/messages |grep powernow
Aug 28 17:01:31 localhost kernel: powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.00.09e)
Aug 28 17:01:31 localhost kernel: powernow-k8:    0 : fid 0x2 (1000 MHz), vid 0x12 (1100 mV)
Aug 28 17:01:31 localhost kernel: powernow-k8:    1 : fid 0xa (1800 MHz), vid 0xa (1300 mV)
Aug 28 17:01:31 localhost kernel: powernow-k8:    2 : fid 0xc (2000 MHz), vid 0x6 (1400 mV)
Aug 28 17:01:31 localhost kernel: powernow-k8:    3 : fid 0xe (2200 MHz), vid 0x2 (1500 mV)
```

Two thoughts, make sure that powernow is enabled in your bios. Second, make sure you're using the AMD64 LiveCD, the x86 CD is more generic and likely won't support AMD64 specific features.

EDIT: Forgot to mention that I'm using Hoary (5.04) both on the desktop and the LiveCD.

---

### Post by baylisscg on 2005-08-31
Hi,

   Well further to FluffyElmo's post. AFAIK CPU scaling / throttling is handled by CPUFreq in the kernel try ```
lsmod | grep cpufreq
```. Ubuntu uses powernowd to control CPUFreq from userland. You should have an init.d script at ```
/etc/init.d/powernowd
``` you can get details of how it is configured from ```
man powernowd
```. If you want to change the default function create a file ```
/etc/default/powernowd
``` and define OPTIONS with your prefered ones. e.g. ```
OPTIONS="-q -m=0"
``` test it by calling ```
sudo /etc/init.d/powernowd restart
```.

My Athlon64 3000+ (Venice) scales between 1GHz and 1.8GHz although I did require a BIOS upgrade to enable Cool n' Quiet on my motherboard.

I would point out that, once the motherboard manufacturer got their stuff toghether, Ubuntu works *much* better than Windows XP for this.

Hope that was what you were looking for.

---

