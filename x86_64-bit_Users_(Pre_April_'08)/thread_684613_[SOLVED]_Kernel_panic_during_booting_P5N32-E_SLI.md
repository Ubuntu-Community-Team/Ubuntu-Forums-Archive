---
title: "[SOLVED] Kernel panic during booting P5N32-E SLI"
date: 2008-02-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by bojam on 2008-02-01
I have installed Gutsy on a new build PC, dual booting Vista-64.
The h/ware consists of ASUS M/B P5N32-E SLI Plus, 4GB Ram 3 SATA 320GB H/Disks,
an 8500 NVidea graphics cards...  all of which I investigated before buying and seemed to be compatible with linux. 

But I get as far as the init boot process the last sane message is

forcedeth: using HIGHDMA
Kernel Panic - not syncing:Attempted to kill init!

As far as I can tell the install process succeeded.

Vista runs perfectly ok and the cpu is not running too hot.

Help....

---

### Post by dlpfmVfH on 2008-02-01
don't know what went wrong with your install,

but I'm running almost the same hardware and 7.10 and 8.04 installed perfect.

using:
asus p5n-e SLI mobo, Q6600 2,4 ghz geforce 8500 silent, and 2 sata disk 500 gb.

didn't need to change anything when installing, just booted the cd, pointed to the disk to install, and waited.

---

### Post by Yellow Pasque on 2008-02-01
It does indeed seem like somehing went wrong with the install. If you downloaded an iso, did you verify the md5sum? Have you verified that the CD burned correctly?

---

### Post by bojam on 2008-02-01
I also had the same problem with the 32 bit version and feisty disks.  So although you might be right about the install I doubt its because of the cd's.

I have tried different schemes of partitioning but always the same problem...
 
It seems to be missing a config file at the init stage but which it is I can't tell as the dmesg mesages aren't available when I boot using the live cd.

---

### Post by Yellow Pasque on 2008-02-01
Can you mount the filesystem with the LiveCD?
The dmesg log is kept in the /var/log directory.

---

### Post by bojam on 2008-02-01
I did mount the partitions and the logs hadn't been written to, which I thought was odd..
There was nothing in the /proc either... but the rest of the install seemed ok with /etc, /usr etc ...

There weren't any errors during install except for the security updates not being available... but that seemed normal since I hadn't configured any network services.

But in the install logs there were squashfs errors but ... So I tried the non 32 bit version and failed at the same point booting up..  I'm a little surprised as I have managed to put Ubuntu on three machines with no problem, a dual boot dual celeron abit BP6 and a laptop.

But none had sata drives...

I tried reformatting and installing to ext3 partitions instead of the reiserfs, which I prefer but still the same problem...

---

### Post by dlpfmVfH on 2008-02-02
which cd did you use, the live cd install version, or the alternate one??

because I installed mine with a live cd, just to check out, if ubuntu starts with my configuration and if it finds all my hardware...

I checked also the network settings, just so It can find locales and updates before and install them right from the start.

---

### Post by bojam on 2008-02-02
I installed from the 64 bit cd.. but had the same problem with the 32 bit cd as well.

I haven't been able to get the network adaptor recognised.  Which module do I need?

I cannot remember setting up the network before installing before.

Cheers

---

### Post by bojam on 2008-02-03
I have done another install I didn't get the security warning.   I changed my modprobe.conf to switch off msi  but I still get to the same point in the boot process when it panics....


Help

---

### Post by dlpfmVfH on 2008-02-03
does the 64-bit live cd, start up?
and does it get your network up and running?

checked my lsmod and dmesg for forcedeth driver, (the one for your network)
and found it was working correctly for me...
**dmesg:**
```
[   32.717801] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   33.233224] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:1d:60:4a:8e:e5
[   33.233227] forcedeth 0000:00:14.0: highdma pwrctl timirq gbit lnktim desc-v3
```

running hardy heron at the moment, so version 0.61 could be newer then gutsy... don't know about that...

---

### Post by bojam on 2008-02-03
The live cd works after I did:

modprobe -r forcedeth
modprobe forcedeth msi=0 msix=0

The restarted the interfaces.   This just allowed me install without getting the security warning.

After restarting, I got the same message.  So I added the lines:

alias eth0 forcedeth
alias eth1 forcedeth
options msi=0 msix=0 

To the modprobe.conf file and rebooted and got the same kernel panic...

Init: Error parsing configuration: No such file or directory
Kernel panic - not syncing: Attempted to kill Init

At which point the capslock & shiftlock leds  flash continuously and I have to do a hard reset....

---

### Post by dlpfmVfH on 2008-02-04
try adding noapic to grub kernel line...
and see if that helps...

---

### Post by bojam on 2008-02-04
No difference ... I did a search for the error message but couldn't find it in the /etc.

---

### Post by bojam on 2008-02-04
Sussed it nothing do with forcedeth....It was the way I partitioned my hard disks ie I had a separate /etc why you cannot I do not but when I revised by partitions it worked... this should be changed or at least the installer should warn the user...

Thanks to everyone who gave me pointers...

---

### Post by dlpfmVfH on 2008-02-05
please mark your thread as solved then...

I'm happy for you, that you found out what the problem was.

---

### Post by bojam on 2008-02-09
As I said in my previous posting thanks....

Dont put /etc on its own partition...

---

### Post by Yellow Pasque on 2008-02-09
Yes, we see that. Now aboe is requesting that you mark the thread as solved (uunder thread tools menu I believe)

---

