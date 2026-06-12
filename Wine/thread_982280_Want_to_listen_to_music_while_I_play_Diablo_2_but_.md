---
title: "Want to listen to music while I play Diablo 2 but can't."
date: 2008-11-14
forum: Wine
---

### Post by tee2 on 2008-11-14
Hi,

I want to listen to music while I play Diablo 2 WITH the sound effects from D2. I can only do one or the other though and I can't figure out how to fix this. Any help would be appreciated.

edit: using wine 1.1.8 btw, if other info is needed let me know.

---

### Post by cogadh on 2008-11-14
You probably have a sound card that can't do hardware mixing, in which case it can only do one stream of audio at a time (in Linux). What do you have for a sound card?

---

### Post by tee2 on 2008-11-14
This is on a laptop, and I'm not sure what chipset it has. Are there any commands I can run that will give this information?

---

### Post by cogadh on 2008-11-14
"lspci" should tell you what you need, but considering that is a laptop, I kind of doubt it has a hardware mixing sound chipset. It would still help to know what it is, there are ways to configure ALSA to do software mixing that may work for your sound card.

---

### Post by tee2 on 2008-11-14
> **cogadh said:**
> "lspci" should tell you what you need, but considering that is a laptop, I kind of doubt it has a hardware mixing sound chipset. It would still help to know what it is, there are ways to configure ALSA to do software mixing that may work for your sound card.

```
tee@Steven:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300]
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
03:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
03:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

```

Looks like AC'97?

---

### Post by cogadh on 2008-11-14
Yep, its an Intel AC'97 based audio controller. It does not support hardware mixing. I will probably not be able to help you much with getting software mixing to work (I am *far* from an expert with it), but this should help get you started:
[http://alsa.opensrc.org/index.php/Dmix](http://alsa.opensrc.org/index.php/Dmix)

---

### Post by tee2 on 2008-11-14
> **cogadh said:**
> Yep, its an Intel AC'97 based audio controller. It does not support hardware mixing. I will probably not be able to help you much with getting software mixing to work (I am *far* from an expert with it), but this should help get you started:
[http://alsa.opensrc.org/index.php/Dmix](http://alsa.opensrc.org/index.php/Dmix)

Um, what should I do? I have Dmix apparently and that link is how to set up Dmix. Or am I missing something?

---

