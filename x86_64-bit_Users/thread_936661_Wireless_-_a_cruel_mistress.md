---
title: "Wireless - a cruel mistress"
date: 2008-10-03
forum: x86 64-bit Users
---

### Post by au_vagabond on 2008-10-03
Me and ubuntu are ex-lovers. We used to be so close... and then I started dating fedora and eventualy became a huge distro whore leaving my beloved behind. I hit rock bottom when I started using sabayon. However, just today, I reinstalled Ubuntu, and it was like the old times. Joy, happiness, TF2 running, Wireless working fine.

And then I rebooted.

After attempting to reboot to unmount a CIFS share (which i couldn't unmount using the usual command, as apparently the unmount command "wasn't installed) my wireless suddenly disappeared. Feeling scared and confused, I re-rebooted just in case, and it still didn't work.

After going through a bottle of Valium and six boxes of tissues, I dragged myself to my netbook remix eeepc (which by the way is the pimp), and typed this cry for HELPPPP!!!!!

The card is atheros based, and as I said was working swimmingly until I rebooted - which could be an issue. Coincidentally, Steam also got an error message on reboot about vgui2.dll, but that is probably not relevant.

In any case, HELLPPPPPP!!!!

lspci -nn result:
```

00:00.0 Host bridge [0600]: Intel Corporation 82P965/G965 Memory Controller Hub [8086:29a0] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation 82P965/G965 PCI Express Root Port [8086:29a1] (rev 02)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 02)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev f2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller [8086:2810] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller [8086:2820] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)
00:1f.5 IDE interface [0101]: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller [8086:2825] (rev 02)
01:00.0 VGA compatible controller [0300]: nVidia Corporation G70 [GeForce 7600 GS] [10de:0392] (rev a1)
03:00.0 SATA controller [0106]: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller [197b:2363] (rev 02)
03:00.1 IDE interface [0101]: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller [197b:2363] (rev 02)
04:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller [11ab:4364] (rev 12)
**05:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor [168c:0013] (rev 01)**

```
Also worth noting that my wireless card works fine on windows.


_______-
Ps, sorry if this already exists somewhere, I am just ridiculously exasperated right now. Humour me this once...:) Also, sorry for posting this in the wrong section, only just realised. Probably worth moving it.

---

