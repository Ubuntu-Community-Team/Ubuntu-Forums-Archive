---
title: "High Mem Support"
date: 2008-07-10
forum: x86 64-bit Users
---

### Post by Jangla on 2008-07-10
Before posting, please bear in mind I'm a Linux n00b and will need very detailed instructions on doing anything! :)

So, I've got Ubuntu Heron installed on a Dell T105 with 8GB Ram and an AMD64 Opteron CPU.

Just finished running KernelCheck (after finding it from the master kernel thread) and had hoped that would allow my installation to utilise the full 8GB I have in the machine - but no. Going to the System Monitor shows me that the system only has 3.2GiB of memory.

Things I noticed along this whole process: 
KernelCheck - HIGHMEM options were greyed out. I had presumed this was because it was already a given that it would use all 8GB.
We had to do the original install with high mem support off owning to a bug whereby it wouldn't mount the CD rom for installation unless we did.
I've seen people mention checking the CONFIG_HIGHMEM63G option is on but there are several folders in my ubuntu-hardy/debian/config folder which have the config.generic file in so I'm not sure which one is actually being used - is there a way to check?
Some of the config.generic files are a lot longer than others and some have no CONFIG_HIGHMEM line in at all (commented out or otherwise).

So, can anyone help me figure out why this thing won't open up the full power of the machine?

Again, bear in mind that while I'm technically able (having used Windows based OS's for along time) I'm new to Linux. 

Thanks in advance! :)

---

### Post by ajgreeny on 2008-07-10
If you installed the standard 32bit version of ubuntu, 3.2 GB ram is all that will show as 32bit OSs can not in theory use more than that.  It is not a ubuntu characteristic, but a general computer system limit of 32bit systems.  For more than that to be usable you should have installed the 64bit iso system, which would, I think, have shown your full 4GB ram in use.

If this is your situation, I'm afraid you can not make the change without a reinstall of the 64bit OS.  However, unless you really need the extra ram, I suggest you continue as you are until the next version comes out in October, and then consider upgrading to that with a clean install of the 64bit version.

If you did use the 64bit version this time I don't know what has happened as it should, as far as I know, show the full memory usage.  If you are not sure use ```
uname -m
``` in terminal and the output number will finish with 64 if it is a 64bit operating system.

---

### Post by Jangla on 2008-07-10
Nope - it's definitely the 64 bit installation.

And I have 8GB of RAM I want to use - not 4GB. That's where the troubles began - when you try and run the CD installation with 8GB it refuses to mount the CD drive so you have to add an installation option to only use 4GB.

Only trouble is, as I'm finding out now, getting it back up to use the full 8GB that are in the machine is not easy - hence my post.

---

### Post by ajgreeny on 2008-07-10
Sorry, mis-typed 4 instead of 8, but anyway, you already have the 64bit system, so I can't help further, I'm afraid.

---

### Post by ByteJuggler on 2008-07-10
You might try (just a guess) kernel boot option:

```
mem=8G
```

---

### Post by Jangla on 2008-07-10
Tried that - no joy :(

Did sudo /boot/grub/menu.lst

added mem=8G to the end of the # kopt line

the did sudo update-grub

rebooted - no change, still using 4GB

---

### Post by ByteJuggler on 2008-07-10
I just want to check, can you post the output of

```
sudo uname -a
```

please? Tx.

---

### Post by Jangla on 2008-07-10
Linux ubuntu-server01 2.6.25.10-ultimate #1 SMP Thu Jul 10 10:26:34 BST 2008 x86_64 GNU/Linux

---

### Post by tribaal on 2008-07-10
Silly question:
Did you run a memtest from the install CD? This will let you rule out a hardware problem...

- Trib'

---

### Post by Jangla on 2008-07-10
We did actually - when the cd wouldn't mount we thought it might be a hardware issue but the memtest was fine which eventually led us to find the issue with having 8GB in there to start with and having to use the 4GB install switch.

Also found something about installing from a USB device so if I can't solve this I might have to just start from scratch and dig out a USB stick from somewhere.

Update - just ran sudo lshw and it reports all 4 2GB ram banks so it knows it's there, it just can't use it in the OS

---

### Post by heinzbitte on 2008-07-10
This is probably a stupid question but since you say you are new to ubuntu, did you used to run windows with that computer?  If so, did it access all of the ram?

---

### Post by cariboo on 2008-07-10
What is the output of Applications-->Accessories-->Terminal:

```
free
```

Top or Htop will show you memory usage too.

Jim

---

### Post by felker2 on 2008-07-10
A few checks / questions:

[LIST=1]
[*]How much memory does your BIOS report at boot?
[*]If it's 4GB, have you looked for "memory hole remapping" / "memory hoisting" in the BIOS? It should be on.
[*]Have you run the memtest from the GRUB-menu (just after the BIOS-boot)? How much memory does it report.
[*]Can you post the output of "dmesg | head -20" here (see mine below)?
[/LIST]

Remark: Ubuntu 64-bit does *not* need any tweaking with special kernel settings like the ones you described in your original post.



```

