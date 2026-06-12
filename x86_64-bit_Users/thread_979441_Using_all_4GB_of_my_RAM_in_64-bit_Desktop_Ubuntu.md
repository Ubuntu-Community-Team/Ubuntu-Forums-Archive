---
title: "Using all 4GB of my RAM in 64-bit Desktop Ubuntu"
date: 2008-11-12
forum: x86 64-bit Users
---

### Post by Griddleabus on 2008-11-12
Hello,

I am new to forum, but I have been using Ubuntu for a few years. 

I have an HP Pavilion a1477c and I just added in more RAM, for a total of 4GB of RAM; I am running 8.10 Ubuntu 64-bit. Well, Ubuntu only notices 3280908 total RAM, via *free* command. When I F-key into my BIOS settings, all 4GB are shown; however, HP boot-up screen (prior to OS taking over) shows only 3.3GB (approx).

:confused: Am I stuck with losing 1GB of usable RAM, from my 4GB total? Is Ubuntu at fault? Likely user-error (me) at some point? Is my hardware at fault? What can I try next? ](*,)

I have been through numerous thread archives on various web sites and I tried everything I found so far (tried server edition; checked BIOS for remapping options and saw none; added *iommu=noaperture* to the kernel boot line; and some other ideas I came across on Google. None have worked so far. FYI- I have no license for any 64-bit Windows OS, in order to test if Windows can see all 4GB; however, VirtualBox limits my 32-bit XP-Pro to 2GB - which is same thing when I try native\dual-boot install XP-Pro - which I expected technically speaking, due to nature of 32-bit and adding more RAM than that).


HP [lists]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00617492&lc=en&dlc=&cc=us&product=1847040") this PC's RAM maximum as (note the asterisk isn't very informative, but it does make me wonder how much, specifically, may not be seen): > "4 GB* (4 x 1 GB) requires the replacement of the installed 512 MB DIMMs

*Actual available memory may be less"

----

Other info:

> $ uname -a

Linux GONZO 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:06 UTC 2008 x86_64 GNU/Linux

-

> $ free
             total       used       free     shared    buffers     cached
Mem:       3280908    3248556      32352          0       9440    1409448
-/+ buffers/cache:    1829668    1451240
Swap:      2819368       5612    2813756

-

> $ uname -m
x86_64


-

> $ uname -r 
2.6.27-7-generic

-

> $ dmesg | head -20
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-7-generic (buildd@crested) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Tue Nov 4 19:33:06 UTC 2008 (Ubuntu 2.6.27-7.16-generic)
[    0.000000] Command line: root=UUID=6cd8f58a-d9eb-44f0-a3a4-27f290a357c8 ro quiet splash 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cbef0000 (usable)
[    0.000000]  BIOS-e820: 00000000cbef0000 - 00000000cbef3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cbef3000 - 00000000cbf00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0xcbef0 max_arch_pfn = 0x3ffffffff
[    0.000000] init_memory_mapping
[    0.000000]  0000000000 - 00cbe00000 page 2M

---

### Post by jmate24 on 2008-11-12
bios may need updating. if you can backup your files on ubuntu, back them up and then wipe and install windows then install your LAN Driver that is on the CD that came with your motherboard. then go to the motherboard manufacturers website and look for a bios update it is usualy in their 'Support' or 'Downloads' section of thier website then download and install it may need a floppy but might not because it is a 64-bit board or if they have an online install/updater use it. then wipe and install ubuntu or your favorite linux OS and restore your files.

---

### Post by Griddleabus on 2008-11-12
hi jmate24, My BIOS is the current version (I forgot to mention in my post that I already checked this).

---

### Post by Jouke74 on 2008-11-12
*"Actual available memory may be less" 

This is actually very informative. Check if your BIOS has a memory remapping function (PAE or stuff like that). Read your motherboard manual and use them if they are not turned on. Even with all these options correct it might not be possible to see all memory. Depends on the motherboard.

---

