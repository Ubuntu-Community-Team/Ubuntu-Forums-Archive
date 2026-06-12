---
title: "Slow USB and SATA Transfer Speeds in Jaunty 9.04"
date: 2009-05-05
forum: x86 64-bit Users
---

### Post by l33ch on 2009-05-05
Since installing Ubuntu 9.04 I noticed USB and Hard Drive transfers are not very fast. I'm transferring 15gb to an external HDD right now and it's going about 4MB a sec. At first it starts at  25MB/sec then it just slows down to a crawl. 

I've been following this thread and this is exactly whats going on:

[http://ubuntuforums.org/showthread.php?t=1112701](http://ubuntuforums.org/showthread.php?t=1112701)

I have tried mounting the external usb HDD with -o sync or -o async and even -o nosync and the only thing they do is increase the initial "burst" speed but the transfer rate still slows to a crawl after a couple minutes. By default, I get constant 4mb/sec transfers if I use the automount function under nautilus (i.e. just clicking on the found external drive).

USB 2.0 is enabled and no legacy support is enabled.
I have an AMD64 5600+ and a biostar ta790gxba2 motherboard

Included is my lspci, lsusb, and lsmod:

lsmod
```
Module                  Size  Used by
usb_storage            94912  1 
binfmt_misc            18572  1 
ppdev                  16904  0 
bridge                 63904  0 
stp                    11140  1 bridge
bnep                   22912  2 
lp                     19588  0 
parport                49584  2 ppdev,lp
snd_emu10k1_synth      15488  0 
snd_emux_synth         46208  1 snd_emu10k1_synth
snd_seq_virmidi        14464  1 snd_emux_synth
snd_seq_midi_emul      16000  1 snd_emux_synth
snd_emu10k1           162720  3 snd_emu10k1_synth
snd_hda_intel         557364  3 
snd_ac97_codec        133848  1 snd_emu10k1
snd_seq_dummy          11524  0 
ac97_bus               10368  1 snd_ac97_codec
snd_seq_oss            41984  0 
snd_pcm_oss            52352  0 
snd_mixer_oss          24960  1 snd_pcm_oss
snd_seq_midi           15744  0 
snd_rawmidi            33920  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event     16512  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_pcm                99336  4 snd_emu10k1,snd_hda_intel,snd_ac97_codec,snd_pcm_oss
snd_seq                66272  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_util_mem           13184  2 snd_emux_synth,snd_emu10k1
snd_timer              34064  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device         16276  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
emu10k1_gp             11520  0 
snd_hwdep              16776  2 snd_emux_synth,snd_emu10k1
i2c_piix4              20112  0 
psmouse                64028  0 
gameport               21520  2 emu10k1_gp
snd                    78792  24 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_hda_intel,snd_ac97_codec,snd_seq_oss,snd_pcm_oss,snd_mixer_oss,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device,snd_hwdep
soundcore              16800  1 snd
snd_page_alloc         18704  3 snd_emu10k1,snd_hda_intel,snd_pcm
k8temp                 13440  0 
pcspkr                 11136  0 
serio_raw              14468  0 
nvidia               8123768  36 
ohci1394               42036  0 
ieee1394              108288  1 ohci1394
r8169                  46596  0 
mii                    14464  1 r8169
usbhid                 47040  0 
fbcon                  49792  0 
tileblit               11264  1 fbcon
font                   17024  1 fbcon
bitblit                14464  1 fbcon
softcursor             10368  1 bitblit
```

lspci
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9800 GT (rev a2)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:05.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
03:05.1 Input device controller: Creative Labs SB Audigy Game Port (rev 03)
03:05.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port

```

lsusb
```
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 05e3:0702 Genesys Logic, Inc. USB 2.0 IDE Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```
 

When looking for solutions to this problem I noticed the suggestion of modprobe -r ehci_hcd

But when I try that it says Module ehci_hcd not found. Maybe this is the problem? If anyone can help me with this I would greatly appreciate it. Let me know if you need more information. Thanks!

---

### Post by Arup on 2009-05-05
Hi its most likely and probably a BIOS and AMD issue, I say this because the same phenomenon happens on my AMD Phenom PC but doesn't happen either on the Intel dual quads or older P-IV PCs.

---

### Post by GuiGuy on 2009-05-13
> **Arup said:**
> Hi its most likely and probably a BIOS and AMD issue, I say this because the same phenomenon happens on my AMD Phenom PC but doesn't happen either on the Intel dual quads or older P-IV PCs.

Disagree. While I am no expert on these matters, I can make a couple of observations that suggest the problem is more likely ubuntu (AMD64?);

I am severely affected by slow SATA performance under ubuntu since hardy. It continues in jaunty. Hardware is ASUS (M3A and ASUS_M2N-VM_DH), both AMD AM2 x2 processors, using a mix of WD, SEAGATE and MAXTOR SATA HDDs. 

DMA is definitely on. I am not using RAID, because it is such a pain to set up under Linux. Large file copy between SATA <> SATA disks is extremely slow (< 10MiBs and often between 2 and 5) and will render the PC useless or very unresponsive until the copy completes. Large file or multiple file deletes has a similar effect. 

Boot the same machine in WinXP or OpenSuse and there is no problem. 

I suggest the problem is with Ubuntu. 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/371212](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/371212)
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1467465.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1467465.html)

The SATA issue has been unresolved for too long IMO. I intend moving my PCs back to OpenSUSE this weekend, which is of course the nice thing about linux. One has choice.

---

### Post by isecore on 2009-05-18
I have this same issue. Disk-speeds are acceptable, but when copying from HDD to USB it's incredibly slow - starts off fast but rapidly falls and ~600 megabyte might take literally an hour or more to copy onto a thumbdrive - IF it even finishes.

CPU-usage also shoots through the roof when copying. On my quad-core Phenom it's virtually impossible to do anything while copying. If anyone wants my hardware-specs, let me know. I'll be happy to provide them.

I think this is an Ubuntu-issue, and I'm not going to jump ship to another distro, simply because I'm too lazy to learn a new distros quirks :)

---

### Post by GuiGuy on 2009-05-18
> **isecore said:**
> 
I think this is an Ubuntu-issue, and I'm not going to jump ship to another distro, simply because I'm too lazy to learn a new distros quirks :)

I note this bug has been escalated. Whereas previously it had been unrated for over a year (!) is is now 


importance: 	Undecided &#8594; Medium
status: 	In Progress &#8594; Triaged 

The annoying thing about this is that most users don't realise their affected by it until they start some serious file copying. I know I simply accepted the sometimes sloth like performance of relatively smart hardware running Ubuntu as a 'quirk'. Then one day I decided to run some tests and now it 'bugs' ;) the me no end. 

I have an interchangeable SATA boot drive system so to change OS on a 'clean' disk is relatively easy. Running OpenSuse with KDE4.2, it does not seem to be affected by [the SATA bug]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/119730").

> 
starts off fast but rapidly falls and ~600 megabyte might take literally an hour or more to copy onto a thumbdrive

There are some suggestions on speeding up the performance on the bug page linked above, although none have helped me. 

Cheers

---

### Post by InlawBiker on 2009-05-21
> **GuiGuy said:**
> Disagree. While I am no expert on these matters, I can make a couple of observations that suggest the problem is more likely ubuntu (AMD64?);

I am severely affected by slow SATA performance under ubuntu since hardy. It continues in jaunty. Hardware is ASUS (M3A and ASUS_M2N-VM_DH), both AMD AM2 x2 processors, using a mix of WD, SEAGATE and MAXTOR SATA HDDs. 


I have the same problem, since 8.04 and now with 9.04, SATA performance is terrible, even copying from one partition to another on the same drive.

This is on a Thinkpad T61 laptop with an internal 320gb Seagate 7200rpm SATA disk, a few external USB 2.0 -> SATA drives, and USB thumb drives of various sizes.

I've had a feeling it's related to USB.  I have a few USB drives mounted, one is a disk and one's a thumb drive.  When they're attached, SATA to SATA copies are just as slow as a thumb drive.  When I unmount them the performance goes back up.

As an adhoc test, I copied a bunch of files from one partition to another on the same internal SATA disk, each around 700MB.  No USB in the picture.

Average was around 6MB/s. Then I unmounted the USB drives, performance on SATA to SATA copies went to ~30MB/s.  Which still seems slow to me, but at least it's improved.

If I mount the USB drives again performance stays up at 30MB/s, so I don't know what triggers this.  I'll do some more testing when time allows and post it back to the launchpad bug.

```
hdparm -tT /dev/sda 

/dev/sda:
 Timing cached reads:   5466 MB in  1.99 seconds = 2743.25 MB/sec
 Timing buffered disk reads:  230 MB in  3.01 seconds =  76.30 MB/sec
```

---

### Post by amontero on 2009-05-27
I'm having the same problem.  Transfers from my SATA drive to an external USB are about 5 MB/s.  Transfers between two different SATA drives in my system are around 19 MB/s.  These slow speeds are killing me!  Any suggestions would be greatly appreciated!

I'm running a fresh install of Jaunty on an AMD64 architecture.

Here's my lspci:
```
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:10.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:11.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
01:05.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
01:05.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
01:05.4 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] (rev 05)
01:06.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
01:06.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
01:06.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
01:06.4 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] (rev 05)
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 GS (rev a2)
amontero@janus:~$ sudo lsmod | grep ehci
amontero@janus:~$ sudo lspci
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:10.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:11.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
01:05.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
01:05.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
01:05.4 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] (rev 05)
01:06.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
01:06.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
01:06.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
01:06.4 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] (rev 05)
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 GS (rev a2)
```

Here is lsmod:
```
Module                  Size  Used by
isofs                  43688  0 
udf                    92584  0 
crc_itu_t              10496  1 udf
nls_iso8859_1          13440  0 
nls_cp437              15104  0 
vfat                   21120  0 
fat                    65592  1 vfat
binfmt_misc            18572  1 
ppdev                  16904  0 
bridge                 63904  0 
stp                    11140  1 bridge
bnep                   22912  2 
video                  29204  0 
output                 11648  1 video
input_polldev          12688  0 
lp                     19588  0 
parport                49584  2 ppdev,lp
lgdt330x               17924  2 
cx88_dvb               32772  0 
cx88_vp3054_i2c        11264  1 cx88_dvb
tuner_simple           24084  4 
tuner_types            26240  1 tuner_simple
tda9887                19844  4 
tda8290                23428  0 
tuner                  36036  0 
snd_hda_intel         557364  3 
snd_seq_dummy          11524  0 
snd_seq_oss            41984  0 
cx88_alsa              21384  2 
snd_pcm_oss            52352  0 
snd_mixer_oss          24960  1 snd_pcm_oss
snd_seq_midi           15744  0 
cx8802                 27012  1 cx88_dvb
snd_pcm                99336  3 snd_hda_intel,cx88_alsa,snd_pcm_oss
cx8800                 45036  0 
cx88xx                 88104  4 cx88_dvb,cx88_alsa,cx8802,cx8800
snd_rawmidi            33920  1 snd_seq_midi
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
ir_common              56068  1 cx88xx
i2c_algo_bit           15364  2 cx88_vp3054_i2c,cx88xx
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
videobuf_dvb           16516  3 cx88_dvb,cx8802,cx88xx
dvb_core              106924  3 lgdt330x,cx88_dvb,videobuf_dvb
tveeprom               23428  1 cx88xx
compat_ioctl32         18304  1 cx8800
videodev               45184  4 tuner,cx8800,cx88xx,compat_ioctl32
snd_timer              34064  2 snd_pcm,snd_seq
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
k8temp                 13440  0 
pcspkr                 11136  0 
psmouse                64028  0 
serio_raw              14468  0 
nvidia               8123768  36 
v4l1_compat            23940  1 videodev
v4l2_common            23296  2 tuner,cx8800
btcx_risc              13960  4 cx88_alsa,cx8802,cx8800,cx88xx
videobuf_dma_sg        22660  5 cx88_dvb,cx88_alsa,cx8802,cx8800,cx88xx
videobuf_core          29828  5 cx8802,cx8800,cx88xx,videobuf_dvb,videobuf_dma_sg
snd                    78792  20 snd_hda_intel,snd_seq_oss,cx88_alsa,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm
usbhid                 47040  0 
usb_storage            94912  0 
forcedeth              68368  0 
floppy                 75816  0 
fbcon                  49792  0 
tileblit               11264  1 fbcon
font                   17024  1 fbcon
bitblit                14464  1 fbcon
softcursor             10368  1 bitblit
```

---

### Post by cariboo on 2009-05-28
I don't know what I'm doing wrong, I have an MSI K9NGM2 with an AMD X2 3400+ cpu, it's about 3 years old. I consistently get 35-40MB/sec transfer rates transfering between an IDE and a SATA drive. Running hdparm always shows that the SATA drive is slower than the IDE drive, this could very well be a motherboard problem. Both drives are fprmatted as ext4.

---

### Post by GuiGuy on 2009-05-28
> **cariboo907 said:**
> Running hdparm always shows that the SATA drive is slower than the IDE drive, this could very well be a motherboard problem. Both drives are fprmatted as ext4.

That IDE has faster xfer speed under Ubuntu than SATA is easily demonstrated. That this problem has been around so long and affects so many is almost shameful. Just as well Ubuntu isn't a commercial OS.

---

### Post by benoy4007 on 2009-05-28
Check USB support for your external HDD.

---

### Post by isecore on 2009-05-28
> **benoy4007 said:**
> Check USB support for your external HDD.

You need to be a little bit more specific what you're talking about, and to who you're saying this. Check what? That the drive has USB-support? That it's plugged into say a USB 2.0 compliant port? That it is 2.0 compliant? What?

---

### Post by GuiGuy on 2009-05-28
> **isecore said:**
> You need to be a little bit more specific what you're talking about, and to who you're saying this. Check what? That the drive has USB-support? That it's plugged into say a USB 2.0 compliant port? That it is 2.0 compliant? What?

There's some discussion about this and other "it might or might not fix it" suggestions in [the bug post on launchpad]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/119730").

---

### Post by InlawBiker on 2009-05-28
The slow-ata problem has been a problem for me for quite a while now.  I did a few tests, hopefully this will help somebody troubleshoot the issue.  This could possibly be an issue with the ntfs-3g driver for me.

System is a Thinkpad T61 laptop.

/dev/sda is a 360gb 7200rpm Seagate SATA drive

/dev/sda1 is my 32bit Ubuntu install (ext3)
/dev/sda3 is an ntfs partition (ntfs-3g driver), mounted at /media/storage

gregs@t61:/media$ uname -a
Linux t61 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

Here's a copy from one file to another on the exact same partition on the ntfs drive.

gregs@t61:/media/storage$ time cp bigfile.avi bigfile2.avi

real    1m18.355s
user    0m0.176s
sys     0m4.728s

**= 8.99 MB/s** Man, that's slow.

Now I'll copy the file from the ntfs partition to the ext3 partition:

gregs@t61:/media/storage$ time cp bigfile2.avi /home/gregs

real    0m11.883s
user    0m0.036s
sys     0m3.616s

**= 59 MB/s** - faster!

Now I'll copy the same file on the same ext3 partition to itself.

gregs@t61:/media/storage$ cd
gregs@t61:~$ ls -l bigfile2.avi
-rwxr-xr-x 1 gregs gregs 735428608 2009-05-28 15:35 bigfile2.avi
gregs@t61:~$ time cp bigfile2.avi bigfile.avi

real    0m11.382s
user    0m0.040s
sys     0m3.368s

**= 61.6 MB/s**

So, I removed ntfs-3g and compiled/installed the latest version by hand and it's still dog-slow.  Not sure what to do now.

---

### Post by JonDubya on 2009-05-30
Same problem here...AMD64 as well (I've read in the past it seems to not effect x86/32bit ubuntu).

ntfs cp to same drive (~700MB):
time cp cd1.avi test.avi 

real	0m46.536s
user	0m0.016s
sys	0m1.588s

=15MB/s

ntfs cp to different ntfs drive:
time cp test.avi /home/jonathan/Video 
real	0m16.436s
user	0m0.040s
sys	0m1.948s

= 42.6MB/s

ntfs cp to ext3:
time cp test.avi ~

real	0m15.675s
user	0m0.016s
sys	0m1.912s

=44.7MB/s

ext3 to same ext3:
time cp ~/test.avi ~/test2.avi

real	0m21.312s
user	0m0.024s
sys	0m1.688s

=32.9MB/s
*shrug* Wonder why those are still slow for SATA 2 speed connections.  Vista was always faster, with constant speeds around the 60MB/s mark.

Copying to USB flash essentially stalls after ~280MB, anywhere from 500K/s to 4MB/s.  Tried the old remedies to no avail.  Extremely frustrating.  Still can't believe it's not been remedied.

---

### Post by alex2399 on 2009-06-01
Same USB problem here. On 8.04/8.10 I was able to rmmod/modprobe ehci_hcd to get my flashdrive (SanDisk U3 4GB) recognized. Was working at USB 2.0 speeds then. Same for my external USB HDD (WD 1TB).

Now I can plug them in, they are automounted as opposed to 8.04/8.10 but are extremely slow. Read from flashdrive goes at about 600kB, external HDD also only 600kB. 


syslog output for flashdrive
```

Jun  1 12:08:02 alex-desktop kernel: [  363.008025] usb 1-8: new high speed USB device using ehci_hcd and address 2
Jun  1 12:08:02 alex-desktop kernel: [  363.372308] usb 1-8: configuration #1 chosen from 1 choice
Jun  1 12:08:02 alex-desktop kernel: [  363.438141] Initializing USB Mass Storage driver...
Jun  1 12:08:02 alex-desktop kernel: [  363.438246] scsi6 : SCSI emulation for USB Mass Storage devices
Jun  1 12:08:02 alex-desktop kernel: [  363.438312] usb-storage: device found at 2
Jun  1 12:08:02 alex-desktop kernel: [  363.438315] usb-storage: waiting for device to settle before scanning
Jun  1 12:08:02 alex-desktop kernel: [  363.438316] usbcore: registered new interface driver usb-storage
Jun  1 12:08:02 alex-desktop kernel: [  363.438318] USB Mass Storage support registered.
Jun  1 12:08:07 alex-desktop kernel: [  368.448107] usb-storage: device scan complete
Jun  1 12:08:07 alex-desktop kernel: [  368.484541] scsi 6:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  3.21 PQ: 0 ANSI: 2
Jun  1 12:08:08 alex-desktop kernel: [  368.660533] sd 6:0:0:0: [sdc] 8027793 512-byte hardware sectors: (4.11 GB/3.82 GiB)
Jun  1 12:08:08 alex-desktop kernel: [  368.784534] sd 6:0:0:0: [sdc] Write Protect is off
Jun  1 12:08:08 alex-desktop kernel: [  368.784536] sd 6:0:0:0: [sdc] Mode Sense: 03 00 00 00
Jun  1 12:08:08 alex-desktop kernel: [  368.784538] sd 6:0:0:0: [sdc] Assuming drive cache: write through
Jun  1 12:08:08 alex-desktop kernel: [  369.260037] sd 6:0:0:0: [sdc] 8027793 512-byte hardware sectors: (4.11 GB/3.82 GiB)
Jun  1 12:08:08 alex-desktop kernel: [  369.384028] sd 6:0:0:0: [sdc] Write Protect is off
Jun  1 12:08:08 alex-desktop kernel: [  369.384030] sd 6:0:0:0: [sdc] Mode Sense: 03 00 00 00
Jun  1 12:08:08 alex-desktop kernel: [  369.384031] sd 6:0:0:0: [sdc] Assuming drive cache: write through
Jun  1 12:08:08 alex-desktop kernel: [  369.384035]  sdc: sdc1
Jun  1 12:08:08 alex-desktop kernel: [  369.460145] sd 6:0:0:0: [sdc] Attached SCSI removable disk
Jun  1 12:08:08 alex-desktop kernel: [  369.460193] sd 6:0:0:0: Attached scsi generic sg3 type 0
Jun  1 12:08:13 alex-desktop hald: mounted /dev/sdc1 on behalf of uid 1000
```


syslog output for external HDD
```
Jun  1 13:53:45 alex-desktop kernel: [ 6706.488029] usb 1-2: new high speed USB device using ehci_hcd and address 3
Jun  1 13:53:46 alex-desktop kernel: [ 6706.808953] usb 1-2: configuration #1 chosen from 1 choice
Jun  1 13:53:46 alex-desktop kernel: [ 6706.820632] scsi7 : SCSI emulation for USB Mass Storage devices
Jun  1 13:53:46 alex-desktop kernel: [ 6706.820698] usb-storage: device found at 3
Jun  1 13:53:46 alex-desktop kernel: [ 6706.820700] usb-storage: waiting for device to settle before scanning
Jun  1 13:53:51 alex-desktop kernel: [ 6711.848585] usb-storage: device scan complete
Jun  1 13:53:51 alex-desktop kernel: [ 6711.884038] scsi 7:0:0:0: Direct-Access     WD       10EAVS External  1.75 PQ: 0 ANSI: 4
Jun  1 13:53:51 alex-desktop kernel: [ 6712.060029] sd 7:0:0:0: [sdd] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
Jun  1 13:53:51 alex-desktop kernel: [ 6712.184026] sd 7:0:0:0: [sdd] Write Protect is off
Jun  1 13:53:51 alex-desktop kernel: [ 6712.184028] sd 7:0:0:0: [sdd] Mode Sense: 23 00 00 00
Jun  1 13:53:51 alex-desktop kernel: [ 6712.184030] sd 7:0:0:0: [sdd] Assuming drive cache: write through
Jun  1 13:53:51 alex-desktop kernel: [ 6712.360532] sd 7:0:0:0: [sdd] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
Jun  1 13:53:51 alex-desktop kernel: [ 6712.484040] sd 7:0:0:0: [sdd] Write Protect is off
Jun  1 13:53:51 alex-desktop kernel: [ 6712.484043] sd 7:0:0:0: [sdd] Mode Sense: 23 00 00 00
Jun  1 13:53:51 alex-desktop kernel: [ 6712.484045] sd 7:0:0:0: [sdd] Assuming drive cache: write through
Jun  1 13:53:51 alex-desktop kernel: [ 6712.484049]  sdd: sdd1
Jun  1 13:53:51 alex-desktop kernel: [ 6712.560153] sd 7:0:0:0: [sdd] Attached SCSI disk
Jun  1 13:53:51 alex-desktop kernel: [ 6712.560203] sd 7:0:0:0: Attached scsi generic sg4 type 0
Jun  1 13:54:42 alex-desktop ntfs-3g[8339]: Version 2009.2.1 external FUSE 27 
Jun  1 13:54:42 alex-desktop ntfs-3g[8339]: Mounted /dev/sdd1 (Read-Write, label "", NTFS 3.1) 
Jun  1 13:54:42 alex-desktop ntfs-3g[8339]: Cmdline options: rw,nosuid,nodev,uhelper=hal,locale=nl_NL.UTF-8 
Jun  1 13:54:42 alex-desktop ntfs-3g[8339]: Mount options: rw,nosuid,nodev,uhelper=hal,silent,allow_other,nonempty,relatime,fsname=/dev/sdd1,blkdev,blksize=4096 
Jun  1 13:54:42 alex-desktop hald: mounted /dev/sdd1 on behalf of uid 1000
```


relevant dmesg output
```

    3.776313] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.776332] ehci_hcd 0000:00:13.5: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    3.776346] ehci_hcd 0000:00:13.5: EHCI Host Controller
[    3.776381] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 1
[    3.776403] ehci_hcd 0000:00:13.5: applying AMD SB600/SB700 USB freeze workaround
[    3.776421] ehci_hcd 0000:00:13.5: debug port 1
[    3.776444] ehci_hcd 0000:00:13.5: irq 19, io mem 0xfe029000
[    3.788016] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00
[    3.788057] usb usb1: configuration #1 chosen from 1 choice
[    3.788074] hub 1-0:1.0: USB hub found
[    3.788079] hub 1-0:1.0: 10 ports detected
[    3.788161] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.788171] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.788178] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    3.788205] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    3.788230] ohci_hcd 0000:00:13.0: irq 16, io mem 0xfe02e000
[    3.848023] usb usb2: configuration #1 chosen from 1 choice
[    3.848040] hub 2-0:1.0: USB hub found
[    3.848048] hub 2-0:1.0: 2 ports detected
[    3.848107] ohci_hcd 0000:00:13.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.848115] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    3.848138] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    3.848161] ohci_hcd 0000:00:13.1: irq 17, io mem 0xfe02d000
[    3.904026] usb usb3: configuration #1 chosen from 1 choice
[    3.904040] hub 3-0:1.0: USB hub found
[    3.904047] hub 3-0:1.0: 2 ports detected
[    3.904106] ohci_hcd 0000:00:13.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.904113] ohci_hcd 0000:00:13.2: OHCI Host Controller
[    3.904138] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 4
[    3.904161] ohci_hcd 0000:00:13.2: irq 18, io mem 0xfe02c000
[    3.960026] usb usb4: configuration #1 chosen from 1 choice
[    3.960040] hub 4-0:1.0: USB hub found
[    3.960049] hub 4-0:1.0: 2 ports detected
[    3.960106] ohci_hcd 0000:00:13.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.960115] ohci_hcd 0000:00:13.3: OHCI Host Controller
[    3.960145] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 5
[    3.960156] ohci_hcd 0000:00:13.3: irq 17, io mem 0xfe02b000
[    4.016027] usb usb5: configuration #1 chosen from 1 choice
[    4.016045] hub 5-0:1.0: USB hub found
[    4.016052] hub 5-0:1.0: 2 ports detected
[    4.016107] ohci_hcd 0000:00:13.4: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.016114] ohci_hcd 0000:00:13.4: OHCI Host Controller
[    4.016139] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 6
[    4.016150] ohci_hcd 0000:00:13.4: irq 18, io mem 0xfe02a000
[    4.072024] usb usb6: configuration #1 chosen from 1 choice
[    4.072042] hub 6-0:1.0: USB hub found
[    4.072049] hub 6-0:1.0: 2 ports detected
[    4.072104] uhci_hcd: USB Universal Host Controller Interface driver
```


lsusb output
```
alex@alex-desktop:~$ lsusb
Bus 001 Device 003: ID 1058:1003 Western Digital Technologies, Inc. 
Bus 001 Device 002: ID 0781:5406 SanDisk Corp. Cruzer Micro 1/4GB Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

lsmod output
```
alex@alex-desktop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          13440  1 
nls_cp437              15104  1 
vfat                   21120  1 
fat                    65592  1 vfat
usb_storage           115392  2 
binfmt_misc            18572  1 
fglrx                2419744  31 
ppdev                  16904  0 
bridge                 63904  0 
stp                    11140  1 bridge
bnep                   22912  2 
input_polldev          12688  0 
video                  29204  0 
output                 11648  1 video
lp                     19588  0 
parport                49584  2 ppdev,lp
tuner_simple           24084  1 
tuner_types            26240  1 tuner_simple
tuner                  36036  0 
tvaudio                34620  0 
snd_seq_dummy          11524  0 
bttv                  214100  0 
snd_hda_intel         557620  3 
snd_seq_oss            41984  0 
snd_bt87x              23844  1 
snd_seq_midi           15744  0 
ir_common              56068  1 bttv
snd_rawmidi            33920  1 snd_seq_midi
snd_pcm_oss            52352  0 
compat_ioctl32         18304  1 bttv
videodev               45184  4 tuner,tvaudio,bttv,compat_ioctl32
v4l1_compat            23940  1 videodev
i2c_algo_bit           15364  1 bttv
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_mixer_oss          24960  1 snd_pcm_oss
psmouse                64028  0 
v4l2_common            23296  3 tuner,tvaudio,bttv
videobuf_dma_sg        22660  1 bttv
videobuf_core          29828  2 bttv,videobuf_dma_sg
btcx_risc              13960  1 bttv
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_pcm                99592  3 snd_hda_intel,snd_bt87x,snd_pcm_oss
pcspkr                 11136  0 
tveeprom               23428  1 bttv
serio_raw              14468  0 
i2c_piix4              20112  0 
k8temp                 13440  0 
snd_timer              34064  2 snd_seq,snd_pcm
snd                    78792  18 snd_hda_intel,snd_seq_oss,snd_bt87x,snd_rawmidi,snd_pcm_oss,snd_seq,snd_mixer_oss,snd_seq_device,snd_pcm,snd_timer
soundcore              16800  1 snd
snd_page_alloc         18704  3 snd_hda_intel,snd_bt87x,snd_pcm
ohci1394               42036  0 
ieee1394              108288  1 ohci1394
r8169                  46596  0 
mii                    14464  1 r8169
fbcon                  49792  0 
tileblit               11264  1 fbcon
font                   17024  1 fbcon
bitblit                14464  1 fbcon
softcursor             10368  1 bitblit

```

So they are detected as high speed (USB 2.0) devices, connected to the right (internal) USB 2.0 hub but don't function at speeds of USB 2.0 devices, more like USB 0.1 or so.........

Also installed 2.6.28-12-generic kernel, instead of 2.6.28-11-generic that is used by Jaunty now.

Edit: Just tested with kernel 2.6.30-rc7, still the same issue...read at about 600-700kB

---

### Post by alex2399 on 2009-06-02
I fixed my USB problems by updating the BIOS. Read from USB flash @10MB/s, write @13MB/s. Read from USB HDD @23MB/s and write @30MB/s.
These are dstat figures.

You can read my bug posts with logs and dstat traces here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/334914](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/334914)

name is alex123.

---

### Post by waspinator on 2009-06-05
I'm also having problems with transfer speed. Just yesterday, ubuntu 9.04 was transfering files to USB at 25-30 Mb/sec. Today I tried to burn a DVD and it took 2 hours and still failed. I decieded to copy the dvd image over so I could burn it in  windows, but now my usb transfer is at 2.5 MB/sec! I changed nothing in the bios, and the only thing I installed was UNetbootin. (very strange name for an app btw).

Was there an update or something that messed up the speeds in the last couple days? (June 4, 2009). I don't really know what to do, but if an update doesn't come along and fix this, I'll have to reinstall ubuntu and turn off all updates. UNetbootin

---

### Post by GuiGuy on 2009-06-05
> **waspinator said:**
> I'm also having problems with transfer speed. Just yesterday, ubuntu 9.04 was transfering files to USB at 25-30 Mb/sec. Today I tried to burn a DVD and it took 2 hours and still failed. I decieded to copy the dvd image over so I could burn it in  windows, but now my usb transfer is at 2.5 MB/sec! I changed nothing in the bios, and the only thing I installed was UNetbootin. (very strange name for an app btw).

This problem HAS to be with jaunty. I have just installed 8.04 AMD64 on our home entertainment system where 9.04 failed, reporting "ata :Softreset failed (device not ready)" 

On 8.04 everything's fine and SATA performance is where it should be. 

I have now installed Mythdora 10.1, and everything's good. This SATA thing is, IMO, a ubuntu 9.04 issue. I know it's free software, I know that many are donating their talents and time to make it what it is, and I thank them, but I find puzzling to say the least that a bug like this is allowed to go on so long. I've now moved one of my PCs to a new distro. My desktop work PC is next.

Cheers

---

### Post by isecore on 2009-06-05
> **GuiGuy said:**
> This problem HAS to be with jaunty. I have just installed 8.04 AMD64 on our home entertainment system where 9.04 failed, reporting "ata :Softreset failed (device not ready)" 

