---
title: "PC terribly slow when copying files"
date: 2008-07-10
forum: x86 64-bit Users
---

### Post by robcar on 2008-07-10
I recently bought a PC with an AMD Athlon X2 5000+ and 4GB RAM: should be pretty fast! Well, not so fast...
I had problems with the installation of Ubuntu, because it didn't recognize the dvd-rom and I had to boot with the all_generic_ide option in Grub, which I left in menu.lst even after the successful installation, because otherwise my pc rebooted everytime I inserted a cd.

Now when I copy files from an USB stick to the desktop or from a folder to another onto the harddisk, even from the Bash and even as root (with sudo) the CPUs go 100%, Firefox freezes and goes grey, I can't open any program as long as the copying has finished (or I cancel it) and the pc becomes incredibly slow.

Don't know if it's related to 64bit; anyway this is my kernel:
$ uname -a
Linux athlon64 2.6.24-19-generic #1 SMP Wed Jun 18 14:15:37 UTC 2008 x86_64 GNU/Linux

This is part of my dmesg, with the lines related to DMA (which I read could cause problem):

less dmes2.log | grep -i dma
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1222 pages reserved
[    0.000000]   DMA zone: 2721 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 833304 pages, LIFO batch:31
[   32.329181] PCI-DMA: Disabling AGP.
[   32.329360] PCI-DMA: aperture base @ 4000000 size 65536 KB
[   32.329364] PCI-DMA: using GART IOMMU.
[   32.329370] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[   32.987711] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xe800 irq 14
[   32.987713] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xe808 irq 15
[   33.314273] ata3: PATA max UDMA/100 cmd 0x9f0 ctl 0xbf0 bmdma 0xd400 irq 23
[   33.314275] ata4: PATA max UDMA/100 cmd 0x970 ctl 0xb70 bmdma 0xd408 irq 23
[   33.640944] ata5: PATA max UDMA/100 cmd 0x9e0 ctl 0xbe0 bmdma 0xc000 irq 22
[   33.640946] ata6: PATA max UDMA/100 cmd 0x960 ctl 0xb60 bmdma 0xc008 irq 22
[   33.842930] ata5.00: ATA-7: MAXTOR STM3160215AS, 3.AAD, max UDMA/133
[   34.316859] ata6.00: ATAPI: ASUS    DRW-2014L1T, 1.02, max UDMA/66
[   36.680704] forcedeth 0000:00:0a.0: highdma csum timirq gbit lnktim desc-v3

What else? Ask me and I'll post more logs.

Btw, just to stress, the problem is not the speed of copying itself, which seems fine, it's the performance of the pc whenever I do the copying.

TIA

--
rob

---

### Post by robcar on 2008-07-10
I've just discovered a thing: what's actually going close to 100% on the Cpu's is the IOWAIT.
I can see evidence of that in the Gnome panel's system Monitor and also if I install sysstat and type:

```
sudo sar -u 2 5
Linux 2.6.24-19-generic (athlon64) 	10/07/2008

11:32:09        CPU     %user     %nice   %system   %iowait    %steal     %idle
11:32:11        all      1,95      0,00     19,95     78,10      0,00      0,00
11:32:13        all      3,21      0,00     21,98     74,81      0,00      0,00
11:32:15        all      3,59      0,00     24,64     71,77      0,00      0,00
11:32:17        all      1,72      0,00     17,24     81,03      0,00      0,00
11:32:19        all      1,20      0,00     18,55     80,24      0,00      0,00
Media:          all      2,34      0,00     20,49     77,18      0,00      0,00

```

So I'm quite sure there's a problem (or a bottleneck) with the management of my disk subsystem.
Hey, know what? I just tried an OpenSuse 11.0 64bit LiveCD and I don't experience the sluggishness there!

TIA

--
rob

---

### Post by robcar on 2008-07-10
Addon:

