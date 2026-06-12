---
title: "[SOLVED] ubuntu 8.10 only sees 3.2GB"
date: 2008-11-16
forum: x86 64-bit Users
---

### Post by melenor on 2008-11-16
I recently installed ubuntu 8.10 x64 and it only sees 3GB instead of 4GB vista sees 4GB but not ubuntu. Any help would be appreciated. thanks

---

### Post by bodhi.zazen on 2008-11-16
With that number my first guess (without going into a discussion about PAE) would be you installed the 32 bit version.

Can you post the output of ```
uname -m
```

---

### Post by melenor on 2008-11-16
```
:~$ uname -m
x86_64
```
yah i already checked this.

---

### Post by felker2 on 2008-11-16
> **melenor said:**
> I recently installed ubuntu 8.10 x64 and it only sees 3GB instead of 4GB vista sees 4GB but not ubuntu. Any help would be appreciated. thanks

Are you sure Vista really has access to the full 4GB? Vista's Control Panel will *say* "4GB" if 4GB is installed, even when Vista can only *use* 3.12 GB (for example Vista itself is 32-bit or when the hardware does something wrong). See [http://support.microsoft.com/kb/929605](http://support.microsoft.com/kb/929605)

Anyway, back to Ubuntu:
1) Which Mobo / Chipset / CPU are you using?
2) How old is your Mobo / BIOS?
3) What does "dmesg | head -25" show you?
4) What does "free -m" show you?

The important stuff in the dmesg-command is the line "BIOS-e820: 0000000100000000 - 0000000120000000 (usable)": that's memory that's mapped onto the above-4GB region, which only 64-bit HW and SW can use.



```
sander@ubuntu804:~$ dmesg | head -25
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-7-generic (buildd@crested) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Tue Nov 4 19:33:06 UTC 2008 (Ubuntu 2.6.27-7.16-generic)
[    0.000000] Command line: root=UUID=f6b0b4b8-a4c5-4dc0-a6e5-c6706741df4e ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000d7ee0000 (usable)
[    0.000000]  BIOS-e820: 00000000d7ee0000 - 00000000d7ee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000d7ee3000 - 00000000d7ef0000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000d7ef0000 - 00000000d7f00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000120000000 (usable)
[    0.000000] last_pfn = 0x120000 max_arch_pfn = 0x3ffffffff
[    0.000000] last_pfn = 0xd7ee0 max_arch_pfn = 0x3ffffffff
[    0.000000] init_memory_mapping
[    0.000000]  0000000000 - 00d7e00000 page 2M
[    0.000000]  00d7e00000 - 00d7ee0000 page 4k
[    0.000000] kernel direct mapping tables up to d7ee0000 @ 8000-e000
sander@ubuntu804:~$

```

---

### Post by melenor on 2008-11-16
1.) nForce4/not sure/AMD Athlon X2 4200+
2.) pretty old, don't think it has been updated in 2 years
3.) ```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-7-generic (buildd@crested) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Tue Nov 4 19:33:06 UTC 2008 (Ubuntu 2.6.27-7.16-generic)
[    0.000000] Command line: root=UUID=5ab39747-7cfd-46ee-9579-7ee5690e2c2e ro quiet splash 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cfff0000 (usable)
[    0.000000]  BIOS-e820: 00000000cfff0000 - 00000000cfff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cfff3000 - 00000000d0000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0xcfff0 max_arch_pfn = 0x3ffffffff
[    0.000000] init_memory_mapping
[    0.000000]  0000000000 - 00cfe00000 page 2M
[    0.000000]  00cfe00000 - 00cfff0000 page 4k
[    0.000000] kernel direct mapping tables up to cfff0000 @ 8000-e000
[    0.000000] last_map_addr: cfff0000 end: cfff0000
[    0.000000] RAMDISK: 377b1000 - 37fef58a
[    0.000000] DMI 2.3 present.

```
4.) ```
             total       used       free     shared    buffers     cached
Mem:          3269       1284       1984          0         24        335
-/+ buffers/cache:        924       2344
Swap:         3851          0       3851

```


no idea how to check exactly what mobo and chipset i have sorry.

---

### Post by felker2 on 2008-11-16
Aha:

> [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0xcfff0 max_arch_pfn = 0x3ffffffff


The Linux kernel is not seeing anything above the 0000000100000000, and thus you cannot use your 4GB.

Mobo / BIOS: "pretty old, don't think it has been updated in 2 years", which makes me think your Mobo / BIOS is the problem.

I would 1) update the BIOS and then 2) check the BIOS for something like "memory mapping" and "memory hoisting". That is the feature that maps parts of your 4GB from the IO-reserverd area to the above-4GB area, making it accessible for 64-bit OSes. You should turn that on.

If you know the brand / make / product number of your Mobo, you can find online whether it supports memory hoisting and 4+ GB at all.

---

