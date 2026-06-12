---
title: "Problems with PCI Intel PRO/1000 GT?"
date: 2009-03-20
forum: x86 64-bit Users
---

### Post by MGlosenger on 2009-03-20
I have just installed an Intel Pro/1000 GT PCI network adapter in my Ubuntu x64 8.10 box and while Ubuntu does recognize the adapter, it continually fails to find a connection.  The same connection works fine with my old (100Mb) adapter, and my router recognizes that something is plugged into it with the new card.

I've tried installing Intel's latest drivers as per their instructions with no luck.  I've tried searching the web without finding anything specific.

I am running kernel version 2.6.27.11.  The full model # of the adapter is PWLA8391GT.

Anyone run into this before or have any ideas?  I'm stumped.

---

### Post by MGlosenger on 2009-03-20
And - Ubuntu reports the card as an Intel 82541PI Gigabit Ethernet Controller, both before and after the new driver.

---

### Post by MaindotC on 2009-03-20
Please post the output of:
```

lspci
lshw -C network
lsmod

```

---

### Post by MGlosenger on 2009-03-20
Here's the output - I notice that lsmod reports a usage count of 0 for e1000..  that seems wrong..?

Thank you.


lspci

00:00.0 Host bridge: ALi Corporation M1695 K8 Northbridge [PCI Express and HyperTransport]
00:01.0 PCI bridge: ALi Corporation PCI Express Root Port
00:02.0 PCI bridge: ALi Corporation PCI Express Root Port
00:03.0 PCI bridge: ALi Corporation PCI Express Root Port
00:04.0 Host bridge: ALi Corporation M1689 K8 Northbridge [Super K8 Single Chip]
00:05.0 PCI bridge: ALi Corporation AGP8X Controller
00:06.0 PCI bridge: ALi Corporation M5249 HTT to PCI Bridge
00:07.0 ISA bridge: ALi Corporation M1563 HyperTransport South Bridge (rev 70)
00:07.1 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:11.0 Ethernet controller: ALi Corporation ULi 1689,1573 integrated ethernet. (rev 40)
00:12.0 IDE interface: ALi Corporation M5229 IDE (rev c7)
00:12.1 IDE interface: ALi Corporation ULi 5289 SATA (rev 10)
00:13.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:13.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:13.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:13.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc R600 [Radeon HD 2900 Series]
01:00.1 Audio device: ATI Technologies Inc R600 Audio Device [Radeon HD 2900 Series]
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller
05:06.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
05:07.0 Ethernet controller: Intel Corporation 82541PI Gigabit Ethernet Controller (rev 05)



lshw -C network

  *-network               
       description: Ethernet interface
       product: 82541PI Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 7
       bus info: pci@0000:05:07.0
       logical name: eth1
       version: 05
       serial: 00:1b:21:2f:e3:68
       size: 10MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm pcix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k3-NAPI duplex=full firmware=N/A latency=32 link=yes mingnt=255 module=e1000 multicast=yes port=twisted pair speed=10MB/s
  *-network
       description: Ethernet interface
       product: ULi 1689,1573 integrated ethernet.
       vendor: ALi Corporation
       physical id: 11
       bus info: pci@0000:00:11.0
       logical name: eth0
       version: 40
       serial: 00:13:8f:61:6b:b4
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=uli526x driverversion=0.9.3 latency=32 link=no maxlatency=40 mingnt=20 module=uli526x multicast=yes port=MII
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 3a:a4:24:fe:42:3c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes



lsmod