sander@ubuntu804:~$ dmesg | head -20
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@yellow) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:15:37 UTC 2008 (Ubuntu 2.6.24-19.34-generic)
[    0.000000] Command line: root=UUID=f6b0b4b8-a4c5-4dc0-a6e5-c6706741df4e ro quiet splash
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
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 884448) 1 entries of 3200 used
[    0.000000] Entering add_active_range(0, 1048576, 1179648) 2 entries of 3200 used
[    0.000000] end_pfn_map = 1179648
[    0.000000] DMI 2.4 present.
sander@ubuntu804:~$

```

---

### Post by Jangla on 2008-07-10
> **heinzbitte said:**
> This is probably a stupid question but since you say you are new to ubuntu, did you used to run windows with that computer?  If so, did it access all of the ram?
Brand new machine so it's never had anything on it before.

> **cariboo907 said:**
> What is the output of Applications-->Accessories-->Terminal:

```
free
```

Top or Htop will show you memory usage too.

Jim

I'll let you know when I'm back in the office tomorrow morning.

> **felker2 said:**
> A few checks / questions:

[LIST=1]
[*]How much memory does your BIOS report at boot?
[*]If it's 4GB, have you looked for "memory hole remapping" / "memory hoisting" in the BIOS? It should be on.
[*]Have you run the memtest from the GRUB-menu (just after the BIOS-boot)? How much memory does it report.
[*]Can you post the output of "dmesg | head -20" here (see mine below)?
[/LIST]

Remark: Ubuntu 64-bit does *not* need any tweaking with special kernel settings like the ones you described in your original post.

```

sander@ubuntu804:~$ dmesg | head -20
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@yellow) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:15:37 UTC 2008 (Ubuntu 2.6.24-19.34-generic)
[    0.000000] Command line: root=UUID=f6b0b4b8-a4c5-4dc0-a6e5-c6706741df4e ro quiet splash
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
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 884448) 1 entries of 3200 used
[    0.000000] Entering add_active_range(0, 1048576, 1179648) 2 entries of 3200 used
[    0.000000] end_pfn_map = 1179648
[    0.000000] DMI 2.4 present.
sander@ubuntu804:~$

```

1. 8GB reported at boot.
2. Not applicable I presume.
3. Will try that in the morning.
4. Will try that in the morning.

Remark: If you're referring to the need to add a switch to the install command to avoid issues with the CD drive mounting, I would beg to differ. If you're referring to the greyed out options in kernelcheck then that's what I figured :)

---

### Post by Jangla on 2008-07-11
Results of sudo free:

```

             total       used       free     shared    buffers     cached
Mem:       3354248     570200    2784048          0      83068     219444
-/+ buffers/cache:     267688    3086560
Swap:      9823708          0    9823708

