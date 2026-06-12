---
title: "xen-hypervisor-3.0-amd64 crash reboot"
date: 2006-10-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by tall-male on 2006-10-30
I installed Xen xen-hypervisor-3.0-amd64 (Edgy AMD64 with Intel Core 2 Duo E6600) using the following Grub config:

title Xen 3.0 
       kernel /xen-3.0-amd64.gz
       module /xen0-linux-2.6.17-6-generic-xen0 root=/dev/sdb3 ro 
       module /xen0-linux-2.6.17-6-generic-xen0.initrd.img
       savedefault
       boot

However, soon after the kernel boots, it seems to crash causing a reboot. I managed to make a screenshot just before the reboot. (see picture) It hardly gives any valuable information.

Just about the same configuration on an AMD 32 bit system boots perfectly. Anyone having the same.

---

### Post by hernan43 on 2006-10-30
I am having the same exact problem. I am using the not-64-bit version though. I too have a Core 2 Duo setup.

---

### Post by johnyaya on 2006-10-30
I am having problems with booting the amd64 hypervisor as well. In my case, I get a message: "Kernel panic - not syncing: Attempted to kill the idle task!"

My grub/menu.lst:
title XEN/2.6.17
root (hd0,0)
kernel /boot/xen-3.0-amd64.gz
module /boot/xen0-linux-2.6.17-6-generic-xen0 root=/dev/sda1 ro
module /boot/xen0-linux-2.6.17-6-generic-xen0.initrd.img

# cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      :                   Intel(R) Xeon(TM) CPU 2.80GHz
stepping        : 1
cpu MHz         : 2800.197
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 1
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall lm constant_tsc pni monitor ds_cpl cid cx16 xtpr
bogomips        : 5604.47
clflush size    : 64
cache_alignment : 128
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      :                   Intel(R) Xeon(TM) CPU 2.80GHz
stepping        : 1
cpu MHz         : 2800.197
cache size      : 1024 KB
physical id     : 3
siblings        : 2
core id         : 0
cpu cores       : 1
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall lm constant_tsc pni monitor ds_cpl cid cx16 xtpr
bogomips        : 5600.69
clflush size    : 64
cache_alignment : 128
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 2
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      :                   Intel(R) Xeon(TM) CPU 2.80GHz
stepping        : 1
cpu MHz         : 2800.197
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 1
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall lm constant_tsc pni monitor ds_cpl cid cx16 xtpr
bogomips        : 5600.58
clflush size    : 64
cache_alignment : 128
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 3
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      :                   Intel(R) Xeon(TM) CPU 2.80GHz
stepping        : 1
cpu MHz         : 2800.197
cache size      : 1024 KB
physical id     : 3
siblings        : 2
core id         : 0
cpu cores       : 1
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall lm constant_tsc pni monitor ds_cpl cid cx16 xtpr
bogomips        : 5600.72
clflush size    : 64
cache_alignment : 128
address sizes   : 36 bits physical, 48 bits virtual
power management:

---

### Post by ajajaj on 2006-10-30
> 

Just about the same configuration on an AMD 32 bit system boots perfectly. Anyone having the same.

I too, am having this problem on AMD 3800+ AM2 system

When running 32bit xen it works fine.

The minute I try to run 64 bit xen from universe, it does the same thing as above.

HOWEVER, installing from binaries works as far as booting dom0, but no domU's will boot.

---

### Post by robert114 on 2006-11-01
My Xen kernel doesn't boot either I'm using edgy 64

---

### Post by robert114 on 2006-11-02
so ajajaj, installing the 32 bit binaries doesn't help either?

---

### Post by xucchini on 2006-11-03
Just FYI my xen kernel stalls on reboot after installing 

xen-hypervisor-3.0
xen-image-xen0-2.6.17-6-generic-xen0
xen-utils-3.0

and running

mkinitramfs -o /boot/xen0-linux-2.6.17-6-generic-xen0.initrd.img 2.6.17-6-generic-xen0

This is amd64 Edgy server.

It usually freezes where last kernel msg is "migration_cost=420", 
or "PCI: Using configuration type 1".

---

### Post by glenndavy on 2006-11-03
just putting my hand up to say have I have same/similar issue - kernel panic, then reboot  during boot from xen-3.0-amd64. too fast to take in message. 
I have intel core2duo 6300. for any other information that may help - just ask :-)
thx
glenn

---

### Post by ddave01 on 2006-11-05
Yep, got similar results (with my 2x64 AMD4600) following the howto.

Xen starts to boot, runs scripts/local-premount then scripts/local-bottom and after scripts/init-bottom it hangs.

Not sure what else I can offer as help.

Has someone submitted a bug report?  Anyone tried to compile the source?

ddave

---

### Post by BullCreek on 2006-11-08
Another me too - Turion 64x2 notebook.  Sure would like to get Xen working so I can run trixbox and xp in VMs.  Has anyone had any luck solving this problem???

