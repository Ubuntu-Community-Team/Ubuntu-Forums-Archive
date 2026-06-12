---
title: "ubuntu 8.10 amd64 use less than 4gigabyte of ram"
date: 2008-12-02
forum: x86 64-bit Users
---

### Post by simosauro on 2008-12-02
I've a strange problem
I've installed ubuntu 8.10 amd64 on my Desktop
the hardware configuration is:
Mainboard Asrock 4core 1333-FullHd
Cpu: Intel Core Duo Quad 6600
Ram 4 Gigabyte
Video card Nvida 9400GT
The system monitor says that I've only 3.4 Gigabyte of ram.
There is a on board video card, in the bios setup I've put the first video card as PCI Express, and the maximum of shared memory for the on board video card 32 Megabyte. But noting change in the system monitor of ubuntu
Anybody know what's wrong?
Thank you

---

### Post by felker2 on 2008-12-02
Your question is a FAQ (see [http://ubuntuforums.org/showthread.php?p=6190212](http://ubuntuforums.org/showthread.php?p=6190212)). Short explanation: your OS is only using the RAM below the 4GB limit, and not the RAM (0.6 - 0.8 GB) that's remapped above that limit.

So here's the FGA (Frequently Given Answer):

Post the outputs of these commands:

```
uname -a
free -m
dmesg | head -25
```

and upgrade your BIOS 

and enable "memory hole remapping" or "memory hoisting" in your BIOS 

HTH

---

### Post by simosauro on 2008-12-02
uname -a
Linux Covo 2.6.27-9-generic #1 SMP Thu Nov 20 22:15:32 UTC 2008 x86_64 GNU/Linux

 free -m
             total       used       free     shared    buffers     cached
Mem:          3456       1063       2392          0         22        553
-/+ buffers/cache:        487       2969
Swap:         1906          0       1906

dmesg | head -25
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-9-generic (buildd@yellow) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Nov 20 22:15:32 UTC 2008 (Ubuntu 2.6.27-9.19-generic)
[    0.000000] Command line: root=UUID=c265d81b-1b3b-4801-bbde-d6c9833fc276 ro quiet splash 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000dbfb0000 (usable)
[    0.000000]  BIOS-e820: 00000000dbfb0000 - 00000000dbfc0000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000dbfc0000 - 00000000dbff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000dbff0000 - 00000000dc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0xdbfb0 max_arch_pfn = 0x3ffffffff
[    0.000000] init_memory_mapping
[    0.000000]  0000000000 - 00dbe00000 page 2M
[    0.000000]  00dbe00000 - 00dbfb0000 page 4k
[    0.000000] kernel direct mapping tables up to dbfb0000 @ 8000-e000
[    0.000000] last_map_addr: dbfb0000 end: dbfb0000
[    0.000000] RAMDISK: 377ac000 - 37fefa05

How can I update the bios version if the asrock ar all for vista or dos and with the emulator don't work?
thanks

---

### Post by Waappu on 2008-12-02
> **simosauro said:**
> How can I update the bios version if the asrock ar all for vista or dos and with the emulator don't work?
thanks

Hi

I have used "Win LiveCD" successfully for upgrading BIOS
[http://www.nu2.nu/pebuilder/](http://www.nu2.nu/pebuilder/)

Of course you need find first some WIN machine where you can create CD

---

### Post by felker2 on 2008-12-02
> **simosauro said:**
> 
[ 0.000000] BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[ 0.000000] BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[ 0.000000] last_pfn = 0xdbfb0 max_arch_pfn = 0x3ffffffff


Well, as expected, there it is: your BIOS only offers the memory until 0000000100000000 (=4GB boundary) and does not offer the memory that's remappend onto the above-4GB-area.

> **simosauro said:**
> 

How can I update the bios version if the asrock ar all for vista or dos and with the emulator don't work?
thanks

I update my Asus BIOS by going into the BIOS setup and then read the BIOS.BIN file from a USB stick. No OS needed. As Asrock is Asus' little brother / son, you could check if your Asrock has got that feature too.

---

### Post by simosauro on 2008-12-05
Sorry for the delay in the  answer, I have upgrade the bios to the last version  but nothing change
ubuntu still find 3.4 Gigabyte
I'm depressed

---

### Post by felker2 on 2008-12-05
> **simosauro said:**
> Sorry for the delay in the  answer, I have upgrade the bios to the last version  but nothing change
ubuntu still find 3.4 Gigabyte
I'm depressed

I can imagine. ;-)

Have you tried to find "memory hole remapping" or "memory hoisting" or something like that in your BIOS? It should be enabled.

BTW: how old is your motherboard? I guess it's new as you have very new CPU, right? So that can't be the problem; and I would expect the motherboard and BIOS would just show the 4GB to your Linux OS ...

---

### Post by simosauro on 2008-12-05
Hi

the mainboard, is not old, I have buy the pc in July and the bios version on the mainboard was 1,60 with the upgrade is now 1,70
I find a options called memory remap It was disable I tried to put enable but if  I do that linux do not start anymore.

---

### Post by lavinog on 2008-12-05
> **simosauro said:**
> Hi

the mainboard, is not old, I have buy the pc in July and the bios version on the mainboard was 1,60 with the upgrade is now 1,70
I find a options called memory remap It was disable I tried to put enable but if  I do that linux do not start anymore.

What happens when it doesn't start?
when grub loads highlight the kernel you want to boot to and press 'e'
highlight the kernel line and press 'e' again
at the end of the line replace 'quiet splash' with 'verbose' (no quotes)
press enter then 'b'
Try and take a screenshot of the message it gives when it fails to boot (use a camera if you have one.)

---

### Post by pdaigneault on 2008-12-05
Hi, If you are using internal graphics, Just a guess? could your board assign 4):P00meg to that and thus only show 3.6g of memory

---

### Post by simosauro on 2008-12-06
Hi I have follow your instruction and I have attach a png file with the shoot of the screen, I hope that you can help me
thanks
Thanks
thansk

---

### Post by felker2 on 2008-12-06
You screendump is showing "Memory: 4046572k/5242880k available". Strange: "Memory: 4.046.572 k/ 5.242.880k available", which looks like 5GB.

So let's compare that with my own 4GB 64-bit system: "Memory: 3916876k/4718592k available". Ah: 4.718.592k is probably caused by the memory remapping into high areas.

So I would conclude your system 1) does see 4GB to use (good), and 2) the memory is remapped into very high regions. So: What does "free -m" show you?



