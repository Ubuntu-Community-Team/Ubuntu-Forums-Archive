---
title: "major laptop problems"
date: 2008-02-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by mike941 on 2008-02-08
Ok i already typed up a long paragraph then accidently went back and lost it all so i'll just make a list this time because its late.
1. ubuntu deosn't recognize that i use a laptop and deosn't show me the battery power level(i've tried to get 3rd party apps to run in the panel but that didn't work)
2. The sound card isn't working
3. Ubuntu fails to sleep and hibernate properly
4. 2 weeks ago as i tried to switch to a vesa driver i accidently messed up my system and had to manually reconfigure the xorg.conf(not sure if that's the files actual name but pretty sure) file and would like to get that back to normal.
I think that's everything all my system information is in my sig. O and the wifi card and graphics card isn't recognized but i think those first 4 things are about as much as i can handle right now.

---

### Post by renzokuken on 2008-02-08
i may be able to help with a couple. firstly, which version of ubuntu are you using?

2. do you know what sound chipset you are using? running **lsusb** or **lspci** may help

4. open a terminal and run ```
sudo dpkg-reconfigure xserver-xorg
``` this will get you a wizard to help configure your xorg.cong

---

### Post by mike941 on 2008-02-08
I use ubuntu 7.10.

---

### Post by mike941 on 2008-02-08
O and i can't tell if the auto-detect worked. I ran the command you told me to and the i just got a message that gave me an ok option but never let me say ok and end the autoconfiguerer so i don't know if it took effect. Any help with the laptop/laptop battery detection would be greatly appreciated as that is my biggest problem right now.

---

### Post by Yellow Pasque on 2008-02-09
Go to a terminal and run this for us please:
```
sudo update-pciids; lspci
cat /proc/asound/card0/codec#* | grep Codec
```

You might also find some useful settings by typing this in the terminal:
```
gconf-editor
```
Look under /apps/gnome-power-manager for the power settings

---

### Post by mike941 on 2008-02-13
I ran the first line of commands Temujin told me to run and got this i'll edit the rest in as i run them. Sorry about taking so long to respond i ended up DLing alot of live cd's and found out that PCLOS gnome edition works really well for me and am trying to install it so i can dual boot.
Here's what i got from sudo update-pciids; lspci
21:20:48 (78.57 KB/s) - `/usr/share/misc/pci.ids.gz.new' saved [130934/130934]

Done.
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:07.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]
02:00.0 Ethernet controller: Atheros Communications, Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
08:01.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
08:01.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
08:01.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
08:01.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
08:01.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)
08:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

cat /proc/asound/card0/codec#* | grep Codec gave me this:
Codec: Conexant ID 2c06
Codec: Realtek ALC883

---

### Post by renzokuken on 2008-02-14
looks like you have the same soundcard as me. i had to update ALSA to the latest version to get it working.

have a look at this post for a howto

[http://ubuntuforums.org/showpost.php?p=3121014&postcount=4](http://ubuntuforums.org/showpost.php?p=3121014&postcount=4)

---

### Post by basilf on 2008-03-05
I have even a worse problem, I own a Acer Aspire 5050 5430 and can't even boot the CD.  The laptop has
a ATI Video 256M but locks up when it reads the video card the ATI Radeon Xpress so far I have given up on ever using Ubuntu on my laptop even Windows XP x64 is not working 100% as I can't get the MMC/SD reader to work no matter how hard I try ENE website is no use and total @$#$ waste of time.

If anyone can tell me howto install Linux on this compuer please let me know, I had Ubuntu on my systems  until recently when my desktop died going to a Acer might have been a mistake, Dell I have been told supports Ubuntu but not here in Canada.

---

### Post by Yellow Pasque on 2008-03-05
basilf, have you tried safe graphics mode or the alternate install CD?

---

### Post by basilf on 2008-06-26
> **Temüjin said:**
> basilf, have you tried safe graphics mode or the alternate install CD?

I have treid literally everything. I tried not only Ubuntu 8.04 but Mandrivia, Fedora, OpenSUSE I have got to the menu and partitioning only to try to boot into any Linux to get CPU errors Such as CPU#1 error and then it hangs.

I have givenup will sell this piece of crap its got 4 GB of RAM and Office 2007 Ultimate, works fine under Vista 32 felt a bit of a ripoff since its a 64 bit system. I tried installing Vista x64 Ultimate and that is just another headache drivers don't work and for some devices don't excist.

This is a total piece of crap Computer I can't wait to get rid of it, next system will be a Apple, PC's with Vista suck.

---

