---
title: "Hauppauge PVR-150 for FM Radio"
date: 2008-07-22
forum: x86 64-bit Users
---

### Post by SirShaggy on 2008-07-22
Hi All,
I have recently installed Ubuntu 8.04 x86_64 in place of Windows XP Pro. It is great for me, doing what I need it to. There are 2 items I must figure out/get working. I'll have 2 threads as they are different. 

I have a Hauppauge PVR-150 tuner card I use to listen to the radio(In Windows). I do not watch TV with it at all. I want to make this work in Ubuntu. I have seen a lot of post about this card, they all focus on TV though. I don't want the TV to work, just the radio. Is there anyone who has successfully done this? Any howto's on this? Help would be very appreciated.

The card shows up under lspci:
shaggy@shaggys-PC2:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:08.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:09.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:09.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:09.2 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:0a.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:0a.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:0c.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:0d.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0d.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0d.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:0e.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:10.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:12.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:16.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:17.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7950 GT] (rev a1)
02:08.0 FireWire (IEEE 1394): Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller (rev 01)
02:09.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
02:0a.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
03:00.0 PCI bridge: Texas Instruments XIO2000(A)/XIO2200(A) PCI Express-to-PCI Bridge (rev 03)
04:01.0 USB Controller: NEC Corporation USB (rev 43)
04:01.1 USB Controller: NEC Corporation USB (rev 43)
04:01.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
04:02.0 FireWire (IEEE 1394): Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller (rev 01)
06:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7950 GT] (rev a1)


but only shows it as a video controller. I know it has a radio tuner, I've used it.

Here is the last part of dmesg:
[   35.723376] Linux video capture interface: v2.00
[   35.782435] ivtv:  Start initialization, version 1.1.0
[   35.782520] ivtv0: Initializing card #0
[   35.782523] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   35.826629] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   35.826639] ACPI: PCI Interrupt 0000:02:0a.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 18
[   35.874292] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08c9)
[   35.907760] tveeprom 2-0050: Hauppauge model 26552, rev G1B6, serial# 10302916
[   35.907763] tveeprom 2-0050: tuner model is Philips FM1236 MK5 (idx 116, type 43)
[   35.907765] tveeprom 2-0050: TV standards NTSC(M) (eeprom 0x08)
[   35.907767] tveeprom 2-0050: audio processor is CX25843 (idx 37)
[   35.907769] tveeprom 2-0050: decoder processor is CX25843 (idx 30)
[   35.907770] tveeprom 2-0050: has radio, has no IR receiver, has no IR transmitter
[   35.907772] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   36.087584] tuner 2-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   36.087604] tda9887 2-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   36.087605] tuner 2-0043: type set to tda9887
[   36.090598] tuner 2-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   36.119586] cx25840 2-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[   36.145551] wm8775 2-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   36.155567] tuner-simple 2-0061: type set to 43 (Philips NTSC MK3 (FM1236MK3 or FM1236/F))
[   36.155570] tuner 2-0061: type set to Philips NTSC MK3 (F
[   36.159211] ivtv0: Registered device video1 for encoder MPG (4096 kB)
[   36.159231] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   36.159249] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   36.159268] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   36.159289] ivtv0: Registered device radio0 for encoder radio
[   36.159291] ivtv0: Initialized card #0: Hauppauge WinTV PVR-150
[   36.159312] ivtv:  End initialization
  This shows some bits about the radio tuner, I THINK?!?!

Any ideas?

Thanks,
SirShaggy

---

### Post by SirShaggy on 2008-07-29
Well, I installed ivtv-utils from the repos, typed ivtv-radio -f 97.10 and it fired right up. It was run as /dev/video24 instead of /dev/radio0 or what not. It played for 3 hours just fine. I installed gnomeradio, clicked on the menu item, "FM-Radio Tuner" and nothing happened. Then, I tried CLI again, "ivtv-radio -f 97.10" and it seems everything has quit. I can't get any sound from the tuner at all. I do still have sound in .mp3's, videos, movies, You Tube and all that. Just not from the tuner card. I am about to try MythTV to see if I learn anything new. Just seems strange that it works then don't again.

SirShaggy

---

### Post by dragonneus on 2008-07-30
Im using a simple usb FM radio dongle and am having issues also. There doesnt seem to be a /dev/radio or /dev/radio0

from dmesg:

[ 1586.609193] hiddev96hidraw0: USB HID v1.11 Device [[www.rding.cn](www.rding.cn) RDing PCear FM Radio] on usb-0000:02:0e.0-2

This works fine in windows anyone have an idea?

---

