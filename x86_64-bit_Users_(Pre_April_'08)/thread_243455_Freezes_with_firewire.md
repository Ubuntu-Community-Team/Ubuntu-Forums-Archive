---
title: "Freezes with firewire"
date: 2006-08-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by jbernardo on 2006-08-25
Hi,
I have a AMD64 3200+ (first generation) on a msi K8T NEO motherboard. Whenever I do some firewire transfers (rsync to a external drive) it hangs solid after a couple of minutes. I leave a "tail -f /var/log/syslog" running on a konsole just to see if it shows anything, but no luck. The only symptoms are that rsync hangs (running rsync -v on a konsole to have some output) and in 2 seconds the whole system hangs solid. I am unable to get a dmesg output between the rsync hand and the system hanging. ](*,) 
Tha same external disk (and the same rsync command) works if I use USB2 instead of firewire, but with some pauses that coincide with "reset high speed USB device using ehci_hcd" entries in syslog. I can only imagine that it is the first of these pauses that kills firewire and my pc.
Any ideas? :-k 
Thanks!

---

### Post by jbernardo on 2006-08-25
Forgot to add the output of lspci:

```
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8385 [K8T800 AGP] Host Bridge (rev 01)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
0000:00:06.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
0000:00:08.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 03)
0000:00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
0000:00:0d.0 RAID bus controller: Promise Technology, Inc. PDC20378 (FastTrak 378/SATA 378) (rev 02)
0000:00:0e.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
0000:00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
0000:00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
```


and lsmod:
```
Module                  Size  Used by
sbp2                   27268  0
ohci1394               36684  0
ieee1394              368472  2 sbp2,ohci1394
cpufreq_ondemand        9128  1
cpufreq_userspace       8544  0
cpufreq_powersave       2688  0
powernow_k8            12480  0
freq_table              5888  1 powernow_k8
rfcomm                 44512  0
l2cap                  29376  5 rfcomm
bluetooth              58116  4 rfcomm,l2cap
ppdev                  10760  0
sony_acpi               6548  0
pcc_acpi               15488  0
video                  18248  0
button                  8288  0
acpi_sbs               24024  0
ac                      6600  1 acpi_sbs
i2c_acpi_ec             6400  1 acpi_sbs
tc1100_wmi              8520  0
battery                11656  1 acpi_sbs
dev_acpi               14724  0
hotkey                 13128  0
container               5696  0
ipv6                  298240  16
dm_mod                 62536  1
af_packet              27020  4
w83627hf               30736  0
hwmon_vid               3456  1 w83627hf
eeprom                  9040  0
i2c_isa                 6848  1 w83627hf
fuse                   41112  4
sr_mod                 19108  0
lp                     14464  0
snd_seq_dummy           4868  0
snd_seq_oss            37796  0
snd_seq_midi           10816  0
snd_seq_midi_event      9408  2 snd_seq_oss,snd_seq_midi
snd_seq                63512  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_via82xx            32360  1
gameport               18640  1 snd_via82xx
snd_ac97_codec        109820  1 snd_via82xx
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            58784  0
snd_mixer_oss          19968  1 snd_pcm_oss
snd_pcm               104008  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              28424  2 snd_seq,snd_pcm
snd_page_alloc         13328  2 snd_via82xx,snd_pcm
snd_mpu401_uart         9792  1 snd_via82xx
snd_rawmidi            31072  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device         10704  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
usb_storage            81472  1
pcspkr                  3016  0
snd                    68000  13 snd_seq_oss,snd_seq,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
tuner                  45604  0
soundcore              12640  1 snd
r8169                  33352  0
cx8800                 37772  0
tvaudio                27676  0
serio_raw               9156  0
i2c_viapro             10840  0
parport_pc             40176  1
parport                43532  3 ppdev,lp,parport_pc
psmouse                39748  0
floppy                 73544  0
cx88xx                 69152  1 cx8800
i2c_algo_bit           10568  1 cx88xx
video_buf              25924  2 cx8800,cx88xx
ir_common              11588  1 cx88xx
nvidia               5432600  12
tveeprom               18768  1 cx88xx
i2c_core               26048  11 i2c_acpi_ec,w83627hf,eeprom,i2c_isa,tuner,tvaudio,i2c_viapro,cx88xx,i2c_algo_bit,nvidia,tveeprom
r1000                  18752  0
shpchp                 50720  0
pci_hotplug            32592  1 shpchp
v4l1_compat            14340  1 cx8800
v4l2_common             8448  1 cx8800
btcx_risc               6216  2 cx8800,cx88xx
videodev               13056  2 cx8800,cx88xx
tulip                  57312  0
sg                     43056  0
tsdev                   9600  0
evdev                  13888  2
usbhid                 42400  0
ext3                  145360  6
jbd                    70312  1 ext3
raid5                  30464  1
md_mod                 76152  2 raid5
xor                     7120  1 raid5
ide_generic             2176  0
ehci_hcd               35592  0
uhci_hcd               36000  0
usbcore               146428  5 usb_storage,usbhid,ehci_hcd,uhci_hcd
ide_cd                 35104  0
cdrom                  40568  2 sr_mod,ide_cd
via82cxxx              10244  0 [permanent]
generic                 6724  0
sata_via               11460  4
sd_mod                 20864  15
sata_promise           14468  16
libata                 84960  2 sata_via,sata_promise
scsi_mod              159928  7 sbp2,sr_mod,usb_storage,sg,sd_mod,sata_promise,libata
thermal                15884  0
processor              29160  2 powernow_k8,thermal
fan                     5832  0
capability              6536  0
commoncap               9088  1 capability
vga16fb                14480  1
cfbcopyarea             4544  1 vga16fb
vgastate                9792  1 vga16fb
cfbimgblt               3584  1 vga16fb
cfbfillrect             5184  1 vga16fb
fbcon                  42496  72
tileblit                3520  1 fbcon
font                    9344  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3136  1 bitblit
```

/proc/cpuinfo:
```
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 4
model name      : AMD Athlon(tm) 64 Processor 3200+
stepping        : 8
cpu MHz         : 2000.089
cache size      : 1024 KB
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext lm 3dnowext 3dnow lahf_lm
bogomips        : 4007.68
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp
```

Anything else, just ask.

---

### Post by jbernardo on 2006-09-06
Seems like nobody's using firewire... :(

---

