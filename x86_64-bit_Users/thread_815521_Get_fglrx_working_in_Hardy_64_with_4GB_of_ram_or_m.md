---
title: "Get fglrx working in Hardy 64 with 4GB of ram or more - update"
date: 2008-06-01
forum: x86 64-bit Users
---

### Post by sonni_kuba on 2008-06-01
I was wondering if there has been any development on running the proprietary ATI drivers without disabling PCI remap memory. I have been trying to rewrite my /proc/mtrr tables, but without much success, and I actually need to use all of my 8GB of RAM. 

Thanks in advance,
S

---

### Post by kingtaurus on 2008-06-02
Can you post your system specs (memory on graphics card, memory in system) and current mtrr tables?

---

### Post by sonni_kuba on 2008-06-03
> Can you post your system specs (memory on graphics card, memory in system) and current mtrr tables? 

Sure here are the specs,

system memory is 8 GB
graphics card is HD 2600 w/ 256 MB
current mtrr tables

reg00: base=0xd0000000 (3328MB), size= 256MB: uncachable, count=1
reg01: base=0xe0000000 (3584MB), size= 512MB: uncachable, count=1
reg02: base=0x00000000 (   0MB), size=8192MB: write-back, count=1
reg03: base=0x200000000 (8192MB), size= 512MB: write-back, count=1
reg04: base=0x220000000 (8704MB), size= 128MB: write-back, count=1
reg05: base=0x228000000 (8832MB), size=  64MB: write-back, count=1

---

### Post by kingtaurus on 2008-06-03
I think the issue is with the base=0xd0000000 being declared uncachable. I think I'll also output from lspci -v (attach the output to your next post).

---

### Post by sonni_kuba on 2008-06-03
Thank you kingtaurus for your interest in helping me sort this case out; I actually wrote a script to rewrite the mtrr talbes as previously posted by AsuLUTZKY

[http://ubuntuforums.org/showthread.php?p=4766662]("http://ubuntuforums.org/showthread.php?p=4766662")

However, this did not solve the problem. In the end, I need to use both my RAM and graphics card together for imaging analysis and cannot afford to waste any more time ... so ... I decided that it was time to upgrade !!!

I bought a 512MB ZOTAC 8800 GT card for $170, and sold the ATI HD 2600 for $50 on Craigslist. As I am writing this, this setup is working perfectly, without the hassle of ATI's configuration madness.

In a sense, I am disappointed that I had to upgrade a fairly decent and new video card, but the difference in Linux support between ATI and NVIDIA is too significant to be ignored.

---

### Post by ASULutzy on 2008-06-03
Yep, I still have to use my mtrr fixup script in order to use fglrx and 4 GB of ram
```
#!/bin/sh
# Fixup /proc/mtrr

echo "disable=2" >| /proc/mtrr
echo "disable=1" >| /proc/mtrr
echo "disable=3" >| /proc/mtrr
echo "disable=4" >| /proc/mtrr
echo "disable=0" >| /proc/mtrr
echo "base=0x00000000 size=0x80000000 type=write-back" >| /proc/mtrr
echo "base=0x80000000 size=0x40000000 type=write-back" >| /proc/mtrr
echo "base=0xC0000000 size=0x10000000 type=write-back" >| /proc/mtrr
echo "base=0x100000000 size=0x20000000 type=write-back" >| /proc/mtrr
echo "base=0x120000000 size=0x10000000 type=write-back" >| /proc/mtrr
```

edit: I think the problem might also stem from how Asus' memory remap feature works in their BIOS.

I have the ASUS-P5k vanilla, and I think I've seen most of the other people with the ATI + >3.2GB of ram have an ASUS P5k board

---

### Post by kingtaurus on 2008-06-04
I just wanted to make a clarifying point. I don't think this is just an AMD/ATI problem, because according to [https://bugs.launchpad.net/linux/+bug/210780]("https://bugs.launchpad.net/linux/+bug/210780") this issue also effects computers with 4GB and an Intel Graphic Card.

sonni_kuba - Hopefully you'll have less issues :)

---

### Post by sonni_kuba on 2008-06-04
> I don't think this is just an AMD/ATI problem

Actually, whatever the problem is, it certainly doesn't apply to the NVIDIA G92 cards, as I got the 8800 GT running with 8 GB of RAM.

Thanks again to both of you for your help, although ubuntu hardware detection has improved vastly since Warthog (if you can remember those days ;-)), there is still potential to grow, though I think the problem here is more to do with ATI ... but given their financial woes, I don't blame them for not investing heavily into *nix graphics driver development.