I disabled a couple of things under System-Preferences-Sessions, like Applet Tracker,  Bluetooth manager and Tracker and now the pc seems more responsive and the IOWAIT has diminished:

```
sudo sar -u 2 5
Linux 2.6.24-19-generic (athlon64) 	10/07/2008

12:12:31        CPU     %user     %nice   %system   %iowait    %steal     %idle
12:12:33        all      0,99      0,00     16,79     80,25      0,00      1,98
12:12:35        all      2,03      0,00     17,97     39,49      0,00     40,51
12:12:37        all      3,65      0,00     25,79     32,60      0,00     37,96
12:12:39        all      1,43      0,00     27,62     30,00      0,00     40,95
12:12:41        all      1,00      0,00     25,00     30,00      0,00     44,00
Media:          all      1,82      0,00     22,70     42,39      0,00     33,09
```

But I'm sure it can do better than that.

---

### Post by robcar on 2008-07-10
I didn't post the results of hdparm, which, after some googling, seem not good:

```

sudo hdparm -Tt /dev/sda

/dev/sda:
 Timing cached reads:   2278 MB in  2.00 seconds = 1138.87 MB/sec
 Timing buffered disk reads:   28 MB in  3.20 seconds =   8.75 MB/sec

```

---

### Post by robcar on 2008-07-10
Sorry, just another addon:

```

sudo hdparm -i /dev/sda

/dev/sda:

 Model=MAXTOR STM3160215AS                     , FwRev=3.AAD   , SerialNo=            6RA5TE2J
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=2048kB, MaxMultSect=16, MultSect=?1?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=312581808
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode

```

---

### Post by LinuX-M@n1@k on 2008-07-10
> **robcar said:**
> Now when I copy files from an USB stick to the desktop or from a folder to another onto the harddisk, even from the Bash and even as root (with sudo) the CPUs go 100%, Firefox freezes and goes grey, I can't open any program as long as the copying has finished (or I cancel it) and the pc becomes incredibly slow.

Same thing here too.

Ubuntu 8.04
Kernel: 2.6.24-19-generic

CPU: P4 2.4GHz
RAM: 1GB DDR-800

---

### Post by ByteJuggler on 2008-07-10
I would guess it's precisely the "all_generic_ide" option that's causing the slowdown.... You'll have to wait for the fix to be released so you can remove this option from your boot line.  It might be an idea to look if this bug is already reported on Launchpad, and if not, to report it.  If Fedora works, it's likely that there's a patch already somewhere in the works, even so it would be best to report it on Launchpad if it's not already known, and point out that the issue doesn't exist for you under Fedora. Launchpad is [here.]("https://bugs.launchpad.net/ubuntu")

---

### Post by robcar on 2008-07-10
> **ByteJuggler said:**
> I would guess it's precisely the "all_generic_ide" option that's causing the slowdown.... You'll have to wait for the fix to be released so you can remove this option from your boot line.  It might be an idea to look if this bug is already reported on Launchpad, and if not, to report it.  If Fedora works, it's likely that there's a patch already somewhere in the works, even so it would be best to report it on Launchpad if it's not already known, and point out that the issue doesn't exist for you under Fedora. Launchpad is [here.]("https://bugs.launchpad.net/ubuntu")

Well, I think you're right, after all!
I disabled the "all_generic_ide" option in my grub conf and now that's what I got:

```
sudo hdparm -Tt /dev/sda

/dev/sda:
 Timing cached reads:   2378 MB in  2.00 seconds = 1189.02 MB/sec
 Timing buffered disk reads:  224 MB in  3.01 seconds =  74.46 MB/sec

```

And the transfer rate during file transfer has improved a lot too, EVEN THOUGH the whole system is quite unresponsive as long as the file transfer is in progress. And I still got the CPU IOWAIT almost at 100%.

Btw, thanks, you pointed me to the right direction. I'll do some more tests and I'll let you know.

--
rob

---

