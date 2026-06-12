---
title: "k8 smp panics"
date: 2005-10-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by brianglass on 2005-10-15
I can boot fine into 2.6.12-9-amd64-generic, but when I try to boot into 2.6.12-9-amd64-k8-smp I get a kernel panic. The messages fly by too fast for me to read them.

I have:

Athlon64 X2 3800+
DFI NF4-DAGF MOBO
Ubuntu 5.10 AMD64

I have flashed the bios with the latest version that claims to support dual core. The bios reports 2 CPUs upon power-up.

Help?

UPDATE: The error I see has to do with the kernel not being able to sync. Actually the error message looks remarkably like the screenshot in [this]("http://www.ubuntuforums.org/showthread.php?t=64804&highlight=smp+panic") post.

I've also tried adding noapic, nolapic, and acpi=off to the kernel boot arguments to no avail.

---

### Post by viniosity on 2005-10-23
I had the same problem..  I had to step back to my old kernel and uninstall the one that came with breezy.  I know it's not a solution, but until another version of the SMP kernel is released I'm not going to risk anything else.

---

### Post by dnight on 2005-10-29
I am experiencing this problem too in a dual opteron 64 machine :(

First it came when I upgraded from hoary to breezy. I was thinking it was something related to upgrading, so I started a fresh install of breeze. And when I installed the smp kernel the problem came back again :(

I would like to report this too and bump this thread for a faster new kernel smp correction. It's just not working at all. :???:

From a fresh breezy I could not install the older kernel :( so I am using only one processor now, oh god... ](*,)

---

### Post by lverdestar on 2005-10-31
I installed kernel 2.6.11-9-amd64-k8-smp  from the universe repository on a dual Opteron HP DL145 and it worked fine. Both processors are initialized. 
The synaptic upgrade manager also installed cramfsprogs and initrd-tools. 
 The newer kernel 2.6.12-9amd64-k8-smp that I had installed previously still does not boot. I have not tried reinstalling it.

---

### Post by dnight on 2005-11-28
Modifying BIOS option MultiProcess Specification from 1.4 to 1.1 solved my problem today. Why the older kernel didn't required this? :???:
EDIT
Sorry.  crashed again :P

---

### Post by vivedekananda on 2005-11-28
I removed the options "splash" and "quit" from the kernel booting parameters list and I am able to boot on it, though the machine doesn't seem to be very stable (crashed while copying from a dvd but only once ), 
unfortunately there are no modules for my network card in 2.6.11 kernel, and I am too lazy to compile so I will stick with 2.6.12

we'll have to wait for a new smp kernel I guess

---

### Post by edrumwri on 2005-12-01
I'm afraid that I too am having this problem, if anyone out there is keeping score.  On kernel 2.6.12-10 SMP, my machine kernel panics right after uncompressing the kernel (regardless of whether noapic, nolapic, acpi=off, notsc options are added).  If I regress to kernel 2.6.11-9 SMP, things progress a bit farther but I still get the message:

Begin: Running /scripts/init-premount ...
FATAL: Error inserting fan (/lib/modules/2.6.11-9-amd64-k8-smp/kernel/drivers/acpi/fan.ko): No such device
FATAL: Error inserting thermal (/lib/modules/2.6.11-9-amd64-k8-smp/kernel/drivers/acpi/thermal.ko): No such device
Done.
Begin: Mounting root file system ...
Begin: Running /scripts/local-top ...
Done.
ALERT! /dev/sda1 does not exist.  Droping to a shell!

BusyBox v1.00-pre10 (Debian 20040623-1ubuntu22) Built-in-shell (ash)
Enter 'help' for a list of built-in-commands.

/bin/sh: can't access tty; job control turned off
# 

Note that I still have the acpi=off option set in grub...

---

### Post by edrumwri on 2005-12-02
Ok, I got it to work by upgrading to the latest stable linux kernel, 2.6.14-3.  For those like me that can't wait for SMP (and also like the preemptible kernel :), here's what you can do.

1.  Download the latest stable kernel source from [http://www.kernel.org](http://www.kernel.org)

2.  Extract the source to your /usr/src directory

3.  Proceed using instructions from [http://ubuntuforums.org/showthread.php?t=85064&highlight=SMP](http://ubuntuforums.org/showthread.php?t=85064&highlight=SMP) **except** for the following changes:

a) Do not install the linux sources from Ubuntu [it's unnecessary].  
b) When making the symbolic link to the linux source directory, the kernel name will necesarily change.  
c) When you type "make old config", it's going to prompt you for information.  In general, you can just hit enter to pick the default option.
d) When you type "make menuconfig", you need to make sure to enable SMP (it's turned off by default).  I'd also recommend the lowest-latency kernel.  I also turned off "K8 NUMA" support under processor type and changed my processor to AMD64 from generic x86 processor.

I apologize if my instructions are a bit elementary, but it seems that everyone around here is content to wait for the next Ubuntu release rather than compiling their own kernel.  I need all my processing power, and Dapper Drake (and its newer kernel) is scheduled for release in April.

---

### Post by vivedekananda on 2006-01-16
2.6.15 kernel is working fine for me, so far, you can download the deb files from here :
[http://www.ma.ic.ac.uk/~lubo/kernel/kernel-image-2.6.15.deb](http://www.ma.ic.ac.uk/~lubo/kernel/kernel-image-2.6.15.deb)

---

### Post by kakashi on 2006-02-07
i tried the above kernel. BUT i cant get gnome to start. i can start icewm and top can show 2 procs but gnome deos not start. please help.

---

### Post by vivedekananda on 2006-03-21
the kernel was compiled specifically for my machnine,
probably thats the reason why it doesn't work properly on yours

try compiling your own kernel using the instruction by edrumwri,
it worked ok for me, and thats how I made the kernelxxx.deb

---

### Post by finlaylabs on 2006-03-23
Hi, has anyone got any further with this? Boot also stalls for me with the latest x86 smp kernel : linux-image-2.6.12-10-k7-smp

It stalls on the splash screen at "Loading modules" and does nothing from there.

Im on a Sun w2100z with dual-Opteron 250's, 8GB RAM and Nvidia FX3000 DH.

The standard non-smp x86 kernel works fine.

---

### Post by vivedekananda on 2006-03-25
I have compiled a 2.6.15 smp kernel and it works fine for me for several months already

---