```

Results of dmesg | head -20:

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Linux version 2.6.25.10-ultimate (root@ubuntu-server01) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Jul 10 10:26:34 BST 2008
[    0.000000] Command line: root=UUID=98ed0ff7-d4f1-4bdc-a600-258df80ff180 ro mem=10G quiet splash mem=4G
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ca000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fff0000 (usable)
[    0.000000]  BIOS-e820: 000000007fff0000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 0000000080000000 - 00000000cfee0000 (usable)
[    0.000000]  BIOS-e820: 00000000cfee0000 - 00000000cfef2000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cfef2000 - 00000000cff7f000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cff80000 - 00000000d0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000230000000 (usable)
[    0.000000] Entering add_active_range(0, 0, 157) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 524272) 1 entries of 3200 used


```

I've noticed there is something weird about that code above: I added the mem=10G to try and get it to recognise all the ram but I didn't put the mem=4G bit in so I've no idea where that's coming from.

HOORAY! Found where that extra mem=4G was being added, removed it and now it's sorted!

Thanks everyone for your help!

For anyone reading this for help later on, it was a few lines down from the #kopt line in /boot/grub/menu.lst Search the whole file for "mem=" to make sure you've only got it declared once and then save the file, run sudo update-grub and reboot.

---

### Post by felker2 on 2008-07-11
Good to hear it now works.

What I don't understand: your dmesg shows "Linux version 2.6.25.10-ultimate (root@ubuntu-server01)", whereas my uptodate 64-bit Ubuntu says "Linux version 2.6.24-19-generic".

So: do you know how you got that .25 kernel? Did you compile that yourself? Or did you install Ubuntu Server which could have another kernel? Or ... ?

---

### Post by Jangla on 2008-07-11
> **felker2 said:**
> Good to hear it now works.

What I don't understand: your dmesg shows "Linux version 2.6.25.10-ultimate (root@ubuntu-server01)", whereas my uptodate 64-bit Ubuntu says "Linux version 2.6.24-19-generic".

So: do you know how you got that .25 kernel? Did you compile that yourself? Or did you install Ubuntu Server which could have another kernel? Or ... ?
I used kernelcheck: [http://kcheck.sourceforge.net/](http://kcheck.sourceforge.net/)

Very easy to use and did pretty much everything for me. The only option I changed was that it had set its options up to optimse for a generic 64 bit machine so I changed it to AMD64 Opteron specific.

It did everything else for me - downloaded the latest version, compiled it and everything. Brilliant!

---

### Post by felker2 on 2008-07-11
> **Jangla said:**
> I used kernelcheck: [http://kcheck.sourceforge.net/](http://kcheck.sourceforge.net/)

Very easy to use and did pretty much everything for me. The only option I changed was that it had set its options up to optimse for a generic 64 bit machine so I changed it to AMD64 Opteron specific.

It did everything else for me - downloaded the latest version, compiled it and everything. Brilliant!

OK. But could that other kernel (combined with incorrect settings) be the root cause of the non-recoginizing of your 8GB? In other words: did the plain Ubuntu installation correctly recognize the 8GB? Maybe you can boot an older kernel from the GRUB menu, or boot from the live CD (64-bit of course).

---

### Post by dcstar on 2008-07-13
> **Jangla said:**
> 
........
I've noticed there is something weird about that code above: I added the mem=10G to try and get it to recognise all the ram but I didn't put the mem=4G bit in so I've no idea where that's coming from.

HOORAY! Found where that extra mem=4G was being added, removed it and now it's sorted!

Thanks everyone for your help!

For anyone reading this for help later on, it was a few lines down from the #kopt line in /boot/grub/menu.lst Search the whole file for "mem=" to make sure you've only got it declared once and then save the file, run sudo update-grub and reboot.

You shouldn't need any "mem=" option unless you specifically want to **limit** the amount of RAM your kernel uses. The normal Ubuntu install does not set this parameter AFAIK, if you use other sources or modify things from the standard then these sorts of issues can arise.

---

