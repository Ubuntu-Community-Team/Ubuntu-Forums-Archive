---
title: "Suddenly getting logged out"
date: 2007-05-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2007-05-31
Ubuntu Feisty amd64, up to date on Compaq R3240 laptop. Here is what is on the machine:

```
jjj@Devil5:~$ lspci
00:00.0 Host bridge: nVidia Corporation nForce3 Host Bridge (rev a4)
00:01.0 ISA bridge: nVidia Corporation nForce3 LPC Bridge (rev a6)
00:01.1 SMBus: nVidia Corporation nForce3 SMBus (rev a4)
00:02.0 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.1 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.2 USB Controller: nVidia Corporation nForce3 USB 2.0 (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 Audio (rev a2)
00:06.1 Modem: nVidia Corporation nForce3 Audio (rev a2)
00:08.0 IDE interface: nVidia Corporation nForce3 IDE (rev a5)
00:0a.0 PCI bridge: nVidia Corporation nForce3 PCI Bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 AGP Bridge (rev a4)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go 32M] (rev a3)
02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01)
```

The problem is that at least once a day I get dumped back to a login prompt, exactly as if I had typed Ctrl-Alt-Bksp. Of curse, this kills everything that I had running. I think the culprit is Firefox, which is:

```
Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.8.1.3) Gecko/20061201 Firefox/2.0.0.3 (Ubuntu-feisty)
```

It happens mostly when I click on a link to open it in a new tab, but just now it happened as I refreshed the amd64 forum page. It has also happened when doing things in OpenOffice.org, so it's not just Firefox.

Normally I use the nVidiia driver, but I switched to the nv driver, and it didn't make any difference.

It would help me sleuth down what the problem is if I knew what kinds of things could trigger a logout. Has anyone run into this before? Any suggestions where to look?

---

### Post by optimarcus_prime on 2007-05-31
I've actually experienced the same problem, but have not yet found an answer.  For me, the logout usually occurs while loading a video within Firefox using the MPlayer plugin.

---

### Post by rajarshihri on 2007-12-21
Yes,
I am also having same problem.
to me, it happened when I was using mplayer while firefox remaining opened....
I am having 64bit Intel architecture.

one more query.....

does anybody know from where to get and install flash player for ia64...?:(
thanks in advance

---