On 8.04 everything's fine and SATA performance is where it should be. 

I have now installed Mythdora 10.1, and everything's good. This SATA thing is, IMO, a ubuntu 9.04 issue. I know it's free software, I know that many are donating their talents and time to make it what it is, and I thank them, but I find puzzling to say the least that a bug like this is allowed to go on so long. I've now moved one of my PCs to a new distro. My desktop work PC is next.

Cheers

I've had crappy performance since 8.04. USB is slower than molasses, CPU usage shoots through the roof on intense disk I/O etc. It all started when I bought my current computer about a year ago. I was kind of hoping this would've been sorted out until now, but apparently not...

---

### Post by orefice.matteo on 2009-06-07
Hi

I have the similar problem, I go to explain:
[LIST]
[*]first, when I copy large amount of data other user input driven application became unresponsive, also compiz become unresponsive, and mouse pointer is slow. I installed jaunty from 2 day, but I cannot remember the same behaviour on debian testing, compiz never was interrupted by a file transfer or IO intensive operation
[*]slow transfer between the same disk. My disk is a HITACHI DESKSTAR, ubuntu provide support through libata pata_amd. Now I am tryng to recompile the kernel to use old ide suppor
[*]also i think there are problem with cpu governor, the aggressive profile for powernowd is slow, i lowered the lower e upper threshold to make it better
[*]i tried also to hack some kernel param, only noapic and apci=pci seems to be a bit better
[*]also file transfer from usb external drive and disk are slow and they make unresponsive experience 
[/LIST]

Matteo

---

### Post by orefice.matteo on 2009-06-07
I have an AMD64 also, I forgive to tell

---

### Post by isecore on 2009-06-07
A screenshot of what things normally look like. About 30 seconds after this was taken the speed dropped to under 400 kb/sek. At the time of the screenshot it had been copying for about 20 minutes. 20 frickin' minutes for 400 megabytes? Pathetic.

---

### Post by orefice.matteo on 2009-06-08
I changed the X nice priority in /etc/X11/Xwrapper.config to -5 and i seems to be X more responsive during the copy process, the pointer do not stop anymore.

I also recompiled 2.6.28-13-generic without libata support for my amd, pata_amd.

The transfer speed seems to be better! around 12 MByte/s for HD<->USB disk , i noticed that file copy in nautilus was lower than mc copy o dd copy, It was a problem with X priority maybe. Now I try with normal kernel and back libata

---

### Post by cmost on 2009-06-13
*Bump*

