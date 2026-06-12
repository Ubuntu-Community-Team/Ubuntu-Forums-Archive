---
title: "64bit only finding 3GB Ram?"
date: 2008-05-06
forum: x86 64-bit Users
---

### Post by StephenDeli22 on 2008-05-06
I just upgraded from 2gb to 4gb of Ram.  My BIOS recognizes 4gb but Ubuntu only recognizes 3gb?  I have done searches but this seems to only be a problem with 32bit OS'.  Im wondering why my 64bit is not seeing all of the ram????

---

### Post by amohanty on 2008-05-06
Can you post the output of 
uname -a

AM

---

### Post by felker2 on 2008-05-06
And post the first 15 lines of dmesg ("dmesg | head -15"), as explained on [http://ubuntuforums.org/showpost.php?p=4683674&postcount=3](http://ubuntuforums.org/showpost.php?p=4683674&postcount=3)

---

### Post by jespdj on 2008-05-06
Some possibilities:

Does your BIOS have a 'memory remapping' setting somewhere? Make sure that it is enabled.

Do you have a video card that doesn't have its own dedicated video memory, but uses part of the main memory instead? If yes, then that's where your memory has gone.

Some motherboards or BIOSes unfortunately don't support 4 GB very well, so that part of the memory won't show up. You could try finding the latest BIOS version on the website of your motherboard manufacturer and flashing your BIOS to the latest version.

---

### Post by Julius on 2008-05-06
> **jespdj said:**
> Some possibilities:
[B]
Does your BIOS have a 'memory remapping' setting somewhere? Make sure that it is enabled.[/B]



I would definitely check this first

---

### Post by fbroce on 2008-05-06
> **StephenDeli22 said:**
> I just upgraded from 2gb to 4gb of Ram.  My BIOS recognizes 4gb but Ubuntu only recognizes 3gb?  I have done searches but this seems to only be a problem with 32bit OS'.  Im wondering why my 64bit is not seeing all of the ram????

Try this:

Make sure the memory hole remapping in your bios is enabled ..
and add this to your grub or lilo boot config.

iommu=65534,noagp,soft

grub is in /boot/grub then edit menu.lst and append this to the kernel line:

/boot/vmlinuz-2.6.24-16-generic root=UUID=96b6fee4-e087-428b 22a-cdcee67f502f ro quiet iommu=65534,noagp,soft

lilo.conf

append="iommu=65534,noagp,soft"

That fixed it for me.

Fred

---

### Post by StephenDeli22 on 2008-05-06
> **jespdj said:**
> Some possibilities:

Does your BIOS have a 'memory remapping' setting somewhere? Make sure that it is enabled.

Do you have a video card that doesn't have its own dedicated video memory, but uses part of the main memory instead? If yes, then that's where your memory has gone.

Some motherboards or BIOSes unfortunately don't support 4 GB very well, so that part of the memory won't show up. You could try finding the latest BIOS version on the website of your motherboard manufacturer and flashing your BIOS to the latest version.


I am at work right now so I cannot run any of those commands just yet.  However, my BIOS does recognize 4gb, it is ubuntu that does not. HP's BIOS is very crippled and will not let me change anything to do with memory remapping.  BIOS is also updated to the most recent version.

I have an NVIDIA GeForce 7400, 128mb shared and 128mb discrete.  So it is not taking a full gb away.

I will post the output of the commands posted recently as soon as I can.

---

### Post by fbroce on 2008-05-06
I think if you will try what I suggested it will work. PCI-E takes some memory in the 3 to 4 gb range. The kernel options will allow remapping memory.

Fred

---

### Post by StephenDeli22 on 2008-05-06
Where exactly in grub will I be appending this to?  Im not sure exactly where to put it.  Also, why cant I save in Grub, it says I have no permission??

---

### Post by adi_8079 on 2008-05-07
> **fbroce said:**
> Try this:

Make sure the memory hole remapping in your bios is enabled ..
and add this to your grub or lilo boot config.

iommu=65534,noagp,soft

grub is in /boot/grub then edit menu.lst and append this to the kernel line:

/boot/vmlinuz-2.6.24-16-generic root=UUID=96b6fee4-e087-428b 22a-cdcee67f502f ro quiet iommu=65534,noagp,soft

lilo.conf

append="iommu=65534,noagp,soft"

That fixed it for me.

Fred

Hi, I have more or less the same problem. I can see only 3.8Gb instead of 4Gb. Should I be able to see all of it? 
I have a Thinkpad T61p and recently upgraded the memorry to 4Gb, which is by the way recognized by the BIOS (however, no memory remapping function :(). The video card came with discrete memory. 

below is the output for "dmesg | head -20"

```
[    0.000000] Linux version 2.6.24-16-generic (buildd@yellow) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 12:47:45 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
[    0.000000] Command line: root=UUID=07ddd84e-075f-4443-babf-c06c3357fbb5 ro quiet splash iommu=65534,noagp,soft
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d800 (usable)
[    0.000000]  BIOS-e820: 000000000009d800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bfeb0000 (usable)
[    0.000000]  BIOS-e820: 00000000bfeb0000 - 00000000bfecc000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bfecc000 - 00000000bff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bff00000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 000000013c000000 (usable)
[    0.000000] Entering add_active_range(0, 0, 157) 0 entries of 3200 used

```

---

### Post by lamborghiniwang on 2008-05-07
> **adi_8079 said:**
> Hi, I have more or less the same problem. I can see only 3.8Gb instead of 4Gb. Should I be able to see all of it? 
I have a Thinkpad T61p and recently upgraded the memorry to 4Gb, which is by the way recognized by the BIOS (however, no memory remapping function :(). The video card came with discrete memory. 

below is the output for "dmesg | head -20"

```
[    0.000000] Linux version 2.6.24-16-generic (buildd@yellow) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 12:47:45 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
[    0.000000] Command line: root=UUID=07ddd84e-075f-4443-babf-c06c3357fbb5 ro quiet splash iommu=65534,noagp,soft
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d800 (usable)
[    0.000000]  BIOS-e820: 000000000009d800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bfeb0000 (usable)
[    0.000000]  BIOS-e820: 00000000bfeb0000 - 00000000bfecc000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bfecc000 - 00000000bff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bff00000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 000000013c000000 (usable)
[    0.000000] Entering add_active_range(0, 0, 157) 0 entries of 3200 used

```

I think you're fine. I am also running 64bit Hardy on a T61p (14" version) and I'm also seeing 3.8GB. In dmesg I see the following line:
```

[   13.847626] Memory: 3976864k/5177344k available (2466k kernel code, 150164k reserved, 1309k data, 316k init)

```
I assume the ~150MB of reserved memory refers to those marked as "reserved" in the BIOS-e820 lines, while the "PCI-E memory" hole usually refers to the one "0000000100000000 - 000000013c000000" which is marked as "usable" in the T61p case.

---

### Post by jazzman65 on 2008-05-07
I've got the exact same problem with Hardy only seeing 3 GB of RAM.  The bios sees all 4, but Hardy only reads about 3.1.  Can't quite figure out why just yet.  Otherwise, I'm loving 64 bit!  :)

---

### Post by StephenDeli22 on 2008-05-07
> **fbroce said:**
> Try this:

Make sure the memory hole remapping in your bios is enabled ..
and add this to your grub or lilo boot config.

iommu=65534,noagp,soft

grub is in /boot/grub then edit menu.lst and append this to the kernel line:

/boot/vmlinuz-2.6.24-16-generic root=UUID=96b6fee4-e087-428b 22a-cdcee67f502f ro quiet iommu=65534,noagp,soft

lilo.conf

append="iommu=65534,noagp,soft"

That fixed it for me.

Fred

Well I figured out how to input that into grub and now ubuntu wont load. It says loading kernel and never does anything.  My recovery one does work though.... Any thoughts?

---

### Post by fbroce on 2008-05-07
You append it to the kernel line in grub. It worked for me. My bios sees the 4096mb ram but unless I use the iommu=65534,noagp,soft in lilo.conf, I don't see the 4gb ram. It should work with grub also..just append it to the kernel line in /boot/grub/menu.lst

kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=96b6fee4-e087-428b 22a-cdcee67f502f ro quiet iommu=65534,noagp,soft

reboot and cross your fingers!

Fred

---

### Post by adi_8079 on 2008-05-07
> **lamborghiniwang said:**
> I think you're fine. I am also running 64bit Hardy on a T61p (14" version) and I'm also seeing 3.8GB. In dmesg I see the following line:
```

[   13.847626] Memory: 3976864k/5177344k available (2466k kernel code, 150164k reserved, 1309k data, 316k init)

```
I assume the ~150MB of reserved memory refers to those marked as "reserved" in the BIOS-e820 lines, while the "PCI-E memory" hole usually refers to the one "0000000100000000 - 000000013c000000" which is marked as "usable" in the T61p case.

I guess you are right, I did dmesg again and I'm able to see the same thing you did. Thanks, I feel relieved :)
```
[   17.601022] Memory: 3977672k/5177344k available (2466k kernel code, 149356k reserved, 1309k data, 316k init)
```

---

### Post by StephenDeli22 on 2008-05-08
> **fbroce said:**
> You append it to the kernel line in grub. It worked for me. My bios sees the 4096mb ram but unless I use the iommu=65534,noagp,soft in lilo.conf, I don't see the 4gb ram. It should work with grub also..just append it to the kernel line in /boot/grub/menu.lst

kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=96b6fee4-e087-428b 22a-cdcee67f502f ro quiet iommu=65534,noagp,soft

reboot and cross your fingers!

Fred


Like I said earlier, Im pretty sure I did something wrong.  Now my main kernel isnt booting but the recovery one will.  Is there a way to edit the kernel without it actually loading.  Could you also post your entire kernel with the appended memory finder?

---

### Post by raidensix on 2008-05-08
You can always boot using the recovery kernel and edit the menu.lst  .

---

### Post by lazyart on 2008-05-08
I just upgraded my machine to 4 gb and had the same problem.

THIS IS NOT UNUSUAL.  The top of memory is also the address space for devices and it makes the memory inaccessible.

You can read about it here: [http://www.itwriting.com/blog/?postid=152](http://www.itwriting.com/blog/?postid=152)

Don't blame anyone but the motherboard manufacturers.

---

### Post by jazzman65 on 2008-05-08
> **lazyart said:**
> I just upgraded my machine to 4 gb and had the same problem.

THIS IS NOT UNUSUAL.  The top of memory is also the address space for devices and it makes the memory inaccessible.

You can read about it here: [http://www.itwriting.com/blog/?postid=152](http://www.itwriting.com/blog/?postid=152)

Don't blame anyone but the motherboard manufacturers.

But is it really motherboard-related if the bios sees all 4 GB's?  My mobo reports 4086M, but Hardy only reports 3 GiB.  That's what is a little confusing to me.

I tell you though, I'm loving this 64 bit!  \\:D/

---

### Post by Jouke74 on 2008-05-09
Yes it is motherboard related. Furthermore, the assumption that all your memory that the BIOS sees is also available for the OS is simply wrong.

---

### Post by jazzman65 on 2008-05-09
If that assumption is incorrect and the bios-reported memory is not completely available to the OS, then I'm curious to know why that is, especially to the tune of almost a full GB.  Also, I've seen other posts where Hardy recognizes almost the same amount of memory that the bios reports.  My mobo is spec'ed to support 8 GB, so I guess I just didn't expect to lose a full GB when going up to 64 bit.

I'd just like to understand why!  :)

---

### Post by lazyart on 2008-05-09
Funny thing is, after I posted about the missing gig, I went into my system setup and found a setting that would let me remap the "memory hole".  I enabled it and unlocked the rest of my RAM (I now show 3900+ MB). Check your bios and see if there is anything relating to memory hole or DRAM 4GB.

I'm sure there is a reason why it's disabled by default-- I speculate that it might affect performance (I think I noticed a hit but I can't say for sure).

---

### Post by jazzman65 on 2008-05-09
I've searched my bios and I haven't found anything about memory remapping, etc.  To me, it would be strange if it was disabled by default because this mobo is supposed to handle 8 GB.

---

### Post by lefterist on 2008-05-09
My BIOS has the memory remapping option and its suppose to support up to 8G but still the hardy desktop kernel failed to see the memory after installing another 2G RAM (4G total). I installed the server kernel and everything works good without using any additional kernel options.

---

### Post by jespdj on 2008-05-10
lefterist: Are you sure you are running 64-bit Ubuntu? The 32-bit Ubuntu Server kernel has support for [PAE]("http://en.wikipedia.org/wiki/Physical_Address_Extension") built in and that's why even the 32-bit version can see more than 3.x GB. (PAE is a trick to make a 32-bit OS be able to address more than 4 GB).

---

### Post by lefterist on 2008-05-10
> **jespdj said:**
> lefterist: Are you sure you are running 64-bit Ubuntu? The 32-bit Ubuntu Server kernel has support for [PAE]("http://en.wikipedia.org/wiki/Physical_Address_Extension") built in and that's why even the 32-bit version can see more than 3.x GB. (PAE is a trick to make a 32-bit OS be able to address more than 4 GB).

I sure hope so! :)
$ uname -m
x86_64

$ dmesg | head -n 20
> [    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-16-server (buildd@yellow) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:15:38 UTC 2008 (Ubuntu 2.6.24-16.30-server)
[    0.000000] Command line: root=UUID=379be512-5c1a-4e8f-b565-299d3320962d ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cff80000 (usable)
[    0.000000]  BIOS-e820: 00000000cff80000 - 00000000cff8e000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cff8e000 - 00000000cffe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cffe0000 - 00000000d0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 851840) 1 entries of 3200 used
[    0.000000] Entering add_active_range(0, 1048576, 1245184) 2 entries of 3200 used
[    0.000000] end_pfn_map = 1245184
[    0.000000] DMI 2.4 present.


---

### Post by StephenDeli22 on 2008-05-10
uname -m
```
x86_64
```

dmesg | head -n 20
```
[    0.000000] Linux version 2.6.24-16-generic (buildd@yellow) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 12:47:45 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
[    0.000000] Command line: root=UUID=af8d831b-f181-45dc-903b-2b06546274f7 ro quiet splash iommu=65534,noagp,soft
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bfe70000 (usable)
[    0.000000]  BIOS-e820: 00000000bfe70000 - 00000000bff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bff00000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 786032) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI present.

```

With that code appended to my kernel line my ram dropped from 3.0 to 2.9.  My BIOS still sees 4gb.  Anyone have any ideas?

---

### Post by fjgaude on 2008-05-10
Well, it is difficult to know the "why" of this kind of issue. I have two partitions on a drive, one for Ubuntu 64-bit; the other, 32-bit. In one case the OS shows 4GB; in the other, 3.6GB. Nothing in the BIOS is changed and there is nothing there to change regarding re-mapping memory.

My MB is Gigabyte GA-P35-DS4.

When folks start using 8GB I'm sure we will find more issues with less than max RAM showing.

---

### Post by Kilz on 2008-05-10
> **lefterist said:**
> I sure hope so! :)
$ uname -m
x86_64

and 
> **StephenDeli22 said:**
> uname -m
```
x86_64
```

uname -m gives you the hardware type, not the installed operating system . Its possible to install the i386 version on 64bit hardware. 
What does ```
uname -a
``` return.

---

### Post by dcstar on 2008-05-10
> **fjgaude said:**
> 
I have two partitions on a drive, one for Ubuntu 64-bit; the other, 32-bit. In one case the OS shows 4GB; in the other, 3.6GB. Nothing in the BIOS is changed and there is nothing there to change regarding re-mapping memory.


That is exactly how things should work, a 32 bit O/S will "max out" at under 4G (because motherboard resources will use address space), and a 64 bit O/S will go past that limit (if the M/B allows it to.......)

---

### Post by StephenDeli22 on 2008-05-11
> **Kilz said:**
> What does ```
uname -a
``` return.

```
Linux stephen-laptop 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64 GNU/Linux

```

---

### Post by olivierp on 2008-05-11
Those seeing 3.8/3.9Gb may be chasings ghosts for the last 100Mb...
Be careful of rounding with Kb Mb & Gb values.
I have 4Gb in this laptop, no kernel options, and a BIOS that doesn't allow remapping of the "3Gb memory hole". The graphics card is a NVidia GeForce Go 7300 PCI Express, reporting 512Mb. I have no clue wether it's "shared" or not, but I doubt the card really has 512Mb.

System Monitor shows me 3.9Gb. Here's what free and /proc/meminfo report. The -b -m & -g options report in bytes, megabytes & gigabytes. No options shows kilobytes

```

olivierp@cromo:~$ uname -a
Linux cromo 2.6.24-17-generic #1 SMP Thu May 1 13:57:17 UTC 2008 x86_64 GNU/Linux
olivierp@cromo:~$ dmesg | grep Memory:
[   21.216273] Memory: 4043056k/5242880k available (2488k kernel code, 149892k reserved, 1319k data, 320k init)
olivierp@cromo:~$ free | grep -E "used|^M"
             total       used       free     shared    buffers     cached
Mem:       4050892    2778976    1271916          0     192772    1665216
olivierp@cromo:~$ free -b | grep -E "used|^M"
             total       used       free     shared    buffers     cached
Mem:    4148113408 2845491200 1302622208          0  197398528 1705181184
olivierp@cromo:~$ free -m | grep -E "used|^M"
             total       used       free     shared    buffers     cached
Mem:          3955       2713       1242          0        188       1626
olivierp@cromo:~$ free -g | grep -E "used|^M"
             total       used       free     shared    buffers     cached
Mem:             3          2          1          0          0          1
olivierp@cromo:~$ grep MemTotal /proc/meminfo 
MemTotal:      4050892 kB
olivierp@cromo:~$ 

```

---

### Post by lefterist on 2008-05-11
> **Kilz said:**
> uname -m gives you the hardware type, not the installed operating system . Its possible to install the i386 version on 64bit hardware. 
What does ```
uname -a
``` return.

Yes, its very possible all right, but I was under the false impression it would return the OS. In any case its a 64 install for sure and there is no mistake about this.

Returns:
```
Linux Ubuntu-test 2.6.24-16-server #1 SMP Thu Apr 10 13:15:38 UTC 2008 x86_64 GNU/Linux
```

---

### Post by lamborghiniwang on 2008-05-12
> **olivierp said:**
> Those seeing 3.8/3.9Gb may be chasings ghosts for the last 100Mb...
Be careful of rounding with Kb Mb & Gb values.
I have 4Gb in this laptop, no kernel options, and a BIOS that doesn't allow remapping of the "3Gb memory hole". The graphics card is a NVidia GeForce Go 7300 PCI Express, reporting 512Mb. I have no clue wether it's "shared" or not, but I doubt the card really has 512Mb.

System Monitor shows me 3.9Gb. Here's what free and /proc/meminfo report. The -b -m & -g options report in bytes, megabytes & gigabytes. No options shows kilobytes

```

olivierp@cromo:~$ uname -a
Linux cromo 2.6.24-17-generic #1 SMP Thu May 1 13:57:17 UTC 2008 x86_64 GNU/Linux
olivierp@cromo:~$ dmesg | grep Memory:
[   21.216273] Memory: 4043056k/**5242880k** available (2488k kernel code, 149892k reserved, 1319k data, 320k init)
olivierp@cromo:~$ free | grep -E "used|^M"
             total       used       free     shared    buffers     cached
Mem:       4050892    2778976    1271916          0     192772    1665216
olivierp@cromo:~$ free -b | grep -E "used|^M"
             total       used       free     shared    buffers     cached
Mem:    4148113408 2845491200 1302622208          0  197398528 1705181184
olivierp@cromo:~$ free -m | grep -E "used|^M"
             total       used       free     shared    buffers     cached
Mem:          3955       2713       1242          0        188       1626
olivierp@cromo:~$ free -g | grep -E "used|^M"
             total       used       free     shared    buffers     cached
Mem:             3          2          1          0          0          1
olivierp@cromo:~$ grep MemTotal /proc/meminfo 
MemTotal:      4050892 kB
olivierp@cromo:~$ 

```
I am also have 4GB installed and the total available memory in Hardy is 70MB less than yours. 
```

lamborghiniwang@bumble:~$ uname -a
Linux bumble 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64 GNU/Linux
lamborghiniwang@bumble:~$ dmesg|grep Memory:
[   18.589861] Memory: 3976864k/**5177344k** available (2466k kernel code, 150164k reserved, 1309k data, 316k init)
lamborghiniwang@bumble:~$ free | grep -E "used|^M"
             total       used       free     shared    buffers     cached
Mem:       3985496    1990700    1994796          0     109624    1087960
lamborghiniwang@bumble:~$ grep MemTotal /proc/meminfo
MemTotal:      3985496 kB

```

I assume both machine has 4GB RAM physically installed, and it seems the reserved memory is roughly the same (149892k vs 150164k), so the only possible reason that I'm seeing 70MB less memory than you is because of the figure followed by the slash in the dmesg output (5177344k vs 5242880k). It looks like although my motherboard has the ability to remap the memory hole, somehow the added addresses beyond 4GB is less than the one in your case, so there are still some amount of memory that is "cut-off" in the higher end.

I am not sure if it is kernel related or hardware related, or if it could be solved. But it would always be nice if there is a possibility to squeeze a little bit more out of it. :D

---

### Post by melenor on 2008-05-12
I have the same problem i have AMD64 installed but it only shows 3.2GB RAM, 4GB shows up in my XP install. I will try some of the suggestions in a little and post back with results.

---

### Post by olivierp on 2008-05-12
I've had a couple of pm's wondering where my kernel comes from:
```
Linux cromo **2.6.24-17-generic** #1 SMP Thu May 1 13:57:17 UTC 2008 x86_64 GNU/Linux
```

Enable the hardy-proposed repository, and it's there. There's also an updated restricted modules package, for those who need it.

---

### Post by StephenDeli22 on 2008-05-21
Well I finally figured out why my OS will not read all 4gb.  My Intel 945 chipset can read 4gb but can only address to the OS 3gb.  It seems to be a corner HP cut when they built my laptop, putting a 32bit chipset with a 64bit processor.  Im sure they assumed that nobody would move away from 32 bit XP. 

So to everyone that has a similar issue to mine, check your chipset and see if it can physically address all of your ram.

---

### Post by melenor on 2008-05-21
Allright i have Ubuntu 8.04 AMD64 installed and it only sees 3.2GB but when i was using Vista 64-bit it saw all 4GB so it isn't my chipset. Can someone help me please?

---

### Post by Guilden_NL on 2008-09-05
I turned it on and it went from 3.1GB to 3.9GB.  All of the discussion around use by PCI-E etc was excellent, no need to chase that 100MB when it is being used by video etc.

Two thumbs up for the excellent insights here! :guitar:

---

### Post by JagerQ on 2008-09-23
Same problem but I'm only seeing 2.5 GB of ram. 

2.6.24-19-generic #1 SMP Wed Jun 18 14:15:37 UTC 2008 x86_64 GNU/Linux

I'll try the flags on boot to see if it helps. I've got a dedicated video card that can use system ram, so maybe that's my issue.

---

### Post by cprofitt on 2008-09-23
There is a difference between GiB and GB... the System Monitor in Ubuntu uses GiB.

[http://en.wikipedia.org/wiki/GiB](http://en.wikipedia.org/wiki/GiB)

---

### Post by tuxxy on 2008-09-23
I agree, 4GB should show up around 3.8 figure, also heres a link to the [64-bit users group]("http://ubuntuforums.org/group.php?groupid=258")

---