---

### Post by pcflyer44 on 2008-06-20
:confused:Hi I am having a similar problem with my system and it seems more like Ubuntu is having problems reading the AGP port than the video cards because I put in a PCI card and it is having no trouble at all. In the system setup I can see that the AGP bridge has been loaded but it can not see the video cards and I have used nvidia and ati.


system
nforce3 motherboard
768MB ram
now running nvidia FX5500 PCI 256MB
want to run ATI X1300 AGP 256MB
first video was nvidia FX5600xt AGP 128MB

---

### Post by Ubumble on 2008-07-02
It looks like the mtrr remapping is the fix I have been searching for. I have one question though, is there something special about the individual registers?  I ask because the output from my /proc/mtrr has the same bases and sizes as the ones ASULutzy started with in a previous post, but mine are assigned to different registers.  Thanks for any answers or directions to answers.

---

### Post by stchman on 2008-07-02
> **sonni_kuba said:**
> I was wondering if there has been any development on running the proprietary ATI drivers without disabling PCI remap memory. I have been trying to rewrite my /proc/mtrr tables, but without much success, and I actually need to use all of my 8GB of RAM. 

Thanks in advance,
S

Hardy 64 should support 8GB RAM.  64 bit OS can  support MASSIVE amounts of RAM.

Does the fglrx driver give you problems?

---

### Post by kingtaurus on 2008-07-02
The mtrr tables have been known to cause problems for both Intel and and AMD/ATI (using fglrx) graphics cards.

---

### Post by HughR on 2008-09-18
I have this problem so I've written an experimental program to rejig MTRRs.  It may not work -- it may require more MTRRs than the hardware supports.

Read about it here: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/224404/comments/42](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/224404/comments/42)

I would really like feedback.

---

### Post by Dyst Mingus on 2008-12-07
Hi-
I am running Intrepid with 8GB RAM. Have this:

```
> lspci | grep ATI
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3850
01:00.1 Audio device: ATI Technologies Inc Radeon HD 3870 Audio device

```
I have written a script to rewrite the mtrr however, i am unable to get the system to write a nested write-back section in the first 4GB section. I have created the first 4GB as write-back and i can create a nested write-back in the second 4GB. My problem... need the write-back base in the first 4GB for my card. 

Here is my code. The top comments show the original table.
```
#!/bin/bash

#================================================================================
# This is a script for fixing the mtrr tables to work with fglrx driver
# on my system with 8GB RAM. Previous mtrr:
#
#     reg00: base=0x00000000 (   0MB), size=4096MB: write-back, count=1
#     reg01: base=0xe0000000 (3584MB), size= 512MB: uncachable, count=1
#     reg02: base=0xd0000000 (3328MB), size= 256MB: uncachable, count=1
#     reg03: base=0x100000000 (4096MB), size=4096MB: write-back, count=1
#     reg04: base=0x200000000 (8192MB), size=1024MB: write-back, count=1
#     reg05: base=0x230000000 (8960MB), size= 256MB: uncachable, count=1
#     reg06: base=0xcff00000 (3327MB), size=   1MB: uncachable, count=1
#================================================================================

# Disable previous entries. Outer allocations first, neted allocations last.

echo "disable=0" >| /proc/mtrr
echo "disable=3" >| /proc/mtrr
echo "disable=2" >| /proc/mtrr
echo "disable=1" >| /proc/mtrr
echo "disable=6" >| /proc/mtrr
echo "disable=5" >| /proc/mtrr
echo "disable=4" >| /proc/mtrr

# Set new values.
echo "base=0x00000000 size=0x100000000 type=write-back" >| /proc/mtrr
echo "base=0xe0000000 size=0x20000000 type=uncachable" >| /proc/mtrr
echo "base=0xd0000000 size=0x10000000 type=write-back" >| /proc/mtrr
echo "base=0x100000000 size=0x100000000 type=write-back" >| /proc/mtrr
echo "base=0x200000000 size=0x40000000 type=write-back" >| /proc/mtrr
echo "base=0x230000000 size=0x10000000 type=uncachable" >| /proc/mtrr
echo "base=0xcff00000 size=0x100000 type=uncachable" >| /proc/mtrr
echo "Tables Written."

```

Upon completion the table looks like this:

```
> cat /proc/mtrr
reg00: base=0x00000000 (   0MB), size=4096MB: write-back, count=1
reg01: base=0xe0000000 (3584MB), size= 512MB: uncachable, count=1
reg02: base=0x100000000 (4096MB), size=4096MB: write-back, count=1
reg03: base=0x200000000 (8192MB), size=1024MB: write-back, count=1
reg04: base=0x230000000 (8960MB), size= 256MB: uncachable, count=1
reg05: base=0xcff00000 (3327MB), size=   1MB: uncachable, count=1

```

I need the 0xd0000000 as write-back as that is what the vid card uses. I have tried changing the order and tried to make the 0xe0000000 base assignmet write-back to see if it would write. It will not. If i make them both uncachable they will both write, but no good for fglrx. Can anybody explain to me why this is happening? i will take "shot-in-the-dark" suggestions, but i would rather understand why.

thanks loads pals!

-damon

---

### Post by HughR on 2008-12-07
> **Dyst Mingus said:**
> . Can anybody explain to me why this is happening? i will take "shot-in-the-dark" suggestions, but i would rather understand why.

The rules for MTRRs is arcane.  But I did the work for you.  Read the previous comment.

I tried my program on your setup and it looks as if it can solve your problem.  Just barely: after the dust settles, there will be no spare MTRRs.

I will leave it as an exercise for you to run my program.  I want more testing.  Play with it, read the documentation, learn from it -- I did.

Random other facts:

Your video card driver most likely wants Write-Combining, not Write-Back.  The driver can change an MTRR as long as it isn't nested.

If there is no nesting, Uncachable need not be specified since it is the default.

Nesting rules are bad and the kernel deals badly with nesting.

You certainly didn't have to delete and replace all of the MTRRs.  In particular, none of the settings for things above 4G need to be changed.

---

### Post by Dyst Mingus on 2008-12-08
looked at your stuff before i posted. cannot dl your code, connection refused. can you stick it in a code blok and post it? thnx

-d

---

### Post by HughR on 2008-12-13
> **Dyst Mingus said:**
> looked at your stuff before i posted. cannot dl your code, connection refused. can you stick it in a code blok and post it? thnx

-d

Sorry for the slow reply: my desktop computer has had a hardware failure.

I updated the mtrr-uncover program a few times.  There are several versions in that FTP directory.  Go for the one with the latest date in its name.

[ftp://ftp.cs.utoronto.ca/pub/hugh/](ftp://ftp.cs.utoronto.ca/pub/hugh/)

Here is a very recent report of success with this tool:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/210780/comments/27](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/210780/comments/27)

---

### Post by r m h on 2008-12-13
HughR - mtrr-uncover indicates it needs more MTRRs than available?!

~/Desktop# ./mtrr-uncover
Initial MTRR configuration:
 0  0x000000000-0x1ffffffff write-back
         4  0x0bf800000-0x0bfffffff uncachable
         3  0x0c0000000-0x0ffffffff uncachable
 1  0x200000000-0x2ffffffff write-back
 2  0x300000000-0x33fffffff write-back
./mtrr-uncover: 11 MTRRs needed but only 8 in architecture.



Background:
Yesteday, I built a new super workstation:
Asus Rampage II Extreme mainboard
Intel Core i7 940 (2.94GHz)
12GB RAM (6x2GB)
ATI Radeon HD 4850 video card (PCI-Express) on PCIbus 2
ATI Radeon HD 4850 video card (PCI-Express) on PCIbus 3
3Ware 9650 with 6 SATA II HDD RAID (PCI-Express) on PCIbus 6

Last night I installed Ubuntu 8.10 x86_64 then naively installed the ATI/AMD FGLRX proprietary drivers (module fglrx-8.543) and that blew up my X windows, so I backed that out and started researching.  That research led me to many places, including here.

~/Desktop# cat /proc/mtrr
reg00: base=0x00000000 (   0MB), size=8192MB: write-back, count=1
reg01: base=0x200000000 (8192MB), size=4096MB: write-back, count=1
reg02: base=0x300000000 (12288MB), size=1024MB: write-back, count=1
reg03: base=0xc0000000 (3072MB), size=1024MB: uncachable, count=1
reg04: base=0xbf800000 (3064MB), size=   8MB: uncachable, count=1

~/Desktop# lspci -v
...
02:00.0 VGA compatible controller: ATI Technologies Inc RV770 [Radeon HD 4850]
	Subsystem: PC Partner Limited Device e810
	Flags: bus master, fast devsel, latency 0, IRQ 24
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at fb8e0000 (64-bit, non-prefetchable) [size=64K]
	I/O ports at 8000 [size=256]
	Expansion ROM at fb8c0000 [disabled] [size=128K]
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Legacy Endpoint, MSI 00
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [100] Vendor Specific Information <?>