I'm having this problem with Jaunty running the 2.6.30 kernel.  Any workarounds?  This is a deal breaker for me as it affects my ability to stream my mp3's from my two external 1 Tera byte hard disks.  Ubuntu devs should be ashamed of themselves for releasing code with this serious a flaw!  :(

---

### Post by rob martin on 2009-06-13
I too am experiencing dismal transfer speeds.  Any help would be appreciated.:(

---

### Post by GuiGuy on 2009-06-13
> **cmost said:**
> *Bump*

I'm having this problem with Jaunty running the 2.6.30 kernel.  Any workarounds?  This is a deal breaker for me as it affects my ability to stream my mp3's from my two external 1 Tera byte hard disks.  Ubuntu devs should be ashamed of themselves for releasing code with this serious a flaw!  :(

I think you, and everyone else affected by this, needs to flag [https://bugs.launchpad.net/bugs/119730](https://bugs.launchpad.net/bugs/119730) - even with all the responses that are already there, not much seems to be happening. And to top it off [I'm now getting this]("https://bugs.launchpad.net/bugs/285392"). It brought two PCs down in my house before I realised what was going on. 

As I mentioned elsewhere, I'm finding it hard to remain positive about Ubuntu, especially with all the "quirks" jaunty has introduced. 

Cheers

---

### Post by cmost on 2009-06-13
I moved back to Kernel 2.6.29.4 (found here:  [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)) and that seemed to remedy the situation for now.  As to GuiGuy's suggestion about making bug reports, I was shocked at the number of people reporting this bug and the blatant inaction by the developer community.  Apparently this bug has existed for amd64 users since Ibex!!!  Shocking that it hasn't been fixed by now.  Ubuntu is becoming the new Microsoft.  The attitude seems to be all about bringing flashy new desktop bling with little regard for quality control.  Anyone thinking "Vista" here?  Get with it Ubuntu!  People want a desktop OS that works.  I've long thought that Ubuntu should switch to an annual release schedule with a mid-year freshening of popular packages.  Oh well.  I guess we wait for Koala...

---

### Post by intel on 2009-06-13
Yes, these are known issues with SB600/SB700 chipsets, & Linux kernel USB subsystem.

USB support is problematic, and there is NO solution possible,

Also Note: Windows does NOT have this problem, on the same h/w.
Clearly, there are some workarounds possible, but no-one's(kernel devs) interested.
(AMD profit is down, so they are unable to help you,
kernel devs are given complimentary copies of better h/w (free)
 so they don't care about these cheap h/w chipsets etc)

Nothing can be done, sell this h/w and buy another setup, hopefully you'll have better luck.

i.e unless,....unless you want to start kernel, usb host driver programming?

---

### Post by merlinus on 2009-06-13
I found this:

[http://www.nabble.com/USB-troubles-with-SB600-SB700-chipsets-td23587677.html](http://www.nabble.com/USB-troubles-with-SB600-SB700-chipsets-td23587677.html)

---

### Post by isecore on 2009-06-13
> **GuiGuy said:**
> As I mentioned elsewhere, I'm finding it hard to remain positive about Ubuntu, especially with all the "quirks" jaunty has introduced.

In my experience, these quirks, bugs and annoyances have been here since at least Hardy. That's when I started experiencing them, at the same time I upgraded to my current computer.

---

### Post by cmost on 2009-06-13
Thanks Merlinus!  I hunted high and low for a workaround and didn't spot this tidbit.  Will check it out and report back!  Cheers!

---

### Post by GuiGuy on 2009-06-14
> **merlinus said:**
> I found this:

[http://www.nabble.com/USB-troubles-with-SB600-SB700-chipsets-td23587677.html](http://www.nabble.com/USB-troubles-with-SB600-SB700-chipsets-td23587677.html)

Thanks. I'm sure it'll be useful to the odd geek or fanboy, but those of us not that way inclined will, I am sure, be left only all the more bewildered.

---

### Post by GuiGuy on 2009-06-14
> **intel said:**
> 
Clearly, there are some workarounds possible, but no-one's(kernel devs) interested.
(AMD profit is down, so they are unable to help you,
kernel devs are given complimentary copies of better h/w (free)
 so they don't care about these cheap h/w chipsets etc)


Which begs the question; Why then bother with a specific [Ubuntu AMD64 install iso]("http://www.ubuntu.com/getubuntu/downloadmirrors")?

---

### Post by dcstar on 2009-06-14
> **GuiGuy said:**
> Which begs the question; Why then bother with a specific [Ubuntu AMD64 install iso]("http://www.ubuntu.com/getubuntu/downloadmirrors")?

Huh?, it is a 64-bit ISO **not a specific AMD** ISO that will work on all CPUS that use the particular 64-bit instruction set, it is just labelled that way for convenience.

---

### Post by dcstar on 2009-06-14
> **cmost said:**
> I moved back to Kernel 2.6.29.4 (found here:  [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)) and that seemed to remedy the situation for now.  As to GuiGuy's suggestion about making bug reports, I was shocked at the number of people reporting this bug and the blatant inaction by the developer community.  Apparently this bug has existed for amd64 users since Ibex!!!  Shocking that it hasn't been fixed by now.  Ubuntu is becoming the new Microsoft.  The attitude seems to be all about bringing flashy new desktop bling with little regard for quality control.  Anyone thinking "Vista" here?  Get with it Ubuntu!  People want a desktop OS that works.  I've long thought that Ubuntu should switch to an annual release schedule with a mid-year freshening of popular packages.  Oh well.  I guess we wait for Koala...

Ubuntu are not kernel **developers**, Ubuntu (and all the other distros) are kernel **users**.

If there are generic problems in the Linux kernels then they have to be addressed by the kernel developers - there is little to be gained by complaining about Ubuntu on this issue.

If you want/need a kernel that does not have this problem, then there are still older LTS versions of Ubuntu available that may work the way things used to with this apparent chipset - and they will be supported for wuite a while.

---

### Post by GuiGuy on 2009-06-14
> **dcstar said:**
> Huh?, it is a 64-bit ISO **not a specific AMD** ISO that will work on all CPUS that use the particular 64-bit instruction set, it is just labelled that way for convenience.

Oh?

ubuntu-8.04.2-alternate-amd64.iso

---

### Post by isecore on 2009-06-14
> **GuiGuy said:**
> Oh?

ubuntu-8.04.2-alternate-amd64.iso

AMD were the first to release processors based on the 64-bit extensions to x86 and called it AMD64, thus it was labeled AMD64 in the release tree. Intel followed suit a while later, licensing the technology from AMD but renaming it EM64T instead, since they didn't want to showcase that AMD beat them to the punch. It works the same way though.

The label is as previously stated simply a convenience and a remnant from when the technology was introduced.

---

### Post by cmost on 2009-06-14
> **dcstar said:**
> Ubuntu are not kernel **developers**, Ubuntu (and all the other distros) are kernel **users**.

If there are generic problems in the Linux kernels then they have to be addressed by the kernel developers - there is little to be gained by complaining about Ubuntu on this issue.

If you want/need a kernel that does not have this problem, then there are still older LTS versions of Ubuntu available that may work the way things used to with this apparent chipset - and they will be supported for wuite a while.

Yet when a kernel exhibits a serious flaw such as this one, Ubuntu will still happily pass it to their users.  Instead, Ubuntu developers should inform the Kernel developers that they will not include the kernel until the issue is addressed.  Since Ubuntu is the number one, most popular Linux distribution it has some clout!  It's not realistic to recommend users to stick with an old, outdated release while hoping, praying that the developers one day decide to fix a serious issue.  Your argument is like saying "if you don't like it, lump it."  That simply won't fly in a community trying to coax users away from Windows and Mac.  Just my two cents.

---

### Post by alex2399 on 2009-06-14
Then file usefull bug reports! Just complaining does not help in anyway. You cannot expect developers to go through all the lines of code and have them hypothesize which lines in the code could be a problem in your specific case. They just do not have a magic crystal ball they can rub to get the answer to your problem, you have to give them usefull info.

Anyway as you guys should have read I fixed the exact same problem. It was a BIOS issue. Anyone of you already searched for the latest BIOS of your motherboard, installed it, tested it and run dstat traces before and after? Thats what is asked in the launchpad bugreport [https://bugs.launchpad.net/bugs/119730](https://bugs.launchpad.net/bugs/119730)

---

### Post by PatrickVogeli on 2009-06-14
I would rather say that the ubuntu devs are both developers and users. Ubuntu has its own kernel team, and I'm sure that if they find a bug upstream (mainline kernel) and they know how to fix it, they send the patch upwards. 

Also, I'd guess that if ubuntu said "Hey there, we won't be using kernel bla bla bla because of bla bla bla" the answer would simply be something like "Ok, now piss off and let us work, we don't care".

---

### Post by cmost on 2009-06-14
> **alex2399 said:**
> Then file usefull bug reports! Just complaining does not help in anyway. You cannot expect developers to go through all the lines of code and have them hypothesize which lines in the code could be a problem in your specific case. They just do not have a magic crystal ball they can rub to get the answer to your problem, you have to give them usefull info.

Anyway as you guys should have read I fixed the exact same problem. It was a BIOS issue. Anyone of you already searched for the latest BIOS of your motherboard, installed it, tested it and run dstat traces before and after? Thats what is asked in the launchpad bug report [https://bugs.launchpad.net/bugs/119730](https://bugs.launchpad.net/bugs/119730)

Dozens have already filed a bug report on this issue and it hasn't made a difference.  Furthermore, updating the BIOS isn't an option for everyone.  For example, I'm running the latest BIOS update available for my system and further updates will not be forthcoming.  Finally, the squeaky gate gets the oil.  If people blithely accept what they're given and don't complain when they're dissatisfied then mediocrity becomes the norm.

---

### Post by adam.ec on 2009-06-19
I'm just trying to move away from Jaunty and having to shift everything on USB memory sticks. Exactly the same thing is happening to me... AMD64 Distro but on Intel Core2Duo system with Intel motherboard.

Even copying on the same hard disk but between partitions is slow. I'm down to 150kbytes a second on USB transfers and haven't managed to burn a single CD or DVD successfully yet. Not sure if it is kernel problems because Arch and Fedora 11 don't suffer from this. I have three machines with Jaunty on and all have the same issue.

---

### Post by shane2peru on 2009-06-19
This seems to be a 64bit issue and seemingly an Ubuntu issue.  I hate to try another distro, so I will just have to tough it out.  I just copied a bunch of data via the command line and it was very fast.  It seems to be a GUI issue, and perhaps could be narrowed down to Gnome?  Are any KDE users experiencing this issue?  I don't think this is a kernel issue.  

Shane

---

### Post by GuiGuy on 2009-06-20
> **cmost said:**
>  If people blithely accept what they're given and don't complain when they're dissatisfied then mediocrity becomes the norm.

I think many are quite unaware of the problem until they actually start doing some serious file transfers. I'd notice the slow down in system performance but dismissed it as an interim glitch. Only when I had to do some large scale file transfers did I wake up that this was actually a bug.

---

### Post by GuiGuy on 2009-06-20
> **shane2peru said:**
>  Are any KDE users experiencing this issue?  


I can confirm that the problem is on the AMD64 distro irrespective of desktop environment. I have tested Gnome, KDE4.x and xfce (my mythbuntu backend). 

It does not occur on the 32 bit distros, AFAIK. But with it there are other problems; for example very low DVD speeds, at least on AMD  hardware.

---

### Post by Arup on 2009-06-20
I have no issues on the dual quad core Intel but with Phenom I have the same issue. A new BIOS update made it little better.

---

### Post by schmolch on 2009-06-20
Same issue on 2 All-Intel 32bit Thinkpads.

---

### Post by GuiGuy on 2009-06-20
I just posted this on the bug list. In a way I regret having seemingly over-reacted this way, but I am really coming to the 'enough is enough' stage

> 
So in the last couple of days kernel 2.6.28-13 arrived. I'd hope it
would make a difference.

I suppose it did. Now my mythbuntu box comes to standstill when copying
files. Transferring a 1G file between two SATA drives took a blistering
8, read it and weep, 8 minutes!!!

Sorry, I'm loosing it here. Linux is no longer an option.


---

### Post by Arup on 2009-06-20
> **GuiGuy said:**
> I just posted this on the bug list. In a way I regret having seemingly over-reacted this way, but I am really coming to the 'enough is enough' stage

As a last resort why not give Kernel 2.6.30 from Ubuntu ppa a try. Also give Fedora 11 a spin, no need to ditch Linux.

---

### Post by schmolch on 2009-06-21
> **GuiGuy said:**
> Sorry, I'm loosing it here. Linux is no longer an option. 

Im with you there, i use Linux exclusively since 10 years and it has never been that buggy and troublesome.

And dont waste your time with 2.6.30, i use karmic and 2.6.30 on both my machines and its no help.

---

### Post by tenmoi on 2009-06-21
THis status quo has been since I can't remember. But pls don't blame it on ubuntu or the kernel. NAUTILUS may be the culprit. Just install mc- the good old midnight commander and see if the transfer speed improves. It does well on my machine.:P

---

### Post by schmolch on 2009-06-21
I can use cp or rsync and its not any faster.
950kb/s transfering a 700 MB file to a usb stick, usb hdd or sdhc card.

---

### Post by tenmoi on 2009-06-22
> **schmolch said:**
> I can use cp or rsync and its not any faster.
950kb/s transfering a 700 MB file to a usb stick, usb hdd or sdhc card.

Here are the results on my machine:
1. Hard disk to hard disk: hd2hd.pnp
2. Hard disk to usb: hd2usb (which started at 41 M/s)

So I can safely say that NAUTILUS IS THE CULPRIT.

---

### Post by alex2399 on 2009-06-22
These figures don't show anything thats of use and only add to the confusion. It doesn't show if it is being cached or *really* written to the disk. My machine caches 200MB of a file and no GUI will show you this. So in nautilus or MC, whatever you use it will let you see it is going really fast in the right circumstances, but in reality it is going dead slow and still copying for a long time, even if your GUI closes or shows it is finished, it is still copying!

So again you need to use dstat to get reliable info. Go to terminal and enter

```
dstat -f
```

and copy away.

See, it ain't that hard

---

### Post by schettj on 2009-06-22
I am seeing something similar 

using a usb 2.0 wifi dongle (dlink dwa130) in N mode with ndiswrapper, test speed via iperf. 

Speed from box to a server on lan: 40Mbit - this is OK for my N gear and matches WinXP performance in same location

Speed from lan to box: 12Mbit - this is suspect - 12mbit would be usb 1.0 speed - XP mode same hardware/location gets 40mbit both directions

Verified dongle is detected as usb 2.0, and is shown on usb 2.0 root hub

Updated bios (wow that was fun) - no change

Hardware is x86 HP xw8000 xenon with intel uch4 controller, bios set USB NOT in legacy mode.

Seems like the inbound half is running in 1.x mode, outbound half is 2.0 mode. I'm stumped.

---

### Post by GuiGuy on 2009-06-22
> **dcstar said:**
> Ubuntu are not kernel **developers**, Ubuntu (and all the other distros) are kernel **users**.

If there are generic problems in the Linux kernels then they have to be addressed by the kernel developers - there is little to be gained by complaining about Ubuntu on this issue.

The [Launchpad bug list messages]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/119730?comments=all") advise me that the slow SATA issue is Ubuntu specific. 

Who to believe? ANyway, I will put it to the test and advise.

---

### Post by tenmoi on 2009-06-23
> **alex2399 said:**
> These figures don't show anything thats of use and only add to the confusion. It doesn't show if it is being cached or *really* written to the disk. My machine caches 200MB of a file and no GUI will show you this. So in nautilus or MC, whatever you use it will let you see it is going really fast in the right circumstances, but in reality it is going dead slow and still copying for a long time, even if your GUI closes or shows it is finished, it is still copying!

So again you need to use dstat to get reliable info. Go to terminal and enter

```
dstat -f
```

and copy away.

See, it ain't that hard


I did just as you had suggested and here is the result. And although I did not film the two windows - one for mc and one for dstat - I am happy to tell you that when mc finished copying, dstat only reported 3 more lines of disk activity (It's realy hard for me to describe this situation b/c English is not my tongue, but when mc had done copying I could see dstat report -64M 3 more times and then -0M) 

So my conclusion is mc does a good job of copying, at least on my machine. There is not that background copying on my machine. 

What do you think?

---

### Post by Paladiamors on 2009-06-23
I have a similar problem here with the slow transfer problems.

My system is a:

Athlon 5000 x2 64 bit CPU, Geforece 9600 512 MB, 4 GB memory, 500 GB HD x2 running Jaunty x64-AMD

The transfer starts off fast at about 25 MB/sec and then slows down to about 5 MB/sec while copying from HD -> HD (a different one) or while copying from HD -> Removable HD.

The problem rears its head especially while copying large files (larger than 2GB). I am currently trying to copy 42 GB of data and it's going to take me 2 hours! Having to wait that long it kind of agonizing.

Any kind of fix would be great!

Thanks

---

### Post by tenmoi on 2009-06-23
> **Paladiamors said:**
> I have a similar problem here with the slow transfer problems.

My system is a:

Athlon 5000 x2 64 bit CPU, Geforece 9600 512 MB, 4 GB memory, 500 GB HD x2 running Jaunty x64-AMD

The transfer starts off fast at about 25 MB/sec and then slows down to about 5 MB/sec while copying from HD -> HD (a different one) or while copying from HD -> Removable HD.

The problem rears its head especially while copying large files (larger than 2GB). I am currently trying to copy 42 GB of data and it's going to take me 2 hours! Having to wait that long it kind of agonizing.

Any kind of fix would be great!

Thanks

Have you installed mc and tried copying with it or used the cp command line?

---

### Post by GuiGuy on 2009-06-26
> **Arup said:**
> As a last resort why not give Kernel 2.6.30 from Ubuntu ppa a try. Also give Fedora 11 a spin, no need to ditch Linux.

Thank you. I have switched to Fedora and all is well.

---

### Post by schmolch on 2009-06-27
My usb speed is back to normal (25MB/s) on both of my karmic boxes today.

---

### Post by Arup on 2009-06-27
> **GuiGuy said:**
> Thank you. I have switched to Fedora and all is well.

Great, probably kernel 2.6.29 made the difference I guess.

---

### Post by GuiGuy on 2009-06-27
> **Arup said:**
> Great, probably kernel 2.6.29 made the difference I guess.

Yea, I didn't realise it was on 2.6.29. I moved my mythbuntu backend to mythdora as well today. So, of the four linux PCs in the house, only the wife's eeepc remains on eeebuntu. 

Bit of a sad parting in a way...

---

### Post by Arup on 2009-06-27
> **GuiGuy said:**
> Yea, I didn't realise it was on 2.6.29. I moved my mythbuntu backend to mythdora as well today. So, of the four linux PCs in the house, only the wife's eeepc remains on eeebuntu. 

Bit of a sad parting in a way...

Not at all, you are still on Linux and thats all that matters, there is choice here unlike in the other OS world. I never could endear to Fedora 11 even though its truly cutting edge. Thankfully I have none of the issues listed on the forum with Ubuntu so I can stick to Ubuntu.

---

### Post by learningcurb on 2009-06-27
I'm running 9.04 (the 32-bit version) and I have an older Intel southbridge (ICH7) and I ran into this problem.  Copy speeds in Nautilus were capped at 5MB/s to the USB drive.  However it works fine from the commandline with cp-a with speeds of 20-30MB/s.  I also tried the Fedora LiveCD and got 20-30MB/s speeds from Nautilus.

So at least for me, the problem seems to be Nautilus, not Ubuntu.

---

### Post by Anthon berg on 2009-07-03
> **dcstar said:**
> Ubuntu are not kernel **developers**, Ubuntu (and all the other distros) are kernel **users**.

If there are generic problems in the Linux kernels then they have to be addressed by the kernel developers - there is little to be gained by complaining about Ubuntu on this issue.

If you want/need a kernel that does not have this problem, then there are still older LTS versions of Ubuntu available that may work the way things used to with this apparent chipset - and they will be supported for wuite a while.

[SIZE="4"]**The bug is in the Ubuntu patches to the kernel.**[/SIZE]

Ubuntu kernel: Slow.
The exact corresponding kernel from the mainline kernel in PPA: Fast.

---

### Post by GuiGuy on 2009-07-03
> **Anthon berg said:**
> [SIZE="4"]**The bug is in the Ubuntu patches to the kernel.**[/SIZE]

Ubuntu kernel: Slow.
The exact corresponding kernel from the mainline kernel in PPA: Fast.

Correct. The fix is easy; use another distro. I did and things just work!

---

### Post by Anthon berg on 2009-07-03
> **GuiGuy said:**
> Correct. The fix is easy; use another distro. I did and things just work!

The mainline kernel does wonders, too.

But indeed, something is rotten in the state of Denmark.

---

### Post by isecore on 2009-07-03
> **Anthon berg said:**
> The mainline kernel does wonders, too.

But indeed, something is rotten in the state of Denmark.

One big problem with the mainline kernel however is that it doesn't include any proprietary drivers or such thing. Thus keeping for example your graphics card running at speed becomes quite a hassle - especially for non-techies.

I wonder why Ubuntu doesn't look into this issue further.

---

### Post by GuiGuy on 2009-07-03
> **Anthon berg said:**
> The mainline kernel does wonders, too.

Not for people like me. Generally if I start mucking about with the kernel or even dare to type modprobe things have a a habit of falling into a heap for me. 

I'm the GuiGuy, and have been since the Amiga ):P

Cheers

---

### Post by Arup on 2009-07-03
> **GuiGuy said:**
> Not for people like me. Generally if I start mucking about with the kernel or even dare to type modprobe things have a a habit of falling into a heap for me. 

I'm the GuiGuy, and have been since the Amiga ):P

Cheers

They got the GUI for compiling kernel as well.

---

### Post by Bert_421 on 2009-07-04
Good stuff here, I was going to try to install Ubuntu on the WD raptors raid 0. thank you now i will not waste my time trying. It looked like a vary big task. 

Maybe this is why Windows is so successful, you have all these different Linux distro out there focus on there own stuff if they were like Windows all focus on one objective maybe linux could have more of the piece of pie. 
I guess i will try Fedora out.

---

### Post by GuiGuy on 2009-07-04
> **Bert_421 said:**
>  
I guess i will try Fedora out.

Worked for me.

---

### Post by Arup on 2009-07-04
> **Bert_421 said:**
> Good stuff here, I was going to try to install Ubuntu on the WD raptors raid 0. thank you now i will not waste my time trying. It looked like a vary big task. 

Maybe this is why Windows is so successful, you have all these different Linux distro out there focus on there own stuff if they were like Windows all focus on one objective maybe linux could have more of the piece of pie. 
I guess i will try Fedora out.

If Linux goes the WINDOWS way of becoming a boring single distro, there won't be any takers trust me. Ubuntu has no issues with RAID, I have installed RAID on quite a few systems here and am yet to come across any glitches.

---

### Post by QIII on 2009-07-04
I must not be living right.

Kernel:  2.6.28-11.

AMD Phenom II x 4 3.0 GHz
8 GB RAM

I'm getting 40+ MB/s transfer rate to and from USB.

88+ hd to hd (separate physical drives) from ext3 to NTFS.

55+ hd to hd  (separate physical drives) from NTFS to ext3.

Better, apparently, than what you are all getting.

But the wide difference between ext3 -> NTFS and NTFS -> ext3 may be significant.

Perhaps the difference is neither Ubuntu or the kernel.

It might be the ext3 file system.

---

### Post by Arup on 2009-07-04
> **QIII said:**
> I must not be living right.

Kernel:  2.6.28-11.

AMD Phenom II x 4 3.0 GHz
8 GB RAM

I'm getting 40+ MB/s transfer rate to and from USB.

88+ hd to hd (separate physical drives) from ext3 to NTFS.

55+ hd to hd  (separate physical drives) from NTFS to ext3.

Better, apparently, than what you are all getting.

But the wide difference between ext3 -> NTFS and NTFS -> ext3 may be significant.

Perhaps the difference is neither Ubuntu or the kernel.

It might be the ext3 file system.


I use ext4 with my Samsung Spinpoints and I have no such issues so I guess it has to be hardware specific.

---

### Post by shane2peru on 2009-07-04
> **Bert_421 said:**
> Maybe this is why Windows is so successful, .......

Ha ha, ha ha, ha ha, haaaa, haaaaa  :lolflag:     That is funny, when I stopped laughing I brought myself back into composure long enough to respond.  That was a joke right?   I mean I took it as one.  That isn't my definition of successful, yes they currently own the market, but that is not what I would define as successful in terms of an OS.  That was very funny though.  :lolflag:  Thanks for the laugh.

Shane

---

### Post by tsvetan on 2009-07-04
That's not funny at all!
It's a shame!
I'm using Linux since 10 years ago, but I was not expecting to have such issues with my brand new HP ProBook:

 - Slow SATA - this is horrible. It takes minutes to copy 600 - 700Mb. It's simply not acceptable and unfortunately no one cares (for years).
 - ATI drivers didn't change so much for last 5 years. I had to disable compiz (even if I don't like and use such eye candies) in order to have some kind of suspend & hibernate. Some kind of because it's not stable - suspend, wake-up and then try to play video - BUM, system hangs. It's reproducible! And this seems to be just a minor issue. I didn't count how many times I had to hard restart my machine...

To be honest everything else is OK - fast, great installation, great user experience, but such "small" issues change the whole picture. But who cares about the installation when the system is not stable, when you don't know what will happen after you close the notebook -simple, small things that break the whole story.

What is a succesful OS?

---

### Post by Bert_421 on 2009-07-04
How many company use Windows?
How many personal pc use Windows? 
How many company use Linux?
How many personal pc use Linux?
Windows 90%
Apple 9% Very good audio / video 
Linux and all the distro .5 % 
.5 % error margin 
What make people buy windows. I did not see anybody pointing a gun to anybody head and told them to buy windows.
They keep buying it because ?????? 
as far as that goes linux is giving it a way for [SIZE=4][COLOR=Red]FREE[/COLOR][/SIZE] and still only has a vary vary vary small share in the business - personal pc market [COLOR=Red]there is something to laugh about[/COLOR].:lolflag:shane2peru

all i was trying to convey is that if there was only a couple for distro maybe the kernel developers would be able to fix issue faster instead of having to deal with so many different needs of all the distro. kind of odd i think that i have to try a different distro to see if my pc will work correctly. usb , raid etc.

---

### Post by QIII on 2009-07-04
Saying that Windows is better because of market share is falling into the logical fallacy known as the Bandwagon Fallacy.

Which is better is independent of the relative popularity of each.

90% of people "buy" Windows because they buy computers with Windows installed.

ATI drivers, like just about everyone else's, were proprietary.  They have only recently been introduced as open source, so it might be reasonable to expect that it might take more than a day or two to have distro specific drivers included.

In the meantime, Catalyst has worked fine for me in Ubuntu with the exception that I have to toggle between Compiz and Metacity for satisfactory video performance sometimes.

As far as transfer speed, "theoretical" limits are academic.  

I'm getting about the "practical" limit for USB 2.0, but less than the "theoretical" limit.

I'm getting a lot less than SATA 3's 3 Gbps spec, which "theoretically" should provide 375 GB/s.

If you have a system with water pressure rated at 375 gpm and a delivery system rated at 60 gpm, you are only going to get 60 gpm.  And if you have a connecting pipe between the high pressure ends that only allows for 10 gpm, you'll be limited to 10 gpm.

The question would be:  Why does QIII get better transfer rates than us? 

I don't have the answer for that.  

Looking for answers on a forum is constructive.  Complaining and moaning is not.  If you are genuinely concerned about what the "developers" do, you have the option to help.  You have the option to test Karmic right now.  Spend your efforts doing that rather than sitting on your plump behinds and carping after the fact.  Sorry.  Just the ranting of an old Army Officer who listened to too much whining from people who were happy to complain but less happy to get out of their "f*rt sacks" and actually work.

---

### Post by shane2peru on 2009-07-04
Hmm, I always find it soooo odd that so many windows supporters are here.  I really did think that was a joke.  I guess because we are on Linux forums.  I didn't know that windows supporters hung out here.  At any rate I have 4 computers running Ubuntu.  Two have sata drives, and both have the speed issue fixed.  I didn't do anything at all, but updates. :)  I know this is a problem, and by no means am making light of the problem.  I also know Linux is not without it's problems, but windows .... well, better not go down that road, this thread is about sata, usb and slow transfer speeds.  Let's stay on topic. If everyone would file a bug report too, and stick with it here it is:  [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/119730](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/119730)

So complain, no troubleshoot there. :)  I think working through commandline helps as well as installing gnome-commander ```
sudo apt-get install gnome-commander
```  and give that a try.  It is a nice two pain graphical file manager.  Perhaps those will help.  For command line try:
```

cp -v /source/of/file /destination/to/copy/to

```
the -v is verbal.  It seemed like both of those helped me when it was sloooow in Nautilus.

Shane

---

### Post by Arup on 2009-07-06
Plenty of disguised covert Win fanboyz here and guess what, file transfer in Windows sucks even more. One of the reasons there are various utilities to speed up the measly transfer rates. FlexTk is one, there are many more so don't go chiming it works in Windows routine just because sheep follow it. Windows has admitted to the issue of slow tranfers as well, the fact that you have anti virus and other security programs scanning every files in background while they are transferred doesn't make it any better in Win.

---

### Post by Anthon berg on 2009-07-06
> **QIII said:**
> Perhaps the difference is neither Ubuntu or the kernel.

It might be the ext3 file system.

No, it's the Ubuntu patches to the kernel, on certain hardware.

> **Arup said:**
> Plenty of disguised covert Win fanboyz here and guess what, file transfer in Windows sucks even more.

No, in fact the badly patched Ubuntu kernel makes Ubuntu suck more. Mainline kernel is fine though.

---

### Post by Arup on 2009-07-06
> **Anthon berg said:**
> No, it's the Ubuntu patches to the kernel, on certain hardware.



No, in fact the badly patched Ubuntu kernel makes Ubuntu suck more. Mainline kernel is fine though.

Doesn't suck here, runs fine, if it was that bad an issue don't you think Ubuntu team would take an emergency move and issue patches for it. Why would Ubuntu deliberately patch their kernel to make it look bad.

---

### Post by shane2peru on 2009-07-06
> **Anthon berg said:**
> No, it's the Ubuntu patches to the kernel, on certain hardware.



No, in fact the badly patched Ubuntu kernel makes Ubuntu suck more. Mainline kernel is fine though.

If you just want to complain do it verbally starring at the screen.  We aren't here to help complaints. :)  If you are really concerned, then file a bug report.

Shane

---

### Post by tsvetan on 2009-07-06
There are bug reports (just google around). And I don't think that someone here complaints about this issue. Instead we're looking for a solution. And be sure that windows is not a solution - I don't care if it is faster or slower and why, I want to use Ubuntu, not windows.

The only important point is that this is a major Ubuntu issue for a long time without resolution. Unfortunately I cannot find an "official" statement from the kernel team so far.

Best Regards,
Tsvetan

---

### Post by ocsid80 on 2009-07-06
> **Arup said:**
> Plenty of disguised covert Win fanboyz here and guess what, file transfer in Windows sucks even more. One of the reasons there are various utilities to speed up the measly transfer rates. FlexTk is one, there are many more so don't go chiming it works in Windows routine just because sheep follow it. Windows has admitted to the issue of slow tranfers as well, the fact that you have anti virus and other security programs scanning every files in background while they are transferred doesn't make it any better in Win.

FlexTk is now available for Ubuntu as well.

Freeware FlexTk Express for Ubuntu 9.04 is available here:

[http://www.flexense.com/downloads_linux_ubuntu904.html](http://www.flexense.com/downloads_linux_ubuntu904.html)

---

### Post by Arup on 2009-07-06
> **ocsid80 said:**
> FlexTk is now available for Ubuntu as well.

Freeware FlexTk Express for Ubuntu 9.04 is available here:

[http://www.flexense.com/downloads_linux_ubuntu904.html](http://www.flexense.com/downloads_linux_ubuntu904.html)

WOW! thats news for me, thanks for the heads up but unfortunately, its x32 and not x64.

---

### Post by ocsid80 on 2009-07-07
> **Arup said:**
> WOW! thats news for me, thanks for the heads up but unfortunately, its x32 and not x64.

x64 version is here:

[http://www.flexense.com/downloads_linux_ubuntu904_x64.html](http://www.flexense.com/downloads_linux_ubuntu904_x64.html)

---

### Post by Arup on 2009-07-07
> **ocsid80 said:**
> x64 version is here:

[http://www.flexense.com/downloads_linux_ubuntu904_x64.html](http://www.flexense.com/downloads_linux_ubuntu904_x64.html)

Thanks a lot.

---

### Post by Anthon berg on 2009-07-07
> **Arup said:**
> Doesn't suck here, runs fine, if it was that bad an issue don't you think Ubuntu team would take an emergency move and issue patches for it. Why would Ubuntu deliberately patch their kernel to make it look bad.

The Ubuntu developers are of course not deliberately breaking the kernel, what a stupid thing to say, but they ARE adding features that ARE causing breakage of the kernel - on certain systems. It's simple lack of competence, and lack of testing, rather than malice.

> **shane2peru said:**
> If you just want to complain do it verbally starring at the screen.  We aren't here to help complaints. :)  If you are really concerned, then file a bug report.

Shane

Sirs, both of you,

I have already contributed to any bug reports I can find - INCLUDING A FIX FOR THE PROBLEM. The post you quote, Shane, isn't a complaint but A FIX.

---

### Post by Arup on 2009-07-07
> **Anthon berg said:**
> The Ubuntu developers are of course not deliberately breaking the kernel, what a stupid thing to say, but they ARE adding features that ARE causing breakage of the kernel - on certain systems. It's simple lack of competence, and lack of testing, rather than malice.



Sirs, both of you,

I have already contributed to any bug reports I can find - INCLUDING A FIX FOR THE PROBLEM. The post you quote, Shane, isn't a complaint but A FIX.

Lack of competence from one of the most popular distro which singlehandedly made Linux the buzz word on desktop.....................I heard it all.

Thank you.

---

### Post by Anthon berg on 2009-07-07
> **Arup said:**
> Lack of competence from one of the most popular distro which singlehandedly made Linux the buzz word on desktop.....................I heard it all.

Thank you.

That's no logic.
The marketing team is great, the kernel team isn't doing such a great job. As evidenced by the broken kernel!

---

### Post by Arup on 2009-07-07
> **Anthon berg said:**
> That's no logic.
The marketing team is great, the kernel team isn't doing such a great job. As evidenced by the broken kernel!

No broken kernel here, runs like a dream on myriads of machines I have installed Jaunty in, x32 and x64 variety. My own system has two Samsung 1TBs and file transfer is no issue there. It could be hardware/BIOS specific but generalizing and declaring that Ubuntu has shipped Jaunty with a broken kernel is a bit presumptuous. There is no marketing of Ubuntu or any other Linux distros, they don't make any money from us so we pick Ubuntu based on what we see, feel, experience and like. I have tried out every other major distro out there and settled for Ubuntu, so have others here. In case you feel it has a broken kernel for you, its Linux and thankfully, you have the choice to move over to another distro as others have done but for myself and many others running Ubuntu without any hitches, we don't feel that the kernel is broken in Ubuntu.

---

### Post by Anthon berg on 2009-07-07
> **Arup said:**
> No broken kernel here, runs like a dream on myriads of machines I have installed Jaunty in, x32 and x64 variety..

Dude,

it's hardware specific, has occurred in 4 machines at my workplace with various motherboards/chipsets/configuration, and the only consistent fix is installing the mainline kernel. The only difference is the Ubuntu patches to the kernel. That means the kernel is patched by Ubuntu developers, and as it causes breakage, the fault is with those developers. End of story.

Just because it doesn't happen to you doesn't mean it isn't real.

P.s.: You're shooting the messenger.

---

### Post by Arup on 2009-07-07
> **Anthon berg said:**
> Dude,

it's hardware specific, has occurred in 4 machines at my workplace with various motherboards/chipsets/configuration, and the only consistent fix is installing the mainline kernel. The only difference is the Ubuntu patches to the kernel. That means the kernel is patched by Ubuntu developers, and as it causes breakage, the fault is with those developers. End of story.

Just because it doesn't happen to you doesn't mean it isn't real.

P.s.: You're shooting the messenger.

And in the same way, just because its happening to you and some others don't mean its the rule.

You are trying to generalize with conjectures.

---

### Post by Anthon berg on 2009-07-07
> **Arup said:**
> And in the same way, just because its happening to you and some others don't mean its the rule.

You are trying to generalize with conjectures.

Whatever. The kernel is broken. How is it not broken if it breaks IO on multiple machines? Check the bug reports!

Simply:
The Ubuntu patches need to be gone over, one by one, on a machine that exhibits the broken behavior, and the patch / combination of patches that causes the slow I/O behavior needs to be fixed, and then the Ubuntu kernel patches aren't break the kernel anymore.

---

### Post by Arup on 2009-07-07
The poor incompetent and hopeless Ubuntu devs, just can't bring out a bug free kernel, hmm makes me wonder how it manages to stay at the top of the distro watch list. No one distro will be bug free, show me one and I will show you delusionary utopia. Having said that, Ubuntu usually manages to keep it clean, accusing Ubuntu devs of releasing a disto with a glaring bug for something as important as file transfer is nothing short of ridiculous. Hardware, BIOS everything has a bearing on the issues. Many people here post issues assuming they are Ubuntu specific only to find out that it was due to their motherboard's faulty BIOS or lack of proper drivers.

---

### Post by Anthon berg on 2009-07-08
> **arup said:**
> the poor incompetent and hopeless ubuntu devs, just can't bring out a bug free kernel, hmm makes me wonder how it manages to stay at the top of the distro watch list.

[size="7"]check the bug reports[/size]

---

### Post by Arup on 2009-07-08
> **Anthon berg said:**
> [size="7"]check the bug reports[/size]

Has the bug report been accepted by team Ubuntu? There are those who made settings in their BIOS and it solved the issue, I have a strong suspicion its some interaction between system BIOS and Ubuntu kernel. In my case, the AMD Phenom machine using ASUS motherboard transfers slower than my Intel motherboard dual quad cores. Both systems have Samsung 1TB Spinpoint.

---

### Post by Anthon berg on 2009-07-08
Bug #119730: Slow SATA performance 

Affects: linux (Ubuntu)   	   Triaged   	   Medium 

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/119730?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/119730?comments=all)

And certainly we have tried any and all BIOS and scheduler combinations settings ranging from stock to logically better than stock to improbably weird and desperate. The only thing to consistently and always fix the slow IO was to install a mainline kernel.

Sir, I apologise for being rude. Sincerely.  The reason I have been rude in this thread is that the bug has cost me a lot of time and effort, and my emotions got the best of me when I saw doubts of its existence.

---

### Post by Arup on 2009-07-08
> **Anthon berg said:**
> Bug #119730: Slow SATA performance 

Affects: linux (Ubuntu)   	   Triaged   	   Medium 

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/119730?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/119730?comments=all)

And certainly we have tried any and all BIOS and scheduler combinations settings ranging from stock to logically better than stock to improbably weird and desperate. The only thing to consistently and always fix the slow IO was to install a mainline kernel.

Sir, I apologise for being rude. Sincerely.  The reason I have been rude in this thread is that the bug has cost me a lot of time and effort, and my emotions got the best of me when I saw doubts of its existence.

I can well relate to your frustration and just because I am not facing this issue doesn't mean it doesn't exist. However having said that, can you try this out on any other machine you might have access to and see if this problem surfaces again.

---

### Post by Anthon berg on 2009-07-08
> **Arup said:**
> I can well relate to your frustration and just because I am not facing this issue doesn't mean it doesn't exist. However having said that, can you try this out on any other machine you might have access to and see if this problem surfaces again.

How so? - btw, I have experienced this on four different machines at work, w. pretty different hardware setups - same story every time.

---

### Post by Shawn Reist on 2009-07-08
Hello,

I have noticed the slow transfer rates and have been hunting around a while and trying things here and there to see if I can change something.  I have disabled the legacy USB support and transfers did increase slightly but nothing of note.

all that to no success.  I would consider myself a newbie even though I have gone full linux for the last 2 years.

I still have Ubuntu 7.10 on a SCSI HD and I changed the boot order and copied the rough information down. if other would like I can change the boot orders again and acquire more specific information.

In a nut shell here is the info I have.

Computer Supermicro P4D6C+

1. Dual Intel® Xeon® processors 1.5 GHz
2. Intel® 860 Chipset
3. 512MB 600/800MHz RDRAM
4. 1x Intel® 82559 10/100 Ethernet Controller
5. Adaptec AIC-7899W Dual-Channel Ultra160 SCSI
6. 2 x 64-bit PCI expansion slots
7. 4xAGP Pro slot
8. Zero-Channel RAID Support
9. 4Mb Flash EEPROM with Award® BIOS
--------------------
/df

lrm                        254704      2192    252512   1% /lib/modules/2.6.28-13-generic/volatile
/dev/sda1              	 75459076  10569680  61056292  15% /					IDE
/dev/sdb1             	 16856312   5939032  10061020  38% /media/disk				SCSI
/dev/sdc1             	 17778960   3728164  13154776  23% /media/17gig				SCSI
/dev/sdd1             	  3903472   1944704   1958768  50% /media/PNY				USB
//192.168.0.97/volume_1	479691308 344281220 135410088  72% /home/shawn/storage			SATA (network)

---------------

Linux Icabaud 2.6.24-23-generic #1 SMP Wed Apr 1 21:47:28 UTC 2009 i686 GNU/Linux

able to transfer 869.3 MB file to  USB 2 flash drive
	transfer rates 9.2 MB/s

transfer from Netdrive
	Dlink DNS-323
	transfers are 1.2-1.3 MB/sec



Linux icabaud 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009 i686 GNU/Linux
File tansfers start off at 7.7 MB/sec and drop to 4.4 MB/sec

transfer from Netdrive
	Dlink DNS-323
	transfers are 948 KB/sec

OpenSUSE live CD 11.1

able to transfer 869.3 MB file to  USB 2 flash drive
	transfer rates 12 MB/s tappering to 10.5 MB/s

transfer from Netdrive
	Dlink DNS-323
	transfers are 4 MB/sec
-------------------

hope this helps or makes sense to someone.

---

### Post by Anthon berg on 2009-07-10
> **Shawn Reist said:**
> Hello,

I have noticed the slow transfer rates and have been hunting around a while and trying things here and there to see if I can change something.  I have disabled the legacy USB support and transfers did increase slightly but nothing of note.

all that to no success.  I would consider myself a newbie even though I have gone full linux for the last 2 years.

Hi,
I am starting to sound like a broken record, sorry all, but I really, really recommend you try the mainline ("vanilla") Linux kernel.

You can get a package here: 
[https://wiki.ubuntu.com/KernelTeam/MainlineBuilds?action=show&redirect=KernelMainlineBuilds](https://wiki.ubuntu.com/KernelTeam/MainlineBuilds?action=show&redirect=KernelMainlineBuilds)

It only takes a few minutes to do, is a pretty easy install - for sure easier than changing BIOS settings, and is completely removable. Disclaimer: I've read that you may have issues with video card drivers, but I haven't had that problem myself.

---

### Post by mante on 2009-07-12
Using Jaunty 64bit.
Mainline kernel tested:
Linux mante-desktop 2.6.29-02062906-generic #02062906 SMP Fri Jul 3 10:17:03 UTC 2009 x86_64 GNU/Linux

but hard disk copy performance for large files still below 5Mb/sec

---

### Post by GuiGuy on 2009-07-12
> **Arup said:**
> I can well relate to your frustration and just because I am not facing this issue doesn't mean it doesn't exist.

In support of Anthon Berg, I have tested and put up with this for some time on a number of machines. The problem occurs repeatedly on AMD64 AM2 dual core CPUs. The Mobos are ASUS M3A, M2H and several Gigabyte variants.

To suggest that the user is to blame for choosing hardware that suffers from the problem is disingenuous. 

On the same machines  installing 32 bit Ubuntu removes the problem.

A change to another 64bit distro, Fedora in my case, solves it very nicely. 


Cheers

---

### Post by Shawn Reist on 2009-07-12
Hello,

what kernel did you use:

I am presently running 9.04 Jaunty
[INDENT]2.6.28-13-generic[/INDENT]

I tried a two versions from the mainline WIKI without much success.

version 2.6.29-02062906
[INDENT]transfer rates were slower, apparmor failed to load[/INDENT]

version 2.6.28-02062809
[INDENT]transfers started off fast then tapered down to very slow, apparmor failed to load as well.[/INDENT]
[INDENT]12.x MB/S start of a 890 Meg file, about the 1/2 way mark transfer rates decreased to 3.6 MB/S[/INDENT]

wondering if I should try one of the daily builds and what other things I could do.

---

### Post by Arup on 2009-07-13
> **GuiGuy said:**
> In support of Anthon Berg, I have tested and put up with this for some time on a number of machines. The problem occurs repeatedly on AMD64 AM2 dual core CPUs. The Mobos are ASUS M3A, M2H and several Gigabyte variants.

To suggest that the user is to blame for choosing hardware that suffers from the problem is disingenuous. 

On the same machines  installing 32 bit Ubuntu removes the problem.

A change to another 64bit distro, Fedora in my case, solves it very nicely. 


Cheers

No one is blaming hardware, however its apparent that this issue effects some and not all Ubuntu users so one can't make a general assumption that its a faulty kernel released by team Ubuntu without testing. What it definitely looks like is a BIOS/Hardware/OS issue combined and therefore if it can't be fixed, better to move on to another distro which thankfully linux offers.

---

### Post by adam.ec on 2009-07-13
I have an Intel Core2Duo E4400 and E6600 on Intel D945GNCL and Intel DG33 respectively. I use four USB flash drives and an LG USB external DVD drive. The flash drives all start off at around 4MB/s and crawl down to ~360KB/s. The DVD drive starts at 1.2MB/s and drops to around 90KB/s and no longer will write to DVD. By the time it gets to roughly 70% of the way through a disk the burning app (three tried so far) suddenly shows the progression as 0% and 30 minutes later jst tells me the burn failed with errors, but none are in the log.

Hard drive transfers are unbearable slow as well (~3.5MB/s) and I've tried swapping to IDE drives with no luck. Obviously I've also used Canonicals SATA solutions.

I am using the 64bit Ubuntu as well but I definitely do not have any AMD hardware so I am dubious to believe the problem is just AMD based.

> ...therefore if it can't be fixed, better to move on to another distro which thankfully linux offers

As I have said in a previous post we shouldn't have to move to another distro - Jaunty has been Ubuntu's most unstable release so far with lots of silly errors in it which, unfortunately, really affects productivity with it. I moved over to Fedora 11 which was fantastic for the first few weeks. Then the whole thing just started slowing down. I was finding it hard to install some very basic applications from source as well, either ending in failure or just too many restrictions for some bizarre reason. Archlinux was next, and I am still using it but vital apps like gnome-system-tools have been broken for what seems like years. I also have an issue with font rendering in any desktop other than Gnome. I've had problems again with package management being unbelieveably slow in Mandriva and actually quite difficult to navigate for something that should be so simple. Searching for packages was almost impossible (also a problem in Fedora). So, based on this premise it looks like Slackware will be making it onto the desktop big time, though I'm still yet to encounter errors on Sabayon and Gentoo.

For most users though, we just need something that works. I like playing around with distros but my main job is programming and I don't have time to fiddle around with correcting so many OS errors. I might be the only one thinking this way but it would be great if Ubuntu would provide big updgrade distros every 18 months or so and 'rolling release' type updates in between. Every six months is just too often, but I still hear folk complaining about Debian and Red Hat slow releasing. Thing is, at least they are stable, and they work.

---

### Post by Arup on 2009-07-13
I also suggest you try out Sidux which though being bleeding edge is quite stable and manages to be among the quickest of distros. Only thing is that its less GUI and more cli.

---

### Post by webit on 2009-07-14
Same for me. SATA transfers are terrible slow:

> /dev/sda5:
 Timing cached reads:     2 MB in  3.30 seconds = 621.49 kB/sec
 Timing buffered disk reads:    2 MB in  3.29 seconds = 622.11 kB/sec

while ATA transfers are very well:

> /dev/sdb4:
 Timing cached reads:   776 MB in  2.00 seconds = 387.39 MB/sec
 Timing buffered disk reads:  160 MB in  3.01 seconds =  53.11 MB/sec

It was OK few days/weeks ago (SATA is my archive I don't use often, but when I do - I need good transfers). I'm using 2.6.28-13 kernel. CPU is AMD Athlon 2800+, SATA disk is 80GB's Maxtor 6Y080M0.

---

### Post by welchy on 2009-07-14
Mine is also very slow. Have tried both 32bit and 64bit Jaunty, both clean installs on a Intel Q6600, 4gb machine, MSI P965 Platinum mboard with latest bios.

Interestingly its not always slow, sometimes starts of fast, can copy a CD image at full speed for example, but copying later on I notice I get about 5MB per second SATA -> SATA (Even on the same disk)

USB also terribly slow, but I don't care about that so much.

Suggestion of a Vanilla Kernel doesn't help much as my understanding is that restricted drivers are then not available, please correct me if I'm wrong.

I could switch Distro's, but I think Ubuntu is great and Jaunty is really good, except this darn speed issue....

---

### Post by Anthon berg on 2009-07-14
> **welchy said:**
> Suggestion of a Vanilla Kernel doesn't help much as my understanding is that restricted drivers are then not available, please correct me if I'm wrong.

It would be extra nice if you could try it to see if that is the problem.

---

### Post by welchy on 2009-07-14
> **Anthon berg said:**
> It would be extra nice if you could try it to see if that is the problem.

That is a very fair point !

I just tried the real-time kernel, and all that did was lock up my machine about 30 seconds after I logged into Xorg before I had a chance to try the SATA transfer speeds.

Will give the vanilla kernel a go and report back, compiling nvidia modules aren't that big a hassle anyways, and its the only restricted driver I use :-)

---

### Post by welchy on 2009-07-14
> **Anthon berg said:**
> It would be extra nice if you could try it to see if that is the problem.

Trying the Vanilla kernel was good advice, but unfortunatley made no difference to my symptoms.

After login copied one 700mb file ~30mb/second.

Next 700mb file dropped to ~4mb/second.

Next 700mb file dropped to ~4mb/second.

All were different files around 700mb
All were given 30 seconds between runs
All were 'time cp file dest' at the command line, no GUI's used
All were copying from SATA -> same SATA disk.

Also tried one 700mb file from the original SATA disk to a different SATA disk got ~4.3 mb/second

Nothing else running on the machine.

And before anyone tells me, I know this is not the most scientific of tests :-) , but the results match my symptoms since using Jaunty 100%, I.E. SATA performance after reboot sometimes *ok* for a while, but then drops off an does not come back until reboot.

uname -a : Linux Zilla 2.6.30-020630-generic #020630 SMP Wed Jun 10 09:04:38 UTC 2009 x86_64 GNU/Linux

Kernel Deb : linux-image-2.6.30-020630-generic_2.6.30-020630_amd64.deb

If anyone has any other thoughts or suggestions I'd be happy to try them out. I really don't want to switch distro's, I like Ubuntu a lot, but ~4mb/second SATA performance is a real drag :-(

---

### Post by Anthon berg on 2009-07-14
[IMG]http://i234.photobucket.com/albums/ee225/kalleo89/emot-eng99.gif[/IMG]
orz

OK, what finally fixed things for me was the mainline kernel. In the meantime, I had:

- Disabled all accoustic management stuff I could disable (didn't seem to do anything)

- Set SATA mode to AHCI in the BIOS (not sure about that one)

- Overclocked my FSB so that I had a 400MHz FSB and a 2:1 memory clock ratio (which seemed to help a lot!, but that makes no sense :/ ), keeping CPU speed mostly the same

- Turned off atimes on all partitions (e.g. noatime in options line in fstab)

... and that's all I can remember doing. Some of these had a small effect. Very strangely, the FSB overclock felt like it had the biggest impact. But what finally got things to really click into place was the mainline kernel, and it made the biggest difference.

FWIW I have a Gigabyte GA-P35-DS4 (or GA-P35-DS4R?), and a 2.4 GHz Q6600 now running at 2.8GHz, 8GB DDR 800 memory, four 750 GB Seagate drives and a 1.5 TB Samsung drive.

---

### Post by welchy on 2009-07-15
Thanks for the tips. Might have a play around with my bios settings etc...

---

### Post by Anthon berg on 2009-07-15
> **welchy said:**
> Thanks for the tips. Might have a play around with my bios settings etc...

Hi, I just remembered one fairly important one - I installed a BIOS update on my board, in which there was a "Super I/O Code Update", according to Gigabyte. I see you've got the latest BIOS, welchy, but I think the info should be in the thread.

---

### Post by Arup on 2009-07-15
> **Anthon berg said:**
> Hi, I just remembered one fairly important one - I installed a BIOS update on my board, in which there was a "Super I/O Code Update", according to Gigabyte. I see you've got the latest BIOS, welchy, but I think the info should be in the thread.

This is quite an important fact, might explain why some are having issues and others arent' In my case the BIOS update on my asus board with Phenom improved substantially after the latest BIOS update, it still isn't close to the Intel board with dual quad core but its not bad either like before.

---

### Post by mister_playboy on 2009-07-15
I have no trouble with my external USB HDDs, but writing to a USB stick has the some problem described in the first post... a burst of normal speed, and then a crawl of a few MB a minute.  :(

This issue didn't occur with 8.10 for me... just on 9.04.

---

### Post by PatrickVogeli on 2009-07-16
it seems I'm too having the problem. I'm not using the stock ubuntu kernel, but a custom compiled 2.6.30.1. 

Copying files to a Kingston data traveller 4gb usb stick started at nearly 9 MB/s, now its transferreing at 3,1 MB/s..

This is just ridiculous.

**EDIT:** Ok, forget this one. I have now disabled USB legacy support in the BIOS and it works now. I get 7-8 MB/s in my USB stick (fat32 formatted) and 12-14MB/s in my Wester Digital usb HDD (2,5" drive, formated ext2).

So I guess it's fine.

---

### Post by welchy on 2009-07-17
I flashed my bios with the latest available bios from MSI.

I don't see anything in there related to the problem.

Just to make sure I wasn't going mad I installed Debain 'Testing', SATA speed back to normal with no other changes....

Not sure what it is with Jaunty but it definitely doesn't like my hardware :-(

---

### Post by GuiGuy on 2009-07-17
> **PatrickVogeli said:**
> 
**EDIT:** Ok, forget this one. I have now disabled USB legacy support in the BIOS and it works now. I get 7-8 MB/s in my USB stick (fat32 formatted) and 12-14MB/s in my Wester Digital usb HDD (2,5" drive, formated ext2).

So I guess it's fine.

Thanks for this. I had moved on to Fedora because of the appalling USB and SATA performance issues with Ubuntu64. 

Nevertheless, I restored to my previous Ubuntu HDD image for a test. On my ASUS M3A and M2H boards if I disable USB legacy support the USB transfer speeds improve dramatically. However, I lose access to the DBTV PCI tuner cards.

I then tried AUTOMATIC USB Legacy Support and now I have good USB performance to Flash Drives and external HDDs. DBTV PCI cards are working as well.

However, and sadly, SATA performance remains slower than the snails in our garden. I'll put Fedora back and will wait for the next installment. 

**UPDATE:** Spoke too soon. I let a long copy operation run from an internal HDD to and external HDD. While it started off OK it's now back to a trickle. Probably less than 100k per second. A 5meg MP3 is taking about 20 seconds. :( - As I said, it's a shame. Back to Fedoraa.


Again, thanks

---

### Post by PatrickVogeli on 2009-07-18
forget about what I've said. I've just tried again to make sure and the same is happening again. Transferring a 1,4GByte file starts at 13+ and now, after having copied 500MB is at 3,6MB... great eh?

I'll boot into karmic and report.

---

### Post by amsum on 2009-07-18
I am facing the similar problem. I am able to copy-paste on USB with FAT32 file system at decent rate of 18-20 mbps. But the same operation on external HDD with NTFS file system is giving the speed of 975 kbps (pathetic!!!... less than 1 mbps).

---

### Post by ufmace on 2009-07-18
I don't think I'm seeing this problem on my system, but I thought I'd throw in my 2 cents anyways incase it helps someone else solve their problem.

I'm currently copying a 50GB folder from one SATA drive to another, and it's been going at around 50MB/s for over 10 minutes now. I haven't done any formal tests on IDE, USB, or Firewire yet, but I don't seem to have any problems playing movies from drives connected over IDE or Firewire.

I'm using 9.04 64 bit with a Gigabyte GA-MA780G-UD3H mobo, and I haven't messed with the bios at all. Processor is a Phenom II X2 550, and 4GB of RAM. Let me know if you want any more information.

---

### Post by GuiGuy on 2009-07-19
> **ufmace said:**
> 
I'm using 9.04 64 bit with a Gigabyte GA-MA780G-UD3H mobo, and I haven't messed with the bios at all. Processor is a Phenom II X2 550, and 4GB of RAM. Let me know if you want any more information.

... what kernel version?

---

### Post by PatrickVogeli on 2009-07-19
tried karmic too: the same is happening.

---

### Post by ufmace on 2009-07-19
> **GuiGuy said:**
> ... what kernel version?

2.6.28-14-generic

---

### Post by aj_the_first on 2009-07-20
So can someone summarize for me?:
Is there a fix (besides using a different kernel)? and if so, what is it?
 
I recently updated to Jaunty, and then transfered all my media back on the the computer, about 100 gigs, and it took 23 hours for a transfer rate of about 1MB/sec.
That was about four times slower than Intrepid, which I already thought was quite slow.
I really don't want to switch, but I'm not sure I can live with this....

---

### Post by Arup on 2009-07-20
> **aj_the_first said:**
> So can someone summarize for me?:
Is there a fix (besides using a different kernel)? and if so, what is it?
 
I recently updated to Jaunty, and then transfered all my media back on the the computer, about 100 gigs, and it took 23 hours for a transfer rate of about 1MB/sec.
That was about four times slower than Intrepid, which I already thought was quite slow.
I really don't want to switch, but I'm not sure I can live with this....

Have you tried disabling USB Legacy support in BIOS?

---

### Post by aj_the_first on 2009-07-20
> **Arup said:**
> Have you tried disabling USB Legacy support in BIOS?
 
 
I hadn't yet.  I saw that someone earlier in the post had and it didn't work for him, but I'll give that a try and report.

---

### Post by aj_the_first on 2009-07-20
> **Arup said:**
> Have you tried disabling USB Legacy support in BIOS?
 
 
Well, I just gave it a try and it worked for the external hard drive: now transfering at 16.8 MB/sec, WAY better than the 1MB/sec...
...unfortunately I found out that my webcam must be a legacy device because it no longer works.
Guess it is time to find a USB 2.0 webcam... or is that 3.0 now?  Surely my old computer doesn't have 3.0 support yet?

---

### Post by Arup on 2009-07-21
> **aj_the_first said:**
> Well, I just gave it a try and it worked for the external hard drive: now transfering at 16.8 MB/sec, WAY better than the 1MB/sec...
...unfortunately I found out that my webcam must be a legacy device because it no longer works.
Guess it is time to find a USB 2.0 webcam... or is that 3.0 now?  Surely my old computer doesn't have 3.0 support yet?

There are many cheapo USB 2.0 cams, some based on ZC0301 chip and they all work fine on Ubuntu, USB 1.0 is a drag and legacy support slows down Linux and Windows both.

---

### Post by speedkreature on 2009-07-21
Has the issue been fixed or is there some hardware not affected?  It seems kind of newbish to ask given the time from the last post, but I don't think I have this problem.

Jaunty x86-64 (some 32-bit libs installed via getlibs)
AMD Phenom II X3 710
Gigabyte GA-MA790XT-UD4P (BIOS by Award, factory version)
Intel X25 64GB SSD, /,  ext3
4x 1GB Crucial 1066MHz DDR2
WD Caviar Green 2TB HDD, /home, ext4
Seagate FreeAgentGo 250GB, /media/AgentOrange, ext3
OCZ Rally2 16GB USB stick, /media/OCZ_Rally2, FAT32

Intel SSD to WD HD is about 34MB/s
WD HD to Intel SSD is about 36MB/s
Intel SSD/WD HD to FreeAgentGo is about 31MB/s
IntelSSD/WD HD to OCZ Rally2, is about 28MB/s
OCZ Rally to any drive is about 24MB/s

Is that about normal?....I've never experienced read/write throughput greater than 36MB/s on anything that wasn't comercial grade (I.E. the RAID 60 Fibre Channel SAN at work would be considered "commercial grade")  Theoritical throughput on SATAII should be around 38MB/s---I don't get even close to these values in Windows (XP, Vista, Server 2003, and Server 2008 are all I've observed).
In fact, I have a Vista x86-64 workstation that has a WD Caviar Green 2TB HDD and the highest throughput I've been able to sustain was about 21MB/s.

---

### Post by Arup on 2009-07-21
Your transfer speeds are way lower than what I get with my Spinpoints, I dont' even have a SSD so in your case, SSD should be real fast.

---

### Post by ufmace on 2009-07-22
> **speedkreature said:**
> Has the issue been fixed or is there some hardware not affected?  It seems kind of newbish to ask given the time from the last post, but I don't think I have this problem.

Jaunty x86-64 (some 32-bit libs installed via getlibs)
AMD Phenom II X3 710
Gigabyte GA-MA790XT-UD4P (BIOS by Award, factory version)
Intel X25 64GB SSD, /,  ext3
4x 1GB Crucial 1066MHz DDR2
WD Caviar Green 2TB HDD, /home, ext4
Seagate FreeAgentGo 250GB, /media/AgentOrange, ext3
OCZ Rally2 16GB USB stick, /media/OCZ_Rally2, FAT32

Intel SSD to WD HD is about 34MB/s
WD HD to Intel SSD is about 36MB/s
Intel SSD/WD HD to FreeAgentGo is about 31MB/s
IntelSSD/WD HD to OCZ Rally2, is about 28MB/s
OCZ Rally to any drive is about 24MB/s

Is that about normal?....I've never experienced read/write throughput greater than 36MB/s on anything that wasn't comercial grade (I.E. the RAID 60 Fibre Channel SAN at work would be considered "commercial grade")  Theoritical throughput on SATAII should be around 38MB/s---I don't get even close to these values in Windows (XP, Vista, Server 2003, and Server 2008 are all I've observed).
In fact, I have a Vista x86-64 workstation that has a WD Caviar Green 2TB HDD and the highest throughput I've been able to sustain was about 21MB/s.

I was getting about 50MB/s on my copy from one hard drive to another on a setup pretty close to yours, posted on the last page. Both hard drives were WD Caviar models on SATA 3Gb/s. Maybe yours should be a little faster, but it doesn't sound like you're seeing the really terrible transfer speeds that some of these guys are seeing. FWIW, I calculated theoretical throughput on SATA as 384MB/s.

---

### Post by Shawn Reist on 2009-07-25
Hello,

I still consider myself a newbie...

so to summarize from a newbie point of view...

2 different issues

transfers to USB devices
transfers to SATA drives

transfers start out fast... (maybe) and get slower..

Possible short term fixes...
[INDENT]Disabling legacy USB support
Revert to older version of Ubuntu or change flavour.
Flash BIOS (does not work for all)[/INDENT]

To me it sounds like a conflict in the programming, most people report fast starts to the data transfers and then they get slower... for some to the extreme.

Does anyone know what programs specifically control data transfers to devices and the updates that have occurred in sequence.

What are the differences in how data was transfered in older versions of Ubuntu compared to now (is this possible)?

There should be a way to track this problem down and figure out a way to fix it rather then just bitching about it.

I have an older system that still has a HD with 7x on it..  what logs or commands should I use to help track this problem down.

---

### Post by niw_uk1964 on 2009-07-28
I have been suffering from this problem of slow file transfers on an 8GB Phenom II x4 940 system running on a Gigabyte 790-ds4h motherboard. Transfers to a USB2.0 external drive were initially quick-ish at around 35MB/s and then slowed to a crawl at around 5MB/s.

Whilst I was waiting for this to complete...hours I might add (!) I decided I would install the proprietary ATI video driver for my board (it uses a Radeon 3200 IIRC)....once I had done that my transfer speed jumped back up to 35MB/s where it has stayed since.

I was already running a generic kernel....most bizarre!

I don't understand it and being a bit of a Linux novice I am unlikely to. I can only relate my observations.

---

### Post by Jags_FL on 2009-07-29
I'm also having the same issue of extremely slow USB transfer speeds in Jaunty 9.04 on two of my machines (a lappy & a desktop).

As many have stated, 2+ GB files starts around 25 MB and very quickly crawl downs to around 3.3 MB. 

I know this thread is in "x86 64-bit Users" forum but the systems I'm having the issue are both 32-bit intel-nvidia machines. Both are multi-boot systems and I do get 30+ MB speed on Windows 7 on both of 'em.

I've almost read the entire thread and many others, has anyone found any definitive solution? Many thanks.

---

### Post by Arup on 2009-07-29
> **Jags_FL said:**
> I'm also having the same issue of extremely slow USB transfer speeds in Jaunty 9.04 on two of my machines (a lappy & a desktop).

As many have stated, 2+ GB files starts around 25 MB and very quickly crawl downs to around 3.3 MB. 

I know this thread is in "x86 64-bit Users" forum but the systems I'm having the issue are both 32-bit intel-nvidia machines. Both are multi-boot systems and I do get 30+ MB speed on Windows 7 on both of 'em.

I've almost read the entire thread and many others, has anyone found any definitive solution? Many thanks.

Try disabling USB Legacy support in BIOS, works for many.

---

### Post by GuiGuy on 2009-07-29
> **Shawn Reist said:**
> 
[INDENT]Disabling legacy USB support

Whilst this seems to fix transfer speeds, it has an unwanted side effect in that other USB devices may not work. For example, when I tried it my DVICO DBTV PCI dual tuner card stopped working. One of the tuners is USB 2.0 dependent.

---

### Post by GuiGuy on 2009-07-29
> **Jags_FL said:**
> 
I've almost read the entire thread and many others, has anyone found any definitive solution? Many thanks.

Change distro. I went Fedora, which performs well.

---

### Post by mattmull on 2009-07-29
I was wondering if anyone else is using whole disk encryption with 9.04?

I have a Dell latitude, and spent the better part of 2 weeks trying different things to increase disk performance, but whenever I did anything disk intensive (like a large disk copy or compiling), my machine would almost become unusable.  My sata/ahci rates would start out around ~30mbs, but eventually stabilize around 20mbs.  I'm wondering if it's a combo of the poor disk i/o performance with 9.04 plus encryption.

When I rolled back to 8.04 w/ encryption, my disk rate jumped back up to 80mbs.  I really liked some of the improvements in 9.04, but it was borderline unusable while running stuff like VMware.

---

### Post by _khAttAm_ on 2009-07-31
^when I tried backup with Remastersys, my processor hit the 70 degrees C mark and I shut it down immediately.

I have tried every possible option here, upgraded to 2.6.30. Has anyone tried 2.6.31 or +? Did it help?

I think I should finally switch to a new OS... I will go Debian Lenny. Or should I go Linuxmint? Do they share the same problem? I want a Debian based distro because I love the debian package management. I will miss Ubuntu though. By the way, has anyone with this problem upgraded to 9.10? Did it help?

---

### Post by GuiGuy on 2009-07-31
> **_khAttAm_ said:**
> 
I think I should finally switch to a new OS... I will go Debian Lenny. Or should I go Linuxmint? Do they share the same problem? I want a Debian based distro because I love the debian package management. I will miss Ubuntu though. By the way, has anyone with this problem upgraded to 9.10? Did it help?

[RANT]
Agree. Change! I have had up to the gills with Ubuntu. These days it seems every update breaks something and the things that really need attention, like the SATA, USB and ATA:Software reset Failure bugs never get a mention. 

I went with Fedora on my main desktop and mythdora to replace mythbuntu on my home entertainment system backend. No regrets. Conversely, on one of the mythbuntu frontends in our house [this happened ]("http://ubuntuforums.org/showthread.php?t=1226891")on an upgrade yesterday. The frontend will be receiving a dose of mythdora this weekend.

As you say, one feels a little guilty leaving Ubuntu behind. But when I think about the recent frustrations I think I can live with the guilt. 
[/RANT]

There, I feel much better now...

---

### Post by coogur on 2009-07-31
I didn't get the chance to read the whole discussion however, I do remember reading somewhere that if AHCI is not enabled in the BIOS, SATA works in IDE emulation.. maybe this has an impact on speed performance on SATA transfers and USB storage devices as the data funnels through the IO controller.  I ended up disabling USB legacy and enabled AHCI, I am getting constant 30MB/s transfers between SATA partitions..  USB transfers is not fast.. I wasn't aware that this issue was related to Ubuntu.
 
Linux kernel 2.6.19+ supports AHCI as per the AHCP wiki.
[http://en.wikipedia.org/wiki/Advanced_Host_Controller_Interface](http://en.wikipedia.org/wiki/Advanced_Host_Controller_Interface)

---

### Post by Arup on 2009-07-31
Gui Guy, 

While I fully understand your situation, Ubuntu works for most of us here and works well, in most cases it works better than other distros and is far easier and simpler to setup. Fedora has come a long way with being desktop friendly but it still has miles to go before it comes close to Ubuntu in terms of ease of use, software setup etc. Try to find instructions on Fedora forum for compliling or a ppa for a mplayer with vdpau and you will see my point. Fedora's package management is still a joke, its quirky at best and depending on persons, many who tried Fedora 11 went back to Ubuntu because they had issues with it. In the end you use what suits you but then suggesting Fedora is not the solution. In my case even with backports enabled, not one single upgrade has caused any issues. You can see I use OSS4 for sound and compile my own nvidia and mplayer. Same goes for the other PCs I have installed Ubuntu in. I am glad to see you took my advice and stuck to Linux and Fedora worked out for you, after all its still Linux all the way. When you have time and feel like going back to Debian, try Sidux, its far more cutting edge than Fedora ever will be and you might be pleseantly surprised with the performance you get.

---

### Post by GuiGuy on 2009-07-31
> **coogur said:**
> I didn't get the chance to read the whole discussion however, I do remember reading somewhere that if AHCI is not enabled in the BIOS, SATA works in IDE emulation.. maybe this has an impact on speed performance on SATA transfers and USB storage devices as the data funnels through the IO controller.  I ended up disabling USB legacy and enabled AHCI, I am getting constant 30MB/s transfers between SATA partitions..  USB transfers is not fast.. I wasn't aware that this issue was related to Ubuntu.
 
Linux kernel 2.6.19+ supports AHCI as per the AHCP wiki.
[http://en.wikipedia.org/wiki/Advanced_Host_Controller_Interface](http://en.wikipedia.org/wiki/Advanced_Host_Controller_Interface)

That's understood. But when AHCI is enabled many of us with AMD CPU boards get the wonderful [ATA: software reset failed bug]("https://bugs.launchpad.net/bugs/285392") which locks the system on boot. I am really, really starting to wonder about the future viability of Linux.

---

### Post by GuiGuy on 2009-07-31
> **Arup said:**
> Gui Guy, 

While I fully understand your situation, Ubuntu works for most of us here and works well, in most cases it works better than other distros and is far easier and simpler to setup.

I suggest a little reading of the launchpad bug list will give a better insight just how pathetically buggy linux can be, especially in the ubuntu guise. 

I accept that it works for many of you, so good luck. The fact remains there are severe, long term bugs that affect some very common and modern hardwares. I'm talking CPUs and motherboards.  Those bugs are no closer to being resolved, AFAIK, then they were when first raised. The SATA bug goes back over a year. The ATA software reset bug started with Ubuntu 9.04. 

Notably
[https://bugs.launchpad.net/bugs/285392](https://bugs.launchpad.net/bugs/285392)
[https://bugs.launchpad.net/bugs/119730](https://bugs.launchpad.net/bugs/119730)

This does not enhance the reputation of Linux and in the end has those affected looking at alternatives, perhaps even glancing back at Windows and maybe experimenting with Win7. I certainly am.

---

### Post by niw_uk1964 on 2009-08-01
I've enabled AHCI mode and disabled USB legacy mode in the bios.

Things have improved somewhat.

I am getting consistent 70MB/s between various SATA drives. From SATA to USB2 I am getting 36MB/s.

I am happy with this. Now I need to see if I can sort out the frequent pauses I am getting with Firefox when the system just stops responding for seconds at a time.

I get the ATA software reset bug happening in either modes when booting. Is the pausing I experience above likely to be related to this?

---

### Post by Arup on 2009-08-01
> **GuiGuy said:**
> I suggest a little reading of the launchpad bug list will give a better insight just how pathetically buggy linux can be, especially in the ubuntu guise. 

I accept that it works for many of you, so good luck. The fact remains there are severe, long term bugs that affect some very common and modern hardwares. I'm talking CPUs and motherboards.  Those bugs are no closer to being resolved, AFAIK, then they were when first raised. The SATA bug goes back over a year. The ATA software reset bug started with Ubuntu 9.04. 

Notably
[https://bugs.launchpad.net/bugs/285392](https://bugs.launchpad.net/bugs/285392)
[https://bugs.launchpad.net/bugs/119730](https://bugs.launchpad.net/bugs/119730)

This does not enhance the reputation of Linux and in the end has those affected looking at alternatives, perhaps even glancing back at Windows and maybe experimenting with Win7. I certainly am.


In the same sense, go to MS newsgroup and see how many unresolved issues MS has, same goes for Apple, no software is perfect and that includes Linux. Go right ahead and enjoy the virus laden CPU hogging world of Windows 7, you will be back. Do remember, not all on Linux are suffering from SATA or ATA bugs. Its not the end of the world for all of us.

---

### Post by Arup on 2009-08-01
> **niw_uk1964 said:**
> I've enabled AHCI mode and disabled USB legacy mode in the bios.

Things have improved somewhat.

I am getting consistent 70MB/s between various SATA drives. From SATA to USB2 I am getting 36MB/s.

I am happy with this. Now I need to see if I can sort out the frequent pauses I am getting with Firefox when the system just stops responding for seconds at a time.

I get the ATA software reset bug happening in either modes when booting. Is the pausing I experience above likely to be related to this?


Can you tell me what video driver you are using? If its 180.44 for nvidia, it has issues with FF.

---

### Post by niw_uk1964 on 2009-08-01
See below re. video driver. It's a Radeon 3300 igp on a Gigabyte GA-MA790GP-DS4H. I am using the ATI proprietary driver.

Sadly I am having to use my Windows machine now because my system has become too unstable with AHCI mode enabled.

> **niw_uk1964 said:**
> I have been suffering from this problem of slow file transfers on an 8GB Phenom II x4 940 system running on a Gigabyte 790-ds4h motherboard. Transfers to a USB2.0 external drive were initially quick-ish at around 35MB/s and then slowed to a crawl at around 5MB/s.

Whilst I was waiting for this to complete...hours I might add (!) I decided I would install the proprietary ATI video driver for my board (it uses a Radeon 3200 IIRC)....once I had done that my transfer speed jumped back up to 35MB/s where it has stayed since.

I was already running a generic kernel....most bizarre!

I don't understand it and being a bit of a Linux novice I am unlikely to. I can only relate my observations.

---

### Post by niw_uk1964 on 2009-08-01
> **niw_uk1964 said:**
> See below re. video driver. It's a Radeon 3300 igp on a Gigabyte GA-MA790GP-DS4H. I am using the ATI proprietary driver.

Sadly I am having to use my Windows machine now because my system has become too unstable with AHCI mode enabled.

I've turned off AHCI mode and stablity has returned. Firefox is stable again. What I forget to mention is that with AHCI enabled FF was also forgetting passwords. With AHCI off it's remembering them again!

Disk write speeds have dropped to 50-55MB/s (SATA) and 22-25MB/s (USB2)


After my initial approval of Ubuntu 9.04 64-bit it's all a bit disappointing. I am coming across too many problems with this distro and I can feel a move back to Windows coming on simply because the overall performance under 9.04 is just too poor. :(

I don't want to try another distro cos I run 9.04 netbook remix on my Dell Mini 9...and it's just fine on that.

---

### Post by niw_uk1964 on 2009-08-01
Right...I decided to just vape the partition and start from scratch with AHCI enabled and a fresh install.

Everything is running just fine atm and I am getting 85MB/s on SATA and just under 40MB/s on USB2.

No pauses or hangs and I am thrashing my machine with 3 virtual machines running on a gig of RAM each..all doing disk writes too.

---

### Post by _khAttAm_ on 2009-08-02
> **coogur said:**
> I didn't get the chance to read the whole discussion however, I do remember reading somewhere that if AHCI is not enabled in the BIOS, SATA works in IDE emulation.. maybe this has an impact on speed performance on SATA transfers and USB storage devices as the data funnels through the IO controller.  I ended up disabling USB legacy and enabled AHCI, I am getting constant 30MB/s transfers between SATA partitions..  USB transfers is not fast.. I wasn't aware that this issue was related to Ubuntu.
 
Linux kernel 2.6.19+ supports AHCI as per the AHCP wiki.
[http://en.wikipedia.org/wiki/Advanced_Host_Controller_Interface](http://en.wikipedia.org/wiki/Advanced_Host_Controller_Interface)

My Gigabyte GA-G31M-S2L does not have any option in the BIOS saying AHCI. However, I changed the "On-Chip SATA Mode" to Enhanced as suggested in one of the forums. I also disabled USB legacy support. Still, I'm getting USB transfer rate of 1.4MBps, which is terrible. Starts good and slowly degrades.. reaches to 300KBps while copying a 700MB file. The device works well on another Windows box. I don't have Windows on mine to test it.

> **Arup said:**
> Gui Guy, 

While I fully understand your situation, Ubuntu works for most of us here and works well, in most cases it works better than other distros and is far easier and simpler to setup. Fedora has come a long way with being desktop friendly but it still has miles to go before it comes close to Ubuntu in terms of ease of use, software setup etc. Try to find instructions on Fedora forum for compliling or a ppa for a mplayer with vdpau and you will see my point. Fedora's package management is still a joke, its quirky at best and depending on persons, many who tried Fedora 11 went back to Ubuntu because they had issues with it. In the end you use what suits you but then suggesting Fedora is not the solution. In my case even with backports enabled, not one single upgrade has caused any issues. You can see I use OSS4 for sound and compile my own nvidia and mplayer. Same goes for the other PCs I have installed Ubuntu in. I am glad to see you took my advice and stuck to Linux and Fedora worked out for you, after all its still Linux all the way. When you have time and feel like going back to Debian, try Sidux, its far more cutting edge than Fedora ever will be and you might be pleseantly surprised with the performance you get.
Well let me add my experience. I have tried Opensuse 11 and the package management is worst I can imagine. Whenever I wanted to upgrade, I'd have to cross my fingers and hope it completed. There is no room for large update, because of slow internet connection and frequent power cuts at my place. I know it is my problem but Ubuntu first downloads the all the debs and when they are downloaded, installs it unlike OpenSuse, which downloads a package, installs it, deletes it (I can't back it up so I cn give to a frend of mine who does not have internet) and then downloads the next. Now what happens is, when it is interrupted, some new packages are installed and their dependencies are yet to be installed. That leaves the system broken. Fedora 10 was no better with package management (thats the last version of Fedora I tried). So I have come to a conclusion that no rpm-based system can compete with Debian based systems in terms of package management. I may be wrong though. I don't want my system broken when I restart after an update. And I have never faced that with Ubuntu.

Has anyone experienced this with Lenny? Or Linuxmint..(I guess Linuxmint has it since it has been derived from Ubuntu, but Still asking)

---

### Post by _khAttAm_ on 2009-08-02
> **niw_uk1964 said:**
> Right...I decided to just vape the partition and start from scratch with AHCI enabled and a fresh install.

Everything is running just fine atm and I am getting 85MB/s on SATA and just under 40MB/s on USB2.

No pauses or hangs and I am thrashing my machine with 3 virtual machines running on a gig of RAM each..all doing disk writes too.
What happened before reinstall? did you try enabling AHCI? Did it improve things? Do you think Fresh install with AHCI enabled will do the trick?

---

### Post by niw_uk1964 on 2009-08-02
> **_khAttAm_ said:**
> What happened before reinstall? did you try enabling AHCI? Did it improve things? Do you think Fresh install with AHCI enabled will do the trick?

First time round I enable AHCI after install which, perhaps with hindsight, was not a good thing to do.

Second time round I enable AHCI and then performed a clean install after vaping my partitions.

It is still running beautifully. Very fast and responsive now. I'm much happier with it.

---

### Post by niw_uk1964 on 2009-08-02
> **_khAttAm_ said:**
> 
Has anyone experienced this with Lenny? Or Linuxmint..(I guess Linuxmint has it since it has been derived from Ubuntu, but Still asking)

I am running a Mint vm atm the moment (I'm positing from FF within my Mint VM, running on top of Ubuntu 9.04 64-bit) and it's not bad at all. It uses Synaptic for package management as does Ubuntu.

---

### Post by _khAttAm_ on 2009-08-02
> **niw_uk1964 said:**
> I am running a Mint vm atm the moment (I'm positing from FF within my Mint VM, running on top of Ubuntu 9.04 64-bit) and it's not bad at all. It uses Synaptic for package management as does Ubuntu.
Thank you. 
What about the bug? Does it exist in LinuxMint?

I'm downloading Lenny.

---

### Post by niw_uk1964 on 2009-08-03
> **_khAttAm_ said:**
> Thank you. 
What about the bug? Does it exist in LinuxMint?

I'm downloading Lenny.

It's not really directly comparable to be honest. A virtual machine is emulated hardware. The bug doesn't show up, but I don't think you can use that as an indicator that it won't show up in Mint.

---

### Post by Arup on 2009-08-04
> **niw_uk1964 said:**
> First time round I enable AHCI after install which, perhaps with hindsight, was not a good thing to do.

Second time round I enable AHCI and then performed a clean install after vaping my partitions.

It is still running beautifully. Very fast and responsive now. I'm much happier with it.

Your case truly defines its not a Ubuntu issue but an issue which could be related to BIOS, transfer modes etc. So far not a single Intel manufactured board has given me any grief but few of ASUS and MSI boards with AMD have.

---

### Post by Anthon berg on 2009-08-04
> **Arup said:**
> Your case truly defines its not a Ubuntu issue but an issue which could be related to BIOS, transfer modes etc.

Sorry, can't agree with that.

---

### Post by Arup on 2009-08-04
> **Anthon berg said:**
> Sorry, can't agree with that.

Agree or not, its not an universal issue but I can relate to those who are facing the issue.

---

### Post by speedkreature on 2009-08-04
FYI, I'm running Kubuntu 9.04 x86-64 liveCD right now and I'm seeing transfers in excess of 100MB's from my /home drive (sdc1).

So far my peak transfer, as I'm trying to get my files off the home drive for a clean install, is around 250MB/s which it holds for only short periods of time (a second or two).  I have lots of small and lots of very large (> 2GB) files and when it hits the larger files (say 100MB+) it does slow to around 30MB/s.  So while transfer rates are fluctuating wildly, I am seeing much higher transfer rates than before.  I don't even get this in Windows Vista (17-28MB/s).
I've posted my hardware already but here it is again since there have been some changes...

Gigabyte GA-MA790XT-UD4P (JMicron 20360/20363 + ATI SB700/800 SATA Controllers)
    AMD Phenom II X3 710
        8GB DDR2
        GeForce 8400 GS
        Intel SSDSA2MH08 80GB SSD (/dev/sda, ext3, /)
        Gigabyte i-RAM 1GB RAM Disk (/dev/sdb, swap)
        2x DVD/RW
        WD WD2002FYPS-0 2TB HDD (/dev/sdc, ext4, /home)

The disks on the ATI SATA controller transfer hella fast (>100MB/s).  The disk on the JMicron SATA controller peak at about 40MB/s

/dev/sda:
 Timing cached reads:   7432 MB in  2.00 seconds = 3717.88 MB/sec
 Timing buffered disk reads:  726 MB in  3.00 seconds = 241.70 MB/sec
ubuntu@ubuntu:~$ sudo hdparm -tT /dev/sdb

/dev/sdb:
 Timing cached reads:   7424 MB in  2.00 seconds = 3713.96 MB/sec
 Timing buffered disk reads:  312 MB in  3.01 seconds = 103.74 MB/sec
ubuntu@ubuntu:~$ sudo hdparm -tT /dev/sdc

/dev/sdc:
 Timing cached reads:   7456 MB in  2.00 seconds = 3729.81 MB/sec
 Timing buffered disk reads:  320 MB in  3.01 seconds = 106.44 MB/sec

There's my 2 cents.

---

### Post by niw_uk1964 on 2009-08-04
That's very impressive performance.

My quote figures are with a test set of files:

2 x 700MB and 2 x 1.5GB. I expect to see significantly lower write rates with multitudes of small files.

---

### Post by speedkreature on 2009-08-05
Well, Kubuntu 9.04 x86-64 is installed and performance went down the toilet.  I'm no better off now than when I was running Ubuntu 9.04--but no worse either.  I didn't really expect a performance difference, just wanted to play with KDE4 (It's shiny!).   I don't plan on abandoning Ubuntu because of this issue, though.
I still maintain speeds better than many people in this thread (around 30MB/s) but it's dismal compared to where it should be.

I think this conclusively shows this is not directly a BIOS problem as BIOS settings have not changed.  The only differences between a LiveCD and and a post-install system is a writable root file system and data is on a hard drive vs a RAM disk.

I was actually content with drive performance before I stumbled across this thread...Now I'm just hoping this gets fixed stat.

---

### Post by GuiGuy on 2009-08-05
> **speedkreature said:**
> 
I think this conclusively shows this is not directly a BIOS problem as BIOS settings have not changed.  The only differences between a LiveCD and and a post-install system is a writable root file system and data is on a hard drive vs a RAM disk.

Demonstrably it is a ubuntu issue. I moved to Fedora on my main desktop (AMD AM2 X2, ASUS mobo), and the performance improvement on USB and SATA is dramatic. 

Anyway, enough said before the fanboys come back out.

---

### Post by Arup on 2009-08-05
Definitely Ubuntu and AMD issue, Fedora fanboi notwithstanding ;)

---

### Post by _khAttAm_ on 2009-08-05
I moved to Debian Lenny with Gnome and it is a lot faster in boot up and performance. The applications are older and there are some problems (not this) but there are workarounds. The kernel is older 2.26, and maybe (or maybe not) thats the reason the bug is not there. I have installed synaptic for package management. I have changed nautilus settings to make it feel like Ubuntu, that I was used to. So far, it is good.

---

### Post by Arup on 2009-08-05
> **_khAttAm_ said:**
> I moved to Debian Lenny with Gnome and it is a lot faster in boot up and performance. The applications are older and there are some problems (not this) but there are workarounds. The kernel is older 2.26, and maybe (or maybe not) thats the reason the bug is not there. I have installed synaptic for package management. I have changed nautilus settings to make it feel like Ubuntu, that I was used to. So far, it is good.

It is a kernel issue for 2.6.28 as later 29 and 30 don't seem to exhibit this problem. Fedora 11 is on 29 and sidux is on 30 and both seem to have no such issues.

---

### Post by darco on 2009-08-05
I am running the .30 kernel...w/two flash drives, 1 set to ntfs and the other is fat32, the fat32 bombs out. With the ntfs drive, I was able to transfer a 4gig file in about 5mins....I think my lowest speed was around 14mb per sec.

darco

*ps, enable ACHI and it made no difference

---

### Post by niw_uk1964 on 2009-08-06
I've been doing some large scale file management and I am getting SATA-SATA transfers in excess of 90MB/s. I really don't know what to suggest for you guys. FWIW my Kernel is 2.6.28-14.

I got much improved performance by vaping my partition, enabling AHCI mode and then re-installing from scratch.

---

### Post by Arup on 2009-08-06
SATA/SATA is no issue here, I get close to 130MB/s sometimes with my spinpoints, its SATA to USB thats the bottleneck.

---

### Post by GuiGuy on 2009-08-06
> **niw_uk1964 said:**
>  enabling AHCI mode and then re-installing from scratch.

I may have already mentioned it, but due to [another bug]("https://bugs.launchpad.net/bugs/285392") enabling AHCI prevents the (AMD based ASUS M3A, M2H boards) machines from booting. 

Again, I don't see the problem on the latest stable Fedora. 

Cheers

---

### Post by Arup on 2009-08-06
It surely looks like AMD issue rather than Ubuntu or AMD and Kernel 2.6.28 issue as Debian users are experiencing it as well.

---

### Post by _khAttAm_ on 2009-08-06
> **Arup said:**
> It is a kernel issue for 2.6.28 as later 29 and 30 don't seem to exhibit this problem. Fedora 11 is on 29 and sidux is on 30 and both seem to have no such issues.

I upgraded to .29 and then to .30 and even to .31rc in Ubuntu before I made the switch. And I had problems with them too.

---

### Post by _khAttAm_ on 2009-08-06
> **Arup said:**
> It surely looks like AMD issue rather than Ubuntu or AMD and Kernel 2.6.28 issue as Debian users are experiencing it as well.

am on Intel (board manufacturer: Giga-Byte) here and faced the problem..

---

### Post by GuiGuy on 2009-08-06
> **Arup said:**
> It surely looks like AMD issue rather than Ubuntu or AMD and Kernel 2.6.28 issue as Debian users are experiencing it as well.

I know I am not the sharpest tool in the shed, but given the same hardware, the problem did not exist on pre-Jaunty ubuntu(64) nor am I seeing it in Fedora. So, how is it AMD's fault?

---

### Post by Arup on 2009-08-06
> **GuiGuy said:**
> I know I am not the sharpest tool in the shed, but given the same hardware, the problem did not exist on pre-Jaunty ubuntu(64) nor am I seeing it in Fedora. So, how is it AMD's fault?

If you read through the posts, there are those who have installed Lenny with older kernel and have suffered your fate. In that case, why did you have to go to Fedora? Hardy would have done well and you would still be on Ubuntu. Fedora doesn't hold a candle to Ubuntu's convenience and package management.

It seems you are hell bent on pinning it on Ubuntu when many don't suffer your fate. Every opportunity you get, you peddle Fedora, maybe you really should be in Fedora forum instead of Ubuntu.

---

### Post by darco on 2009-08-09
Just did some testing.....
I copied a single file (4.4gigs)
Sata partition (ntfs) to Sata partition (ntfs) 2:06 mins
Same file Sata (ext3) to Sata (ntfs) 1:19 min
Same file Sata (ext3) to USB External HDD (ntfs) 2mins
Same file Sata (ext3) to USB Flash drive(ntfs) 30mins!!!

Running Mint 7 x64 (Ubuntu 9.04, 2.6.30kernel, Intel Q6600, Intel Chipset,usb legacy off, AHCI enabled)

darco

---

### Post by Anthon berg on 2009-08-09
> **Arup said:**
> It seems you are hell bent on pinning it on Ubuntu when many don't suffer your fate. Every opportunity you get, you peddle Fedora, maybe you really should be in Fedora forum instead of Ubuntu.

Maybe you should speak carefully about things you don't have any experience with.

---

### Post by Herstjori on 2009-08-10
While using 8.10 Intrepid I had no real problems transfer to my external USB SATA HDD was on avg about 30MB since changing to 9.04 Jaunty I can't get any faster than 4MB. I don't have any issues with transfers not completing just the speed of them.

Most of what has been suggested in these pages and launchpad links are too advanced for me.

Does anyone have any suggestions for a noob please?

---

### Post by n3had on 2009-08-10
I am using ubuntu 9.04 

specs

AMD X24200+
ASUS M2N-VM DH 

So is this issue realted to AMD/ASUS only? or others are facing it too??

THE CPU goes really high when copying anything to flashdrives.

---

### Post by Arup on 2009-08-10
> **Anthon berg said:**
> Maybe you should speak carefully about things you don't have any experience with.

So should you when you try and generalize it all and condemn a legitimately good distro. Just because its an exception in your case and some others don't make it the rule. What experience are we exactly talking about here, SATA to USB transfer, I think I have well laid out mine unless you have been selectively blind throughout this whole thread for some reason.

---

### Post by Anthon berg on 2009-08-10
> **Arup said:**
> So should you when you try and generalize it all and condemn a legitimately good distro. Just because its an exception in your case and some others don't make it the rule. What experience are we exactly talking about here, SATA to USB transfer, I think I have well laid out mine unless you have been selectively blind throughout this whole thread for some reason.

Go read a book on logic. You're stating things about mine and others' attempts to fix bugs with OUR computers, that you have NO IDEA about! State your own experience, but you CANNOT say anything about what is happening in OTHER PEOPLE'S COMPUTERS.

---

### Post by Arup on 2009-08-10
> **Anthon berg said:**
> Go read a book on logic. You're stating things about mine and others' attempts to fix bugs with OUR computers, that you have NO IDEA about! State your own experience, but you CANNOT say anything about what is happening in OTHER PEOPLE'S COMPUTERS.

You go read a book on rationale, just because you and few others have this issue don't mean its happening to all, dont' spread FUD about the OS just because your hardware or config don't but it. Can you say whats happening in other's PC? How about mine and thousands of others who have absolutely no such issues. Anyways why sit in Ubuntu forum and bitch about it. Do what GUI Guy did, at least he tried out another distro and has found satisfaction there, maybe Ubuntu is not for you, you really should use MS instead. If you really think this was a serious issue crippling Ubuntu Jaunty, don't you think Canonical which has a solid rep of having one of the fastest turn out on patches would have taken action. Either by patching the Kernel or upgrading it to a newer version. The attempts I made to fix bugs at least worked out for some, what have you done so far apart from moan, fret and bitch?

---

### Post by n3had on 2009-08-10
> **Arup said:**
> You go read a book on rationale, just because you and few others have this issue don't mean its happening to all, dont' spread FUD about the OS just because your hardware or config don't but it. Can you say whats happening in other's PC? How about mine and thousands of others who have absolutely no such issues. Anyways why sit in Ubuntu forum and bitch about it. Do what GUI Guy did, at least he tried out another distro and has found satisfaction there, maybe Ubuntu is not for you, you really should use MS instead. If you really think this was a serious issue crippling Ubuntu Jaunty, don't you think Canonical which has a solid rep of having one of the fastest turn out on patches would have taken action. Either by patching the Kernel or upgrading it to a newer version. The attempts I made to fix bugs at least worked out for some, what have you done so far apart from moan, fret and bitch?

guys don't fight .. i've been thrashed by a windoze user because of this bug..

---

### Post by Arup on 2009-08-10
> **n3had said:**
> guys don't fight .. i've been thrashed by a windoze user because of this bug..

So now the plot thickens, if Windows is having this issue as well then its got nothing to do with OS but a combo of particular hardware/BIOS and CPU combined with OS to an extent or driver at the most.

---

### Post by n3had on 2009-08-10
> **Arup said:**
> So now the plot thickens, if Windows is having this issue as well then its got nothing to do with OS but a combo of particular hardware/BIOS and CPU combined with OS to an extent or driver at the most.

I tried copying files to usb flash drive on WIndows XP(virtual) no performance issues..

---

### Post by Anthon berg on 2009-08-10
> **n3had said:**
> guys don't fight .. i've been thrashed by a windoze user because of this bug..

Sorry! :( Lost myself.

I'm having problems like this on several Intel Core 2 machines. Most have Gigabyte boards.

The "magic pill" for me has been to install a mainline kernel, though not everybody is happy with that :) Did you try this?

---

### Post by Anthon berg on 2009-08-10
> **Arup said:**
> So now the plot thickens, if Windows is having this issue as well then its got nothing to do with OS but a combo of particular hardware/BIOS and CPU combined with OS to an extent or driver at the most.

Being "trashed" by a Windows user means that the Windows DOES NOT have the problem.

Speak about your own experience, please.

---

### Post by Anthon berg on 2009-08-10
> **n3had said:**
> I tried copying files to usb flash drive on WIndows XP(virtual) no performance issues..

Whoa, that is pretty interesting. Clever thing to try. Let me get this straight, if you have Linux copy to / from the USB drive, you get slow speed, but in the same linux a Windows virtual machine is OK for speed?

---

### Post by Arup on 2009-08-10
> **Anthon berg said:**
> Being "trashed" by a Windows user means that the Windows DOES NOT have the problem.

Speak about your own experience, please.

Well you know whats my experience and yours is certainly not the universal by any means. Windows doesn't have a problem, well M$ fanboi, its a known fact that Windows chokes on big file transfer more than any other OS. Not only that, we have cachemem and cleanmem utilities to force Windows to release the memory after large file transfer, this bug continues even till today and even a turncoat like Russinovich admits that in his blog and makes a utility for it.

---

### Post by n3had on 2009-08-10
> **Anthon berg said:**
> Sorry! :( Lost myself.

I'm having problems like this on several Intel Core 2 machines. Most have Gigabyte boards.

The "magic pill" for me has been to install a mainline kernel, though not everybody is happy with that :) Did you try this?

thx for the response.. mainline kernel? noob here. How am i supposed to install it? which version?

---

### Post by n3had on 2009-08-10
> **Anthon berg said:**
> Whoa, that is pretty interesting. Clever thing to try. Let me get this straight, if you have Linux copy to / from the USB drive, you get slow speed, but in the same linux a Windows virtual machine is OK for speed?

it seems like that i was trying to copy a 1 gig file and i couldn't calculate the transfer speed on virtual machine. But it was pretty fast compared to host machine where it would stall to 800kbps and system non responsive.

---

### Post by Anthon berg on 2009-08-10
> **n3had said:**
> thx for the response.. mainline kernel? noob here. How am i supposed to install it? which version?

Here's a wiki page:
[https://wiki.ubuntu.com/KernelTeam/MainlineBuilds?action=show&redirect=KernelMainlineBuilds](https://wiki.ubuntu.com/KernelTeam/MainlineBuilds?action=show&redirect=KernelMainlineBuilds)

I assume you have Ubuntu 9.04. Then I'd try this version, v. 2.6.28.10:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.28.10/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.28.10/)

On my personal machine I have Ubuntu 8.10, and I have to use kernel 2.6.27.

The linux-image file should be enough. Do you have 32-bit or 64-bit?
If 32-bit, this one: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.28.10/linux-image-2.6.28-02062810-generic_2.6.28-02062810_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.28.10/linux-image-2.6.28-02062810-generic_2.6.28-02062810_i386.deb)
If 64-bit, this one: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.28.10/linux-image-2.6.28-02062810-generic_2.6.28-02062810_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.28.10/linux-image-2.6.28-02062810-generic_2.6.28-02062810_amd64.deb) (this is what we use at work)

Just download the .DEB and double-click it, enter password and install, and reboot. The system should boot the new kernel by default. You can verify after rebootin by typing "uname -a" in a terminal console. If it says "Linux 2.6.28.10-something-**generic**", you have booted up with the mainline kernel.

Now be warned, the mainline kernel is missing some patches, so you might have problems with video drivers, and you may lose sound in some cases, so I'm not necessarily promoting this as a permanent fix to your problems, but it certainly worked for me. (Although it didn't work for someone else in the thread :( ... Really weird stuff going on here.)

If it doesn't work well for you, you can remove the new package in Synaptic, or just select the old kernel in GRUB when you reboot. Feel free to PM me if you have any trouble with this, it's not too hard to remove this kernel, but it's not immediately obvious how you do it, so I'll be happy to help if there's anything.

---

### Post by Arup on 2009-08-10
> **n3had said:**
> it seems like that i was trying to copy a 1 gig file and i couldn't calculate the transfer speed on virtual machine. But it was pretty fast compared to host machine where it would stall to 800kbps and system non responsive.

Before you do all that, just a simple suggestion, see if there is a BIOS upgrade, then try turning off USB Legacy mode in BIOS and enable AHCI mode for HDD if you can, this has worked for some and has done good to my Phenom PC, your results may vary but its a easier and better solution than the kernel upgrade.

---

### Post by Anthon berg on 2009-08-10
> **Arup said:**
> Before you do all that, just a simple suggestion, see if there is a BIOS upgrade, then try turning off USB Legacy mode in BIOS and enable AHCI mode for HDD if you can, this has worked for some and has done good to my Phenom PC, your results may vary but its a easier and better solution than the kernel upgrade.

+1 on that, good advice. All of this helped on my machine - only perform the kernel [s]upgrade[/s] sidegrade if this DOESN'T work.

The desired, and acheivable, result is full speed on all devices, and most importantly no system stalling at all when you're copying.

---

### Post by Arup on 2009-08-10
> **Anthon berg said:**
> +1 on that, good advice. All of this helped on my machine - only perform the kernel [s]upgrade[/s] sidegrade if this DOESN'T work.

The desired, and acheivable, result is full speed on all devices, and most importantly no system stalling at all when you're copying.

Thank you Mr. Berg.

---

### Post by Anthon berg on 2009-08-10
> **Arup said:**
> Thank you Mr. Berg.

:) Sorry about the nasty words. And p.s., I hate Windows with a passion, and don't have any real interest in dropping Ubuntu. Let's hope this all gets figured out.

---

### Post by n3had on 2009-08-10
> **Anthon berg said:**
> Here's a wiki page:
[https://wiki.ubuntu.com/KernelTeam/MainlineBuilds?action=show&redirect=KernelMainlineBuilds](https://wiki.ubuntu.com/KernelTeam/MainlineBuilds?action=show&redirect=KernelMainlineBuilds)

I assume you have Ubuntu 9.04. Then I'd try this version, v. 2.6.28.10:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.28.10/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.28.10/)

On my personal machine I have Ubuntu 8.10, and I have to use kernel 2.6.27.

The linux-image file should be enough. Do you have 32-bit or 64-bit?
If 32-bit, this one: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.28.10/linux-image-2.6.28-02062810-generic_2.6.28-02062810_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.28.10/linux-image-2.6.28-02062810-generic_2.6.28-02062810_i386.deb)
If 64-bit, this one: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.28.10/linux-image-2.6.28-02062810-generic_2.6.28-02062810_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.28.10/linux-image-2.6.28-02062810-generic_2.6.28-02062810_amd64.deb) (this is what we use at work)

Just download the .DEB and double-click it, enter password and install, and reboot. The system should boot the new kernel by default. You can verify after rebootin by typing "uname -a" in a terminal console. If it says "Linux 2.6.28.10-something-**generic**", you have booted up with the mainline kernel.

Now be warned, the mainline kernel is missing some patches, so you might have problems with video drivers, and you may lose sound in some cases, so I'm not necessarily promoting this as a permanent fix to your problems, but it certainly worked for me. (Although it didn't work for someone else in the thread :( ... Really weird stuff going on here.)

If it doesn't work well for you, you can remove the new package in Synaptic, or just select the old kernel in GRUB when you reboot. Feel free to PM me if you have any trouble with this, it's not too hard to remove this kernel, but it's not immediately obvious how you do it, so I'll be happy to help if there's anything.

ok i've got v. 2.6.28.15 installed on jaunty64 so u say downgrading linux kernel might fix this issue..

---

### Post by Anthon berg on 2009-08-10
> **n3had said:**
> ok i've got v. 2.6.28.15 installed on jaunty64 so u say downgrading linux kernel might fix this issue..

Ah, yes, AFAIK the 2.6.28-15 numbering that Ubuntu uses, and the 2.6.28.10 version numbering in the mainline kernel, aren't directly compatible. See the dash vs. the dot? AFAIK -15 is the same as .10. The difference is that in the -15 version, there are some extra patches and stuff that the Ubuntu kernel team adds. And even then, you can mix and match kernel versions quite a bit, if the package manager allows the install. For instance, I installed a mainline 2.6.24 on an old machine that had an Ubuntu kernel 2.6.22. So you'll be safe.

---

### Post by n3had on 2009-08-10
> **Anthon berg said:**
> :) Sorry about the nasty words. And p.s., I hate Windows with a passion, and don't have any real interest in dropping Ubuntu. Let's hope this all gets figured out.

i am going to try disabling usb legacy support and i'll report later and how do i enable AHCI mode for HDD? and for the time being plz can you give some pointers how to hate windows passionately. I need to have strong reasons for that. I gotta duel with my WINDOZE buddy.

---

### Post by Anthon berg on 2009-08-10
> **n3had said:**
> i am going to try disabling usb legacy support and i'll report later and how do i enable AHCI mode for HDD? and for the time being plz can you give some pointers how to hate windows passionately. I need to have strong reasons for that. I gotta duel with my WINDOZE buddy.

Hehe ... setting the AHCI stuff is different from board to board, I'd suggest finding out what motherboard you have and downloading the manual. Usually though it's some kind of SATA-something setting that you can set from Disabled to Native to RAID to AHCI. or something like that. Usually it's in the Integrated Peripherals part of the BIOS screen.

Windows? Windows is unnecessarily laggy and has viruses :) It's also full of corner cases and weirdness, once you get down into the plumbing. And the Windows bootloader was made by assholes :D I don't know if it's like that still, but searching for files in Windows used to make my computer nearly unusable. Which is just bad programming in the file search, and in the process scheduler, and in the IO scheduler :) One more thing I also really hate - you can't install Windows from an USB key. Nor can you boot into your Windows installation from one. (At least last time I checked it was so difficult that it was basically impossible. And I'm a computer scientist, for chrissakes!)

---

### Post by n3had on 2009-08-10
> **Anthon berg said:**
> Hehe ... setting the AHCI stuff is different from board to board, I'd suggest finding out what motherboard you have and downloading the manual. Usually though it's some kind of SATA-something setting that you can set from Disabled to Native to RAID to AHCI. or something like that. Usually it's in the Integrated Peripherals part of the BIOS screen.

Windows? Windows is unnecessarily laggy and has viruses :) It's also full of corner cases and weirdness, once you get down into the plumbing. And the Windows bootloader was made by assholes :D I don't know if it's like that still, but searching for files in Windows used to make my computer nearly unusable. Which is just bad programming in the file search, and in the process scheduler, and in the IO scheduler :)

ok i'll check the bios i've got ASUS M2N-VM DH .. i wish i had AMI bios AWARD is slow.. and do u've compiz enabled? I've and that including emerald causing great delay 10 secs after gdm using Nvidia 190.18 64bit drivers . I did check some threads over here. I haven't really got the fix. My windows friend laughs at me when he sees the delay. I told him it maybe the graphic drivers or compiz. But i am not sure.. ok i really don't want to bug u thanks for the help

peace

---

### Post by Anthon berg on 2009-08-10
> **n3had said:**
> ok i'll check the bios i've got ASUS M2N-VM DH .. i wish i had AMI bios AWARD is slow.. and do u've compiz enabled? I've and that including emerald causing great delay 10 secs after gdm using Nvidia 190.18 64bit drivers . I did check some threads over here. I haven't really got the fix. My windows friend laughs at me when he sees the delay. I told him it maybe the graphic drivers or compiz. But i am not sure.. ok i really don't want to bug u thanks for the help

peace

I don't have any compositing stuff enabled as I'm using CUDA, and compositing slows GPGPU things down a tiny little bit. Some machines at work have it enabled and it's OK, no unusual delays or anything - they boot up and start faster than the one Windows machine at the office. So at least I can tell you it's fixable! Good luck!

---

### Post by Arup on 2009-08-10
> **Anthon berg said:**
> :) Sorry about the nasty words. And p.s., I hate Windows with a passion, and don't have any real interest in dropping Ubuntu. Let's hope this all gets figured out.

Well I was at equal fault, no hard feelings. Even if Ubuntu doesn't work out, sidux and arch are using the latest kernel 2.6.30, suggest you check them out as well.

---

### Post by speedkreature on 2009-08-10
For what it's worth, transfer speeds are in the same mid-30's to low-40's MB/sec on Fedora 9, 10, & 11, OpenSuSE 11.1, and CentOS 5.2, and 5.3 on my hardware.   Results are the same for 32-bit and 64-bit.  I also experience this problem with OpenSolaris 2009.6 but not the 2008 series.
Haven't tried any previous versions of Ubuntu prior to 8.04 (The same symptoms appear on 8.04-9.04 for me).

I also have this problem with Windows Vista 64-bit (but not 32-bit) and Windows 7, though I experience even slower transfer speeds in all Windows scenarios (excluding 32-bit Vista Business where 110 MB/s sustained is common, except SATA <-> USB stick where mid 40's is the cap).  I will say that when transferring a large amount of data (say 3.7GB) on Vista Business 32-bit, with a few bytes left, my PC blue screens.

I think the issue is much larger than anything on an OS level.  It could range from device firmware, to poorly documented API's.  I've ruled it out in my hardware through exhasutive testing (not all of it documented here), but it is even unclear whether or not there is a BIOS problem in some hardware, or whether changing BIOS settings simply provides a work around.

It's safe to say that we are seeing the identical symptoms on different, but often similar hardware, and that with the myriad combinations possible, this is a very complex issue that likely does not have the same root cause in every case.

For the time being, I am content with the results I am seeing.  However, for the others who have experienced worse performance I genuinely do hope this issue is resolved for their case as soon as possible.

---

### Post by darco on 2009-08-10
> **Anthon berg said:**
> Whoa, that is pretty interesting. Clever thing to try. Let me get this straight, if you have Linux copy to / from the USB drive, you get slow speed, but in the same linux a Windows virtual machine is OK for speed?

I have tried that w/two VM (Win7 and Karmic)and no improvement whatsoever....
I am using the mainline kernel (.30) on my pc and dropped down to my previous stock kernel 28.11 just to make sure this upgrade wasnt the cause. 28.11 was slow as molasses...
There are workarounds but...

darco

---

### Post by Anthon berg on 2009-08-10
> **darco said:**
> I have tried that w/two VM (Win7 and Karmic)and no improvement whatsoever....
I am using the mainline kernel (.30) on my pc and dropped down to my previous stock kernel 28.11 just to make sure this upgrade wasnt the cause. 28.11 was slow as molasses...
There are workarounds but...

darco

So both the Ubuntu kernel and the mainline are slow for you?

And did you try the BIOS wrangling that has been posted in the thread?

---

### Post by darco on 2009-08-10
Yes, only when transferring to a flashdrive....and I know it started recently because I thought it was a defective flash drive so I went a bought a new one. Prior to that I was fine transferring to it, cant recall it being that slow...
An update killed it? 

darco

*edit*- usb legacy off and ahci enabled..ive posted a few times in this thread

---

### Post by _khAttAm_ on 2009-08-10
> **n3had said:**
> I am using ubuntu 9.04 

specs

AMD X24200+
ASUS M2N-VM DH 

So is this issue realted to AMD/ASUS only? or others are facing it too??

THE CPU goes really high when copying anything to flashdrives.

If you read through the thread, you'd know that this issue has also occured in intel cpus and non-asus boards.

> **n3had said:**
> guys don't fight .. i've been thrashed by a windoze user because of this bug..

And I'd been hiding this bug from my Windows Fanboys friends. Not that I boast too much about linux or make the day difficult for a M$ fanboy, they just like to point out faults of what they don't use.

> **Arup said:**
> So now the plot thickens, if Windows is having this issue as well then its got nothing to do with OS but a combo of particular hardware/BIOS and CPU combined with OS to an extent or driver at the most.
> **Anthon berg said:**
> Being "trashed" by a Windows user means that the Windows DOES NOT have the problem.

Speak about your own experience, please.

I remember this bug after I moved solely to intrepid. I was using Windows Vista, Hardy and Mac OS X and did not have this problem with any. I believed my HDD was gone unless I searched for the issue.

> **Anthon berg said:**
> Sorry! :( Lost myself.

I'm having problems like this on several Intel Core 2 machines. Most have Gigabyte boards.

The "magic pill" for me has been to install a mainline kernel, though not everybody is happy with that :) Did you try this?
I tried 2.6.29, 2.6.30 and 2.6.31-rc.. but that did not help. Are we talking about <2.6.28?

> **Anthon berg said:**
> Whoa, that is pretty interesting. Clever thing to try. Let me get this straight, if you have Linux copy to / from the USB drive, you get slow speed, but in the same linux a Windows virtual machine is OK for speed?
Please someone confirm. This is really interesting.

> **Anthon berg said:**
> 
On my personal machine I have Ubuntu 8.10, and I have to use kernel 2.6.27.
Why is that?

> **Arup said:**
> Before you do all that, just a simple suggestion, see if there is a BIOS upgrade, then try turning off USB Legacy mode in BIOS and enable AHCI mode for HDD if you can, this has worked for some and has done good to my Phenom PC, your results may vary but its a easier and better solution than the kernel upgrade.

I believe kernel upgrade is easier than that. But maybe thats just me.

> **n3had said:**
> i am going to try disabling usb legacy support and i'll report later and how do i enable AHCI mode for HDD? and for the time being plz can you give some pointers how to hate windows passionately. I need to have strong reasons for that. I gotta duel with my WINDOZE buddy.

You don't need to hate Windows for using\loving linux. I like Windows and what they have been doing over the past times. They have focused in security and looks and I like it. However, I haven't installed Windows 7 and haven't explored Windows Vista and don't use Windows at all now. I sometimes use Windows Vista and Windows 7 in friends' PCs and it is not much bad (except of course, sometimes Windows machines are infected). And I have not moved coz I have to buy it.. no! All of my friends here and 90+% of the population here (Nepal) use pirated stuff regarding OS coz we have no way to buy (unless we get a Branded PC.. which most of people here don't.. simply it is costly and also coz that way, they'd be paying for the OS.. those who look for Laptops prefer ones with FreeDOS or nothing, as vendor here readily installs any OS of choice.. the choices are Vista, 7 and XP only though...) and M$ is providing Free Windows to students (which I am) to discourage piracy. But I like linux better. I'd even install rpm-based distro (even OpenSuse) rather than move to Windows.

> **Arup said:**
> Well I was at equal fault, no hard feelings. Even if Ubuntu doesn't work out, sidux and arch are using the latest kernel 2.6.30, suggest you check them out as well.
Has anyone tried sidux? I thought it was the kernel and moved to lenny. I have upgraded my lenny kernel to Ubuntu mainline 2.6.30 and haven't experienced anything in SATA to SATA transfers, yet to try USB drives.

---

### Post by Anthon berg on 2009-08-11
> **_khAttAm_ said:**
> 
[QUOTE=Anthon berg;7762159]The "magic pill" for me has been to install a mainline kernel, though not everybody is happy with that :) Did you try this?
I tried 2.6.29, 2.6.30 and 2.6.31-rc.. but that did not help. Are we talking about <2.6.28?[/QUOTE]

I've tried .28, .29 and .30. Fixes things for me at the office, there's a few different machines.

> **_khAttAm_ said:**
> 
[QUOTE=Anthon berg;7762293]On my personal machine I have Ubuntu 8.10, and I have to use kernel 2.6.27.

Why is that?[/QUOTE]

Development machine, can't afford the time to fix a some links against libraries that change in 9.04. Nothing really important, I think most if not all of the machines at the office have 9.04.

---

### Post by Confuzius on 2009-08-11
9.04 x64 with whatever is the current kernel.
Asus M2NPV-VM motherboard and 3800+ AMD processor.
Disableing Legagcy USB sent my transfer rates from ~0.75mb/s back to ~25mb/s

---

### Post by speedkreature on 2009-08-11
This may be worthy of a different thread but...
On the workstation I'm having the slow transfer speeds on, I peak at 2.1MB/s for file transfers over Ethernet (IPv4), then it slowly dwindles...right now I'm at 360KB/s and falling.
I'm trying to transfer around 90GB of files across a gigabit network to a fibre channel SAN that can sustain 1.2Tb/s (150GB/s).  I'm looking at 60+ hours to finish this transfer.

Could the problem be more closely related to how the kernel is buffering the files to be transfered and how certain combinations of hardware support this method, rather than the particular protocol being used?

On another machine (also AMD based with a different Gigabyte board) running 9.04 x86-64, I can maintain 2+ MB/s over Ethernet and don't have the slower SATA <--> SATA and SATA <--> USB performance I do on this machine.  Specs are very similar on both machines except that the one that isn't having the problem uses an Athlon 64 x2 and DDR2, while the one that is having issues uses a Phenom II and DDR3.  All other unlisted hardware is currently the same.

---

### Post by Paladiamors on 2009-08-12
AMD 5200+ Dual CPU
4 GB memory, plus an ECS Motherboard
running Ubuntu 9.04-64 bit

I too get the slow hard data problems while transfering data between hard drives. Starts off at abot 35mb/sec then drops to about 4 mb/sec.

I've installed Ubuntu 9.04-32 bit and don't see any problems on that version. Is there a bug somewhere between the 32 bit and 64 bit SATA drivers somewhere?

---

### Post by dakochan on 2009-08-16
Hi,
I'm using Linux Mint 6 (Ubuntu 8.10) on an AMD Turion 64X2. I also have transfer rate problem with my USB ntfs harddisk. For copying 13GB vmware files the transfer rate on average is about 4 MB/sec.
Since yesterday I made a testing by creating a new partition on my USB harddisk with ext3 filesystem. When I copied the same data into this new partition the transfer rate is higher, about 8 MB/sec (it's twice).
Does this mean that the file system is the problem?
Any explanation for this?

---

### Post by v1nsai on 2009-08-16
In the [bug report]("https://bugs.launchpad.net/ubuntu/+bug/177235") #25 suggested removing ehci_hcd and adding it again.  When I try to remove it I am told that it does not exist in /proc/modules.  'lsmod' also shows that I simply do not have ehci_hcd.  I'm a bit confused about what IS managing my usb devices...I can still transfer things, just very slowly.  And my mp3 player is recognized no problem.....

Someone [posted about this]("http://ubuntuforums.org/showthread.php?t=1113343") in the jaunty beta forum but it's closed now.  Any ideas appreciated, I'm in wtf over here.


EDIT:
okay it gets weirder, here's a few lines from kern.log

```
Aug 16 20:39:30 v3stl kernel: [  597.212035] usb 1-5: new high speed USB device using **ehci_hcd** and address 5
Aug 16 20:39:30 v3stl kernel: [  597.577619] usb 1-5: configuration #1 chosen from 1 choice
Aug 16 20:39:30 v3stl kernel: [  597.579939] scsi7 : SCSI emulation for USB Mass Storage devices
```

ehci_hcd is somewhere...just not in /proc/modules.  And why is it mounting as scsi I'm using IDE HDD's no scsi's anywhere, don't even have scuzzy drive bays.

---

### Post by darco on 2009-08-16
> **v1nsai said:**
> In the [bug report]("https://bugs.launchpad.net/ubuntu/+bug/177235") #25 suggested removing ehci_hcd and adding it again.  When I try to remove it I am told that it does not exist in /proc/modules.  'lsmod' also shows that I simply do not have ehci_hcd.  I'm a bit confused about what IS managing my usb devices...I can still transfer things, just very slowly.  And my mp3 player is recognized no problem.....

Someone [posted about this]("http://ubuntuforums.org/showthread.php?t=1113343") in the jaunty beta forum but it's closed now.  Any ideas appreciated, I'm in wtf over here.


EDIT:
okay it gets weirder, here's a few lines from kern.log

```
Aug 16 20:39:30 v3stl kernel: [  597.212035] usb 1-5: new high speed USB device using **ehci_hcd** and address 5
Aug 16 20:39:30 v3stl kernel: [  597.577619] usb 1-5: configuration #1 chosen from 1 choice
Aug 16 20:39:30 v3stl kernel: [  597.579939] scsi7 : SCSI emulation for USB Mass Storage devices
```

ehci_hcd is somewhere...just not in /proc/modules.  And why is it mounting as scsi I'm using IDE HDD's no scsi's anywhere, don't even have scuzzy drive bays.

I believe w/the newer kernels, they are no longer added as 'modules"  but rather built into the kernel a different way.  Im sure others can explain this better than me....

darco

---

### Post by v1nsai on 2009-08-18
I found a fix that suggested that you add the option 'pci=routeirq' to the end of your kernel line in /boot/grub/menu.lst .  This didn't fix my problem, but I definitely got better speeds, and the status bar was always moving, it used to freeze for long periods of time.  Shows me it's doing something at least.  Speed started out at about 16MB/s and was down to 6 when it finished, but transferred 1.1 GB in about 2 minutes.  Not the worst I've seen lately.

If you wanna try this, remember that it's there when you try making any other modifications because it may interfere for better or for worse.

```
sudo gedit /boot/grub/menu.lst
```
Here's how mine looks
```
title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		6a91d6f2-19c9-4462-a967-0803796688f9
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=6a91d6f2-19c9-4462-a967-0803796688f9 ro quiet splash **pci=routeirq**
initrd		/boot/initrd.img-2.6.28-14-generic
quiet
```

---

### Post by _khAttAm_ on 2009-08-18
Getting 25-30 MBps now (which is what i used to get without problems) with Karmic Koala Alpha 4.

---

### Post by dakochan on 2009-08-18
Your transfer rate to your usb harddisk is 25-30 MBps and you don't need to do anything?
Wow, that's amazing.

---

### Post by Muppeteer on 2009-08-21
Just to add to this. I'm running arch 64, and have horrible I/O performance. I'm running an Asus M3A78 Pro, which has an AMD 780G chipset and SB700 southbridge. Any transfers to or from ext4 to ntfs are extremely cpu intensive and pretty much locks up my system. While the speed is ok, the transfer speed to usb is also horrible. As others have mentioned, they usually start fast and grind to a halt.

Here's some benchmarks:
```
/dev/sda:
 Timing cached reads:   2214 MB in  2.01 seconds = 1103.61 MB/sec
 Timing buffered disk reads:  274 MB in  3.01 seconds =  91.04 MB/sec
bash-4.0# hdparm -Tt /dev/sdb

/dev/sdb:
 Timing cached reads:   2370 MB in  2.00 seconds = 1186.06 MB/sec
 Timing buffered disk reads:  210 MB in  3.01 seconds =  69.86 MB/sec
bash-4.0# hdparm -Tt /dev/sdc

/dev/sdc:
 Timing cached reads:   2308 MB in  2.00 seconds = 1154.53 MB/sec
 Timing buffered disk reads:  258 MB in  3.00 seconds =  85.96 MB/sec
bash-4.0# hdparm -Tt /dev/sdd

/dev/sdd:
 Timing cached reads:   2342 MB in  2.00 seconds = 1170.41 MB/sec
 Timing buffered disk reads:  328 MB in  3.00 seconds = 109.22 MB/sec
```

All drives are sata II & have installed the latest bios. I'm not sure i fit into this category, since most people are getting slow xfer speeds, while only my usb speeds are slow, my main problem is my system grinding to a halt during any file transfers. I've yet to try a custom kernel, but have tried changing the CFQ scheduler to deadline and it seems to have helped a little. As for the usb transfer speed, i have to resort to windows for that.

Here's my lspci
```
bash-4.0# lspci                                                      
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge  
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)                                                                                       
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)  
**00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode] **   
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller           
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTS] (rev a2)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:07.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
03:07.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
03:07.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)

```

I'm not sure of the significance of the sata controller being in IDE mode. All but one drive is set to UDMA6, the other is stuck at UDMA5 even though it is capable of 6. Anyway, i just figured it let you guys know that it doesn't seem to be Ubuntu specific, rather hardware/kernel specific. My solution is to revert back to an Nvidia chipset board, as my last one died and i replaced it with this crap :(

Edit: I tried setting my sata controller to AHCI mode, but hasn't really made any difference. Neither has legacy usb disabled.

---

### Post by GuiGuy on 2009-08-21
> **Muppeteer said:**
> 
Edit: I tried setting my sata controller to AHCI mode, but hasn't really made any difference. Neither has legacy usb disabled.

If I enable AHCI mode on my ASUS M3A or M2H boards (AMD AM2 X2 CPUs with latest BIOS), the dang thing hangs on boot with the "ATAn: software reset failed" error.

It really is a crock.

---

### Post by darco on 2009-08-21
> **GuiGuy said:**
> If I enable AHCI mode on my ASUS M3A or M2H boards (AMD AM2 X2 CPUs with latest BIOS), the dang thing hangs on boot with the "ATAn: software reset failed" error.

It really is a crock.

Heh...for me when AHCI is enabled, my Win7 wont boot up :confused:

darco

---

### Post by dakochan on 2009-08-22
Hi all,

I've a new finding. I tried copy 700MB data using terminal from internal harddisk to usb harddisk (NTFS partition), it finished in 43 seconds. It means the transfer rate is 16 MB !
So, does the problem lie in GNOME?
Is there anyone ever checked the transfer rate using other GNOME distro or non-GNOME Ubuntu?

---

### Post by GuiGuy on 2009-08-22
> **dakochan said:**
> Hi all,
So, does the problem lie in GNOME?


No, Kubuntu is affected as well.

---

### Post by Shawn Reist on 2009-08-22
Hello,

cudo's to v1nsai for the suggestion of pci=routeirq

I thought everything was working great.. transfer speeds doubled... after 12 hours transfer speeds were abysmal.. 

seems I get my best transfers just after a reboot of the computer.

Someone else mentioned about the system logging USB devices as SCSI...and not picking them up properly... or ways to reset how it looks at devices?

USB 2 PNY 4 gig USB stick

```

Aug 22 15:58:14 icabaud kernel: [ 4571.948052] usb 1-1: new high speed USB device using ehci_hcd and address 5
Aug 22 15:58:14 icabaud kernel: [ 4572.093057] usb 1-1: configuration #1 chosen from 1 choice
Aug 22 15:58:14 icabaud kernel: [ 4572.096537] scsi6 : SCSI emulation for USB Mass Storage devices
Aug 22 15:58:19 icabaud kernel: [ 4577.126797] scsi 6:0:0:0: Direct-Access              USB Flash Memory PMAP PQ: 0 ANSI: 0 CCS
Aug 22 15:58:23 icabaud kernel: [ 4580.801573] sd 6:0:0:0: [sdb] 7823360 512-byte hardware sectors: (4.00 GB/3.73 GiB)
Aug 22 15:58:23 icabaud kernel: [ 4580.802156] sd 6:0:0:0: [sdb] Write Protect is off
Aug 22 15:58:23 icabaud kernel: [ 4580.806945] sd 6:0:0:0: [sdb] 7823360 512-byte hardware sectors: (4.00 GB/3.73 GiB)
Aug 22 15:58:23 icabaud kernel: [ 4580.807548] sd 6:0:0:0: [sdb] Write Protect is off
Aug 22 15:58:23 icabaud kernel: [ 4580.807574]  sdb: sdb1
Aug 22 15:58:23 icabaud kernel: [ 4580.849437] sd 6:0:0:0: [sdb] Attached SCSI removable disk
Aug 22 15:58:23 icabaud kernel: [ 4580.849617] sd 6:0:0:0: Attached scsi generic sg2 type 0

```

second USB stick
PNY optima pro attache 8 gig

```

Aug 22 16:28:38 icabaud kernel: [ 6395.912052] usb 1-1: new high speed USB device using ehci_hcd and address 6
Aug 22 16:28:38 icabaud kernel: [ 6396.056608] usb 1-1: configuration #1 chosen from 1 choice
Aug 22 16:28:38 icabaud kernel: [ 6396.064168] scsi7 : SCSI emulation for USB Mass Storage devices
Aug 22 16:28:43 icabaud kernel: [ 6401.116491] scsi 7:0:0:0: Direct-Access              USB DISK 2.0     PMAP PQ: 0 ANSI: 0 CCS
Aug 22 16:28:45 icabaud kernel: [ 6403.262073] sd 7:0:0:0: [sdb] 16121856 512-byte hardware sectors: (8.25 GB/7.68 GiB)
Aug 22 16:28:45 icabaud kernel: [ 6403.262678] sd 7:0:0:0: [sdb] Write Protect is off
Aug 22 16:28:45 icabaud kernel: [ 6403.267707] sd 7:0:0:0: [sdb] 16121856 512-byte hardware sectors: (8.25 GB/7.68 GiB)
Aug 22 16:28:45 icabaud kernel: [ 6403.268956] sd 7:0:0:0: [sdb] Write Protect is off
Aug 22 16:28:45 icabaud kernel: [ 6403.268982]  sdb: sdb1
Aug 22 16:28:45 icabaud kernel: [ 6403.333957] sd 7:0:0:0: [sdb] Attached SCSI removable disk
Aug 22 16:28:45 icabaud kernel: [ 6403.334134] sd 7:0:0:0: Attached scsi generic sg2 type 0

```

What controls how a device is looked at? how is USB 1 or USB 2 selected

---

### Post by PatrickVogeli on 2009-08-22
usb disk as scsi is normal. It's the way it works, and there's nothing wrong with that. Also, ehci (usb2) is being picked up, so no troubles there.

---

### Post by Shawn Reist on 2009-08-23
I don't quite understand... 

usb 1-1: new high speed USB device using ehci_hcd and address 6
usb 1-1: configuration #1 chosen from 1 choice

I can read that it should be the Enhanced Host Controller Interface (i.e. USB2)

Why is it labels "usb 1-1"

What is configuration #1 chosen from 1 choice? is there a second choice or configuration file that should be looked at?

pulled this from log after boot.. 

```

Aug 23 00:02:36 icabaud kernel: [    2.885448] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Aug 23 00:02:36 icabaud kernel: [    2.885545] ehci_hcd 0000:04:01.2: EHCI Host Controller
Aug 23 00:02:36 icabaud kernel: [    2.885701] ehci_hcd 0000:04:01.2: new USB bus registered, assigned bus number 1
Aug 23 00:02:36 icabaud kernel: [    2.885778] ehci_hcd 0000:04:01.2: irq 19, io mem 0xe5106000
Aug 23 00:02:36 icabaud kernel: [    2.896020] ehci_hcd 0000:04:01.2: USB 2.0 started, EHCI 1.00
Aug 23 00:02:36 icabaud kernel: [    2.896201] usb usb1: configuration #1 chosen from 1 choice
Aug 23 00:02:36 icabaud kernel: [    2.896270] hub 1-0:1.0: USB hub found
Aug 23 00:02:36 icabaud kernel: [    2.896291] hub 1-0:1.0: 4 ports detected
Aug 23 00:02:36 icabaud kernel: [    2.896570] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Aug 23 00:02:36 icabaud kernel: [    2.896624] uhci_hcd: USB Universal Host Controller Interface driver
Aug 23 00:02:36 icabaud kernel: [    2.896721] uhci_hcd 0000:04:01.0: UHCI Host Controller
Aug 23 00:02:36 icabaud kernel: [    2.896849] uhci_hcd 0000:04:01.0: new USB bus registered, assigned bus number 2
Aug 23 00:02:36 icabaud kernel: [    2.896894] uhci_hcd 0000:04:01.0: irq 17, io base 0x0000a000
Aug 23 00:02:36 icabaud kernel: [    2.897081] usb usb2: configuration #1 chosen from 1 choice
Aug 23 00:02:36 icabaud kernel: [    2.897150] hub 2-0:1.0: USB hub found
Aug 23 00:02:36 icabaud kernel: [    2.897171] hub 2-0:1.0: 2 ports detected
Aug 23 00:02:36 icabaud kernel: [    2.897396] uhci_hcd 0000:04:01.1: UHCI Host Controller
Aug 23 00:02:36 icabaud kernel: [    2.897523] uhci_hcd 0000:04:01.1: new USB bus registered, assigned bus number 3
Aug 23 00:02:36 icabaud kernel: [    2.897563] uhci_hcd 0000:04:01.1: irq 18, io base 0x0000a400
Aug 23 00:02:36 icabaud kernel: [    2.897737] usb usb3: configuration #1 chosen from 1 choice
Aug 23 00:02:36 icabaud kernel: [    2.897800] hub 3-0:1.0: USB hub found
Aug 23 00:02:36 icabaud kernel: [    2.897818] hub 3-0:1.0: 2 ports detected

```

transfers start out at 7-8 MB/sec then tapper down to 4-3.5 MB/sec

blacklisted both ohci & uhci

transfers after initial reboot started at 11.x MB/sec and tapered down to 9.8 MB/sec
second transfer 6.9 MB/sec tapering down to 4.8 but fluctuating from 4.8-5.2 MB/sec

What else can be done?

I noticed in the log after boot this

```

ehci_hcd 0000:04:01.2: USB 2.0 started, EHCI 1.00
usb usb1: configuration #1 chosen from 1 choice

uhci_hcd 0000:04:01.0: irq 17, io base 0x0000a000
usb usb2: configuration #1 chosen from 1 choice

uhci_hcd 0000:04:01.1: irq 18, io base 0x0000a400
usb usb3: configuration #1 chosen from 1 choice

```

does this mean that regardless if ehci/ohci/uhci they are all using the same choice for configuration file...?

---

### Post by isecore on 2009-08-23
> **GuiGuy said:**
> If I enable AHCI mode on my ASUS M3A or M2H boards (AMD AM2 X2 CPUs with latest BIOS), the dang thing hangs on boot with the "ATAn: software reset failed" error.

It really is a crock.

I get the same error. But my machine boots just fine despite it. AMD Phenom 9550 on a Gigabyte GA-MA790FX-DS5.

---

### Post by KCormier on 2009-08-25
Definitely architecture independent.  I have the same issues on both my old mac (ppc) and my core2duo laptop.  Both are running ubuntu 8.04.  The problem is much worse on my mac though.  If I try to dd a large file (dvd iso) to /dev/null my speeds drop to about 4mb/s and that's with a 7200rpm ide drive inside.  hdparm gives good speeds and if I dd /dev/sda to /dev/null I get great io.  I'm going to run a few more tests and see if I can figure anything else out (including other kernels).

---

### Post by feistybird on 2009-08-26
This works for me, thanks!

> **v1nsai said:**
> I found a fix that suggested that you add the option 'pci=routeirq' to the end of your kernel line in /boot/grub/menu.lst .  This didn't fix my problem, but I definitely got better speeds, and the status bar was always moving, it used to freeze for long periods of time.  Shows me it's doing something at least.  Speed started out at about 16MB/s and was down to 6 when it finished, but transferred 1.1 GB in about 2 minutes.  Not the worst I've seen lately.

If you wanna try this, remember that it's there when you try making any other modifications because it may interfere for better or for worse.

```
sudo gedit /boot/grub/menu.lst
```
Here's how mine looks
```
title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		6a91d6f2-19c9-4462-a967-0803796688f9
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=6a91d6f2-19c9-4462-a967-0803796688f9 ro quiet splash **pci=routeirq**
initrd		/boot/initrd.img-2.6.28-14-generic
quiet
```

---

### Post by jeffreykutcher on 2009-08-26
I'm experiencing the same issues and would like to add some additional observations which may spark someone to come up with a solution.

Running top, the mount.ntfs-3g process attached to the slow drive is spinning the CPU at 80-100%. The transfer rate slowness might be attributed to a denial of service (speculation). A second USB drive also mounted using mount.ntfs-3g on the same machine (identical drives) is spinning the CPU at a constant 15/16% and it's transfer rate is fine. "iostat 5" is returning about 50 tps for the behaving disk and 1-5 tps for the misbehaving one. Block writes per second are 7000-8000 for the behaving drive and 0-1000 for the misbehaving one.

There is something in the mount.ntfs-3g process that's spinning the CPU rather than transferring information, thus the slow transfer rate speed.

Anyone know what's going on inside mount.ntfs-3g?

The two disks I'm using are 1T drives. When they fill to about 89%/90%, the mount.ntfs-3g process begins to spin wildly and tranfer rate drops like a rock.

Further thoughts?

---

### Post by Damon68 on 2009-08-26
> **dakochan said:**
> Hi all,

I've a new finding. I tried copy 700MB data using terminal from internal harddisk to usb harddisk (NTFS partition), it finished in 43 seconds. It means the transfer rate is 16 MB !
So, does the problem lie in GNOME?
Is there anyone ever checked the transfer rate using other GNOME distro or non-GNOME Ubuntu?

> 
Also happening in Kubuntu 


I was having the same issues with my sata II drives and Ubuntu, I recently installed Xubuntu (mostly just to use less resources), and strangley enough I no longer seem to be effected by the sata issue.

I'm pretty new to the linux world and am more than happy to run any tests on my system to try and confirm sata speeds or what have you, but you'll have to pretty much explain what it is you want me to do :P

Or maybe someone else would like to try installing Xubuntu and seeing if their issue is resolved as well.  :)

Damon

example of speeds I'm getting:
800mb transfer
from 1tb ntfs to 1tb ntfs - a little under  minute
from either of the 1tb drives to my main Xubuntu drive (500gb) - under 20 seconds

transfers were done while watching a movie stored on the 1tb drive and deluge transfers running as well.

---

### Post by isecore on 2009-08-27
I've tried all kinds of copies. I've done it in nautilus, done it through shell, etc. No difference.

Every time it's the same thing. Starts out fast for a short while, then the CPU-usage shoots through the roof and transfer goes down to a trickle.

---

### Post by psychobot on 2009-08-28
have you checked to make sure DMA is enabled?

---

### Post by Shawn Reist on 2009-08-29
Hello,

I have been doing some reading and hunting around.

I came across this site about the kernal.

[http://www.mjmwired.net/kernel/Documentation/usb/proc_usb_info.txt]("http://www.mjmwired.net/kernel/Documentation/usb/proc_usb_info.txt")


I have been trying to find these configuration files.

eg. 
> 
**NOTE**:
If /proc/bus/usb appears empty, and a host controller
driver has been linked, then you need to mount the
filesystem.  Issue the command (as root):

mount -t usbfs none /proc/bus/usb


I am still reading,  but does anyone else find that this directory appears empty?

From what I gather so far this is where some of the configuration files are written or can be changed by a root user.

I have also checked my second computer system and the same directory is empty, no configuration files.

after installing USBview I am now able to get information from the USB bus/devices.

Device
```

EHCI Host Controller
Manufacturer: Linux 2.6.28-15-generic ehci_hcd
Serial Number: 0000:04:01.2
Speed: 480Mb/s (high)
Number of Ports: 4
Bandwidth allocated: 0 / 800 (0%)
Total number of interrupt requests: 0
Total number of isochronous requests: 0
USB Version:  2.00
Device Class: 09(hub  )
Device Subclass: 00
Device Protocol: 00
Maximum Default Endpoint Size: 64
Number of Configurations: 1
Vendor Id: 1d6b
Product Id: 0002
Revision Number:  2.06

Config Number: 1
	Number of Interfaces: 1
	Attributes: e0
	MaxPower Needed:   0mA

	Interface Number: 0
		Name: hub
		Alternate Number: 0
		Class: 09(hub  ) 
		Sub Class: 00
		Protocol: 00
		Number of Endpoints: 1

			Endpoint Address: 81
			Direction: in
			Attribute: 3
			Type: Int.
			Max Packet Size: 4
			Interval: 256ms

```
USB 2 PNY 4 Gig Memory stick
```

USB Flash Memory
Manufacturer:         
Serial Number: 5B820E000029
Speed: 480Mb/s (high)
USB Version:  2.00
Device Class: 00(>ifc )
Device Subclass: 00
Device Protocol: 00
Maximum Default Endpoint Size: 64
Number of Configurations: 1
Vendor Id: 0930
Product Id: 6545
Revision Number:  1.10

Config Number: 1
	Number of Interfaces: 1
	Attributes: 80
	MaxPower Needed: 200mA

	Interface Number: 0
		Name: usb-storage
		Alternate Number: 0
		Class: 08(stor.) 
		Sub Class: 06
		Protocol: 50
		Number of Endpoints: 2

			Endpoint Address: 81
			Direction: in
			Attribute: 2
			Type: Bulk
			Max Packet Size: 512
			Interval: 0ms

			Endpoint Address: 02
			Direction: out
			Attribute: 2
			Type: Bulk
			Max Packet Size: 512
			Interval: 0ms

```

---

### Post by PatrickVogeli on 2009-08-30
Could you try adding the following
```
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
```
at the end of /etc/fstab?

Then reboot you computer and check if speed is ok. If it's not or is worse, you can undo that by removing the line and rebooting again.

---

### Post by dakochan on 2009-08-31
> **PatrickVogeli said:**
> Could you try adding the following
```
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
```
at the end of /etc/fstab?

Then reboot you computer and check if speed is ok. If it's not or is worse, you can undo that by removing the line and rebooting again.

Hi Patrick,

I followed your suggestion above. The transfer rate is definitely increase. I have tested for several times by copying a 600MB data to USB harddisk, either NTFS or EXT3. On the first test the lowest transfer rate is 5 MB/sec, which is 25% faster than the previous lowest transfer rate. But, after a few times, the transfer rate seems increase until 20++ MB/sec !!! However, the transfer rate is not so stable, from 20++ MB/sec the transfer rate can drop to 16 MB/sec in a few seconds only. Anyway, it's still much better than before. Thanks a lot, Patrick. :P
Btw, is there the side effect of using the code above?

Regards
DakoChan

---

### Post by PatrickVogeli on 2009-08-31
side effect? I've seen no side effects so far

---

### Post by Shawn Reist on 2009-09-01
Hello,

> **PatrickVogeli said:**
> Could you try adding the following
```
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
```
at the end of /etc/fstab?

Then reboot you computer and check if speed is ok. If it's not or is worse, you can undo that by removing the line and rebooting again.


I have seen a little improvement but it seems to fluctuate, the larger files have a tendency for the transfer rates to drop to 3-5 Mb/sec.

The best transfers I have is when I initially reboot I can see transfers close to 12 Mb/sec. I think I saw 15 Mb/sec once but otherwise they are down to 8-3.5 Mb/sec

The main reason I am looking into this area is that I could not find said configuration files for USB devices. Maybe finding these would help with finding a solution for the slow transfers.

More then just Ubuntu is affected by this... and it varies across platforms and hardware.

---

### Post by dakochan on 2009-09-02
Hi,

Just wandering, how about transfer rate with usb cdrom/dvdrom? Because when I burn a DVD with 4GB data, it took about 1 hour with the transfer rate a little bit more than 1MB/sec.
Do you guys experience the same thing?

(Should I post this in another thread?)

---

### Post by pediatracancun on 2009-09-04
I tried changing the /etc/fstab as suggested with no benefit.
This is definitively a problem of Ubuntu AMD64, because I've my notebook with Jaunty for 32 bytes, and the transference rate is excellent.
Hope we will find a solution pretty soon. Right now I'm transferring a 4 GB file from an external HD to my Jaunty AMD64, and it will take more than 1 hour.

---

### Post by darco on 2009-09-04
Did you try any of the suggested fixes? Adding pci=routeirq, usb legacy off or disabling ahci?
I had usb legacy already in off mode, when disabling ahci, I cannot boot to my Win partition but the transfer rate was'nt affected anyways. I did add the pci=routeirq and it also did not have an effect at least not right away ( I added it a few weeks back) but just now I transfered a 4.4 gig file from an external usb to my desktop and it took 3mins...
 

darco

---

### Post by isecore on 2009-09-05
I've tried all things listed here, and in short none of them does anything that's quantifiable.

I tried the pci=routeirq and it did nothing I could notice. Disabling USB legacy does nothing for me. Adding in the entry to mount USBfs in /etc/fstab only gives me an error about a non-existant mount-point.

That's my experiences with all of these suggested tweaks.

---

### Post by GuiGuy on 2009-09-05
<sigh>
I have put together a new box, destined to be used as a desktop PC, based on an [AMD ATHLON II X2 250 DUAL-CORE 3.0GHZ CPU]("http://www.ddcomputer.com.au/prod-ADX250OCGQBOX-proddes_AMD_ATHLON_II_X2_250_DUAL-CORE_3.0GHZ_CPU.html")  and an [SUS M4A785TD-V-EVO ]("http://www.ddcomputer.com.au/prod-M4A785TD-V-EVO-proddes_ASUS_M4A785TD-V-EVO.html")mobo.

I thought I'd give Ubuntu (64 bit) another try. Same old, same old, I'm afraid. A 4G file, HDD to HDD, takes more than 20 minutes to transfer. The wireless network I have is faster than that. 


:confused:

---

### Post by theZoid on 2009-09-07
I have a DELL Precision Laptop m4400 with Intel CPU, and transferring several gigs of data regularly the rates stay at around 24/MBs....IOW, no problems noted with Jaunty 64 here.

---

### Post by Mander on 2009-09-07
Has anyone found that the speed has only decreased in the last couple of weeks?  It was fine, perhaps a bit slow, but for me it has been getting progressively slower to transfer files or even open directories in nautilus.  I tried the tweaks above to no effect that I can see.

---

### Post by Shawn Reist on 2009-09-07
Hello,

I will disagree that this is only a AMD64 issue.

the dual Intel Xeon system I have is affected; and 
the Asus EEEPC 701

Both these systems are affected. 

This problem has been around for a little while but since the release of 9.04 it has gotten worse within Ubuntu, though I have seen other distro forums with people complaining about slow transfer speeds.

---

### Post by interval1066 on 2009-09-08
I'm still on Hardy, but to reply to those who have mentioned it, I've had no SATA problems. Rig detail below;

---

### Post by dcstar on 2009-09-10
> **interval1066 said:**
> I'm still on Hardy, but to reply to those who have mentioned it, I've had no SATA problems. Rig detail below;

I just did a test with a 3.8 GB file and could do an internal copy to another EXT3 SATA disk at 40.8 MB/s, and 19 MB/s to an external USB NTFS disk.

---

### Post by Shawn Reist on 2009-09-11
Just installed Hardy 8.04.3 LTS 

Transfers to PNY 4 gig USB 2 stick were faster
[INDENT]14.5 MB/sec tapering down to 5.x MB/sec for a 867.4 MB file[/INDENT]
compared to Ubuntu 9.04
[INDENT]starting at 12-8 MB/sec tapering down to 5-2.3[/INDENT]

As to why the difference between versions I have little to no idea.

---

### Post by hansen7007 on 2009-09-11
Think that USB,s perform faster on windows then ubuntu.

---

### Post by Blakefreak on 2009-09-11
I have an AMD64 and since the kernel update my transfers between two internal drives now are on par with Windows 7... Somewhere between 40 to 60 MB/s.
Transfers to my Blackberry have always been 8 MB/s rock solid.  Windows never gets above 5 MB/s.

---

### Post by bero74 on 2009-09-14
I have problems with the latest kernel 2.6.28.15. My hard drive and usb sticks are registred as usb 1.1 devices. Reverting to 2.6.28.14 solved the problem.

---

### Post by Infin1ty on 2009-09-17
I had those problems as well, i went on reading all this thread from the start, did everything, nothing helped.
I then first checked and saw my ntfs-3g (i'm using jaunty) is outdated, i used dpkg -P to the ntfs-3g packages, downloaded from ntfs-3g.org their lateast packages and built it from source using T-H-E-I-R internal fuse system (and not ubuntu's/kernel once which for some odd reason make my cpu usage 100% while copying a single file), so far so good, now i can transfer files without my computer getting stucked as before (before, cpu usage went up roof, now it's calm).
well, still, usb problems.. it only solved the problem when copying from ntfs drivers (on the same hard disk).
so one problem solved.

then i went and searched a little more, it's seems as it's something with the default ubuntu kernel. 
i went and downloaded a kernel source from kernel.org and compiled it according to ubuntu's guide (using make-kpkg) but i did use my OWN CONFIG from scratch, adding only what is neccessery for my system and what i know i will use (it's quiet easy and there are alot of guides over the net), please note that if you use AppArmor it might not work (i'm not using apparmor but i saw you need to somehow to patch the kernel so it will load apparmor modules or something like this, haven't gotten into this yet).
anyhow , i use a Lenovo T400 so i had to recompile my tp_smapi module as well, i can say it was ALOT easier and errorless than before :) (simply compiled from source,no problems).
i also chose the WRITE option on the kernel NTFS Driver (i don't know how but it seemed to help!, i tried without and there were problems with ntfs fs on the dok)
first thing i noticed was the boot was a little bit faster (probably psychology) and also my ATI Graphic card (RADEON HD 3400) prerforms so much better (i never got to make my machine have an uptime of more than 3 days without a freezing screen!! now i can even get it to work for like 1 week with no  problems :)).
anyhow, i first checked my simple USB DOK (Sandisk which sucks big time, also on windows i must say), transfer rate was ~15mb/s (which is much more than before, also i can transfer big files without getting stuck as before i couldn't even finish copying a single big file), and after formatting it to NTFS i could use ntfs-3g, copy and even use the system as nothing interrupt in the background :).

then 3 days ago i was amazed!!! i went and copied a 3gb iso file to an external WD MyPassport Edition Harddisk, speed first went up to 50mb/s!! then it went down to about 40 and only at the end i saw 35~ and not even less!!, also unmounting the device was just in 1 sec! as before it took a few minutes.
then i went and copied a 9gb file!! i didn't get a speed lower than 34mb/s!!! it's way way way way faster than the windows os i also have on this PC.

Today i went and tried to copy a big file to my iPod root folder (just to check as i don't have a real external hard disk except my D.O.K) and i'm attaching a screenshot, i still can't believe i'm getting those speeds :)

the computer also behave so much better with the new kernel.

---

### Post by dakochan on 2009-09-18
Uuuuh.
It's tough if I need to compile a new kernel.... :(

---

### Post by GuiGuy on 2009-09-18
> **dakochan said:**
> Uuuuh.
It's tough if I need to compile a new kernel.... :(

Yup. I've tried it couple of times from instructions in forums like this. It's a great way to ensure the system doesn't restart on the next reboot. 

Acronis to the rescue....

I feel my love affair and indiscretions with Linux are coming to an end....

---

### Post by dakochan on 2009-09-19
GuiGuy, 
Nobody is too stupid to use linux. :)
I've another desktop that's running ubuntu 8.04 LTS, the transfer rate is much faster than my Linux Mint 6.
I think you can try it.

---

### Post by GuiGuy on 2009-09-19
> **dakochan said:**
> GuiGuy, 
Nobody is too stupid to use linux. :)

My signature line is tongue in cheek, right? :P

> 
I've another desktop that's running ubuntu 8.04 LTS, the transfer rate is much faster than my Linux Mint 6.
I think you can try it.

I'm just about ready to give it up or maybe I just couldn't be bothered any more. Linux  seems to take up too much time on 'maintenance' and sorting out. And I am so sick of the sluggish desktop performance, even when the hardware is the best.

Windows7 is looking awfully good to me and I am frequently caught eying off my daughter's MacBook ;)

 Cheers

---

### Post by Arup on 2009-09-19
LOL! in terms of speed, Linux blows Windows and Mac, absolutely no sluggishness after days of use whereas Widnows would slow to a crawl. Mac ain't that hot either and in a recent Phoronix benchmark, Ubuntu actually did excellent bettering Mac's latest offering in majority of the tests done.

There are other distros around and when one doesn't work, we try others. Thats the beauty of Linux. Of course there is the hyped Vista with some tweaks being peddled off as 7, same old file system, same old registry and they call it faster. LOL! thats an understatement.

---

### Post by Infin1ty on 2009-09-25
> **Arup said:**
> LOL! in terms of speed, Linux blows Windows and Mac, absolutely no sluggishness after days of use whereas Widnows would slow to a crawl. Mac ain't that hot either and in a recent Phoronix benchmark, Ubuntu actually did excellent bettering Mac's latest offering in majority of the tests done.

There are other distros around and when one doesn't work, we try others. Thats the beauty of Linux. Of course there is the hyped Vista with some tweaks being peddled off as 7, same old file system, same old registry and they call it faster. LOL! thats an understatement.

Actually, i was very amazed by Windows 7 speed using USB 2.0 devices, it is faster than vista and xp but after fixing up my usb problems in ubuntu, nothing can compare right now :)

and also, people having problems with disk on key, i own a sandisk cruzer u3 (8gb) one, which sucks big time, copying from the d.o.k is no problems (speed is good , around 25mb/s~) but copying to cause problems (in windows as well) but if i take an external real usb 2.0 hard disk (without an external source!) it's fast as up to 40mb/s with no lags in the middle :)

---

### Post by Arup on 2009-09-25
You are right about the brands having an impact, I have noticed that HP which are PNY to be quicker than my Kingston USB thumb drives. Probably something to do with firmware I guess.

---

### Post by GuiGuy on 2009-09-25
> **Infin1ty said:**
> Actually, i was very amazed by Windows 7 speed using USB 2.0 devices, it is faster than vista and xp but after fixing up my usb problems in ubuntu, nothing can compare right now :)

I wasn't going to respond the Arup's reply, largely because would only lead to one of those silly fanboy opinion threads. So thank you for yet again pointing out that linux has some failings severe enough to turn some of us off.

It remains for me that given the same hardware, Linux is useless as a desktop machine except for the most basic of tasks like web access and email checking. Then there is a lack of quality software, especially for the things I want and need to do.

This is not to say I am abandoning Linux. It has its uses; as a file server, dedicated mythTV backend or webserver, it does what it is supposed to and does these things well for me. Ask it to do any more, like perhaps render a video file in background and concurrently edit a large document in OpenOffice, expect to be frustrated. And, as amply pointed out in this thread, forget about large scale file transfers on AMD 64bit based system. (twelve hours to fill a 8G USB device with mp3 files :( ). So, in my office the file server and web server run on linux, in my home the entertainment system runs on MythTV (not mythbuntu because of the dreadful SATA and USB issues). These are the tasks for Linux, not the desktop GUI, IMO.

Last weekend I ditched Ubuntu (KDE) & Fedora as my desktop OSs and have gone back to Windows. Windows Seven in this case. It boots quickly, it is fast, it is responsive. It can run multiple tasks without coming to a grinding halt. And let's not forget, if you want professional quality software, especially for video work or RAD of business applications,  Windows is probably the only option anyway. 

I'll be happy to pay the money for the Win7 desktop gui. It works and lets me get on with actually doing something productive instead of worrying about tweaking performance or waiting for the system to catch up with what I am doing.

And before otheres here decide to flame me to hell, consider I am affected by both of the following issues, neither of which have helped make my linux desktop experience a pleasant one;

[https://bugs.launchpad.net/bugs/119730](https://bugs.launchpad.net/bugs/119730)
[https://bugs.launchpad.net/bugs/427210](https://bugs.launchpad.net/bugs/427210)

Horses for courses and thanks for listening, I'm outta here.

---

### Post by Arup on 2009-09-25
Since we are talking about bugs, here is something that should be an interesting read for sure.

[http://www.pcpro.co.uk/news/enterprise/351487/microsoft-admits-critical-windows-7-bug](http://www.pcpro.co.uk/news/enterprise/351487/microsoft-admits-critical-windows-7-bug)

"An attacker who successfully exploited this vulnerability could take complete control of an affected system," says Microsoft's advisory. "Most attempts to exploit this vulnerability will cause an affected system to stop responding and restart."

As I said, old wine and new bottle and hype hype hype and same old story repeats itself over and over again.

[http://www.infoworld.com/d/windows/critical-windows-7-bug-risks-derailing-product-launch-330](http://www.infoworld.com/d/windows/critical-windows-7-bug-risks-derailing-product-launch-330)

Oh boy! It appears that Microsoft&#8217;s glowing track record with Windows 7 is about to come to an abrupt and unceremonious end. According to various Web sources, the RTM build 7600.16385 includes a potentially fatal bug that, once triggered, could bring down the entire OS in a matter of seconds.

There would be more, just keep watching.

---

### Post by detroit/zero on 2009-09-26
After finding this thread, I'm struck by the similarity of many users' experience compared to my own. I've been fighting this bug since June of 2008 - more on that below in the details. I've found a lot of good advice here that I haven't seen yet, and found some new information and possible fixes.

I've just finished reading 27 pages of [this thread]("http://ubuntuforums.org/showthread.php?t=1150108"), [Bug #119730]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/119730?comments=all") (and all 139 comments), [Bug # 131094]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/131094?comments=all") (and all 244 comments), and [Kernel Bug #12309]("http://bugzilla.kernel.org/show_bug.cgi?id=12309") (and all 408 comments). On top of that, I have a number of forum threads that I've started or take part in as it relates to USB transfer speeds (in no particular order):
                                  [**Slow USB write speeds.**]("http://www.linuxquestions.org/questions/linux-hardware-18/slow-usb-write-speeds.-677588/")
                                  [**Slow USB transfer on 8.04**]("http://ubuntuforums.org/showthread.php?t=793688")
                                  [**Super slow USB speeds - Nautilus, not GVFS, is the culprit.**]("http://ubuntuforums.org/showthread.php?t=911052")
                                  [**Slow usb disk transfer bug discussion - Intrepid**]("http://ubuntuforums.org/showthread.php?t=991794")
                                  [**Unbearably slow USB transfers.**]("http://ubuntuforums.org/showthread.php?t=895386")
                                  [**Slow USB speeds not limited to USB.**]("http://ubuntuforums.org/showthread.php?t=933705")

There are probably others that have died over time and I've forgotten about. In any event, after going through 27 pages of this thread, I have some things I'd like to add:

[LIST]
[*]As the thread title suggests, this isn't limited to SATA drive speeds, but affects USB transfers (both to flash and external HDDs) as well. IMO, it carries over into network file transfer speeds on all manner of protocols (FTP, SSH, NFS, SMB, etc..);
[*]The bug definitely isn't limited to 64-Bit architecture;
[*]The bug isn't limited to certain hardware or manufacturers;
[*]The bug isn't even limited to file transfers: USB mice, keyboard, and speakers all show signs of data flow blockage.
[*]If the bug **is** Ubuntu-specific, then it definitely carries over to the Ubuntu derivatives - I'm using Mint these days and it's definitely present there; however
[*]If the bug **is not** Ubuntu-specific (and I suspect it isn't) some variety of it should be apparent on practically every distro around except those whose kernel patches actually patch it. Indeed, if one searches Google for "'slow usb' + linux" or "'slow file transfer'+'linux'", you can find people using every distro under the sun complaining about this very same problem going as far back as 2004, and probably before.
[*]Arup - you're not helping. For 27 pages of thread, going all the way back to Post #2 on May 6th, you're contributions basically amount to telling people it's all in their heads, mixed with an ample dash of Windows bashing. If you're not affected by this bug, great! Good for you! Now kindly get lost and let those of us who are affected by it discuss our ideas. Your meanderings are off topic at best, and counter productive at worst.
[/LIST]
For me, as you may have read in some of the other threads I've listed, this bug became apparent when I was using Hardy Heron and got kernel update 2.6.24-18. Until then, using Edgy, Feisty, Gutsy, and even the default Ubuntu-shipped CD install of Hardy Heron with kernel 2.6.24-16 (IIRC) on the exact same laptop, the bug wasn't there. (Or if it was, it wasn't nearly as noticeable.)

The hallmarks seem to be the same across the years and across the distros:

[LIST]
[*]Low, but not terribly low starting speeds to file transfers of various types;
[*]Speeds that degrade over time to terribly slow;
[*]Sometimes speeds start slow and build up over time;
[*]Sometimes, in transfers that slow over time, disk I/O freezes completely, effectivly halting the transfer.
[*]GUI sluggishness or even total non-responsiveness while transfers are taking place;
[*]The number of files being transferred doesn't seem to play as key of a role in the bug's severity as does the size of the file(s) being transferred. Me, for instance, In Hardy, Intrepid, Jaunty, and now Mint 7, the threshhold seems to be around 700MB - any single file below 700MB in size transfers at a decent rate from start to finish, any single file or group of files that add up to more than 700MB in size start at around half the "normal" speed and degrades over time to barely a crawl.
[*]Disabling legacy USB support in BIOS rarely, if ever, has any effect other than to make USB ports unusable on hardware with certain BIOS.
[*]Contrary to popular belief, it has absolutely nothing to do with Legacy USB support, nor does it have anything to do with the ehci, uhci, or ahci modules. (You can modprobe and blacklist your heart out and it will never change a thing.)
[*]pci=routeirq as a kernel boot option seems to work for some, but for others it makes things way worse.
[*]It seems that nobody in the kernel team (including "the USB guys") nor the various distro kernel teams, gives a rat's ***. This bugs is, arguably, years old and it's never been touched. I've seen bug reports shot down before they ever got anywhere, even though in Kernel Bug 12309, someone mentions that it's totally reproduceable and even affects Linus' Master Copy.
[/LIST]
All that being said, I'm going to go try the Mainline Kernel 2.6.31 now that I see it's finished, though I don't expect that it will change much.

To this day, I can totally reproduce what kicks this bug into motion (on my system, anyway) by reinstalling Ubuntu 7.04/7.10/8.04 from my official Canonical CDs and allowing it to update from the default kernel/headers/modules to whatever versions are current (or final) for those releases. I've made the offer before, and I'll make it again:
[B]
I will gladly offer SSH/VNC/whatever kind of remote access to a fresh Ubuntu 8.04 install to whomever thinks they have the knowledge or the gumption to identify the cause and possibly offer a solution to this bug.[/B]

System/hardware details attached.

**EDIT: **After two days, I guess I can add myself to the list of people that the Mainline Kernel doesn't work for. I tried a couple different versions according to the chart they provide at the site - no go on all of them.

I had some issues in the meantime with an external USB HDD that I just picked up which (for whatever reason) was formatted NTFS. Bah! While copying files to or from that drive, my system would become totally unusable - but I mainly blame the poor NTFS support rather than this particular bug, though I suspect it does play a part, however small. I managed move enough stuff around and was able to format half the drive at a time as ext3, and now I have "normal" (but not standard) speeds to and from it. Moving files between partitions on my internal HDD are just as slow and painful as ever.

When all's said and done, I'm back to Kernel 2.6.28-15.52 i686, and everything is as it was: 10 to 15Mb/s maximum on transfer speeds that degrade over time to <5Mb/s or worse, whether to external or internal devices.

---

### Post by welchy on 2009-09-29
Detroit/Zero,

An interesting and well thought out summary, and I agree with a lot of it, and thanks for geting the thread back on track !

I would make the following points though :

1. Its possible that all of the problems you have listed are not directly related to 1 bug. I suspect more than one bug, and as you say some of this goes back 5 years. I come back to this in point 4.

2. Don't be too quick to jump to the conclusion that the bugs you are seeing are not hardware specific. I can reproduce the slow SATA transfer and slow USB transfer problems 100% of the time on my  MSI p965 Platinum mother board machine. My other 2 machines are unaffected (using same install media) I have tried all combinations of other components (i.e. hard disks etc) that I can think of, the only common component to me seeing the bug is the mainboard. 

I would be interested to hear if you run Ubuntu (or Mint, or Debian even) on any other machines and if you see the same bug.

3. When using debian testing on the affected machine the bug goes away, which kind of suggests (but not 100%) a ubuntu issue. I have not tried any other distros.

4. Doing any of the other 'fixes' in this thread did nothing for me. I suspect some people get slow USB transfers, think they have this bug, turn of legacy (or similar fix) and think they have fixed this bug, whereas they really had some other issue (Slow USB transfers to be sure, but maybe not this specific bug). I notice that most people who think they have fixed this bug are usually referring to slow USB transfers and rarely mention SATA transfers being affected.

5. I tried vanilla, mainline and even real-time kernels on my affected machine and none of them made a difference.

6. In my experience using HDPARM to test for the bug is useless, it reports speeds as fine but when you actually copy a file the results are terrible. Anyone who thinks they have this bug should just 'time cp file dest' for a large file then do the math to see your transfer speeds. Mine were always about 4 megabytes a second for a large file.


Summary :

All of my reading and testing of this bug (or bugs) leads me to believe Ubuntu (and derivatives) have a conflict with a small number of motherboards causing slow SATA and USB transfers and the rest of the 'issues' and 'fixes' in this thread are possibly just fixes for other similar (but not the same) problems.

Would love to hear of someone running a MSI p965 Platinum mainboard and Ubuntu with no SATA or USB transfer problems which would disprove my theory (at least in part).....

---

### Post by detroit/zero on 2009-09-29
> **welchy said:**
> Detroit/Zero,

An interesting and well thought out summary, and I agree with a lot of it, and thanks for geting the thread back on track !

I would make the following points though :

1. Its possible that all of the problems you have listed are not directly related to 1 bug. I suspect more than one bug, and as you say some of this goes back 5 years. I come back to this in point 4.
True enough. For me at first, all I noticed was the USB issue, as I download a lot and am moving lots of large files to/from an external HDD. After a while, I started noticing that moving files around on partitions on my internal SATA drive were also affected. The first time I saw one going slow, I attributed it to poor NTFS support and the fact that it was moving to a Windows NTFS partition. A couple more times, though, of moving files between my various ext3 partitions led me deeper in to the rabbit hole. 

It's very possible they all come from the same root cause, but I do recognized that they could just as easily be completely independant. At the very least, it's all interrelated somehow.
> **welchy said:**
> 2. Don't be too quick to jump to the conclusion that the bugs you are seeing are not hardware specific. I can reproduce the slow SATA transfer and slow USB transfer problems 100% of the time on my  MSI p965 Platinum mother board machine. My other 2 machines are unaffected (using same install media) I have tried all combinations of other components (i.e. hard disks etc) that I can think of, the only common component to me seeing the bug is the mainboard. 

I would be interested to hear if you run Ubuntu (or Mint, or Debian even) on any other machines and if you see the same bug.

3. When using debian testing on the affected machine the bug goes away, which kind of suggests (but not 100%) a ubuntu issue. I have not tried any other distros.
Currently, I'm running Mint 7 Main (based on Jaunty) on my Toshiba. My wife's Acer laptop was running Jaunty until a few days ago, when she switched to Mint as well. Both comps have Intel processors, but that's where the similarity ends - they're not even the same processor. There's evidence of the bugbeing present on both systems. 

I've not had a chance to build Debian. I've not installed Fedora, but I do use the Fedora 11 Live CD on occasion and there's no evidence of slow down there. But, for that matter, Ubuntu CDs from v8.04 and before don't show it, either.

I do have a Backtrack3 (Based on Slax) install on my HDD that I use often, and there's no evidence of problems there, either.

> **welchy said:**
>  4. Doing any of the other 'fixes' in this thread did nothing for me. I suspect some people get slow USB transfers, think they have this bug, turn of legacy (or similar fix) and think they have fixed this bug, whereas they really had some other issue (Slow USB transfers to be sure, but maybe not this specific bug). I notice that most people who think they have fixed this bug are usually referring to slow USB transfers and rarely mention SATA transfers being affected.

5. I tried vanilla, mainline and even real-time kernels on my affected machine and none of them made a difference.
Same here, now. I've tried them all over the last year, and nothing has any effect.
> **welchy said:**
> 6. In my experience using HDPARM to test for the bug is useless, it reports speeds as fine but when you actually copy a file the results are terrible. Anyone who thinks they have this bug should just 'time cp file dest' for a large file then do the math to see your transfer speeds. Mine were always about 4 megabytes a second for a large file.I never understood that, either. Especially as it relates to the USB aspect, people were always wanting my HDPARM output and copies of dmesg. Over and over again: it's a USB2.0 device, is detected as USB2.0 with USB2.0 speeds, hdparm says it goes as fast as advertised, but when it comes down to it... no go.
> **welchy said:**
>  Summary :

All of my reading and testing of this bug (or bugs) leads me to believe Ubuntu (and derivatives) have a conflict with a small number of motherboards causing slow SATA and USB transfers and the rest of the 'issues' and 'fixes' in this thread are possibly just fixes for other similar (but not the same) problems.

Would love to hear of someone running a MSI p965 Platinum mainboard and Ubuntu with no SATA or USB transfer problems which would disprove my theory (at least in part).....
I'd also like to see more widespread reporting of this, with complete hardware profiles attached. I tried something similar with my thread at LQ, but it quickly turned into a support thread for me, with ample arguing between myself and another clown who said it was "all in my head".

I don't know if Jaunty or Karmic comes with inxi or not. Here's my inxi -F output. See if anything jumps out at you. I put an lspci -v in the attachment on my last post if you want it.
```
zero@zero-laptop:~$ inxi -F
System:    Host zero-laptop Kernel 2.6.28-15-generic i686 (32 bit) Distro Linux Mint 7 Gloria - Main Edition
CPU:       Dual core Intel T2080 (SMP) cache 1024 KB flags (sse3 nx) bmips 6915.4 
           Clock Speeds: (1) 1733.00 MHz (2) 1733.00 MHz
Graphics:  Card Intel Mobile 945GM/GMS 943/940GML Express Integrated Graphics Controller X.Org 1.6.0 Res: 1280x800@59.9hz 
           GLX Renderer Mesa DRI Intel 945GM 20090326 2009Q1 RC2 x86/MMX/SSE2 GLX Version 1.4 Mesa 7.4 Direct Rendering No
Audio:     Card Intel 82801G (ICH7 Family) High Definition Audio Controller driver HDA Intel
           Sound: Advanced Linux Sound Architecture Version 1.0.21
Network:   Card Atheros AR242x 802.11abg Wireless PCI Express Adapter driver ath_pci v: 0.9.4
Disks:     HDD Total Size: 870.2GB (21.4% used) 1: /dev/sda Hitachi HTS54161 120.0GB 
           2: /dev/sdb USB_3.5" 750.2GB 
Partition: ID:/ size: 8.8G used: 4.0G (48%) ID:/home size: 74G used: 64G (91%) ID:swap-1 size: 1.50GB used: 0.01GB (1%) 
Sensors:   System Temperatures: cpu: 58.0C mobo: N/A 
           Fan Speeds (in rpm): cpu: N/A 
Info:      Processes 167 Uptime 8:47 Memory 727.8/993.2MB Client Shell inxi 1.1.13 
```

---

### Post by Arup on 2009-09-29
Very true about different makes of motherboard. Its a BIOS and design issue and very much related to the voltage from the USB port. [http://ubuntuforums.org/showthread.php?t=1276313](http://ubuntuforums.org/showthread.php?t=1276313) Check this thread for more light on this issue, two forum members have sent me mail indicating that they have had superb results after reading this thread and using powered USB hubs.All credits goes to QIII for suggesting the solution. My own Intel boards are not affected by this issue but my ASUS AMD board is. I will be getting a Belkin powered USB hub tomorrow and will report back on the results. Also this bug effects Windows as well including Vista and 7, just not Ubuntu or Linux, plenty of discussion going on about this very same issue on various Windows forums.

---

### Post by Nick Brohman on 2009-09-29
> **Arup said:**
> Very true about different makes of motherboard. Its a BIOS and design issue and very much related to the voltage from the USB port. [http://ubuntuforums.org/showthread.php?t=1276313](http://ubuntuforums.org/showthread.php?t=1276313) Check this thread for more light on this issue, two forum members have sent me mail indicating that they have had superb results after reading this thread and using powered USB hubs.All credits goes to QIII for suggesting the solution. My own Intel boards are not affected by this issue but my ASUS AMD board is. I will be getting a Belkin powered USB hub tomorrow and will report back on the results. Also this bug effects Windows as well including Vista and 7, just not Ubuntu or Linux, plenty of discussion going on about this very same issue on various Windows forums.
Hello , I am one of those who have just added a powered USB hub and not only is my transfer from Camera to PC speed increased, the rate of data collection with the scanning I have just done is making the job enjoyable not tedious as it has been for this very inexperienced user (5 wks.)
I purchased economically & got a Logitech Premium4-Port USB Hub for Notebooks. It reputedly offers up to 480 Mbps transfers. It can be used both powered or not, is convenient for portability or desktop. I've just swapped the short PC connector for the cable I used with my Canon Powershot.

Nicko

---

### Post by welchy on 2009-09-29
> **Nick Brohman said:**
> Hello , I am one of those who have just added a powered USB hub and not only is my transfer from Camera to PC speed increased, the rate of data collection with the scanning I have just done is making the job enjoyable not tedious as it has been for this very inexperienced user (5 wks.)
I purchased economically & got a Logitech Premium4-Port USB Hub for Notebooks. It reputedly offers up to 480 Mbps transfers. It can be used both powered or not, is convenient for portability or desktop. I've just swapped the short PC connector for the cable I used with my Canon Powershot.

Nicko

Hi Nick,

Thanks for the info.

I agree you had an issue and I agree that your new hub seems to have solved your problem, I just don't think that you are seeing the same bug that affects SATA and USB performance that we are trying to resolve in this thread.

If it was purely a hardware problem then using a different OS should not fix the prob, but many people report that rebooting to windows gives them much better USB transfer speed. I did this test myself about an hour ago, reboot to VISTA and got 4 times the USB throughput on my affected machine.

As far as I can tell, this thread was started to resolve the bug where USB *AND* SATA speeds drop to a terrible level, in some cases around 2 meg a second. 2mb per second for USB is bad, but 2mb per second for internal SATA is AWFUL.

Nick, did you observe any SATA speed problems ?

---

### Post by detroit/zero on 2009-09-29
> **welchy said:**
> I agree you had an issue and I agree that your new hub seems to have solved your problem, I just don't think that you are seeing the same bug that affects SATA and USB performance that we are trying to resolve in this thread.

If it was purely a hardware problem then using a different OS should not fix the prob, but many people report that rebooting to windows gives them much better USB transfer speed. I did this test myself about an hour ago, reboot to VISTA and got 4 times the USB throughput on my affected machine.
This "solution" to the USB problem has been making the rounds for a good while now, and is mentioned in one of the threads I link to in my first post here.

Aside from my internal SATA drive, my primary USB storage device is a 750GB hard drive made by the same manufacturer as my laptop (Toshiba) and of course, has it's own external power supply. If Flash memory were all that was affected, I think you'd be on to something there. The fact that USB transfers are slow on self-powered devices as well sort of negates it. I mean, I'm glad it helped you and all, but there's a bigger problem than having to source a couple milliamps of current.
```
zero@zero-laptop:~$ sudo !!
sudo lsusb -v
Bus 001 Device 005: ID 0930:0b09 Toshiba Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0930 Toshiba Corp.
  idProduct          0x0b09 
  bcdDevice            1.12
  iManufacturer           2 TOSHIBA
  iProduct                3 USB 3.5"-HDD
  iSerial                 1 000f285a
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          4 Bulk Only Configuration
    bmAttributes         0xc0
**      Self Powered**
**    MaxPower                2mA**
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              5 Bulk Only Interface
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0001
  Self Powered

```

---

### Post by welchy on 2009-09-29
Detroit/Zero,


When I do a clean boot of 9.04 and a 'time cp an_file any_dest' I am getting around 2-3mb per second (4 mins+ to copy a CD sized iso)

This is copying from a 250g internal SATA to itself with NO USB DEVICES CONNECTED AT ALL (Well apart from my mouse ;-) )

Can you try a similar copy and let me know if your SATA speed is as bad ?

Interestingly, same machine I can SCP off the box to another machine as fast as my network allows (11 mb/sec)

Looks like its the write that is affecting my SATA transfer speeds not the read....

---

### Post by Arup on 2009-09-29
[http://www.everythingusb.com/vista-sp1-usb-performance-14274.html](http://www.everythingusb.com/vista-sp1-usb-performance-14274.html)

 Crave did some testing in their labs and noticed a 44% to 54% decrease in write speeds to USB drives.

[http://forums.techpowerup.com/showthread.php?t=86517](http://forums.techpowerup.com/showthread.php?t=86517)

Also enabling legacy support for USB might be slowing the ports to USB 1 specs thereby causing slow transfer speeds.

---

### Post by welchy on 2009-09-29
Detroit/Zero,

Tried to PM you but forum won't allow it because I have not made enough inane posts ;-)

If you can PM me would appreciate it.

Thx !

---

### Post by detroit/zero on 2009-09-29
> **welchy said:**
> Detroit/Zero,


When I do a clean boot of 9.04 and a 'time cp an_file any_dest' I am getting around 2-3mb per second (4 mins+ to copy a CD sized iso)

This is copying from a 250g internal SATA to itself with NO USB DEVICES CONNECTED AT ALL (Well apart from my mouse ;-) )

Can you try a similar copy and let me know if your SATA speed is as bad ?

Interestingly, same machine I can SCP off the box to another machine as fast as my network allows (11 mb/sec)

Looks like its the write that is affecting my SATA transfer speeds not the read....
Mine, surprisingly, didn't go that slow. Here's my output for the timed cp. To keep things consistent, I disconnected all USB devices (except for the last test, obviously) and the test file is the F11 iso. ls -al says it's about this big:
```
zero@zero-laptop:~$ ls -la | grep Fedora
-rw-r--r--  1 zero zero 721569792 2009-09-29 19:30 Fedora-11-i686-Live.iso
```

First, from my storage location up one level to my home dir (all within the same ext4 partition):
```
zero@zero-laptop:~/Incoming_Files$ time cp Fedora-11-i686-Live.iso  ..
  
real    1m22.890s
user    0m0.068s
sys    0m4.244s
```
Next, from my home folder (ext4) to my Windows NTFS C:/ drive (bah!):
```
zero@zero-laptop:~$ time cp Fedora-11-i686-Live.iso /media/SQ004286V02

real    1m38.892s
user    0m0.120s
sys    0m4.928s
```
From my home dir directly to / (ext4 to ext4):
```
root@zero-laptop:/home/zero# time cp Fedora-11-i686-Live.iso /

real    1m16.058s
user    0m0.052s
sys    0m3.592s
```
And finally, from my home dir to my 750GB USB HDD (ext4 to ext3):
```
zero@zero-laptop:~$ time cp Fedora-11-i686-Live.iso /media/disk

real    0m42.517s
user    0m0.024s
sys    0m5.688s
```

It's pretty consistent. It's a lot better than what I remember the results being the last time I did this sort of test. It's also pretty different than the results I get inside Nautilus.

Not sure what to make of it all..

---

### Post by Nick Brohman on 2009-09-29
> **welchy said:**
> Hi Nick,

Thanks for the info.

I agree you had an issue and I agree that your new hub seems to have solved your problem, I just don't think that you are seeing the same bug that affects SATA and USB performance that we are trying to resolve in this thread.

If it was purely a hardware problem then using a different OS should not fix the prob, but many people report that rebooting to windows gives them much better USB transfer speed. I did this test myself about an hour ago, reboot to VISTA and got 4 times the USB throughput on my affected machine.

As far as I can tell, this thread was started to resolve the bug where USB *AND* SATA speeds drop to a terrible level, in some cases around 2 meg a second. 2mb per second for USB is bad, but 2mb per second for internal SATA is AWFUL.

Nick, did you observe any SATA speed problems ?

Not knowing where to look for SATA problems, I don't know about that.

If you could show me what to look for, I'll do so but I must say I prefer IDE burners to SATA. The D/L SATA burner that was in this box at purchase worked for two weeks.
My previous PC had a 20x SATA burner & that didn't work very well after about 6 weeks. As you will see my HDD is SATA & that seems to be running well.

My HDD is SATA, I used a Canon A470 Powershot Digital cam with USB cable from a JVC Everio HD Camcorder downloading via the Logitech hub thru' what looks to me to be the keyboard port at the front of the PC.

I have an MSI K9N6PGM2 motherboard.

I have downloaded up to a thousand pix taken at 3072 x 2304 & that has taken a fair while. The download tonight was of 143 taken at 1600 x 1200 and the speed of transfer was very, very, fast.

I have since scanned about 150 photos & with setting up the area to scan, tha job was quick, when I get co-ordinated, I think I could do about 50 or more scans/hour.

My all- in-one is a HP 5280 Photosmart, Ported thru' one of the rear Ports.

What I've noticed is that it is fast, in fact it is just like tuning an engine, give the engine the best chance of doing it's job & you will be rewarded with trouble free motoring. If you make an engine labour unnecessarily, performance will suffer.

My point is, I tried the suggestion given to me by Arup and QIII. It worked for me.

As for rebooting to Windows, that is an anathema to me, my views on MS are elsewhere in these forums.

Nicko..:)

ps I'm just about to shoot 987 pix at 3072 x 2304 & if I can download them in less than a 1/2 hr. then I have a solution to a problem I don't have yet....N

Have [COLOR=Red]downloaded 1,900[/COLOR] pix in roughly [COLOR=Red]50 mins[/COLOR].. as it took nearly an hour to download 1,000 before getting the hub, I think my speed of transfer has increased...n

---

### Post by bapoumba on 2009-09-30
The thread has been cleaned _again_ and last conversation removed.

Please, keep it on tracks. Last chance. Next time it'll be gone for good. Thanks.

---

### Post by ibuclaw on 2009-09-30
> **detroit/zero said:**
> Mine, surprisingly, didn't go that slow. Here's my output for the timed cp. To keep things consistent, I disconnected all USB devices (except for the last test, obviously) and the test file is the F11 iso. ls -al says it's about this big:

<snip>

Not sure what to make of it all..

I would very much like to see the output of
```
df -i
```
If I remember correctly, the "slowness" is due to the default block scheduler, cfq. Which is loosing some efficiency on the file transfer throughput with its "fair-share" style I/O. Setting it to "deadline", along with some other tweaks may improve the throughput of the disk, allowing greater transfer speeds, at the cost of keeping the writeback data in cache for a little while longer. Meaning that in the result of a crash, data may be lost (see the Bug #317781 in Launchpad, that pretty much explains the downsides).
 Not surprisingly too, the speed of transfer speeds is also linked to the number of inodes on the disk.

The more free inode space, the quicker the transfer will be. Hence why I ask for '**df -i**'

Regards
Iain

---

### Post by detroit/zero on 2009-09-30
> **tinivole said:**
> I would very much like to see the output of
```
df -i
```If I remember correctly, the "slowness" is due to the default block scheduler, cfq. Which is loosing some efficiency on the file transfer throughput with its "fair-share" style I/O. Setting it to "deadline", along with some other tweaks may improve the throughput of the disk, allowing greater transfer speeds, at the cost of keeping the writeback data in cache for a little while longer. Meaning that in the result of a crash, data may be lost (see the Bug #317781 in Launchpad).
 Not surprisingly too, the speed of transfer speeds is also linked to the number of inodes on the disk.

The more free inode space, the quicker the transfer will be. Hence why I ask for '**df -i**'

Regards
Iain
As requested:```
zero@zero-laptop:~$ df -i
Filesystem            Inodes   IUsed   IFree IUse% Mounted on
/dev/sda6             586368  173092  413276   30% /
tmpfs                 127134       4  127130    1% /lib/init/rw
varrun                127134      78  127056    1% /var/run
varlock               127134       3  127131    1% /var/lock
udev                  127134    1677  125457    2% /dev
tmpfs                 127134       1  127133    1% /dev/shm
lrm                   127134      17  127117    1% /lib/modules/2.6.28-15-generic/volatile
/dev/sda7            4915200   74391 4840809    2% /home
/dev/sdb1                  0       0       0    -  /media/disk
/dev/sdc2            45793280    6196 45787084    1% /media/disk_
```My 750GB HDD is at sdc2 at the moment, but there is also a 2GB thumb drive at sdb1 that I'm putting a Fedora ISO on with Unetbootin.

Sda6 and sda7 are root and home, respectively, on the same 120GB SATA drive.

---

### Post by ibuclaw on 2009-09-30
> **detroit/zero said:**
> As requested:```
zero@zero-laptop:~$ df -i
Filesystem            Inodes   IUsed   IFree IUse% Mounted on
/dev/sda6             586368  173092  413276   30% /
tmpfs                 127134       4  127130    1% /lib/init/rw
varrun                127134      78  127056    1% /var/run
varlock               127134       3  127131    1% /var/lock
udev                  127134    1677  125457    2% /dev
tmpfs                 127134       1  127133    1% /dev/shm
lrm                   127134      17  127117    1% /lib/modules/2.6.28-15-generic/volatile
/dev/sda7            4915200   74391 4840809    2% /home
/dev/sdb1                  0       0       0    -  /media/disk
/dev/sdc2            45793280    6196 45787084    1% /media/disk_
```My 750GB HDD is at sdc2 at the moment, but there is also a 2GB thumb drive at sdb1 that I'm putting a Fedora ISO on with Unetbootin.

Sda6 and sda7 are root and home, respectively, on the same 120GB SATA drive.

And if you were to issue the following on the sda hard drive (you could try sdb and sdc also, to see if it makes any difference too):
```

echo 50 > /proc/sys/vm/vfs_cache_pressure
echo 1024 > /sys/block/sda/queue/nr_requests

```
And then switch between "deadline" and "cfq":
```

echo deadline > /sys/block/sda/queue/scheduler
/* Do tests */
echo cfq > /sys/block/sda/queue/scheduler
/* Do tests */

```
Do you get a noticeable difference between the two?


Also, some people find that this has a huge effect on the system file transfer speeds:
```

echo 1 > dirty_background_ratio
echo 2 > dirty_ratio

```
But that probably won't stop any stuttering, and it certainly isn't an "end all, be all" workaround for the slowness either. Infact, if at all any process runs a sync(), you will quickly see a sudden degrade in performance as the disk goes into a heavy duty operation as it writes all data back to disk.

But, that can easily be worked around too,
Bodhi's [Netbook Optimisation]("http://blog.bodhizazen.net/linux/netbook-optimization/") along with one of my guides to prevent [Firefox 3.0 from calling fsync()]("http://ubuntuforums.org/showthread.php?t=1103926") and optionally fdatasync() too, which should help you see a gain in I/O, as well as application performance.

Regards
Iain

---

### Post by detroit/zero on 2009-09-30
> **tinivole said:**
> And if you were to issue the following on the sda hard drive (you could try sdb and sdc also, to see if it makes any difference too):
```

echo 50 > /proc/sys/vm/vfs_cache_pressure
echo 1024 > /sys/block/sda/queue/nr_requests

```And then switch between "deadline" and "cfq":
```

echo deadline > /sys/block/sda/queue/scheduler
/* Do tests */
echo cfq > /sys/block/sda/queue/scheduler
/* Do tests */

```Do you get a noticeable difference between the two?


Also, some people find that this has a huge effect on the system file transfer speeds:
```

echo 1 > dirty_background_ratio
echo 2 > dirty_ratio

```But that probably won't stop any stuttering, and it certainly isn't an "end all, be all" workaround for the slowness either. Infact, if at all any process runs a sync(), you will quickly see a sudden degrade in performance as the disk goes into a heavy duty operation as it writes all data back to disk.

But, that can easily be worked around too,
Bodhi's [Netbook Optimisation]("http://blog.bodhizazen.net/linux/netbook-optimization/") along with one of my guides to prevent [Firefox 3.0 from calling fsync()]("http://ubuntuforums.org/showthread.php?t=1103926") and optionally fdatasync() too, which should help you see a gain in I/O, as well as application performance.

Regards
Iain
I already have vfs_cache_pressure set to 50 in /etc/sysctl.conf, but as for the other workarounds, that's the first I've seen of any of them as they relate to this.

I'll run some experiments over the next couple days and report my findings back here. 

Thanks for the tips.

---

### Post by Arup on 2009-09-30
Wondering if anyone has tried alternate file managers like PC Man etc. to see if this issue goes away.

---

### Post by tuberculo on 2009-10-01
Would opening a new bug report be useful?

---

### Post by ibuclaw on 2009-10-02
> **tuberculo said:**
> Would opening a new bug report be useful?

No, this is already a known issue, and there are plenty of examples of why this is happening/what went wrong.

Thus far though, any attempt at trying to fix it has been a wasted effort/did not really make much difference in comparison to before/after patch. But we still have lots of ways to work around the issue, albeit, by "virtually" writing data to disk without any write occurring (changes are made in memory, and are sync'd at a later date, ie: after a certain period of time when the dirty writeback cache is expired/nearing full, before an umount of a drive, or before shutdown of the system).

Regards
Iain

---

### Post by hybris99 on 2009-10-03
Hello,

I am not sure that I have the "satan slow transfer" bug, perhaps I just have a slow hard drive. I don't know. Yesterday I got 3Mb/s copying Mp3 files. I got 8Mb/s copying .iso files. (Copying folder to folder on the same partition.) 

My hard drive is a Western Digital 500Gb Eco Green something. (The name doesn't really say "I'm fast")


Anyway, here is what I did to increase my performance:

I changed the "read ahead" for the disk. 

For example, the following will get your current read ahead value:
```

sudo blockdev --getra /dev/sda

```Mine said 256 at first so I changed it to
```

sudo blockdev --setra 65536 /dev/sda

```Experimented with different values for this to get much better transfer rates (4096, 16384, 32768, 65536, 131072, 262144). 

By doing this I got my Mp3 transfer up from 3Mb/s to 6-10 Mb/s. Large file copy increased from 8-15 Mb/s up to 24 Mb/s.

Hope this information helps!

/Hybris99

---

### Post by theZoid on 2009-10-04
> **hybris99 said:**
> Hello,

I am not sure that I have the "satan slow transfer" bug, perhaps I just have a slow hard drive. I don't know. Yesterday I got 3Mb/s copying Mp3 files. I got 8Mb/s copying .iso files. (Copying folder to folder on the same partition.) 

My hard drive is a Western Digital 500Gb Eco Green something. (The name doesn't really say "I'm fast")


Anyway, here is what I did to increase my performance:

I changed the "read ahead" for the disk. 

For example, the following will get your current read ahead value:
```

sudo blockdev --getra /dev/sda

```Mine said 256 at first so I changed it to
```

sudo blockdev --setra 65536 /dev/sda

```Experimented with different values for this to get much better transfer rates (4096, 16384, 32768, 65536, 131072, 262144). 

By doing this I got my Mp3 transfer up from 3Mb/s to 6-10 Mb/s. Large file copy increased from 8-15 Mb/s up to 24 Mb/s.

Hope this information helps!

/Hybris99

My read ahead was 256....changing it to 1024 made a noticeable difference...I didn't gain with numbers higher than that, but rather slowed down a little....average was probably around 26 Mb/s.  250 gig 7200rpm WD HD.

---

### Post by Shawn Reist on 2009-10-13
Hello,

I have not had time to try some of the more recent solutions to the slow transfers...

But I have put 9.10 beta on one of my system hard drives...

USB read write transfers are now at 13.5 - 15.x MB/s for my 4 gig PNY USB 2 stick.

I have no idea what the differences are… I would need some direction on tests to try...

Any suggestions?

---

### Post by isecore on 2009-10-13
> **hybris99 said:**
> Hello,

I am not sure that I have the "satan slow transfer" bug, perhaps I just have a slow hard drive. I don't know. Yesterday I got 3Mb/s copying Mp3 files. I got 8Mb/s copying .iso files. (Copying folder to folder on the same partition.) 

My hard drive is a Western Digital 500Gb Eco Green something. (The name doesn't really say "I'm fast")

Never the less you should get more than 8-10 MB/sec with it. Even a "slow" drive with todays standards are easily capable of 30-40-60 MB per second, not to mention the theoretical maximum for most buses (such as SATA) which are capable of several gigabytes per second of bandwidth.

I have a 10 year-old IBM-drive (the infamous "Deathstar") which is capable of around 35 MB/sec. So don't undersell your drive.

---

### Post by detroit/zero on 2009-10-18
I finally found the source of the problem, at least as far as my setup goes. It seems that Tinvole was a step ahead of me with this, and I had to get to it the hard way, but here's how I did it:

I got frustrated with the Ubuntu/Mint slow transfer rates and decided to check out Fedora. I installed it and ran it for a week or so. Fedora has excellent file transfer speeds, both to and from USB devices and SATA partitions. I copied the kernel config from my Fedora install.

I loaded Mint back into my system and compared the kernel config there with the one I pulled from Fedora. After compileing a half dozen kernels, *Kernel I/O Scheduling* turned out to be the answer.

By default, since I don't know when, Ubuntu started using CFQ (Completely Fair Queuing) for it's Kernel I/O Scheduling default, but there are a few other options available. Anticipatory and Deadline are the two that seem to work best.

I recompiled a new kernel with the Anticipatory I/O Scheduling and, lo and behold, I had my old 30MB/s USB transfer speeds back, and SATA performance was improves two or three times. (Though it's still not as fast a I think an intra-partition transfer should be on a single SATA hard drive, 10 or 12 megs a second is a lot better than two or three.) There's a noticeable drop in system performance while transfers are taking place, but, at least for me, it wasn't half as bad as it was with CFQ enabled.

Take all that with a grain of salt, though, because I've found [forum posts from as far back as 2006]("http://ubuntuforums.org/showthread.php?t=119546") that show people enabling CFQ for the exact same reasons we'll want to disable it here.

Due to some unrelated experiments I was running with Xorg and the catastrophic fail that is the current Intel Video driver setup, I borked my install beyond repair and had to re-do it. Further research into the solution showed me that you can select a default I/O Scheduler at boot up by passing an option on to the kernel.

I found that by appending the string ***elevator=as*** to the end of the kernel parameters in /boot/grub/menu.lst, you can enable anticipatory I/O scheduling. The strings ***elevator=deadline*** and ***elevator=noop*** can be used as well, though I'm not so sure about their effects.
```
title        Linux Mint 7 Gloria, kernel 2.6.28-15-generic
root        (hd0,7)
[COLOR=Blue] kernel        /vmlinuz-2.6.28-15-generic root=/dev/sda6 ro quiet splash elevator=as[/COLOR]
initrd        /initrd.img-2.6.28-15-generic
quiet
```It is also possible to change the I/O scheduler for certain devices without making it a system default, as can be found in [these two]("http://www.cyberciti.biz/faq/linux-change-io-scheduler-for-harddisk/") [blog posts]("http://planet.admon.org/howto/how-to-change-default-io-scheduler/").

I'd be interested in seeing if any of you get similar results by trying these solutions.

---

### Post by dakochan on 2009-10-19
Hi Detroit/Zero,

I've changed the kernel parameters in boot menu, and the result for the first attempt with a 700MB file is:
[INDENT][I]External SATA (NTFS) to Internal SATA (ext3) -> 16-17 MB/s
Internal SATA (ext3) to External SATA (NTFS) -> 20 MB/s[/I][/INDENT]
Both speed are quite amazing for me.
Let me try for a week and see how consistent this solution is. Because  most of the solutions that I tried were only effective for 1st or 2nd attempted, after that the transfer rate came back to the lousy transfer rate.

Thanks Detroit/Zero. I'll be back in a week.

---

### Post by darco on 2009-10-20
Experimented using elevator=as as well as pci=routeirq. Dindt get a chance to try elevator on my x64 but its fine w/pci=routeirq

4.1gb file
Karmic x32 elevator=as enabled
USB (NTFS) to Internal SATA (ext4) -> 19 MB/s approx 4mins
Internal SATA (ext4) to USB (NTFS) -> _3 MB/s approx approx 20mins_


Karmic x64 pci=routeirq enabled
3.3gb file

USB (NTFS) to Internal SATA (NTFS) -> 20 MB/s approx 3mins
Internal SATA (NTFS) to USB (NTFS) -> 20 MB/s approx 3mins
External (NTFS) to Internal Sata (Ext4) -> 30mb approx 3mins   

Windows 7
4.1gb
USB (NTFS) to Internal SATA (NTFS) -> 23 MB/s approx 3mins
Internal SATA (NTFS) to USB (NTFS) -> 13 MB/s approx 7mins

---

### Post by TheLions on 2009-10-23
I had expirencing same slowdowns while copying from: 
IDE HDD <-> SATA HDD
IDE HDD <-> External USB Drive

on MSI nForce4Ultra MBO, AMD Athlon64 X2.

Turning off in BIOS USB Keyboard support and USB Mouse support improved transfer rate.

---

### Post by slumbergod on 2009-10-27
I was one of those people who have complained about crappy USB transfer speeds over the last two or three Ubuntu releases.

It was never my pc (same problem across several different laptops) and nor was it my USB flash drive (works fast-as under Windows).

It wasn't DMA not working and it was not incorrectly loading modules.

In the end I never solved the problem; I just learned to live with it. I just put it down to one of the remaining issues with Linux that never seems to get closer to being sorted. Since it doesn't affect everyone it was never marked as a priority. 

No matter how much I love linux (I don't use anything else) there are still some things that suck. USB data transfer is one of them.

---

### Post by GuiGuy on 2009-10-27
> **slumbergod said:**
> I was one of those people who have complained about crappy USB transfer speeds over the last two or three Ubuntu releases.
<snip>
No matter how much I love linux (I don't use anything else) there are still some things that suck. USB data transfer is one of them.

I note that since installing 9.10 my slow transfer issues are resolved. USB xfer of a 7.5M musical file is almost instantaneous now. A bit like Windows, really :D

PS: I did a clean install though.

---

### Post by detroit/zero on 2009-10-27
> **slumbergod said:**
> In the end I never solved the problem; I just learned to live with it. I just put it down to one of the remaining issues with Linux that never seems to get closer to being sorted. Since it doesn't affect everyone it was never marked as a priority. 

No matter how much I love linux (I don't use anything else) there are still some things that suck. USB data transfer is one of them.
Yeah, but there's a new GDM theme... And, boy oh boy, do those windows ever wobble!

Come on, man! Where's your priorities?

---

### Post by Arup on 2009-10-28
Well there is always a nice Aero theme, the registry, the hype, the party, the fancy GUI, the new AV, HIPS, list goes on......... old wine in new bottle with new wrapper.

---

### Post by detroit/zero on 2009-10-28
> **Arup said:**
> Well there is always a nice Aero theme, the registry, the hype, the party, the fancy GUI, the new AV, HIPS, list goes on......... old wine in new bottle with new wrapper.
If that's your cup of tea knock yourself out.

---

### Post by GuiGuy on 2009-10-28
> **Arup said:**
> Well there is always a nice Aero theme, the registry, the hype, the party, the fancy GUI, the new AV, HIPS, list goes on......... old wine in new bottle with new wrapper.

So long as it hasn't [corked]("http://en.wikipedia.org/wiki/Corked") ;)

---

### Post by Arup on 2009-10-28
> **detroit/zero said:**
> If that's your cup of tea knock yourself out.

Hmm as long as its Darjeeling or Oolong.

---

### Post by Arup on 2009-10-28
> **GuiGuy said:**
> So long as it hasn't [corked]("http://en.wikipedia.org/wiki/Corked") ;)

In this case, its already matured vinegar.

---

### Post by Shawn Reist on 2009-10-28
Hello,

well I have tried just about everything here.. except for finding another USB2 expansion card to install into the computer then disabling legacy USB support.

I have a small Logiix powered USB hub. transfer speeds are a little faster but still tapper down to 2-3 Mb/s or worse..

Even with 9.10 beta and RC are now showing signs of degraded USB transfers on my systems.

I played with the schedulers and read ahead states...and made things worse..

maybe it is something with the scheduler or someoen out there knows how to monitor the schedulers to see if there is something happening there with timing... this is all beyond me.

---

### Post by Arup on 2009-10-29
Update to the upcoming Karmic with latest 2.31 kernel should be a important revelation for this issue. Hopefully it should work out for those suffering from it.

---

### Post by Mander on 2009-10-29
Just thought I'd chime in to say that I've tried installing the "vanilla" kernel as well as adding elevator=as and pci=routeirq to menu.lst.  Copying a random file (77 MB) from an external USB HD (FAT32, if it makes any difference) got about 968 kb/second.  I don't think it is any faster than it was.  

The most annoying problem for me, and I'm not entirely sure if it is really related to the transfer speed problem, is that trying to open any folder (on the local disk, external USB drive, flash drives, etc.) is really really slow to respond.  I can go through the menus to Places -> whatever and it sometimes takes over a minute to even open a Nautilus window.  It's worse with USB drives.  After I have opened a folder the first couple of times, it gets faster.

Anyway just thought I'd add my experience with some of the tweaks in this thread!

---

### Post by detroit/zero on 2009-10-29
> **Mander said:**
> Just thought I'd chime in to say that I've tried installing the "vanilla" kernel as well as adding elevator=as and pci=routeirq to menu.lst.  Copying a random file (77 MB) from an external USB HD (FAT32, if it makes any difference) got about 968 kb/second.  I don't think it is any faster than it was.  

The most annoying problem for me, and I'm not entirely sure if it is really related to the transfer speed problem, is that trying to open any folder (on the local disk, external USB drive, flash drives, etc.) is really really slow to respond.  I can go through the menus to Places -> whatever and it sometimes takes over a minute to even open a Nautilus window.  It's worse with USB drives.  After I have opened a folder the first couple of times, it gets faster.

Anyway just thought I'd add my experience with some of the tweaks in this thread!
Yeah, but don't those windows wobble?

---

### Post by Mander on 2009-10-29
Actually, I disabled compiz because the wobbling windows and stuff was not making my graphics card very happy for some reason.  After a while the whole machine locks up.  I got tired of tweaking it (or rather, I got too busy to continue tweaking) and so I just turned it off.

---

### Post by Arup on 2009-10-29
> **Mander said:**
> Actually, I disabled compiz because the wobbling windows and stuff was not making my graphics card very happy for some reason.  After a while the whole machine locks up.  I got tired of tweaking it (or rather, I got too busy to continue tweaking) and so I just turned it off.

Wouldn't you rather have Aero ;)

---

### Post by Mander on 2009-10-30
> **Arup said:**
> Wouldn't you rather have Aero ;)

:eek:

LOL.  I only wish Vista was fast enough to run Aero on this machine.  Might make the whole experience a little more bearable, but even with  windows 95 graphics and everything I can think of turned off, it is like cold molasses.

Hmm. Maybe there is actually a hardware problem on this beast?

---

### Post by brdhse1 on 2009-10-31
Bummer, Karmic did not solve this for me.  Tried everything on the forum.  What else can we do about this?  As much as I love Ubuntu/Linux, this is almost a deal breaker for me.

---

### Post by detroit/zero on 2009-10-31
> **brdhse1 said:**
> Bummer, Karmic did not solve this for me.  Tried everything on the forum.  What else can we do about this?  As much as I love Ubuntu/Linux, this is almost a deal breaker for me.
I have first hand knowledge that Fedora 11, as one example, doesn't have this issue. From what I understand from people I've been in contact with, neither does Debian.

Ubuntu [isn't the only distro out there]("http://distrowatch.com/"), you know.

---

### Post by piet8stevens on 2009-10-31
My external USB transfer speed in 9.04 was high (do not know how high - it was never a problem). I just upgraded to 9.10, and now I have these slow speeds as well (780Kbytes/s!). Am running on an HP Pavilion TX1000 laptop.

I run both 9.04 and 9.10 without making any changes to the configuration so there must be a change in setup between the two that affects me.

I am new to Linux, so have no idea how to go about solving this.

---

### Post by skotos on 2009-11-02
> **piet8stevens said:**
> My external USB transfer speed in 9.04 was high (do not know how high - it was never a problem). I just upgraded to 9.10, and now I have these slow speeds as well (780Kbytes/s!). Am running on an HP Pavilion TX1000 laptop.

I run both 9.04 and 9.10 without making any changes to the configuration so there must be a change in setup between the two that affects me.

I am new to Linux, so have no idea how to go about solving this.
If you try USB transfer rates after an installation from scratch or from a Live CD, they are as good as before: 25/30 MB/s. 

(See my post on the [feedback page]("http://ubuntuforums.org/showthread.php?t=1305924"), comment 19)

This seems to demonstrate that something goes wrong or does not get updated in the upgrade process and that something has deeply changed in the installation process as well when we are talking about USB hardware and events.

Thus, I would suggest you to simply look for USB problems solutions in the next few days, to let more experts realize the source and suggest good fixes.

---

### Post by nikgare on 2009-11-02
This isn't going to help anyone who like me has pisspoor sata speeds, for example a typle file trynasfer of a file of about 4GB has an speed of about 3 to 4MB/S
This is at best 10 times slower than it should be.

---

### Post by Azraele on 2009-11-03
I confirm that the new kernel and the ubuntu upgrade doesn't solve shxt!!
The issue goes far back in the ubuntu history and it is about time that someone solves it!!!!

however looking out in the /lib/modules/2.6.31-14-generic/kernel/drivers/usb/host/ directory which should have the hi-speed usb 2.0 modules file ehci_hcd and uhci_hci, i found out that these two files are missing.. does anyone have this issue too?

---

### Post by TheLions on 2009-11-03
> **Azraele said:**
> I confirm that the new kernel and the ubuntu upgrade doesn't solve shxt!!
The issue goes far back in the ubuntu history and it is about time that someone solves it!!!!

however looking out in the /lib/modules/2.6.31-14-generic/kernel/drivers/usb/host/ directory which should have the hi-speed usb 2.0 modules file ehci_hcd and uhci_hci, i found out that these two files are missing.. does anyone have this issue too?

```
ls /lib/modules/2.6.31-14-generic/kernel/drivers/usb/host/
```

gives:
hwa-hc.ko  isp116x-hcd.ko  isp1760.ko  oxu210hp-hcd.ko  r8a66597-hcd.ko  sl811_cs.ko  sl811-hcd.ko  u132-hcd.ko  whci  xhci.ko

ubuntu 9.10 amd64

---

### Post by waspinator on 2009-11-03
I'm having very slow transfer rates on 9.10 server between usb and sata also. Is there a way I can benchmark the transfer from cli?

---

### Post by detroit/zero on 2009-11-04
I would say that since the name of this thread is "Slow USB and SATA Transfer Speeds in Jaunty 9.04" and it's over 30 pages long, maybe a new thread for Karmic is in order.

---

### Post by ruffneck on 2009-11-04
I know this isn't a fix but I would like to add that this issue does not seem to affect my Karmic install when trasferring to an external drive connected via eSata.

---

### Post by Azraele on 2009-11-05
Isn't there any kind of linux super expert we can contact to ask for help?
since it doesn't seem that here anybody has even a remote idea on what to do, not to blame anybody, but this problem has at least 4 years..

---

### Post by Azraele on 2009-11-05
Isn't there any kind of linux super expert we can contact to ask for help?
since it doesn't seem that here anybody has even a remote idea on what to do, not to blame anybody, but this problem has at least 4 years..

---

### Post by kixome on 2009-11-05
learn your sata jumpers, most have an option for 150mbps, check the pdfs for you manufacturer!

---

### Post by dakochan on 2009-11-05
According to this thread "http://kerneltrap.org/node/6933", we should disable the sync option when mounting the usb drive.
Anyone know how to disable it?

---

### Post by Azraele on 2009-11-06
> **dakochan said:**
> According to this thread "http://kerneltrap.org/node/6933", we should disable the sync option when mounting the usb drive.
Anyone know how to disable it? 
it is  possible using mount. problem is you can't fix it in /etc/fstab becouse the usbdrive is mounted every time it is plugged in so there is no entry in fstab.

it's a good idea nonetheless

---

### Post by Azraele on 2009-11-08
> **Azraele said:**
> it is  possible using mount. problem is you can't fix it in /etc/fstab becouse the usbdrive is mounted every time it is plugged in so there is no entry in fstab.

it's a good idea nonetheless

but at least for me, it ain't working ):P

---

### Post by brdhse1 on 2009-11-08
Seriously, how can this get escalated??  This is ridiculous.

---

### Post by rockdj on 2009-11-09
First time ever this has happened to me on Ubuntu but it's happening for me on 9.10.  Seems pretty erratic; it was going slow then fast for a bit and then dead slow again.  Happening with an internal copy from my ext3 Linux partition to my NTFS partition...

---

### Post by TheLions on 2009-11-09
> **rockdj said:**
> First time ever this has happened to me on Ubuntu but it's happening for me on 9.10.  Seems pretty erratic; it was going slow then fast for a bit and then dead slow again.  Happening with an internal copy from my ext3 Linux partition to my NTFS partition...

try adding option "async" to your /etc/fstab

---

### Post by Azraele on 2009-11-09
it is not possible! the usbstick is mounted automatically everytime it is plugged in. probably it is doable only with hard drives..but i don't know if adding async to the hard drive line could be useful.. 
i am skeptical..

---

### Post by GuiGuy on 2009-11-10
I had to copy 6G of files to an 8G flash drive today. The PC is pretty smart hardware, Ubuntu 9.10

The copy started of great. Then within a minute or so it was down to a trickle. When I saw it was going to take "about 5 days" to finish the copy I figured "this is no good".

Anyway, I found a solution that sort of works. Make sure that you have network access and a computer with Windows on it. Access the network using the Windows machine and copy the file/s from the Ubuntu PC to the Windows mounted flash drive. 

OK, I'll take my tongue out my cheek now.

---

### Post by skotos on 2009-11-10
If you are running 9.10 and looking a 9.04 post to dig out the dirt and find a solution to the USB problem that comes after Karmic upgrade/installation:

**EVERY USB STICK CAN BE SYSTEMATICALLY/AUTOMAGICALLY MOUNTED AGAIN!** (...and used at full speed)

This is what I have done:[INDENT]I just activated the *Proposed Updates repo* and upgraded the Kernel to **2.6.31-15-generic**.
[/INDENT]That's it.;)

Though it is not safe to run as a regular practice the proposed updates on a production system, this time can be a must to solve this nasty behaviour.
It depends, of course, on how risky can be considered (I would then unflag the Proposed Updates repo soon after and reload the packages list to avoid unnecessary system breaks).

This is - at least - the first definitive solution I have found.

HTH

[COLOR=Blue]**WARNING!!!: SEE POST #341!**[/COLOR]

---

### Post by GuiGuy on 2009-11-10
> **skotos said:**
> 

**EVERY USB STICK CAN BE SYSTEMATICALLY/AUTOMAGICALLY MOUNTED AGAIN!** (...and used at full speed)

This is what I have done:[INDENT]I just activated the *Proposed Updates repo* and upgraded the Kernel to **2.6.31-15-generic**.
[/INDENT]That's it.;)


This doesn't help. These adventurous escapades into the repositories only ever seem to fix things by breaking something else.

---

### Post by GuiGuy on 2009-11-10
> **skotos said:**
> 

This is what I have done:[INDENT]I just activated the *Proposed Updates repo* and upgraded the Kernel to **2.6.31-15-generic**.
[/INDENT]That's it.;)

OK, despite my doubts that this issue would ever be fixed, I updated to 2.6.31-15-generic.

It seems to have actually had a positive effect. A 2G file took only a few minutes to transfer to a USB stick. 

Thanks

---

### Post by Azraele on 2009-11-10
> **GuiGuy said:**
> This doesn't help. These adventurous escapades into the repositories only ever seem to fix things by breaking something else.

I agree. this repo can be nasty bitches, in fact it already happened to me making serious damage to the linux partition and i am looking forward not to lose one again. ;)

I already upgraded to the new kernel and my stats improved a little..:

1.4 Gigs file has a transfer timing of 260 sec..: speed is 5.38 Megs per second. 

It still is not enough for a 2.0 usb.

---

### Post by GuiGuy on 2009-11-10
> **Azraele said:**
> 
1.4 Gigs file has a transfer timing of 260 sec..: speed is 5.38 Megs per second. 
It still is not enough for a 2.0 usb.

On a single 1G file I am seeing a little less than that. 3.5Meg to 4Meg.

Further to that, if there are a bunch of smaller files, say mp3s, xfer speeds slow down substantially. At the end of 100 files the speed was < 1M

---

### Post by rockdj on 2009-11-10
> **TheLions said:**
> try adding option "async" to your /etc/fstab

Thanks heaps, that solves my problem.  The latest kernel update didn't help, but having that option present when I mount my ntfs partition lets me run at 20MB/s+.

Any thoughts on what changed that requires this now?

---

### Post by detroit/zero on 2009-11-11
> **rockdj said:**
> Thanks heaps, that solves my problem.  The latest kernel update didn't help, but having that option present when I mount my ntfs partition lets me run at 20MB/s+.

Any thoughts on what changed that requires this now?
The fact is that this isn't a fix, it's a workaround that only seems to help some people. If you go back to the beginning of this very thread, some people are hailing this as a fix using Jaunty and kernels older than the current one. In fact, if you do a Google search for linux+slow usb, you'll find people naming the async mount option as a fix going all the way back to 2004 and the 2.4 kernel series.

---

### Post by skotos on 2009-11-13
> **GuiGuy said:**
> This doesn't help. These adventurous escapades into the repositories only ever seem to fix things by breaking something else.
[B]_[SIZE=4]WARNING![/SIZE]_
Upgrading from the proposed [COLOR=Red]2.6.31-15.[SIZE=4]28[/SIZE][/COLOR] to the latest proposed 2.6.31-15.[SIZE=4][COLOR=Red]50[/COLOR][/SIZE] can break USB again![/B]

---

### Post by detroit/zero on 2009-11-13
> **skotos said:**
> [B]_[SIZE=4]WARNING![/SIZE]_
Upgrading from the proposed [COLOR=Red]2.6.31-15.[SIZE=4]28[/SIZE][/COLOR] to the latest proposed 2.6.31-15.[SIZE=4][COLOR=Red]50[/COLOR][/SIZE] can break everything again![/B]
I let mine update about four days ago and I can't say I've noticed any breakage.

That being said, and to expand on your warning: People shouldn't be trying experimental fixes and working with unproven packages unless they are prepared to and know how to recover from potentially disastrous outcomes.

---

### Post by skotos on 2009-11-13
> **GuiGuy said:**
> On a single 1G file I am seeing a little less than that. 3.5Meg to 4Meg.

Further to that, if there are a bunch of smaller files, say mp3s, xfer speeds slow down substantially. At the end of 100 files the speed was < 1M
I am still facing this while copying from USB drives to an NFS tree: desolation and despare are the only feelings I can think of.
Starting at 24-26 MB/s and going down to 3-4... and sometimes even stalling... on a 1 Gbps Ethernet LAN!

I think that this might even be related to Nautilus: if I, in fact, try to go back in the tree of the current window, the files operations go worse. It seems a sort of not well multi-threaded job...

---

### Post by skotos on 2009-11-13
> **detroit/zero said:**
> I let mine update about four days ago and I can't say I've noticed any breakage.
YES, the update that may downgrade once again the USB situation has been released just one hour ago!

---

### Post by detroit/zero on 2009-11-13
> **skotos said:**
> YES, the update that may downgrade once again the USB situation has been released just one hour ago!
I didn't realize there was another one. You mentioned 2.6.30-15.50 and when I checked, that's what I had listed```
zero@zero-laptop:~$ uname -a
Linux zero-laptop 2.6.31-15-generic #50-Ubuntu SMP Tue Nov 10 14:54:29 UTC 2009 i686 GNU/Linux
```

---

### Post by Azraele on 2009-11-14
I noticed a thing: i have the latest kernel, if i transfer files (even very large files like 7 gigs) to an external HD the usbspeed is something like 25 Megs per sec, but if i use the usbstick it's much slower.

I think it could be a usbpen driver problem or maybe some strange options on fstab but i really don't know how to chek
Tips are welcome

---

### Post by nomiz on 2009-11-17
How do I downgrade to 2.6.31-15.28? It's not available in de repros :-s

---

### Post by skotos on 2009-11-18
> **nomiz said:**
> How do I downgrade to 2.6.31-15.28? It's not available in de repros :-s
Hi, nomiz, from today - November 18th 2009 - **you do not need 2.6.31-15.x any more** under Karmic.
*You can simply uninstall any proposed update from Synaptic and [COLOR=Blue]**run the update from the regular repositories only.**[/COLOR]*

:popcorn:

If I remind well enough, I rebooted into the old kernel that was not removed and then run Synaptic.
I completely removed all the proposed updates that did not complain about it, then forced the version for all the others in just one step, without exiting Synaptic.
As soon as everything was successfully accomplished, I simply rebooted.:D

After doing this, I updated 

[LIST=1]
[*]initscripts (2.87dsf-4ubuntu12)
[*]system-tools-backends (2.8.2-1ubuntu1)
[*]sysv-rc (2.87dsf-4ubuntu12)
[*]sysvinit-utils (2.87dsf-4ubuntu12)
[/LIST]
:D

The current kernel version I am now successfully running is 2.6.31-14-generic #48

---