### Post by nikgare on 2008-07-10
> I would guess it's precisely the "all_generic_ide" option that's causing the slowdown

If this is the case, can you tell us exactly the make and model of your dvd drive, and we'll try to find some better options for it.

---

### Post by robcar on 2008-07-10
> **nikgare said:**
> If this is the case, can you tell us exactly the make and model of your dvd drive, and we'll try to find some better options for it.

ASUS DRW-2014L1T

thanks

--
rob

---

### Post by nikgare on 2008-07-10
Can't really find much info for that drive :-(
If you leave **all_generic_ide** out of grub, does you machine still boot?
If yes, could you try copying/moving files without that option, to see if it makes a difference?

---

### Post by ByteJuggler on 2008-07-10
> **robcar said:**
> 
And the transfer rate during file transfer has improved a lot too, EVEN THOUGH the whole system is quite unresponsive as long as the file transfer is in progress. And I still got the CPU IOWAIT almost at 100%.


Firstly note that the system being unresponsive during the transfer and the IO-wait thing is in principle seperate issues.

For IO intensive operations, the related processes will always be spending most of their time in an IO-wait state.  (The CPU is still many times faster than the IO process and so the process will still be waiting most of the time for the hard drives to catch up with the IO being done.) 

There's obviously *something* going on however, to slow your PC's responsiveness down while doing IO, but it's not *because* the processes are in IO-Wait state.  We will need to try and figure out what it is.  

What options/modes do you have in the BIOS to control your SATA controller(s)?  Make sure they're running native SATA and not some semi-emulated "IDE" mode.

---

### Post by robcar on 2008-07-10
> **nikgare said:**
> Can't really find much info for that drive :-(
If you leave **all_generic_ide** out of grub, does you machine still boot?
If yes, could you try copying/moving files without that option, to see if it makes a difference?

The machine does boot, but whenever I insert a cd or dvd ... POOOF... it reboots.
The difference without all_generic_ide is tangible, now file transfers are much more fast. But my pc is still quite slow during those operations, which, fortunately, now take less time.

---

### Post by robcar on 2008-07-10
> **ByteJuggler said:**
> Firstly note that the system being unresponsive during the transfer and the IO-wait thing is in principle seperate issues.

For IO intensive operations, the related processes will always be spending most of their time in an IO-wait state.  (The CPU is still many times faster than the IO process and so the process will still be waiting most of the time for the hard drives to catch up with the IO being done.) 

Ok, got it, thanks for the clarification.

> 
What options/modes do you have in the BIOS to control your SATA controller(s)?  Make sure they're running native SATA and not some semi-emulated "IDE" mode.

Well, I don't have many options in the BIOS. I got an ASUS M2N-SLI motherboard... 

I just have the option to disable SATA DMA transfer and an "IDE prefetch mode" which now I disabled, though I guess it only refers to the IDE bus.

Another strange thing is that when I DONT'T put "all_generic_ide" (as I have now) the ubuntu progression bar at boot "splits" into 2 parts.
I also have some "crap" on screen whenever I reboot, as if it were somehow related to my screen or video card.

---

### Post by ByteJuggler on 2008-07-10
> **robcar said:**
> The machine does boot, but whenever I insert a cd or dvd ... POOOF... it reboots.
The difference without all_generic_ide is tangible, now file transfers are much more fast. But my pc is still quite slow during those operations, which, fortunately, now take less time.

Can you investigate your /var/log/syslog and /var/log/message logs to see whether there's any error messages logged just before the crash.  It's rather odd, because in reality the worst that should happen is a kernel panic.  A spontaneous reboot points to serious driver bug or possibly some sort of hardware problem.  The repeatability of the problem however makes me lean towards deriver bug.

If this problem has not been repoted on Launchpad yet it would be very useful if it was reported so someone can look into it and fix it at some point.

---