Now back to your boot process: does the boot halt at this stage, at the "Dentry cache"? I do not see any error. My own system follows with inode stuff (thus harddisk) after the "Dentry cache".

---

### Post by simosauro on 2008-12-06
I don't understand, the image in the previous post show the boot and the pc still block like you see! 
The system don't change stay like in the pic for all the time!!
Install the server version can help me?

---

### Post by lglindfw on 2008-12-06
I'm glad I found this thread!

I was having the same problem on a machine I just built with an AMD64 chip and 4 Gig Ram when I tried installing ubuntu 8.10.  I have been using ubuntu 8.04 on another home-built system and never saw any error messages or problems with it ... but it only had 2 Gig and an AMD64 chip.

My new machine with 8.10 would boot and worked fine after it did (except for issues with Nvidia) ... it just gets the messages at boot about going to BIOS and setting up for access to memory higher than 4 Gig.

Being anal, I reinstalled the new machine with ubuntu 8.04 and using the commands you mentioned above got the following results:
uname -a
Linux 2010-Management-Desktop 2.6.24-22-generic #1 SMP Mon Nov 24 19:35:06 UTC 2008 x86_64 GNU/Linux

free -m
             total       used       free     shared    buffers     cached
Mem:          3959        670       3289          0         58        261
-/+ buffers/cache:        350       3609
Swap:        11593          0      11593