### Post by melenor on 2008-11-17
Thank you so much. Alright I had the latest BIOS but on the FAQ it had this as a question, and it says 
```
Please do the following settings in bios setup: Bios Setup/ Advanced Chipset Feature/
DRAM Configuration/ H/W (or S/W) memory hole remapping Enabled. Then save and exit.
4G memory shown during POST and in bios is total physical memory, If the system couldn&#8217;t detect full 4G memory (available memory) under OS, please refer to our General FAQ.
```

So i did it and now it sees 4GB, I enabled both H/W and S/W Memory Hole Remapping enabled.
Now my question is what the heck is H/W Memory Hole Remapping and S/W Memory Hole Remapping.
Thanks.


mmm.. now ubuntu sees 3.9GB which is wierd i think.

---

### Post by Marshalus on 2008-11-17
I wish it was that easy on my system with this problem. Dell D820 laptop, the chipset is limited to 3.2GB even though it runs x64 Vista, Linux, XP, etc, just fine.

---

### Post by psusi on 2008-11-17
Not sure what it means by HW vs SW, but a memory hole is what you get when you have IO devices, like your video memory, mapped to addresses in the 3-4 GB area.  Those addresses go to your video card instead of to ram, so it leaves a hole of ram addresses that you can't access.  In order to access that ram, the motherboard has to remap other addresses ( above the 4 GB mark ) to those addresses in the 3-4 GB area covered by the video memory.

---

### Post by felker2 on 2008-11-18
> **Marshalus said:**
> Dell D820 laptop, the chipset is limited to 3.2GB even though it runs x64 Vista, Linux, XP, etc, just fine.

So you state you run 64-bit Ubuntu, but your memory is limited to 3.2 GB? 

Which CPU are you using? You can check that with "grep name /proc/cpuinfo".
How much RAM is installed? 
What's the output of "dmesg | head -25", "free -m" and of "uname -a"?

---

### Post by zenarcher on 2008-11-18
My system sees 3961M of the 4GB I have installed, as well.  That is due, I believe, to the fact that a certain portion of RAM is reserved and will not appear.  Looks like you have the right amount being reported, for your 4GB system RAM to me.

Cheers,
zenarcher

---

### Post by psusi on 2008-11-18
> **felker2 said:**
> So you state you run 64-bit Ubuntu, but your memory is limited to 3.2 GB? 

Which CPU are you using? You can check that with "grep name /proc/cpuinfo".
How much RAM is installed? 
What's the output of "dmesg | head -25", "free -m" and of "uname -a"?

Already asked, answered, and problem solved.

---

### Post by felker2 on 2008-11-18
> **psusi said:**
> Already asked, answered, and problem solved.

No, not for Marshalus. Read Marshalus' (= not OP!) post, my quote of his post and my questions to him (not the OP).

---

### Post by felker2 on 2008-11-18
> **felker2 said:**
> So you state you run 64-bit Ubuntu, but your memory is limited to 3.2 GB? 

Which CPU are you using? You can check that with "grep name /proc/cpuinfo".
How much RAM is installed? 
What's the output of "dmesg | head -25", "free -m" and of "uname -a"?

@Marshalus:

On top of the earlier tests, you can test whether your CPU is 64-bit by looking at "grep flags /proc/cpuinfo | grep lm". If that gives output, you have a 64-bit CPU.

The "lm" flag stands for x86-64 / AMD64 (formally "Long Mode (x86-64)")

See kernel file /usr/include/asm/cpufeature.h:

#define X86_FEATURE_LM		(1*32+29) /* Long Mode (x86-64) */

HTH

---

### Post by bodhi.zazen on 2008-11-18
> **felker2 said:**
> On top of the earlier tests, you can test whether your CPU is 64-bit by looking at "grep flags /proc/cpuinfo | grep lm". If that gives output, you have a 64-bit CPU.

How about :

```
grep --color=always lm /proc/cpuinfo
```

If you see a red lm in the output -> you have a 64 bit processor (color is always nice).

(you do not need to grep flags and pipe it to grep lm).

---

### Post by felker2 on 2008-11-18
> **bodhi.zazen said:**
> How about :

```
grep --color=always lm /proc/cpuinfo
```

If you see a red lm in the output -> you have a 64 bit processor (color is always nice).

Cool!

> **bodhi.zazen said:**
> 

(you do not need to grep flags and pipe it to grep lm).

Well, I did that to avoid any unwanted hits on 'lm' anywhere in /proc/cpuinfo, for example a processor named "Almond" or something like that.

---

### Post by bodhi.zazen on 2008-11-18
> **felker2 said:**
> Cool!

Well, I did that to avoid any unwanted hits on 'lm' anywhere in /proc/cpuinfo, for example a processor named "Almond" or something like that.

Well, add single quotes then :twisted:

grep --color=always ' lm ' /proc/cpuinfo

notice it is ' lm ' ( '<space>lm<space>') not 'lm' (no spaces)

will not match "Almond"

---

### Post by dcstar on 2008-11-19
> **melenor said:**
> 
.......
mmm.. now ubuntu sees 3.9GB which is wierd i think.

Do a search on the difference between GiB and GB.

---