### Post by robcar on 2008-07-10
> **ByteJuggler said:**
> Can you investigate your /var/log/syslog and /var/log/message logs to see whether there's any error messages logged just before the crash.  It's rather odd, because in reality the worst that should happen is a kernel panic.  A spontaneous reboot points to serious driver bug or possibly some sort of hardware problem.  The repeatability of the problem however makes me lean towards deriver bug.


Maybe I found something in /var/log/messages. It appeared once, just before a spontaneous reboot.

Jul 10 16:50:21 athlon64 kernel: [  424.471447] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Jul 10 16:50:21 athlon64 kernel: [  424.471453] sr 3:0:0:0: [sr0] Sense Key : Hardware Error [current]
Jul 10 16:50:21 athlon64 kernel: [  424.471457] sr 3:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
Jul 10 16:50:21 athlon64 kernel: [  424.471460] end_request: I/O error, dev sr0, sector 108
Jul 10 16:51:33 athlon64 kernel: [  454.702059] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Jul 10 16:51:33 athlon64 kernel: [  454.702065] sr 3:0:0:0: [sr0] Sense Key : Hardware Error [current]
Jul 10 16:51:33 athlon64 kernel: [  454.702069] sr 3:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
Jul 10 16:51:33 athlon64 kernel: [  454.702072] end_request: I/O error, dev sr0, sector 72
Jul 10 16:51:33 athlon64 kernel: [  454.702074] printk: 37 messages suppressed.
Jul 10 16:52:32 athlon64 kernel: [  477.132840] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Jul 10 16:52:32 athlon64 kernel: [  477.132846] sr 3:0:0:0: [sr0] Sense Key : Hardware Error [current]
Jul 10 16:52:32 athlon64 kernel: [  477.132849] sr 3:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
Jul 10 16:52:32 athlon64 kernel: [  477.132853] end_request: I/O error, dev sr0, sector 240
Jul 10 16:52:32 athlon64 kernel: [  477.132855] printk: 10 messages suppressed.
Jul 10 16:53:37 athlon64 kernel: [  505.321863] printk: 21 messages suppressed.
Jul 10 16:53:37 athlon64 kernel: [  505.321867] gvfs-fuse-daemo[6305] general protection rip:7fcb6c72d423 rsp:7fff76356c50 error:0
Jul 10 16:53:47 athlon64 kernel: [  511.370280] ip6_tables: (C) 2000-2006 Netfilter Core Team
Jul 10 16:53:51 athlon64 exiting on signal 15
Jul 10 16:59:35 athlon64 syslogd 1.5.0#1ubuntu1: restart.

