---
title: "Anyone running WoW smoothly on 10/25 Men?"
date: 2013-01-03
forum: Wine
---

### Post by Thee on 2013-01-03
Hey there!

Im particularly interested in ATI users, as I heard Nvidia users don't have so much FPS issues. But any info would help.

So, some facts first:

- I'm running WoW in OpenGL mode.
- I'm using the proprietary drivers that came with Ubuntu 12.10.
- I have copied WoW to my Ext4 partition.
- I have tried the "GL_ARB_vertex_buffer_object" registry tweak which makes the FPS unstable and worse.
- I did not try to run WoW in a separate X server as it seems a bit complicated to me, although I am not that unfamiliar with Linux but I've been using Ubuntu for only about a month now as my main OS, so its safe to say that Im a beginner. Plus, I like to be able to switch to my desktop for use of Skype or TeamSpeak, etc. And as I read here, it doesn't make big difference running it in separate X server.
- WoW Settings in Windows: Everything set to ULTRA, FPS indoors 100+, populated areas around ~40 FPS, and 25-100 FPS in 25/10 men raids.
- WoW Settings in Ubuntu: Almost everything set to LOW or off, FPS indoors ~25, outdoors ~40 FPS, and 5-30 FPS in 25/10 men raids.

Now when it comes to 10/25 men raids, I get roughly 30 FPS when nothing is happening, but when the fight starts and the effects kick in I get ~18 FPS at best, and as low as 5 FPS in 25 men raids. So 25 men is unplayable and on 10 men not fun at all when a lot of things are going on.

So its obvious the difference is very big in FPS compared to Windows.

My system specs:

```
H/W path        Device     Class       Description
==================================================
                           system      GA-870A-UD3 ()
/0                         bus         GA-870A-UD3
/0/0                       memory      128KiB BIOS
/0/4                       processor   AMD Phenom(tm) II X4 955 Processor
/0/4/a                     memory      128KiB L1 cache
/0/4/c                     memory      512KiB L3 cache
/0/b                       memory      128KiB L1 cache
/0/27                      memory      6GiB System Memory
/0/27/0                    memory      2GiB DIMM 1066 MHz (0.9 ns)
/0/27/1                    memory      2GiB DIMM 1066 MHz (0.9 ns)
/0/27/2                    memory      2GiB DIMM 1066 MHz (0.9 ns)
/0/27/3                    memory      DIMM 1066 MHz (0.9 ns) [empty]
/0/100                     bridge      RX780/RX790 Chipset Host Bridge
/0/100/2                   bridge      RD790 PCI to PCI bridge (external gfx0 po
/0/100/2/0                 display     Barts PRO [Radeon HD 6800 Series]
/0/100/2/0.1               multimedia  Barts HDMI Audio [Radeon HD 6800 Series]
/0/100/9                   bridge      RD790 PCI to PCI bridge (PCI express gpp 
/0/100/9/0                 bus         uPD720200 USB 3.0 Host Controller
/0/100/a                   bridge      RD790 PCI to PCI bridge (PCI express gpp 
/0/100/a/0                 storage     JMB363 SATA/IDE Controller
/0/100/a/0.1               storage     JMB363 SATA/IDE Controller
/0/100/11                  storage     SB7x0/SB8x0/SB9x0 SATA Controller [IDE mo
/0/100/12                  bus         SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
/0/100/12.2                bus         SB7x0/SB8x0/SB9x0 USB EHCI Controller
/0/100/13                  bus         SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
/0/100/13.2                bus         SB7x0/SB8x0/SB9x0 USB EHCI Controller
/0/100/14                  bus         SBx00 SMBus Controller
/0/100/14.1                storage     SB7x0/SB8x0/SB9x0 IDE Controller
/0/100/14.2                multimedia  SBx00 Azalia (Intel HDA)
/0/100/14.3                bridge      SB7x0/SB8x0/SB9x0 LPC host controller
/0/100/14.4                bridge      SBx00 PCI to PCI Bridge
/0/100/14.4/7              multimedia  CM8738
/0/100/14.4/e              bus         TSB43AB23 IEEE-1394a-2000 Controller (PHY
/0/100/14.5                bus         SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
/0/100/15                  bridge      SB700/SB800/SB900 PCI to PCI bridge (PCIE
/0/100/15/0                storage     JMB363 SATA/IDE Controller
/0/100/15/0.1              storage     JMB363 SATA/IDE Controller
/0/100/15.1                bridge      SB700/SB800/SB900 PCI to PCI bridge (PCIE
/0/100/15.1/0   eth0       network     RTL8111/8168B PCI Express Gigabit Etherne
/0/100/15.2                bridge      SB900 PCI to PCI bridge (PCIE port 2)
/0/100/15.3                bridge      SB900 PCI to PCI bridge (PCIE port 3)
/0/100/16                  bus         SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
/0/100/16.2                bus         SB7x0/SB8x0/SB9x0 USB EHCI Controller
/0/101                     bridge      Family 10h Processor HyperTransport Confi
/0/102                     bridge      Family 10h Processor Address Map
/0/103                     bridge      Family 10h Processor DRAM Controller
/0/104                     bridge      Family 10h Processor Miscellaneous Contro
/0/105                     bridge      Family 10h Processor Link Control
/0/1            scsi1      storage     
/0/1/0.0.0      /dev/sda   disk        500GB Hitachi HDS72105
/0/1/0.0.0/1    /dev/sda1  volume      57GiB Windows NTFS volume
/0/1/0.0.0/2    /dev/sda2  volume      279GiB Windows NTFS volume
/0/1/0.0.0/3    /dev/sda3  volume      127GiB Extended partition
/0/1/0.0.0/3/5  /dev/sda5  volume      122GiB Linux filesystem partition
/0/1/0.0.0/3/6  /dev/sda6  volume      5720MiB Linux swap / Solaris partition
/0/2            scsi10     storage     
/0/2/0.0.0      /dev/sdb   disk        122GB Maxtor 6Y120P0
/0/2/0.0.0/1    /dev/sdb1  volume      19GiB Windows NTFS volume
/0/2/0.0.0/2    /dev/sdb2  volume      94GiB Extended partition
/0/2/0.0.0/2/5  /dev/sdb5  volume      94GiB HPFS/NTFS partition
```

So my question:
Is there anyone out there that is running WoW on 10/25 men raids smoothly under Wine with ATI graphics cards, and if so, how?

I just need around ~15 FPS more in raids so I don't have to switch to Windows every time we raid. I don't even mind the low graphic settings.

Or em I doomed to buy Nvidia card or wait for ATI to release better drivers or Blizzard to port WoW? :/

Any tips would be helpful.
Thanks!

---

### Post by Thee on 2013-01-04
bump

---