02:00.1 Audio device: ATI Technologies Inc HD48x0 audio
	Subsystem: PC Partner Limited Device aa30
	Flags: bus master, fast devsel, latency 0, IRQ 34
	Memory at fb8fc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Legacy Endpoint, MSI 00
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [100] Vendor Specific Information <?>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

03:00.0 VGA compatible controller: ATI Technologies Inc RV770 [Radeon HD 4850]
	Subsystem: PC Partner Limited Device e810
	Flags: fast devsel, IRQ 10
	Memory at d0000000 (64-bit, prefetchable) [disabled] [size=256M]
	Memory at fb9e0000 (64-bit, non-prefetchable) [disabled] [size=64K]
	I/O ports at 9000 [disabled] [size=256]
	Expansion ROM at fb9c0000 [disabled] [size=128K]
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Legacy Endpoint, MSI 00
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [100] Vendor Specific Information <?>

03:00.1 Audio device: ATI Technologies Inc HD48x0 audio
	Subsystem: PC Partner Limited Device aa30
	Flags: bus master, fast devsel, latency 0, IRQ 37
	Memory at fb9fc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Legacy Endpoint, MSI 00
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [100] Vendor Specific Information <?>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
...

thoughts?

---

### Post by r m h on 2008-12-13
Update - here's what I did to make it work:

I edited my /etc/X11/xorg.conf file to include 'Busid "PCI:2:0:0"' in the "Device" section.  

I currently have monitors connected to both of the DVI outputs on one of the ATI 4850 cards, the other is not in use at present.  That config (and those 2 extra LCDs) come later.

Here's my working xorg.conf file:

Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "Default Screen" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
	Option	    "EnableMonitor" "crt1,lvds,tv,tmds1,crt2,tmds2,cv,tmds2i"
	BusID       "PCI:2:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
EndSection


My problem now is that regardless of how many times I enable the dual LCDs to have the second one extend the desktop of the primary one, it doesn't stay that way after a reboot.  I have to go back into the ATI Catalyst Control Center and re-extend the desktop to the second LCD.  It always defaults to mirroring what's on the the primary LCD.

thoughts?

---

### Post by HughR on 2008-12-13
> **r m h said:**
> HughR - mtrr-uncover indicates it needs more MTRRs than available?!

```
~/Desktop# ./mtrr-uncover
Initial MTRR configuration:
 0  0x000000000-0x1ffffffff write-back
         4  0x0bf800000-0x0bfffffff uncachable
         3  0x0c0000000-0x0ffffffff uncachable
 1  0x200000000-0x2ffffffff write-back
 2  0x300000000-0x33fffffff write-back
./mtrr-uncover: 11 MTRRs needed but only 8 in architecture.
```


Leading spaces seem to disappear making the indentation disappear.  Using a code block preserves the indentation.

There is no guarantee that mtrr-uncover can find a solution, but it usually does.

How did you invoke it?  Which version did you use?

When I try it with your initial MTRR settings, I get something that appears satisfactory.  I'm using a version that is essentially [ftp://ftp.cs.utoronto.ca/pub/hugh/mtrr-uncover-2008oct01.tgz](ftp://ftp.cs.utoronto.ca/pub/hugh/mtrr-uncover-2008oct01.tgz)

```
$ ./mtrr-uncover --mtrrfile mtrr.sample.rmh
Initial MTRR configuration:
 0  0x000000000-0x1ffffffff write-back
         4  0x0bf800000-0x0bfffffff uncachable
         3  0x0c0000000-0x0ffffffff uncachable
 1  0x200000000-0x2ffffffff write-back
 2  0x300000000-0x33fffffff write-back

Final MTRR configuration:
 0' 0x000000000-0x07fffffff write-back
51' 0x080000000-0x0bfffffff write-back
         4  0x0bf800000-0x0bfffffff uncachable
50  0x100000000-0x1ffffffff write-back
 1  0x200000000-0x2ffffffff write-back
 2  0x300000000-0x33fffffff write-back

Commands for /proc/mtrr to make these changes:
disable=0
disable=3
base=0x000000000 size=0x080000000 type=write-back
base=0x080000000 size=0x040000000 type=write-back
base=0x100000000 size=0x100000000 type=write-back


```

Note that this leaves MTRR 4 still nested.  Since its size is only 8MB, it is probably not a video buffer.  So it is probably not a problem.  What is it?  It does not show up in your (partial) lspci output.

