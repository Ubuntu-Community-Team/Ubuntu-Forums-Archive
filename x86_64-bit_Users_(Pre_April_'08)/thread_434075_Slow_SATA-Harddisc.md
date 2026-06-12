---
title: "Slow SATA-Harddisc"
date: 2007-05-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by Stefan.Gruber on 2007-05-05
Hello everybody,

I've installed Ubuntu 7.04 on a PC with following configuration:

CPU: Intel Core 2 Duo
Mainboard: Intel DG965WH
Harddisc: Samsung SpinPoint T166 16MB SATA II (HD403LJ)

The installation took about 11 hours because the read- and write-speed is extremle low. I ran
```
#time dd if=/dev/zero of=/test bs=1M count=1024
```
which took about 4,5 minutes, on my notebook with a slow IDE-Drive it took 39 seconds, so there has to be something wrong.
One may argue that it is due to defected hardware, but running smartctl said, everything is ok:
```
#smartctl -H /dev/sda
SMART overall-health self-assessment test result: PASSED
```

Any ideas on that?
Thanks,
Stefan.

---

### Post by John Jason Jordan on 2007-05-05
> **Stefan.Gruber said:**
> 
CPU: Intel Core 2 Duo
Mainboard: Intel DG965WH
Harddisc: Samsung SpinPoint T166 16MB SATA II (HD403LJ)

The installation took about 11 hours because the read- and write-speed is extremle low. I ran
```
#time dd if=/dev/zero of=/test bs=1M count=1024
```
which took about 4,5 minutes, on my notebook with a slow IDE-Drive it took 39 seconds, so there has to be something wrong.
One may argue that it is due to defected hardware, but running smartctl said, everything is ok:
```
#smartctl -H /dev/sda
SMART overall-health self-assessment test result: PASSED
```

Any ideas on that?
First, what SATA controller are you using? If it's on the motherboard, is it Intel? If so what version, etc.?

Second, I may not be much help, except I am having problems with dual Western Digital SATA II drives using RAID 1. I am using the SATA II controller on my Abit NF-M2S motherboard, which is nVidia 405 chipset. I ran the same tests you did and got:

sudo time dd if=/dev/zero of=/test bs=1M count=1024
1024+0 records in
1024+0 records out
1073741824 bytes (1.1 GB copied, 16.77 seconds, 64.0 MB/s
0.00user 4.34system 0:17.49elapsed 24%CPU (0avgtext+0avgdata 0maxresident)k
0inputs+0outputs (0major+291minor)pagefaults 0swaps

There doesn't seem to be any problem with my speed, but Im worried about the 291 minor pagefaults. My problem is not speed, but on continuous disk usage I'm getting a shutdown as though I had pulled the power plug out of the wall. I'm tearing my hair out trying to figure out what is wrong. So far I have replaced the power supply and the motherboard. It can't be heat because it happens even if the computer is stone cold and just started up, plus the temp sensors are disabled in th BIOS. This thing could set fire to the sun and it wouldn't shut down.

The lspci command tells me I am using the sata-nv driver, so I am looking for anyone else who has problems with that driver or anything related to SATA II and Linux software RAID 1 (mdadm).

---

### Post by Stefan.Gruber on 2007-05-05
The SATA-controller is a built in by Intel. lspci says:
00:1f.2 SATA controller: Intel Corporation 82801HB (ICH8)

---

### Post by Stefan.Gruber on 2007-05-06
Ok, the solution was to downgarde to the original BIOS, Version 1669:
[http://downloadfinder.intel.com/scripts-df-external/Filter_Results.aspx?strOSs=38&strTypes=all&ProductID=2375&OSFullName=OS%20Independent&lang=eng&sType=prev](http://downloadfinder.intel.com/scripts-df-external/Filter_Results.aspx?strOSs=38&strTypes=all&ProductID=2375&OSFullName=OS%20Independent&lang=eng&sType=prev)

---