dmesg | head -25
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-22-generic (buildd@crested) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Mon Nov 24 19:35:06 UTC 2008 (Ubuntu 2.6.24-22.45-generic)
[    0.000000] Command line: root=UUID=c4baf532-3552-458a-ae5f-dbefd25ad37f ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cffa0000 (usable)
[    0.000000]  BIOS-e820: 00000000cffa0000 - 00000000cffae000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cffae000 - 00000000cfff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cfff0000 - 00000000cfffe000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff700000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 851872) 1 entries of 3200 used
[    0.000000] Entering add_active_range(0, 1048576, 1245184) 2 entries of 3200 used
[    0.000000] end_pfn_map = 1245184
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000FABD0 checksum 0
[    0.000000] ACPI: RSDP 000FABD0, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT CFFA0000, 0040 (r1 122407 RSDT1409 20071224 MSFT       97)
[    0.000000] ACPI: FACP CFFA0200, 0084 (r2 122407 FACP1409 20071224 MSFT       97)

I'm not a real tech heavy and I'm fairly new to Linux, but based on your analysis of Simosauro's results to those commands, it looks like ubuntu 8.04 is using the memory above 4 Gig and I haven't done anything to the BIOS or machine other than go from ubuntu 8.10 to ubuntu 8.04.

Can you tell me if I'm reading that right?  Could this be a bug in ubuntu 8.10 that isn't in unbuntu 8.04?

---

### Post by dcstar on 2008-12-07
> **simosauro said:**
> uname -a
Linux Covo 2.6.27-9-generic #1 SMP Thu Nov 20 22:15:32 UTC 2008 x86_64 GNU/Linux

 free -m
             total       used       free     shared    buffers     cached
Mem:          3456       1063       2392          0         22        553
-/+ buffers/cache:        487       2969
Swap:         1906          0       1906

dmesg | head -25
........
**[    0.000000] RAMDISK: 377ac000 - 37fefa05**
........

Why is this kernel using a Ramdisk?

---

### Post by simosauro on 2008-12-07
I don't know really!
I have try to put the ubuntu 8,10  and boot the pc with the memory remap option enable and  the memory control find more the 4 Gigabyte,  but during the boot the pc stop and don't finish the boot operation 
The same operation with memory remap option disable find 3,5 Gigabyte but everything work!
??????????

---

### Post by ian dobson on 2008-12-07
Hi,

Try blacklisting the intel_agp driver. By adding 

#4Gb memory fix
blacklist intel_agp

to /etc/modprobe.d/blacklist

Regards
Ian Dobson

---

### Post by simosauro on 2009-03-16
Sorry for this late replay but I'm just exit from the hospitl after a car accident!
> 
Try blacklisting the intel_agp driver. By adding

#4Gb memory fix
blacklist intel_agp



you mean that I have to put this line in /etc/modprobe.d/blacklist, if yes I have try but nothing change!

meaby there are some modules to put in my kernel or can you suggest me a good kernel image for my problem?

Tanks

---

### Post by movieman on 2009-03-17
> **simosauro said:**
> The same operation with memory remap option disable find 3,5 Gigabyte but everything work!
??????????

That's not too unusual; my Athlon X2 system wouldn't boot with memory remapping because the BIOS was telling Linux that it had remapped the memory but didn't actually bother to do so. Hence it worked fine until X11 tried to use the high memory for the login screen and locked up the system.

Upgrading the BIOS fixed that problem, I don't know whether there's a newer BIOS for your system that you could try. There are a lot of really buggy BIOSes out there, because systems running a 64-bit OS with 4+GB of RAM have only become popular recently.

---

### Post by goldleader on 2009-03-17
Hi i have the same motherboard with 4GB memory and had the same problems.

To fix it i had to change settings in the BIOS regarding memory.  Can't remember which one it was, but it does work just try changing different ones and see what happens, if you can't get it right let me know and i will have a look into if and see what setting it was i changed.

---

### Post by simosauro on 2009-03-17
I have try a lot of setup without solution! is possible for you paste the setup of your bios ?
Have you recompiled the kernel o you use the generic image?
Tanks a lot
bey

---