---

### Post by r m h on 2008-12-13
HughR -

I downloaded, built, and ran "mtrr-uncover-2008sept30" from your FTP site - it was the latest I saw two days ago.  I see you ran with the Oct 1 version.  

Oops, I grabbed the bottom-most version from the FTP directory, unfortunately the October version lexicographically sorts before the September version.  My bad for not seeing this.

I invoked it as indicated in the previous post 
(as root) ./mtrr-uncover

---

### Post by r m h on 2008-12-13
> 
Note that this leaves MTRR 4 still nested.  Since its size is only 8MB, it is probably not a video buffer.  So it is probably not a problem.  What is it?  It does not show up in your (partial) lspci output.

MTRR 4 is this NIC:

```
04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
	Subsystem: ASUSTeK Computer Inc. Device 81f8
	Flags: bus master, fast devsel, latency 0, IRQ 2294
	Memory at fbafc000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at a800 [size=256]
	Expansion ROM at fbac0000 [disabled] [size=128K]
	Capabilities: [48] Power Management version 3
	Capabilities: [50] Vital Product Data <?>
	Capabilities: [5c] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [e0] Express Legacy Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Kernel driver in use: sky2
	Kernel modules: sky2

```

---

### Post by HughR on 2008-12-15
> **r m h said:**
> MTRR 4 is this NIC:

```
04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
	Subsystem: ASUSTeK Computer Inc. Device 81f8
	Flags: bus master, fast devsel, latency 0, IRQ 2294
	Memory at fbafc000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at a800 [size=256]
	Expansion ROM at fbac0000 [disabled] [size=128K]
	Capabilities: [48] Power Management version 3
	Capabilities: [50] Vital Product Data <?>
	Capabilities: [5c] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [e0] Express Legacy Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Kernel driver in use: sky2
	Kernel modules: sky2

```
The range 0x0bf800000-0x0bfffffff is covered by MTRR 4.  Only part of that range seems to be mentioned in the LSPCI output.

I expect that the NIC driver is content to leave the memory type as uncached so the nesting does not matter.

The only drivers that I've seen that want to change the memory type are video drivers and an Infiniband driver.  But I'm still learning about this stuff.

BTW recent Linus kernels have code to reorganize MTRRs (not written by me).  I don't think that Ubuntu has adopted those kernels yet.  I'm too lazy to check.

---

### Post by Entity` on 2009-05-24
I used mtrr uncover, but I don't know how to fix my mtrr table.

```

0 0x000000000-0x07ffffff write-back
1 0x080000000-0x0bffffff write-back
2 0x0c0000000-0x0cffffff write-back
       3 0x0cff00000-0x0cfffffff uncachable
4 0x100000000-0x11ffffff write-back
5 0x120000000-0x12ffffff write-back

```

Where do I go from here?

---

### Post by HughR on 2009-05-24
> **Entity` said:**
> I used mtrr uncover, but I don't know how to fix my mtrr table.

```

0 0x000000000-0x07ffffff write-back
1 0x080000000-0x0bffffff write-back
2 0x0c0000000-0x0cffffff write-back
       3 0x0cff00000-0x0cfffffff uncachable
4 0x100000000-0x11ffffff write-back
5 0x120000000-0x12ffffff write-back

```

Where do I go from here?

You didn't quote all that mtrr-uncover said.

What did mtrr-uncover say to do?

Is this the "before" or "after" MTRR setting?

If it is "before", then you appear to have a problem.  Your uncachable region is only 1 MiB in size.  If that is your video card's buffer, then you have a very very old card.  Cards that old are not supported by fglrx.

If it is "after", perhaps mtrr-uncover thinks it has presented a solution for you.  I say "perhaps" because you don't show us any other messages that mtrr-uncovered printed.  Assuming it was happy, you need to implement what it suggests; the easiest way is to use the --execute flag (read the manual page: man ./mtrr-uncover.8 ).  Note: it has to be run before X starts; for testing, you can run it and then restart X.

---

### Post by Tomatosoup on 2009-05-24
This is my MTRR table:
```
reg00: base=0x000000000 ( 0MB), size=65536MB, count=1: write-back
reg01: base=0x0bff00000 ( 3071MB), size= 1MB, count=1: uncachable
reg02: base=0x0c0000000 ( 3072MB), size= 1024MB, count=1: uncachable
```

Does seem like kind of an odd table...

But I don't know what it should be like.

I've used the utility mtrr-uncover, which automatically tries to determine a correct MTRR table. Then I do not crash when starting X, but it does fail.

The MTRR utility returns this:
```
Initial MTRR configuration:
0 0x000000000-0xfffffffff write-back
1 0x0bff00000-0x0bfffffff uncachable
2 0x0c0000000-0x0ffffffff uncachable