### Post by EV500B on 2008-11-12
I've heard somewhere that to be able to do that you must patch the kernel or modify something in it as by default it's limited; Don't know why! :-\"
So if you want to you can go to that link [http://www.linux.com/feature/119287](http://www.linux.com/feature/119287) .

---

### Post by Griddleabus on 2008-11-12
Jouke74, as already noted, I tried those options previously. :confused: Yes, it might not be possible. That is what I am trying to find out, whether that "might" is a yes, or a no.

I am still curious whether Ubuntu is at fault, or not (as noted already, my BIOS settings show all 4gb - but my boot-up memory result (before OS takes over) is roughly 3.3____GB; so, does this mean that my OS (Ubuntu 64-bit, 8.10) is not at fault?

EV500B, thanks for the link. I'll try this section when I get back to the PC in question: > On some distributions, you can add a generic kernel that meets your requirement in a matter of moments. In Debian, for instance, use the apt-cache search command to locate a recent linux-image package for a kernel for a 686 processor if you want support for up to 4 gigabytes. If you want support for up to 64 gigabytes, look for a kernel that ends with 686-bigmem. These kernels will enable support for 64GB. Unfortunately, a generic kernel for only 4GB does not exist. Similarly, in Ubuntu, look for a recent kernel image whose package name ends in smp; these kernels are designed for dual core processors, but work on single core processors as well, although sometimes with a small performance hit.

If your distribution does not include a useful generic kernel, or if you want to fine-tune the use of high memory on your system, you need to compile a custom kernel. You should consult your distribution's documentation for the details of where to get the source code and headers and any unique aspects of compiling a kernel for it. However, enabling high memory support involves no more than five parameters in the Firmware Drivers section:

    * Make sure that CONFIG_NOHIGHMEM is not set.
    * Set either CONFIG_HIGHMEM4G or CONFIG_HIGHMEM64G to yes, using whichever one is appropriate for the RAM in your system. If you have Note that you should use the 4 gigabyte parameter for less than 4 gigabytes of RAM, and the 64 gigabyte parameter for 4 or more gigabytes (4 gigabytes of RAM, remember is actually slightly more than that).
    * Set CONFIG_HIGHMEM to yes.
    * Optionally, set CONFIG_DEBUG_HIGHMEM to yes if you want to log error messages. Since many generic kernels turn this option off, you can probably do without it, especially if you do not delete other kernels from your boot manager's menu, so that you can still start your computer if your newly compiled kernel is unusable.

Compile the rest of the kernel as you choose and install it in your boot manager's menu. Consult the documentation for your boot manager for the details of how to do this.

The next time you start your system, run free -m again. This time, the results should reflect the actual amount of RAM installed. In the few cases that it does not, add a parameter to your boot manager to specify the amount of memory on the system. For both GRUB and LILO, the parameter is mem=<amount of RAM>M, placed just after the name of the customized kernel. The amount of RAM should be in megabytes.

Eventually, this problem will disappear as either high memory kernels become the norm in distributions or the transition to 64-bit Linux is finally complete. However, for the next year or so, this solution is likely to remain useful for anyone perplexed by the apparent lack of RAM on their system.

---

### Post by jespdj on 2008-11-12
Note that the whole story with the kernel parameters etc. from EV500B is talking about 32-bit kernels, not 64-bit kernels. With a 64-bit kernel, there is no 4GB limit.

You're not the only one who can't use the whole 4 GB. The BIOS reserves part of the address space for communication with devices such as the video card. Because of this, not the whole 4GB is accessible to the operating system (even if you use a 64-bit OS).

To make the whole 4 GB accessible (or at least 3.8 or 3.9 GB), you need to enable memory remapping in the BIOS. Look around in the BIOS settings if there is a "memory remapping" (or something similar) setting. This setting moves the addresses of devices out of the way, so that the whole RAM can be used.

If your BIOS doesn't have such a setting, then you're most likely out of luck...

---

### Post by Biznoogity on 2008-11-12
Your integrated graphics chipset is reserving a chunk of your RAM.  Set this limit in your BIOS.  Unfortunately you will not get full use of this RAM unless you can disable the onboard graphics and install a new graphics card.  Good luck.

---

### Post by EV500B on 2008-11-13
> **jespdj said:**
> Note that the whole story with the kernel parameters etc. from EV500B is talking about 32-bit kernels, not 64-bit kernels. With a 64-bit kernel, there is no 4GB limit.

You're not the only one who can't use the whole 4 GB. The BIOS reserves part of the address space for communication with devices such as the video card. Because of this, not the whole 4GB is accessible to the operating system (even if you use a 64-bit OS).

To make the whole 4 GB accessible (or at least 3.8 or 3.9 GB), you need to enable memory remapping in the BIOS. Look around in the BIOS settings if there is a "memory remapping" (or something similar) setting. This setting moves the addresses of devices out of the way, so that the whole RAM can be used.

If your BIOS doesn't have such a setting, then you're most likely out of luck...

One difference between the 32bit and 64bit in memory "managing" is in fact that the first one cannot allocate more than 3,454Mb to one application and the second one can. 
Both can have more than 4Gb RAM installed but the 32bit OS will only recognize or use 3Gb,.,.
Surprisingly, in some 64bit operating systems the ability to manage more than 3Gb.. is disabled by default.
Or It can also be the thing that you're saying so if [Griddleabus]("http://ubuntuforums.org/member.php?u=705243") could check in other operating systems like Vista64bit(Sorry some of you don't like it;as i do!) that it is activated in his/her pc's bios.

---

### Post by jmate24 on 2009-04-10
now i am having a similar problem with my 64-bit laptop i originally had 2GB of ram but my laptop can handle 4 so i put in another 2GB SODIMM and now it only sees 2.9GB of the 3GB that is in there.

but i think it has to do with how you calculate the size of ram/hard disk space like, i have a 1,000GB HDD but it only sees 934.5GB of space and each drive is different if i were to go out and by a new 1TB HDD then it might be 929.7GB of space. because of the 'margin of error' the drives and memory are different sizes.

so, don't be alarmed it could just be in the wide realm of 'normal'.

jmate24--

---

### Post by _khAttAm_ on 2009-04-10
what does memtest say?

---

### Post by Slim Odds on 2009-04-10
> **jmate24 said:**
> now i am having a similar problem with my 64-bit laptop i originally had 2GB of ram but my laptop can handle 4 so i put in another 2GB SODIMM and now it only sees 2.9GB of the 3GB that is in there.

Where I come from, 2+2=4    :p

Someone really needs to come up a comprehensive post that deals with this issue. There is so much confusion.

Most of the time, it seems to be an improperly configured or out of date BIOS.

When the "memory remapping"/"memory hole", etc. is enabled, then you'll get the most usable memory. Also, shared memory (like for some video adapters) will eat into the total available.

I have an ASUS mobo with 8G RAM and here's what I get:```
free -m
             total       used       free     shared    buffers     cached
Mem:          7991       4769       3221          0        112       3719
-/+ buffers/cache:        937       7053
Swap:         7812          0       7812

```

---

### Post by jojo1224 on 2009-04-10
Its probably the onboard video card using some of the ram as its own. I know on my server and my laptop I can adjust it from 16MB -128MB but my machines are old so they don\t go over 128MB but my friends newer laptops can use like 386MB ram for the video card.

---

