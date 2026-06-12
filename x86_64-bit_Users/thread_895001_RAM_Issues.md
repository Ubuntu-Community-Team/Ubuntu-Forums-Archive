---
title: "RAM Issues"
date: 2008-08-19
forum: x86 64-bit Users
---

### Post by Uzelth on 2008-08-19
Okay, I've recently read up on MTRR, however I'm still experiencing some problems... No matter what I do, when it comes to disabling register 0 the system hardlocks... I'm not sure if I've got the tables right either, so here goes with the info:

**lspci -vv** (cut to the graphics card bit)
```
05:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1) (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Unknown device 30cf
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 19
	Region 0: Memory at ce000000 (32-bit, non-prefetchable) [size=16M]
	Region 1: Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Region 3: Memory at cc000000 (64-bit, non-prefetchable) [size=32M]
	Region 5: I/O ports at 4000 [size=128]
	Capabilities: <access denied>
```

The graphics card has 256Mb dedicated graphics, I want to recover the rest of the RAM so I have 4Gb again, not 3.7Gb...

**cat /proc/mtrr**
```
reg00: base=0x00000000 (   0MB), size=2048MB: write-back, count=1
reg01: base=0x80000000 (2048MB), size=1024MB: write-back, count=1
reg02: base=0xc0000000 (3072MB), size= 128MB: write-back, count=1
reg03: base=0xc8000000 (3200MB), size=  32MB: write-back, count=1
reg04: base=0x100000000 (4096MB), size= 512MB: write-back, count=1
reg05: base=0x120000000 (4608MB), size= 256MB: write-back, count=1
```

**Register Table** (locks on disable=0)
```
echo "disable=2" >| /proc/mtrr
echo "disable=1" >| /proc/mtrr
echo "disable=3" >| /proc/mtrr
echo "disable=4" >| /proc/mtrr
echo "disable=5" >| /proc/mtrr
echo "disable=6" >| /proc/mtrr
echo "disable=7" >| /proc/mtrr
echo "disable=0" >| /proc/mtrr
echo "base=0x00000000 size=0x80000000 type=write-back" >| /proc/mtrr
echo "base=0x80000000 size=0x40000000 type=write-back" >| /proc/mtrr
echo "base=0xC0000000 size=0x10000000 type=write-back" >| /proc/mtrr
echo "base=0x100000000 size=0x10000000 type=write-back" >| /proc/mtrr
echo "base=0x110000000 size=0x10000000 type=write-back" >| /proc/mtrr
```

**Register Table** (locks up in last bit of booting)
```
echo "disable=2" >| /proc/mtrr
echo "disable=1" >| /proc/mtrr
echo "disable=3" >| /proc/mtrr
echo "disable=4" >| /proc/mtrr
echo "disable=5" >| /proc/mtrr
echo "disable=6" >| /proc/mtrr
echo "disable=7" >| /proc/mtrr
echo "base=0x80000000 size=0x40000000 type=write-back" >| /proc/mtrr
echo "base=0xC0000000 size=0x10000000 type=write-back" >| /proc/mtrr
echo "base=0x100000000 size=0x10000000 type=write-back" >| /proc/mtrr
echo "base=0x110000000 size=0x10000000 type=write-back" >| /proc/mtrr
```

I'd really appreciate if someone can help me remedy this... I'd love to recover the RAM the graphics card has taken... I was 256mb dedicated, not 256Mb dedicated + 256Mb shared :(

---

### Post by cariboo on 2008-08-19
I really doubt if you are going to get any help here, you might be better of going here:

[http://forums.nvidia.com/index.php?showforum=33](http://forums.nvidia.com/index.php?showforum=33)

Jim

---

### Post by cfehunter on 2008-08-19
you should be able to disable the graphics card in the BIOS, this should stop it taking up your RAM.

Also your RAM wont appear as 4.0GB, RAM manufacturers base the size of their RAM on the premise that 1GB is 1000MB.

---

### Post by jespdj on 2008-08-20
> **cfehunter said:**
> Also your RAM wont appear as 4.0GB, RAM manufacturers base the size of their RAM on the premise that 1GB is 1000MB.
No, that's not true.

With harddisks and other storage devices, manufacturers sell them with specs that say 1 GB = 1,000 MB = 1,000,000 KB = 1,000,000,000 bytes, but with RAM, 1 GB = 1024 MB etc.

My computer has 4 GB, and free -b shows that I have 4,154,400,768 bytes of RAM, which is more than 4,000,000,000 which I would have if your claim were true.

---

### Post by Uzelth on 2008-08-20
Yeah,

My BIOS reports 4096Mb RAM, so I've definitely got 4.00Gb, it just seems 32-bit components are stealing some of the RAM.

I find it unbelievable that a 256mb dedicated NVIDIA card needs to take an additional 256Mb... It's ridiculous... As for disabling it in the BIOS: I can't, there's no option for it - just able to change boot order of devices, etc... Nothing controlable RAM or CPU-wise.

---

### Post by Kilz on 2008-08-20
> **Uzelth said:**
> Yeah,

My BIOS reports 4096Mb RAM, so I've definitely got 4.00Gb, it just seems 32-bit components are stealing some of the RAM.

I find it unbelievable that a 256mb dedicated NVIDIA card needs to take an additional 256Mb... It's ridiculous... As for disabling it in the BIOS: I can't, there's no option for it - just able to change boot order of devices, etc... Nothing controlable RAM or CPU-wise.

Are you sure its dedicated? All references I find about the  GeForce 8400M GS say it uses [turbocache]("http://www.nvidia.com/page/turbocache.html"), that means it at least uses some system ram.

From the link

How Does it Work?
The revolutionary TurboCache technology utilizes the additional bandwidth of the PCI Express graphics bus to reach higher levels of graphics performance than traditional video memory solutions, delivering the performance and features you expect from NVIDIA graphics hardware. By allowing the graphics processing unit (GPU) to share the capacity and bandwidth of dedicated video memory **and dynamically available system memory**, TurboCache turbocharges performance and provides larger total graphics memory.

Added one more quote

"Patented hardware and software technologies that render directly to system memory"

---

### Post by Uzelth on 2008-08-20
TurboCache is additional to the dedicated graphics memory, as the description states... There is 256Mb dedicated. I've only encountered the additional 256Mb shared memory with Linux - it runs with 256Mb dedicated on Windows just fine...

---

### Post by Kilz on 2008-08-20
> **Uzelth said:**
> TurboCache is additional to the dedicated graphics memory, as the description states... There is 256Mb dedicated. I've only encountered the additional 256Mb shared memory with Linux - it runs with 256Mb dedicated on Windows just fine...

Windows? You actually believe what its telling you? Its probably using it and setup to lie about its use.

---

### Post by phenest on 2008-08-20
> **Kilz said:**
> Windows? You actually believe what its telling you? Its probably using it and setup to lie about its use.

I wouldn't say Windows is setup to lie, but it doesn't always tell the whole truth.

---