Final MTRR configuration:
0' 0x000000000-0x07fffffff write-back
54' 0x080000000-0x0bfffffff write-back
1 0x0bff00000-0x0bfffffff uncachable
53 0x100000000-0x1ffffffff write-back
52 0x200000000-0x3ffffffff write-back
51 0x400000000-0x7ffffffff write-back
50 0x800000000-0xfffffffff write-back

Commands for /proc/mtrr to make these changes:
disable=0
disable=2
base=0x000000000 size=0x080000000 type=write-back
base=0x080000000 size=0x040000000 type=write-back
base=0x100000000 size=0x100000000 type=write-back
base=0x200000000 size=0x200000000 type=write-back
base=0x400000000 size=0x400000000 type=write-back
base=0x800000000 size=0x800000000 type=write-back
```

I'm now using the 32-bit version of Ubuntu, because I thought it would matter, but it doesn't.

I have an ATI Radeon 3870 X2 512 MB (or I guess 512 MB per core).
(Ubuntu reports only 256 MB!)
And I have a Dell BIOS (XPS 430), latest revision.

---

### Post by HughR on 2009-05-24
> **Tomatosoup said:**
> This is my MTRR table:
```
reg00: base=0x000000000 ( 0MB), size=65536MB, count=1: write-back
reg01: base=0x0bff00000 ( 3071MB), size= 1MB, count=1: uncachable
reg02: base=0x0c0000000 ( 3072MB), size= 1024MB, count=1: uncachable
```

Does seem like kind of an odd table...

But I don't know what it should be like.

I've used the utility mtrr-uncover, which automatically tries to determine a correct MTRR table. Then I do not crash when starting X, but it does fail.


That does seem odd.  Do you really have 64GiB of RAM?  If so, I'm impressed!

mtrr-uncover just looks at the initial MTRR settings and reorganizes them in a way that should help video card drivers.  It doesn't have any way of knowing whether the initial settings are just plain wrong.

As far as I know, having those extra ranges covered should not actually cause problems.

Your initial setup had two uncachable regions (nested within the giant write-back region).  The first, at 1MiB is probably not the video card buffer (too small); the second, at 1GiB might well be (that's quite large for a video card).

The command "lspci -v" should tell you a lot about the video card buffer.  Here, for example, is the part about one of my cards:

```
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600] (prog-if 00 [VGA controller])
        Subsystem: ATI Technologies Inc R9600 Pro primary (Asus OEM for HP)
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 201
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        I/O ports at c000 [size=256]
        Memory at ff4f0000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at ff4c0000 [disabled] [size=128K]
        Capabilities: <access denied>

01:00.1 Display controller: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary)
        Subsystem: ATI Technologies Inc R9600 Pro secondary (Asus OEM for HP)
        Flags: bus master, 66MHz, medium devsel, latency 64
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Memory at ff4e0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

```

How does starting X fail after mtrr-uncover has adjusted the MTRR settings?  Remember, without --execute, mtrr-uncover just describes what it would do.

---

### Post by Entity` on 2009-05-24
> **HughR said:**
> You didn't quote all that mtrr-uncover said.

What did mtrr-uncover say to do?

Is this the "before" or "after" MTRR setting?

If it is "before", then you appear to have a problem.  Your uncachable region is only 1 MiB in size.  If that is your video card's buffer, then you have a very very old card.  Cards that old are not supported by fglrx.

If it is "after", perhaps mtrr-uncover thinks it has presented a solution for you.  I say "perhaps" because you don't show us any other messages that mtrr-uncovered printed.  Assuming it was happy, you need to implement what it suggests; the easiest way is to use the --execute flag (read the manual page: man ./mtrr-uncover.8 ).  Note: it has to be run before X starts; for testing, you can run it and then restart X.

What I posted was all mtrr had returned.  It did not say "before" or "after" or anything like that.  That is all it gave me.  Im sorry for being unclear when I posted that.  It had given me no solution.  My card is also a relatively new HIS 4850.

---