---

### Post by skenliv on 2006-11-09
Same problem here, AMD64 X2 3800+, Have not found any solution to this problem.

---

### Post by genibot on 2006-11-10
I

---

### Post by genibot on 2006-11-10
I get the same error: "Kernel panic - not syncing: Attempted to kill the idle task!" I followed the XenOnEdgy Wiki and my hardware is Intel Xeon dual cores.  Has anyone solved this yet?  Or is anyone else successfully running the Xen-3.0-amd64?

---

### Post by incubus on 2006-11-10
Hi,

Here's the bug complaint in launchpad:

[https://launchpad.net/distros/ubuntu/+source/xen-source-2.6.17/+bug/65788](https://launchpad.net/distros/ubuntu/+source/xen-source-2.6.17/+bug/65788)

Please make sure you join launchpad and post the error messages you're getting there as well -- that's where and how the developers will get feedback.

cheers,
incubus

---

### Post by ariebs on 2006-11-15
In the grub/menu.lst clause, note that you can specify "noreboot" as an argument to xen to keep the system from rebooting and, thus, to preserve the last screen of output. For example, I've got

```

title ubuntu Xen 2.6.16
root            (hd0,1)
kernel /boot/xen-3.0-amd64.gz noreboot
module /boot/xen0-linux-2.6.16-11.2-generic root=/dev/c0d0p2 ro console=tty1
module /boot/xen0-linux-2.6.16-11.2-generic.initrd.img

```

/andy

---

### Post by incubus on 2006-11-15
> **ariebs said:**
> In the grub/menu.lst clause, note that you can specify "noreboot" as an argument to xen to keep the system from rebooting and, thus, to preserve the last screen of output. For example, I've got

```

title ubuntu Xen 2.6.16
root            (hd0,1)
kernel /boot/xen-3.0-amd64.gz noreboot
module /boot/xen0-linux-2.6.16-11.2-generic root=/dev/c0d0p2 ro console=tty1
module /boot/xen0-linux-2.6.16-11.2-generic.initrd.img

```

/andy

Neat trick!  Thanks.

incubus

---

### Post by lprofil on 2006-12-08
Another **"Me too"**

Systemspecs: 

System:           Edgy Eft **64-bit**
Motherboard:      **Asus M2NPV-VM**
HDD: Samsung IDE  SAMSUNG SP2014N
Processoer:       **AMD Athlon 64 3000+**

I will try the tweak with the no reboot feature to post my
error message of xen.
---
Back! The error message is:

[B]RIP <ffffffff8025fd75>{cache_alloc_refill+836} RSP <ffffffff8025fd75>
CR2: ffff880000573020
<0> Kernel panic - not syncing: Attempted to kill the idle task![/B]


Besides: I also tried the Edgy 32-bit version where i get the 

```
kernel: powernow-k8: transition frequency failed
kernel: powernow-k8: fid trans failed, fid 0xa, curr 0x0
```

error.

This is a known bug and actually [there is a patch for it]("http://http://article.gmane.org/gmane.comp.emulators.xen.devel/22282").

Damn, they deleted the site. The link does not exsist anymore.

"Usual" compiling is no problem for me and i also got a "normal" kernel 
compiled. But how to patch a xen-kernel with a binary-patch?
I have no clue.

Anybody who knows how to compile **Xen from Source** on Edgy?

Thanks in advance.

/lprofil

ps: on my Pentium III 733MHz-Server Xen runs like a charme :-/

---

### Post by shadowman on 2006-12-25
Ok well i've got it to quit hanging on boot by adding nousb nosmp to the boot line in grub. See below.  Unfortunately when it boots to the ubuntu log in screen it is ok for about 3 seconds and then reboots.  
I am using an HP notebook with AMD Turion 64 X2 cpu and 1GB ram.

 To make matters worse I don't seem to be able to boot to runlevel 3 with the wonderous new upstart package-even though the doc says "Nothing has changed.  Edit or create the /etc/inittab so that the default runlevel line reads id:3:initdefault:" .  I have this to say about that..not.  Ok I'm ranting and off topic here..sorry.

Anyway here is the menu.lst:
```

title           Ubuntu\Xen 2.6.17-10
root            (hd0,4)
kernel          /xen-3.0-amd64.gz
module          /xen0-linux-2.6.17-6-generic-xen0 root=/dev/sda2 ro nousb nosmp
module          /xen0-linux-2.6.17-6-generic-xen0.initrd.img

```

Anybody know what I need to boot with an ATI Technologies Inc RS482 [Radeon Xpress 200M] card?

---

### Post by e1geo on 2006-12-27
Anyone know if lvm2 runs under edgy xen? My amd64 system hangs while it is examining the disks, which, aside from /boot, are lvm2/raid. Thanks.

---