Module                  Size  Used by
af_packet              29568  0 
binfmt_misc            18700  1 
rfcomm                 51104  0 
sco                    20612  2 
bridge                 64544  0 
stp                    11268  1 bridge
bnep                   23168  2 
l2cap                  33280  6 rfcomm,bnep
bluetooth              70820  6 rfcomm,sco,bnep,l2cap
ppdev                  16904  0 
powernow_k8            23812  1 
cpufreq_powersave      10368  0 
cpufreq_stats          14468  0 
cpufreq_ondemand       16400  1 
freq_table             13568  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
cpufreq_userspace      12420  0 
cpufreq_conservative    16392  0 
container              12288  0 
video                  29204  0 
output                 11776  1 video
wmi                    15808  0 
sbs                    22288  0 
sbshc                  14592  1 sbs
pci_slot               13704  0 
battery                21128  0 
iptable_filter         11520  0 
ip_tables              28176  1 iptable_filter
x_tables               31752  1 ip_tables
ac                     13448  0 
parport_pc             44200  0 
lp                     19588  0 
parport                50096  3 ppdev,parport_pc,lp
snd_hda_intel         492336  1 
tuner_simple           23700  1 
tuner_types            25728  1 tuner_simple
snd_pcm_oss            52608  0 
snd_mixer_oss          25088  2 snd_pcm_oss
tea5767                15620  0 
snd_pcm                99208  2 snd_hda_intel,snd_pcm_oss
tda9887                19844  1 
tda8290                23428  0 
snd_seq_dummy          11524  0 
snd_seq_oss            42368  0 
snd_seq_midi           15872  0 
tuner                  36300  0 
snd_rawmidi            34176  1 snd_seq_midi
snd_seq_midi_event     16768  2 snd_seq_oss,snd_seq_midi
snd_seq                67168  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
evdev                  20512  10 
pcspkr                 11136  0 
psmouse                51612  0 
cx8800                 44660  0 
cx88xx                 83624  1 cx8800
snd_timer              34320  2 snd_pcm,snd_seq
serio_raw              14596  0 
ir_common              52612  1 cx88xx
snd_seq_device         16404  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    79432  9 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           15364  1 cx88xx
tveeprom               23428  1 cx88xx
k8temp                 13568  0 
soundcore              16800  2 snd
compat_ioctl32         18304  1 cx8800
videodev               46720  4 tuner,cx8800,cx88xx,compat_ioctl32
snd_page_alloc         17680  2 snd_hda_intel,snd_pcm
fglrx                2082944  28 
v4l1_compat            24580  1 videodev
v4l2_common            21888  2 tuner,cx8800
videobuf_dma_sg        22788  2 cx8800,cx88xx
videobuf_core          29956  3 cx8800,cx88xx,videobuf_dma_sg
btcx_risc              13448  2 cx8800,cx88xx
isp1760                29200  0 
i2c_ali15x3            16132  0 
button                 15904  0 
uli526x                26256  0 
i2c_ali1535            15492  0 
i2c_ali1563            16132  0 
i2c_core               36128  12 tuner_simple,tea5767,tda9887,tda8290,tuner,cx88xx,i2c_algo_bit,tveeprom,v4l2_common,i2c_ali15x3,i2c_ali1535,i2c_ali1563
shpchp                 42140  0 
pci_hotplug            39216  1 shpchp
usbhid                 39776  0 
hid                    59072  1 usbhid
ext3                  150544  1 
jbd                    66856  1 ext3
mbcache                17924  1 ext3
sr_mod                 24644  0 
cdrom                  47784  1 sr_mod
pata_ali               19332  0 
sata_uli               13444  0 
ata_generic            14212  0 
sd_mod                 45864  3 
crc_t10dif             10240  1 sd_mod
sg                     45408  0 
ehci_hcd               49548  0 
ohci_hcd               35100  0 
usbcore               175888  5 isp1760,usbhid,ehci_hcd,ohci_hcd
pata_acpi              13568  0 
ahci                   43148  2 
e1000                 146628  0 
libata                201312  5 pata_ali,sata_uli,ata_generic,pata_acpi,ahci
scsi_mod              183160  4 sr_mod,sd_mod,sg,libata
dock                   18464  1 libata
thermal                27424  0 
processor              47800  2 powernow_k8,thermal
fan                    13576  0 
fbcon                  51200  0 
tileblit               11264  1 fbcon
font                   17152  1 fbcon
bitblit                14592  1 fbcon
softcursor             10496  1 bitblit
fuse                   68288  3

---

### Post by MGlosenger on 2009-03-20
Oh, and just to make sure there wasn't something wrong with the card, I plugged it into my Windows XP box and it worked perfectly.

---

### Post by MaindotC on 2009-03-20
Yeah I think the driver may not be loaded.  For example, here's my output - I'm using the zd1211rw driver for my Belkin USB in my sig:
```

zd1211rw               64008  0 
ieee80211softmac       34688  1 zd1211rw
ieee80211              38344  2 zd1211rw,ieee80211softmac
usbcore               170288  5 zd1211rw,usbhid,ehci_hcd,uhci_hcd

```

I found this in the readme file:
> This driver is only supported as a loadable module at this time.  Intel is
not supplying patches against the kernel source to allow for static linking
of the driver.
You may have to modprobe it.  Make sure the module is present by trying:
```

modprobe -l | grep e1000

```
The Intel documentation stated it was called e1000 so you should see it in the listing.  If you do see it, try:
```

sudo modprobe e1000

```
This is all in the readme file so please assure me you've read it all and followed all the directions.

---

### Post by MGlosenger on 2009-03-20
SourceForge's drivers look like a slightly earlier version of the drivers I tried (SF has 8.0.6, Intel has 8.0.9).

I tried to install SourceForge's, using the instructions in the README file included in the archive (they are the same for both versions), but still no go.

---

### Post by MGlosenger on 2009-03-20
modprobe -l does list e1000.ko at the location the makefile copied it.

---

### Post by MaindotC on 2009-03-20
After inserting the module with:
```

sudo modprobe e1000

```
I could only suggest that you make that module part of your startup and I believe that's in /etc/modules, then reboot.  You should not have to reboot to get this to work but me being a "user" and not a "programmer" - someone who understands the kernel and source code and all that - I am unable to help you further :(

---

### Post by MGlosenger on 2009-03-20
Does anyone else have any ideas?

---

### Post by MaindotC on 2009-03-20
Intel made the card, so can you contact their customer service?  If not, I'd suggest filing a bug report.  The support people are dedicated and usually very helpful in finding an answer, but replies can usually span once per day due to the high volume of traffic they handle.  It may be difficult because this seems to be an Intel issue and not a Ubuntu issue.  You may want to verify this by making a small partition and loading a different distribution on it such as Fedora, Debian, or Suse.  Try booting with a livecd like Backtrack and see if it is properly detected.

At this point you also have to start weighing the cost of time trying to figure this out versus returning the card and getting a different one.  I know replacing the card doesn't resolve the issue, but unless you're familiar with the kernel and writing device drivers it may be difficult to troubleshoot.  All the support and documentation you need is included in Ubuntu and its constituents of Linux but as you may guess it would take years for you to be competent in handling these low-level issues and typically that's not necessary for everday operation of a linux system like Ubuntu.

---