### Post by HughR on 2009-05-24
> **Entity` said:**
> What I posted was all mtrr had returned.  It did not say "before" or "after" or anything like that.  That is all it gave me.  Im sorry for being unclear when I posted that.  It had given me no solution.  My card is also a relatively new HIS 4850.

Then mtrr-uncover would have said "No changes made." (which you didn't tell us).

I'd say that your problem is not nested MTRRs.

Why do you think that your MTRRs need fixing?  I'm not saying that they don't, but tell us why you think that they do.  You've presented very little data to use for diagnosis.

---

### Post by Entity` on 2009-05-24
Because I admit that I am not at all that brilliant at figuring out code.

I am trying this because someone else had a similar problem that was (somewhat) fixed because he tried your program.  It's just that any graphics driver I try to install results in a system that cannot boot (and eventually locks up) no matter what driver I install.  I tried the restricted driver that was immediately presented to me upon the first bootup, and that at least let my system boot up but very slowly and with a nasty flickering problem that was related to my 3rd cpu pegging out.  I tried to manually install the drivers from ATI's website, with no luck.  I tried the driver found in synaptic, with no luck either.  I even tried the open source drivers, witch would not install properly.

I really do not mean to sound overly forceful, but this problem is really starting to get on my nerves.  I'll try the 64bit version and see if I can get it to go at all.

Im trying to migrate my pc to linux from windows (forever), but I am finding it extremely difficult to do.  Perhaps I should just downgrade to 8.10 and see if I can get a result out of that.

---

### Post by HughR on 2009-05-24
> **Entity` said:**
> 
Im trying to migrate my pc to linux from windows (forever), but I am finding it extremely difficult to do.  Perhaps I should just downgrade to 8.10 and see if I can get a result out of that.

Video drivers can be a pain.  Not my area of expertise, mind you.

I suspect that the HIS 4850 is too recent to be supported by the open-source driver "ati".

For a start, you could tell Linux to use the vesa driver.  This is not going to exploit your card well but I think that it should work.  In fact, I thought that that was what Ubuntu did when it doesn't know about a video card.

Why do you try to install a graphics driver?  Ubuntu's installation will pick one.  Apparently its choice did work.  Is it the case that you only get into trouble when you change the driver?

Does it work better when you have less than 4G of RAM installed?  If not, I suggest you look for another thread or create a new one.  This one seems to be about problems with 4G or more of RAM + ATI card.

Good luck!

---

### Post by markbuntu on 2009-05-24
I have 6GB ram and have not had any ram related problems with the ati drivers with my HD3650 in Hardy or Intrepid amd64. I am not about to try that broken 9.4 driver on Jaunty. I had a bad enough time with it with Hardy.

---

### Post by Entity` on 2009-05-27
I finally installed the 64bit version of Ubuntu 9.04 and it seems to behave a lot better.  However, my mtrr-table seems to have changed slightly.

```
Initial MTRR configuration:
 0  0x000000000-0x07fffffff write-back
 1  0x080000000-0x0bfffffff write-back
 2  0x0c0000000-0x0cfffffff write-back
         3  0x0cff00000-0x0cfffffff uncachable
 6  0x0d0000000-0x0dfffffff write-combining
 4  0x100000000-0x11fffffff write-back
 5  0x120000000-0x12fffffff write-back
No changes made.

```

That is what it has shown me.  Is it me or does 6 seem a bit odd?  Should I change it manually or just leave it.

I have not installed any additional graphics drivers yet, but I want to so I can get 3D acceleration so I can finally move away from windows and play my games.

Also my xorg.conf file is plain empty.  Nothing is there, and I feel that there should be stuff there.

---

### Post by HughR on 2009-05-27
> **Entity` said:**
> I finally installed the 64bit version of Ubuntu 9.04 and it seems to behave a lot better.  However, my mtrr-table seems to have changed slightly.

```
Initial MTRR configuration:
 0  0x000000000-0x07fffffff write-back
 1  0x080000000-0x0bfffffff write-back
 2  0x0c0000000-0x0cfffffff write-back
         3  0x0cff00000-0x0cfffffff uncachable
 6  0x0d0000000-0x0dfffffff write-combining
 4  0x100000000-0x11fffffff write-back
 5  0x120000000-0x12fffffff write-back
No changes made.

