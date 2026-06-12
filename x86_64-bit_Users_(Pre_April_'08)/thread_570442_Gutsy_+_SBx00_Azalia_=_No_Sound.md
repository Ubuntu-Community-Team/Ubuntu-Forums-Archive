---
title: "Gutsy + SBx00 Azalia = No Sound"
date: 2007-10-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by mikecrowe on 2007-10-08
Hi folks,

No flames, please.  I've searched for hours trying to find my combination.  Any help would be appreciated.  I'm mainly looking for a pointer so I can get sound+Skype up and running.

Upgrading Gateway M-1615 from Feisty to Gutsy.  Specs on laptop are:
Processor: AMD Turion™ 64 X2 Mobile Technology TL-56  |  1.8GHz | 512KB x 2 L2 Cache

Hardware scan and lspci:
>         *-multimedia UNCLAIMED
             description: Audio device
             product: SBx00 Azalia
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=64


00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 7915
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon X1200 Series
01:05.2 Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)


Near as I can figure, the snd-atiixp module isn't getting loaded or isn't ready yet for Gutsy.  Does this sound right?

> lsmod | grep snd
snd_hda_intel         337192  0 
snd_pcm_oss            50048  0 
snd_mixer_oss          20096  1 snd_pcm_oss
snd_pcm                94344  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           5380  0 
snd_seq_oss            36864  0 
snd_seq_midi           11008  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event      9984  2 snd_seq_oss,snd_seq_midi
snd_seq                62496  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27272  2 snd_pcm,snd_seq
snd_seq_device         10260  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    69288  9 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              10272  1 snd
snd_page_alloc         12560  2 snd_hda_intel,snd_pcm


dmesg | grep hda yields:
> [   49.551027] hda_intel: azx_get_response timeout, switching to polling mode...
[   50.553481] hda_intel: azx_get_response timeout, switching to single_cmd mode...
[   50.553646] hda_codec: No auto-config is available, default to model=ref
[   50.566752] hda-intel: no codecs initialized


I am also puzzled why this AMD+ATI laptop uses Intel hda drivers.  I guess that's the spec?

TIA
Mike

---

### Post by huck416 on 2007-10-10
I'm getting the same results with a Dell 1521, AMD Turion 64x2 and Gutsy. Tried several fixes and still no sound. Managed to get wireless working OK.

---

### Post by mikecrowe on 2007-10-11
Here's what is quasi-working for me.  Add this to your module configuration:

```
#options snd-hda-intel index=0
# ALSA portion
alias char-major-116 snd
# module options should go here

# OSS/Free portion
alias char-major-14 soundcore
alias sound-slot-0 snd-card-0

# card #1
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss
options snd cards_limit=8
alias snd-card-0 snd-hda-intel
options snd-hda-intel index=0
alias snd-card-1 snd-hda-intel
options snd-hda-intel index=1
alias snd-card-7 snd-usb-audio
options snd-usb-audio index=7

```

---

### Post by mikecrowe on 2007-10-11
> **huck416 said:**
> ...Managed to get wireless working OK.

Which wireless card?  I still haven't gotten my rtl_8187 wifi system up.

---

### Post by jim21164 on 2007-10-12
I just got a new gateway m-1615 also.   I put gentoo on it and had problems with the alsa kernel modules.   I had to install the alsa drivers from [www.alsa-project.org](www.alsa-project.org)... well just an emerge alsa-drivers command with gentoo.  Also have to turn off alsa in the kernel..  I hope this helps it fixed mine and the sound works fine now.   The only problems I still have is the camera, supposed to use uvcvideo driver but it doesn't work and tvtime can't get yuy2 overlay support.

---

### Post by huck416 on 2007-10-12
Thanks mikecrowe for the tip although it didn't work for me. lspci -v shows this for my audio:

```
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
        Subsystem: Dell Unknown device 01fc
        Flags: slow devsel, IRQ 16
        Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

```

This is the output of modinfo soundcore

```
$ modinfo soundcore
filename:       /lib/modules/2.6.22-14-generic/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     548AA54AF08207316C104F8
depends:
vermagic:       2.6.22-14-generic SMP mod_unload 586
```

...and this from lspci -nnvv

```
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia [1002:4383]
        Subsystem: Dell Unknown device [1028:01fc]
        Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin ? routed to IRQ 16
        Region 0: Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
```

Interesting when I run alsaconf it shows my card as:

hda-intel ATI Technologies Inc SBx00 Azalia

so the system can see the card although all other commands result in "no sound card." Weird.:confused:

We'll keep tinkering with it. If I get it working, I'll post the results and what I did.

My wifi is the Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01). I had to blacklist it initially, download and extract the bcmwl5 and use ndiswrapper. After that it worked fine although I did have to edit the interfaces file to include the key for my WEP so it would load properly on boot.