Found this answer in launchpad:
[https://answers.launchpad.net/ubuntu/+question/10811](https://answers.launchpad.net/ubuntu/+question/10811)
where they say to change UDMA mode of the DVD-RW to UDMA2, but my stupid motherboard seems not to let me change that mode :(

---

### Post by ByteJuggler on 2008-07-10
> **robcar said:**
> 
Found this answer in launchpad:
[https://answers.launchpad.net/ubuntu/+question/10811](https://answers.launchpad.net/ubuntu/+question/10811)
where they say to change UDMA mode of the DVD-RW to UDMA2, but my stupid motherboard seems not to let me change that mode :(

You may  be able to force it to UDMA2 from inside Linux with the "hdparm" command.  (Don't know off the top of my head the exact switches, if you get stuck post back and I'll try to help.)

---

### Post by robcar on 2008-07-12
Ok, reported the DVD-ROM - reboot bug on Launchpad:
[https://bugs.launchpad.net/ubuntu/+bug/247853](https://bugs.launchpad.net/ubuntu/+bug/247853)

---

### Post by dcstar on 2008-07-13
> **robcar said:**
> I recently bought a PC with an AMD Athlon X2 5000+ and 4GB RAM: should be pretty fast! Well, not so fast...
I had problems with the installation of Ubuntu, because it didn't recognize the dvd-rom and I had to boot with the all_generic_ide option in Grub, which I left in menu.lst even after the successful installation, because otherwise my pc rebooted everytime I inserted a cd.
.......

Double check **all** IDE Master/Slave/Single device jumper settings on your drives.

There should always be one Master device on any IDE channel, and even though things can work with Slave only (or "Single" on multi-device connections) they can cause trouble.

Also having your hard drives and DVD/CD devices on separate IDE channels is good policy.

Make sure all of the cables are pushed in firmly, do not assume that they are.

---

### Post by robcar on 2008-07-13
> **dcstar said:**
> Double check **all** IDE Master/Slave/Single device jumper settings on your drives.

There should always be one Master device on any IDE channel, and even though things can work with Slave only (or "Single" on multi-device connections) they can cause trouble.

Also having your hard drives and DVD/CD devices on separate IDE channels is good policy.

Make sure all of the cables are pushed in firmly, do not assume that they are.

Well, thanks, but I have **SATA** drives (hard disk and DVR-RW), not IDE ones.

--
rob

---

### Post by robcar on 2008-08-06
Well, as for the original topic I'm waiting for a new 10000rpm SATA Disk (W.D. Velociraptor) which should be the fastest SATA around.
That's because I still sense sluggishness whenever I copy large files and the CPU I/O Wait goes very high.
I'll post results when it arrives.

As for the collateral topic, "pc reboots whenever I insert a cd/dvd without all_generic_ide", I opened a bug in Launchpad, but nobody answered :(
So I installed my old IDE Nec DVD-RW and it works like  a charm!

---

### Post by ByteJuggler on 2008-08-06
> **robcar said:**
> the CPU I/O Wait goes very high

I just want to re-iterate one point, as you still seem to think/imply above that the CPU I/O wait going high during disk intensive (I/O bound) processes  implies there's a problem of somet sort.  On the contrary, the fact is that the CPU I/O wait will be high even for the fastest of disks, when the process is totally I/O bound, e.g. primarly reading/writing to/from a disk.  This is because the CPU's throughput is orders of magnitude faster than even the fastest hard disks, so thus if the CPU's task (process) involves primarily doing I/O (copying bytes from one place to another), then the CPU/process will unavoidably have to wait for the disks to catch up, hence resulting in a high I/O wait percentage.  This is true of even the fastest disks and is not indicative of any problem in your system.

---

### Post by robcar on 2008-08-06
Thanks for the clarification/reiteration.
So what you're basically saying is that it's normal to have a quite unresponsive system during a large (let's say a couple of GB's) file transfer?
Btw isn't it a bit silly that the CPU has to 'wait' for data to come from the hard disk? Couldn't it just give **precedence** to the interactive user activity and lay the file transfer activity in the background? I could easily wait 30 seconds more but I can hardly accept that, during that file transfer, I cannot browse the Internet or launch another program.
Isn't there a way that I could change this behaviour?
For instance I've heard about the 'nice' feature of a process.

Thanks.

---

### Post by ByteJuggler on 2008-08-06
> **robcar said:**
> So what you're basically saying is that it's normal to have a quite unresponsive system during a large (let's say a couple of GB's) file transfer?

No, I'm not saying that.  The sluggishness issue is in principle a seperate issue.  (Correlation does not neccesarily imply causation.)

What I'm saying is that you should expect to see some level of I/O wait on all slow (e.g. disk) I/O operations because your CPU is orders of magnitude faster than a disk device.  To wit: the CPU can transfer GB's of data per second while your hard drive can sustain only about 80MB/sec peak and can burst data only (for SATA 1/2) at about 150MB/300MB sec out of the HDD buffers/cache (which is typically only 16MB or 32MB big.)   So hence, if you're copying gig's of data, you can then hopefully see that it will take your hard drive (for example) probably about 10seconds (in ideal circumstances, in practice on average much more) to linearly read 800MB of that data.  By comparion, your CPU would only take a split second to read/write that data, **_*if *_**it had a source that could supply the data so quickly.  Hence, the CPU will ipso-facto be ***waiting*** while the disks do their thing and physically read the data, hence the I/O wait state being reported for the process doing the I/O. 

Now, whether or not your system is sluggish during I/O is then in principle a seperate orthogonal/independant issue. So, your (a) system may or may not be sluggish during I/O depending on what else is happening at the time in your system, and what motherboard resources/busses etc is locked up by the transfer (which may in turn affect other processes wanting to make use of those resources/busses which thus in turn can manifest as sluggishness.) This is therefore a complex question which depends on many factors, the precise controllers/chipsets in use, the busses in use, the modes being used (DMA vs. PIO for IDE disks for example, IDE emulation vs native for SATA, etc.  Hence why I suggested you turn off the emulation before.)  

The point I'm trying to hammer home is that you should not be thinking in terms of "I've got this I/O WAIT IS HIGH problem and I'd like to lower it" issue to solve your sluggishness problem.  The I/O wait is a natural by product of you doing the I/O, and it will be high on any system doing intensive I/O, whether or not the system is sluggish or not.

> **robcar said:**
> 
Btw isn't it a bit silly that the CPU has to 'wait' for data to come from the hard disk? Couldn't it just give **precedence** to the interactive user activity and lay the file transfer activity in the background? I could easily wait 30 seconds more but I can hardly accept that, during that file transfer, I cannot browse the Internet or launch another program.
Isn't there a way that I could change this behaviour?
For instance I've heard about the 'nice' feature of a process.


Well as I explained above, a process has no choice but to wait for the data to come from a disk.  That is not to say that it should affect the rest of the system, as I've tried to explain above. But nevertheless, the data isn't ready (for the process to process/use) until it's been read off the disk.  And the disk can only read it *so* fast.  So, until it's been read, the process has to wait/block (in a type of sleep state, called "I/O wait", which by the way doesn't in itself harm any other process.  E.g. It is not an active "polling" type state which would was cpu cycles, it is instead itself a blocked/sleeping state where the kernel has blocked execution of that process until a required I/O operation has completed for it to be able to continue running/processing. )

It sounds to me like (for whatever reason) some key resources (busses perhaps) on your motherboard is being locked (almost exclusively?) by the I/O caused by the copy, hence affecting other processes.  I'm not sure why this is on your system, suffice to say that it's not exactly normal, and can depend on a myriad of factors, some of which may be hardware/controller related and thus may not be solvable in software.

Does your system suffer the same sluggishness if you copy from the command line?

As for "nice": Nice/priority level has to do with CPU use.  It doesn't affect I/O use directly.  If your process is CPU bound (e.g. its primarily doing computations/making use of the CPU) then you can ensure it doesn't affect other processes needing the CPU by lowering its priority using the "renice" command.

---

### Post by robcar on 2008-08-06
Many thanks for the long answer. Yes, the problem is present both in Nautilus and in the shell; the DMA mode is udma6 and I removed the all_generic_ide in the boot options, as you had suggested.

Btw the new drive has just arrived so tongiht I'm going to do some benchmarks. I do really hope to have some improvement, even if your previous post made me less optimistic about that...

---

### Post by robcar on 2008-08-09
I finally managed to install the new 10000rpm SATA drive. I also managed to clone my previous disk onto the new one.
I have to say that I'm quite satisfied with it!

Following are some tests that I did.

**Read-Write Test**
First of all I copied 3GB of movies between to folders inside the new disk. The good news is that it took considerably **less time**: 40% faster than the old 7200rpm disk.
The not-so-good news is that the system wasn't as responsive as I wanted; actually I didn't experience a tangible difference in responsiveness and in the I/O wait values with respect to my previous disk.

**Read Test**
The main utilization of my computer is to run some virtual machines: that's my home lab, where I can do also destructive tests that for obvious reasons I cannot do at work, in production environments.
When using virtualization programs like VMWare, the pc and its I/O is under stress during VMs' boots, because it has to read big files, which represents VMs hard disks.
The excellent news is that now those VMs load much faster than before and CPU I/O wait time stays high (but not more than 50%) for **much less** time.

So, after all, I think that a faster disk, rather than the mainstream 7200rpm SATA disks, can make the difference in the overall performance of a computer.

---

### Post by ByteJuggler on 2008-08-09
> **robcar said:**
> So, after all, I think that a faster disk, rather than the mainstream 7200rpm SATA disks, can make the difference in the overall performance of a computer.

Yes.  I suspect the only way to materially increase the responsiveness of your machine during heave I/O would be to get better hardware, either a better motherboard and/or possibly a dedicated SATA controller.  But, as you've already ameliorated the original problem substantially by reducing the period of time the system spends under "I/O stress", so such radical measures is probably not warranted anymore....  Glad you got somewhere towards a satisfactory solution anyway.  :)

---

### Post by wd5gnr on 2008-12-31
Old thread, but I've had the same problem while working with some very large files. Changing the I/O scheduler on the disks to anticipatory seemed to do the best for me:

For my drive on /dev/sdc:

sudo -i
cd /sys/block/sdc/queue
cat scheduler    # should say noop anticipatory deadline [cfq] meaning cfq is set
echo anticipatory >scheduler
cat scheduler   # verify it now says [anticipatory]

Still trying to figure what makes is so very slow. It seems copying or decompressing a large file even with plenty of CPU cycles to spare makes everything jerky. Although the anticipatory scheduler seems to help, it still isn't "transparent".

---

### Post by jpkotta on 2009-01-01
You seem to be using some sort of PATA->SATA translation.  Does your BIOS have an AHCI/native mode for the SATA controller?  If so, enable that and see if it helps.

---

### Post by robcar on 2009-01-01
> **wd5gnr said:**
> 

sudo -i
cd /sys/block/sdc/queue
cat scheduler    # should say noop anticipatory deadline [cfq] meaning cfq is set
echo anticipatory >queue
cat scheduler   # verify it now says [anticipatory]



Thanks for the tip above; but it should be:

```
echo anticipatory >scheduler
```

Btw I'll try that too and see if it makes disk I/O faster.

bye
--
rob

---

### Post by wd5gnr on 2009-01-02
I'm not sure if you meant the PATA->SATA translation to me or someone else. In any event, I don't see any evidence of that. The drives are SATA and they show up as SATA drives.

I got tired of manually munging the scheduler files so I wrote a small app in Gambas to do it for me. You can download a deb file below although I'm not sure how much good it will do since it uses Gambas 2.9 and the Gambas version in the repos is older than that I think. Source is included so if you have Gambas you could probably open it and go from the source archive.

[http://www.hotsolder.com/2009/01/io-scheduling-eleveator-and-gambas.html](http://www.hotsolder.com/2009/01/io-scheduling-eleveator-and-gambas.html)

---

### Post by jpkotta on 2009-01-02
> **wd5gnr said:**
> I'm not sure if you meant the PATA->SATA translation to me or someone else. In any event, I don't see any evidence of that. The drives are SATA and they show up as SATA drives.


No, I was refering to OP.  I didn't even realize how old this thread is.

---

### Post by dcstar on 2009-01-02
> **robcar said:**
> Well, thanks, but I have **SATA** drives (hard disk and DVR-RW), not IDE ones.


Then I am wondering what all the references to PATA drives that you posted were for?

Anyway, I found that removing the tracker package from any Ubuntu system I install makes things much quicker, as it seems to try and index any new file placed anywhere (and this can really slow down any other disk I/O).

---

### Post by stereomuffin on 2009-02-10
> **dcstar said:**
> Then I am wondering what all the references to PATA drives that you posted were for?

Anyway, I found that removing the tracker package from any Ubuntu system I install makes things much quicker, as it seems to try and index any new file placed anywhere (and this can really slow down any other disk I/O).

That tip about removing the tracker package is excellent.
My system is lots quicker, cheers.

---

### Post by sunny_nwho on 2009-02-14
Can you mention here how to remove the tracker package? Even I have a similar situation

---

### Post by chinchillart on 2009-02-17
> **sunny_nwho said:**
> Can you mention here how to remove the tracker package? Even I have a similar situation

I've simply choose System->Preference->Session and disabled Tracker applet and daemon.

**But I'm still experiencing the same problem**.

Large file transfers between two different SATA drives takes forever to complete. Average speed 10MB/s bewteen Samsung SpinPoint F1 ST501lj and WD 1TB-EACS drive. But also between PATA and SATA drives.

In my BIOS the SATA drives are mapped to EIDE. Trying to set the AHCI mode results in a boot failure..

I do have 8.04.2:
```

$ uname -a
Linux ubuntu 2.6.24-23-generic #1 SMP Thu Feb 5 15:00:25 UTC 2009 i686 GNU/Linux

```
:(

---

### Post by jamesnmandy on 2009-02-18
Hello all, I am having the same issue on a brand new fresh install of 8.10 last night....

my issue is actually two part, perhaps one common thing is restricting both?

A. File transfers from my external USB connected HDD to my local HDD are painfully slow.....and not to induce flames, but copying a 7Gb file on Windows 7 (or even Vista or XP for that matter) took all of maybe 20 minutes tops....on Ubuntu it is looking to take a good two hours!  Progress bar is showing a 1Mb/s transfer speed....that's just horrible!  

B. Multi part .rar decompression seems to take just as long on the same file....what took 8 minutes on Windows 7 using WinRar is now taking a couple hours on Ubuntu!

Certainly many other people are having these issues.  I know my hardware is not to blame because this is the same exact hardware, all I did was format and install Ubuntu.  If I am not mistaken Ubuntu is still running on i386 correct?  Could this be part of the issue?  That the OS is not able to take advantage of i486, i586, i686 enhancements?

Would it be better to run Wine and WinRar or 7rar or even Frog?

I checked the system monitor, CPU is barely being used on both cores, memory also barely being used....the system is running normally in terms of responsiveness.  I do not have the same system hang issue the OP was/is having, it's just it seems Ubuntu's ability to transfer files is seriously crippled for some reason.

Help!

---

### Post by ByteJuggler on 2009-02-18
> **jamesnmandy said:**
> 
Certainly many other people are having these issues.  I know my hardware is not to blame because this is the same exact hardware, all I did was format and install Ubuntu.  If I am not mistaken Ubuntu is still running on i386 correct?  Could this be part of the issue?  That the OS is not able to take advantage of i486, i586, i686 enhancements? ... it seems Ubuntu's ability to transfer files is seriously crippled for some reason.


Read the entire thread.  Have you investigated whether some of the reasons listed may apply to you?  (Emulation mode etc.)  It's got nothing to do with the instruction set in use, no.  (Ubuntu uses x64 for 64bit releases and "i686" for 32bit releases.)

---

### Post by fart_flower on 2009-02-28
I'm pretty certain this bugzilla thread is related to the above described problems:
[http://bugzilla.kernel.org/show_bug.cgi?id=12309](http://bugzilla.kernel.org/show_bug.cgi?id=12309)

Sounds like it's a fun bug!

---

### Post by ByteJuggler on 2009-03-01
Hmmm... Well, sounds like the scheduler may have something to do with it then, and that the boot option "elevator=as" may improve matters by using a different scheduler.  Might be worth a shot.  Nevertheless, as I've previously explained, high IO-wait in and of itself is not neccesarily a problem and does not neccesarily imply a sluggish system.  It just so happens in this instance that the two are correlated for a (so far) unknown/undetected reason.

Edit: What a fun bug indeed, having read more of that report... ;)

---