```

That is what it has shown me.  Is it me or does 6 seem a bit odd?  Should I change it manually or just leave it.

I have not installed any additional graphics drivers yet, but I want to so I can get 3D acceleration so I can finally move away from windows and play my games.

Also my xorg.conf file is plain empty.  Nothing is there, and I feel that there should be stuff there.
Thanks for quoting the whole output.

MTRR 6 seems exactly right if X is running.  This isn't the way the BIOS set it up but the X video driver changed it.  The clue is "write-combining".  Your video card's buffer is 0x0d0000000-0x0dfffffff.

Some X video drivers accomplish the same effect using PAT and so the MTRR does not get changed (eg. the nVidia proprietary driver).

A quick look suggests that the only difference between this MTRR setting and the earlier one you showed us is MTRR 6, a change made by the X driver.

I don't think you have an MTRR problem.  Thank goodness.

A 32-bit kernel can only use more than 4G of RAM (address space, to be technically correct) if it has PAE support compiled in.  I don't happen to remember whether the default Ubuntu kernel has PAE, but I would guess not (it costs performance).  So running a 64-bit kernel makes sense.

You may only have 4G of RAM, but the address space has to include both the RAM and I/O devices (like your video card's memory).  In particular, some of the address space below 4G has been used for I/O devices so I think that you have 3/4 G of your 4G of RAM at addresses above 4G.  This is shown by MTRR 4 and 5.

A missing /etc/X11/xorg.conf is fine with recent versions of X.  Many changes have been made to make all the defaults work out for the best.  You only need one to change the behaviour from the default.

---

### Post by Entity` on 2009-05-28
Thank you for your explanation.  I'm about to enable the proprietary drivers to see if anything [good] happens.  If not, well I'll just have to deal with it.

---

### Post by bcschmerker on 2009-05-31
> **HughR said:**
> Video drivers can be a pain.  Not my area of expertise, mind you.

I suspect that the HIS 4850 is too recent to be supported by the open-source driver "ati"....

Why do you try to install a graphics driver?  Ubuntu's installation will pick one.  Apparently its choice did work.  Is it the case that you only get into trouble when you change the driver?

Does it work better when you have less than 4G of RAM installed?  If not, I suggest you look for another thread or create a new one.  This one seems to be about problems with 4G or more of RAM + ATI card.

Good luck!I recently had to do a second rebuild of my Everex, as I had uncommanded shutdowns with the [nVIDIA nForce405/GeForce6100 chipset](http://www.nvidia.com/") on the Elitegroup 'board that I previously used.  The new [Gigabyte MA78GM-S2HP 'board](http://www.gigabyte.com/) that I now run, uses an all-[Advance Micro Devices](http://www.amd.com/) chipset:  the 780G PCI-Express 'set and ATI Radeon HD 3200 GPU.  Both VESA and ATI Xorg servers were unable to probe the HD 3200, so I had to install the fglrx server; I've had no problems to date as of this post (the BIOS currently assigns 128 MB of my 2 GB total RAM to video), but will take a Radeon HD 4xxx standalone PCI-Express video card with 1 GB DDR3 video memory under advisement in the event of memory upgrade to 4+ GB ECC registered.

I'll see what advice I *can* provide after reviewing MTRR and DSDT offline....

Update:  Apparently manufacturers have improved their firmware interfaces since this Thread was started.  My Everex with Gigabyte MA78GM-S2HP reports 1792 of 2048 total MB as write-back and only 2 MB uncacheable, concatenating /proc/mtrr:
```
reg00: base=0x00000000 (   0MB), size=1024MB: write-back, count=1
reg01: base=0x40000000 (1024MB), size= 512MB: write-back, count=1
reg02: base=0x60000000 (1536MB), size= 256MB: write-back, count=1
reg03: base=0x6fe00000 (1790MB), size=   2MB: uncachable, count=1
```Additionally, I had only two warnings and a DSDT.aml object from the Intel ASL Optimizing Compiler, /usr/bin/iasl, after the sequence of commands in "[HOWTO Fix A Buggy DSDT File](http://ubuntuforums.org/showthread.php?t=1036051&highlight=dsdt)."  Anything I missed here?

---

### Post by cozmicharlie on 2009-06-03
I don't have a 64 bit system but I did get my ati/amd working with the proprietary drivers in Jaunty. I have a J&W 780G board and prior to do performing the fix below, the proprietary drivers caused a blank screen when I tried to activate them. This worked for me - I simply checked the Jaunty proposed and backports in update manager, activated the proprietary driver and performed an upgrade.     
Hope this helps.

---

### Post by markbuntu on 2009-06-04
Well, I eventually bit the bullet and installed fglrx because there was no other way that I could find to get my dual monitors working with KDE in Jaunty. The driver actually seems to work OK once I figured out how to turn xrandr off. I wrote a little how-to here


[http://ubuntuforums.org/showthread.php?t=1152121](http://ubuntuforums.org/showthread.php?t=1152121)

---