```
 description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 01
       serial: 00:1c:26:3a:6a:10
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.45+Broadcom,10/12/2006, 4.100. ip=192.168.1.107 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

```

Hope this helps.

---

### Post by Sanek on 2007-10-27
appeared after 
sudo apt-get install linux-backports-modules-generic  & sudo reboot
i'm running gutsy on 1521 amd64 turion
lspci | grep -i audio gave:
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
wifi is in the queue....

---

### Post by ebpowell on 2007-10-31
Same issue on my Inspiron 1521.:(

Been pulling my hair out over the Broadcom wifi. The BCM native driver WON'T GO AWAY (even after rmmod, modprobe -r AND blacklisting,,,ndiswrapper reports that the alternate driver (bcm) is present and loads eth1.,..ndiswrapper SHOULD install wlan0....)

Trying a custom kernel build now.

Native bcm43xx driver is DOA. Acts like it wants to work, but the link quality stays at 0/100, even after it authenticates with the router. Allt his using WEP.

This machine is dangerously close to becoming a Gentoo box...

Inspiron 1521 
Turion64 x2 2.2Ghz
2GB RAM
BCM43xx wifi
BCM 4400 10/100 LAN
ATI Azalia audio

---

### Post by Yellow Pasque on 2007-11-01
If ALSA isn't working for you, ditch it by removing the alsa-core package.

Then, head on over to: [http://www.4front-tech.com/](http://www.4front-tech.com/) and go to their download page. Grab the x64 deb package and try installing that. 

If you get the same error I got about not being able to insert the module, then you'll  have to reboot and hit 'Esc' to get in to GRUB. Now you need to add the soundon command in the boot sequence (I believe it should be the third command). You only need to do this once.

---

### Post by notrump3 on 2007-11-12
Thanks for the help, audio is now working!!

As for wireless... I found a fix for mine on [http://www.linux-geek.org/2007/04/22/dell-1390-native-linux-driver-how-to-updated/](http://www.linux-geek.org/2007/04/22/dell-1390-native-linux-driver-how-to-updated/)

I did this when I had fiesty and it worked for my wireless and wireless didn't break on the upgrade to gutsy....



Dell Inspiron 1521 dual boot vista/ubuntu (gutsy)
AMD Turion 64 X2 TL-64
 ATI Technologies Inc SBx00 Azalia
 Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

---

### Post by Luis Macias on 2007-11-15
iI have a dell1521 too, i have sound working, used method g in the following link: [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

Hope that helps

---

### Post by huck416 on 2007-12-02
Got my sound working. A full explanation of what worked and what else works on my 1521 can be found here. [http://ubuntuforums.org/showthread.php?t=607378](http://ubuntuforums.org/showthread.php?t=607378)  Hope it helps.

---

### Post by quadrispro on 2008-01-17
Hi!

I have an [Olidata Stainer 3050]("http://www.olidata.com/Prodotti_Vendita/Prodotti/Configurazioni/Scheda_conf.asp?conf=SpecTecPerfext_Stainer3050"), lspci:

```

00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon X1200 Series
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)

```

Chipset is AMD RS690MC + ATI SB600

I have installed Ubuntu 7.10 «Gutsy Gibbon», uname -r:
```

2.6.22-14-generic

```

At the first boot headphones didn't mute front speakers, now, since I have added this string in /etc/modprobe.d/alsa-base
```

options snd-hda-intel model=acer position_fix=1

```

I can control spekaers and headphones volume separately. But an issue is still remaining unsolved: during recording, internal mic quality is very low with noises and clicks.

My chipset (SB600) isn't listed in AlsaProject's support page... Someone with the same chipset can give me a solution?


PS: That's my codec:
cat /proc/asound/card0/codec#1 | grep -i codec:
```

Codec: Realtek ALC883

```

---

### Post by quadrispro on 2008-01-26
Errata corrige:
> 
internal mic quality is very low with noises and clicks.


Same problem with the mic jack....

---

### Post by mikecrowe on 2008-02-25
> **Temüjin said:**
> If ALSA isn't working for you, ditch it by removing the alsa-core package.

Then, head on over to: [http://www.4front-tech.com/](http://www.4front-tech.com/) and go to their download page. Grab the x64 deb package and try installing that. 

If you get the same error I got about not being able to insert the module, then you'll  have to reboot and hit 'Esc' to get in to GRUB. Now you need to add the soundon command in the boot sequence (I believe it should be the third command). You only need to do this once.

Awesome -- this did it!  Thank you!!!!

---

### Post by quadrispro on 2008-03-21
I've reported this bug to alsa

[https://bugtrack.alsa-project.org/alsa-bug/bug_view_page.php?bug_id=3862](https://bugtrack.alsa-project.org/alsa-bug/bug_view_page.php?bug_id=3862)

---

