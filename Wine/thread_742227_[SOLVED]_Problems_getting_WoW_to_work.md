---
title: "[SOLVED] Problems getting WoW to work"
date: 2008-04-01
forum: Wine
---

### Post by kc5hwb on 2008-04-01
I followed the instructions here:

[http://ubuntuforums.org/showthread.php?t=579378](http://ubuntuforums.org/showthread.php?t=579378)

When I launch WoW on my laptop, the program launches, the screen goes black and I can hear the game music, but there is no video  The whole screen is black.  If I hit ESC, it closes and goes back to the normal desktop.

Ideas on what I am doing wrong?

---

### Post by thisismalhotra on 2008-04-01
> **kc5hwb said:**
> I followed the instructions here:

[http://ubuntuforums.org/showthread.php?t=579378](http://ubuntuforums.org/showthread.php?t=579378)

When I launch WoW on my laptop, the program launches, the screen goes black and I can hear the game music, but there is no video  The whole screen is black.  If I hit ESC, it closes and goes back to the normal desktop.

Ideas on what I am doing wrong?

I don't know what you are doing wrong as the post seems to be fairly right.

I used following as my guide when I set it up

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

Some tips though: -

1. if you are dual booting dont bother do do the painful install process, just copy your wow folder from you vista/xp partition to linux c: in WINE and run it from there.

2. I installed WINE from synaptic it seems you are using the same.

3. In wine tell wow/wine to use win XP settings and not win vista (some vista stuff is still screwey in WINE)

Also, since you have the music but no video I would suggest and see if your drivers are installed or not...

It would be nice if you can give details of your PC config here too.. Also can you use compiz special effects??

---

### Post by kc5hwb on 2008-04-01
I am not dual booting.

In wine I told it to use Win2000 settings, because when I went into that screen, that was there by default and I just left it.

I will give you more specific specs on my machine tonight, but for now:
I am using a Lenovo Thinkpad Z60m
It is about 1.6GHz with 1GB of RAM.

---

### Post by Sammi on 2008-04-01
Try setting winecfg to XP.
 
What graphics card do you have, and what version is the driver?

---

### Post by kc5hwb on 2008-04-01
Is there a command where I can see that?


I am fairly sure it is an nvidia.  I will have to look it up if I can't find it in the Ubuntu properties somewhere

---

### Post by kc5hwb on 2008-04-01
when I go to system-administration-screens and graphics, my graphics card is set to **i810 Intel Graphics Driver**

And in the device manager is says:
Mobile 915GM/GMS/910GML Express Graphics Controller

---

### Post by thisismalhotra on 2008-04-02
> **kc5hwb said:**
> Is there a command where I can see that?


I am fairly sure it is an nvidia.  I will have to look it up if I can't find it in the Ubuntu properties somewhere

Please use Win XP settings and Please post the output of 

```
lspci -v
```

Sorry but your graphics card is pretty weak (it's an onboard one) I am not sure if it can play WoW or not. run following too:-

```
glxinfo | grep rendering
```

Which should return a line similar to this:

```
direct rendering: Yes
```

IF it returns Yes it can play WoW.

---

### Post by kc5hwb on 2008-04-02
I did the Grep Rendering and it DID return YES on that command.

I also did the lspci command and it returned a long result.  I can't post that result now because I am at work and do not have a network drop connection for my personal laptop here.  But I will try and get one today some time.

---

### Post by kc5hwb on 2008-04-02
Ok, I ganked a network jack here....


> jason@SILAS:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
        Subsystem: IBM Unknown device 0575
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03) (prog-if 00 [VGA])
        Subsystem: IBM Unknown device 058c
        Flags: bus master, fast devsel, latency 0, IRQ 20
        Memory at a0080000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 1800 [size=8]
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Memory at a0040000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
        Subsystem: IBM Unknown device 058c
        Flags: fast devsel
        Memory at 50000000 (32-bit, non-prefetchable) [disabled] [size=512K]
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
        Subsystem: IBM Unknown device 05b7
        Flags: bus master, fast devsel, latency 0, IRQ 20
        Memory at a0000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Memory behind bridge: a0100000-a01fffff
        Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=0a, sec-latency=0
        I/O behind bridge: 00002000-00003fff
        Memory behind bridge: a2000000-a3ffffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000d00fffff
        Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0b, subordinate=12, sec-latency=0
        I/O behind bridge: 00004000-00005fff
        Memory behind bridge: a4000000-a5ffffff
        Prefetchable memory behind bridge: 00000000b0100000-00000000b01fffff
        Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=13, subordinate=13, sec-latency=0
        I/O behind bridge: 00006000-00007fff
        Memory behind bridge: a6000000-a7ffffff
        Prefetchable memory behind bridge: 00000000d0100000-00000000d01fffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: IBM Unknown device 0565
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 1820 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03) (prog-if 00 [UHCI])
        Subsystem: IBM Unknown device 0565
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at 1840 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03) (prog-if 00 [UHCI])
        Subsystem: IBM Unknown device 0565
        Flags: bus master, medium devsel, latency 0, IRQ 22
        I/O ports at 1860 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03) (prog-if 00 [UHCI])
        Subsystem: IBM Unknown device 0565
        Flags: bus master, medium devsel, latency 0, IRQ 23
        I/O ports at 1880 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
        Subsystem: IBM Unknown device 0566
        Flags: bus master, medium devsel, latency 0, IRQ 23
        Memory at a0004000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=14, subordinate=17, sec-latency=64
        I/O behind bridge: 00008000-0000bfff
        Memory behind bridge: a8000000-b00fffff
        Prefetchable memory behind bridge: 00000000d8000000-00000000dfffffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
        Subsystem: IBM Unknown device 0568
        Flags: bus master, medium devsel, latency 0

00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03) (prog-if 80 [Master])
        Subsystem: IBM Unknown device 056a
        Flags: bus master, 66MHz, medium devsel, latency 0
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 1810 [size=16]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
        Subsystem: IBM Unknown device 056b
        Flags: medium devsel, IRQ 11
        I/O ports at 18a0 [size=32]

02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express (rev 11)
        Subsystem: IBM Unknown device 0577
        Flags: bus master, fast devsel, latency 0, IRQ 20
        Memory at a0100000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

14:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
        Subsystem: IBM Unknown device 056c
        Flags: bus master, medium devsel, latency 168, IRQ 20
        Memory at b0000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=14, secondary=15, subordinate=16, sec-latency=176
        Memory window 0: d8000000-dbfff000 (prefetchable)
        Memory window 1: a8000000-abfff000
        I/O window 0: 00008000-000080ff
        I/O window 1: 00008400-000084ff
        16-bit legacy interface ports at 0001

14:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08) (prog-if 10 [OHCI])
        Subsystem: IBM ThinkPad A/T/X Series
        Flags: bus master, medium devsel, latency 64, IRQ 21
        Memory at b0001000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

14:00.2 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
        Subsystem: IBM Thinkpad Z60m
        Flags: bus master, medium devsel, latency 64, IRQ 22
        Memory at b0001800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

14:00.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 08)
        Subsystem: IBM Unknown device 0596
        Flags: medium devsel, IRQ 11
        Memory at b0001c00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

14:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
        Subsystem: Intel Corporation Unknown device 2711
        Flags: bus master, medium devsel, latency 64, IRQ 17
        Memory at b0002000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

---

### Post by thisismalhotra on 2008-04-02
Looks like you don't have a nvidia, and if you have one I doubt it has driver installed for it. Does you laptop has a nvidia sticker/logo on it??

Also, could you post the details spec of your PC?? Like proc, ram, vieo card, model number etc etc...
One more thing is this a fairly new laptop or an old one?? if a new PC you probably have Intel X3100 graphics card but you lspci shows intel 915 GMA which I think ubuntu has drivers in it for.

DO you have enabled extra repositories (unsupported, backports, etc), if no please do so and run

```
sudo apt-get update
sudo apt-get upgrade
```

Also, System -> Preferences -> Hardware Information,

would give you hardware list on your PC

---

### Post by kc5hwb on 2008-04-02
I put the laptop model # in a post up towards the top.  It is a z60m, and it is a fairlly new model, less than 2 years old.  It has a 1.6GHz processor and 1GB of RAM.

The laptop did have an nvidia sticker on it, but it rubbed off a while back.  And System->prefs->hardware info shows the Mobile 915GM Graphics controller.  That is the only graphics controller I see in this view.

I am running the update and upgrade right now.

---

### Post by kc5hwb on 2008-04-02
I tried rebooting after running the apt-get upgrade and still no-go.  My screen is still black.

I could switch the video driver to NV but if it doesn't work and doesn't show any video, I don't know how to get it back.

I hope that I can get this resolved by tomorrow.  If not, I will probably wipe the laptop and install XP again, because I am about to do some traveling and I REALLY WANT to take WoW with me, so I need it on a laptop.

---

### Post by thisismalhotra on 2008-04-03
> **kc5hwb said:**
> I tried rebooting after running the apt-get upgrade and still no-go.  My screen is still black.

I could switch the video driver to NV but if it doesn't work and doesn't show any video, I don't know how to get it back.

I hope that I can get this resolved by tomorrow.  If not, I will probably wipe the laptop and install XP again, because I am about to do some traveling and I REALLY WANT to take WoW with me, so I need it on a laptop.

What OS did laptop come with, I suppose XP?? Did you wipe it out completely or you are dual booting??

What you really need to do is find the manual or something where you have the spec so that we can be sure what is your video card model, or else all efforts are vain :(
You can call the manufacturer and ask this information too..

---

### Post by Sammi on 2008-04-03
Try doing a search for WoW and Intel - you'll probably find more results than you like. The forum is pretty well littered with graphics card troubles relating to ATI and Intel. Nvidia seem to be the only graphics card manufacturor that gives a damn about making functional drivers for Linux.

I consider myself to be lucky to have a Nvidia, and because of that I know little or nothing about Intel configuration.

---

### Post by kc5hwb on 2008-04-03
It came with XP, yes.  And it should have an onboard nvidia card because there was a sticker on the laptop when I bought it.

---

### Post by thisismalhotra on 2008-04-04
> **kc5hwb said:**
> It came with XP, yes.  And it should have an onboard nvidia card because there was a sticker on the laptop when I bought it.

IDK, but I will try to look up for some intel card instructions on wow installation for you and see what we com up with.. GL with Xp till then.

---

### Post by aoanla on 2008-04-04
Are you sure it had an nVidia logo on this laptop? 
A quick googling for "Lenovo Thinkpad Z60m" only returns two versions - the default one with an Intel graphics solution, and an upgraded option with an ATI Mobility x600...

---

### Post by thisismalhotra on 2008-04-04
> **aoanla said:**
> Are you sure it had an nVidia logo on this laptop? 
A quick googling for "Lenovo Thinkpad Z60m" only returns two versions - the default one with an Intel graphics solution, and an upgraded option with an ATI Mobility x600...

Thats what I saw too, Motherboard maybe one from nvidia but does not sound so as it has intel integrated graphics to it??

---

### Post by kc5hwb on 2008-04-05
That's possible.  I am pretty sure it was an Nvidia logo, but I could be wrong, since it rubbed off and it is gone now.

I put XP on it, loaded all the updates and drivers for XP, loaded WoW and Burning Crusade and it works perfectly.  This proves that my video card will handle the game.  So I guess the trick is just finding what card I have and what drivers Ubuntu has for it.

I'd much rather drop this XP load and put Ubuntu back on.  It pained me to put windows on again... sharp, searing pain, like poking yourself in the eye with a meat cleaver that just got out of a to-the-death battle with a weed water and lost.  Yea, it hurts.

---

### Post by thisismalhotra on 2008-04-07
> **kc5hwb said:**
> That's possible.  I am pretty sure it was an Nvidia logo, but I could be wrong, since it rubbed off and it is gone now.

I put XP on it, loaded all the updates and drivers for XP, loaded WoW and Burning Crusade and it works perfectly.  This proves that my video card will handle the game.  So I guess the trick is just finding what card I have and what drivers Ubuntu has for it.

I'd much rather drop this XP load and put Ubuntu back on.  It pained me to put windows on again... sharp, searing pain, like poking yourself in the eye with a meat cleaver that just got out of a to-the-death battle with a weed water and lost.  Yea, it hurts.

Well if you installed windows it means you had to install all the drivers back too, so go into device manager and look up all the make/model of components and post them here so that we are sure they all work with ubuntu....

---

### Post by BombeNissen on 2008-04-07
Its pretty easy to find out what model you have, simply go to this: [Lenovo Support]("http://www-307.ibm.com/pc/support/site.wss/homeLenovo.do?country=uk") and type in the Model number, like mine is a "2007-FUG", then it should say if its the Intel or ATI/nVidia gfx card.

Anyway, I have a similar problem, but this is a ati x1400 card that i got running perfectly, but when i enter the game X freezes. I can still hear the music, but my mouse isent working and i cant alt+ctrl+backspace to restart it..

lspci -v
> 
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
        Subsystem: Lenovo Unknown device 2015
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: ee100000-ee1fffff
        Prefetchable memory behind bridge: 00000000d8000000-00000000dfffffff
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Lenovo ThinkPad T60/R60 series
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at ee400000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: ee000000-ee0fffff
        Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 00004000-00005fff
        Memory behind bridge: ec000000-edffffff
        Prefetchable memory behind bridge: 00000000e4000000-00000000e40fffff
        Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=0b, sec-latency=0
        I/O behind bridge: 00006000-00007fff
        Memory behind bridge: e8000000-e9ffffff
        Prefetchable memory behind bridge: 00000000e4100000-00000000e41fffff
        Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0c, subordinate=13, sec-latency=0
        I/O behind bridge: 00008000-00009fff
        Memory behind bridge: ea000000-ebffffff
        Prefetchable memory behind bridge: 00000000e4200000-00000000e42fffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Lenovo ThinkPad T60/R60 series
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 1800 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Lenovo ThinkPad T60/R60 series
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at 1820 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Lenovo ThinkPad T60/R60 series
        Flags: bus master, medium devsel, latency 0, IRQ 22
        I/O ports at 1840 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Lenovo ThinkPad T60/R60 series
        Flags: bus master, medium devsel, latency 0, IRQ 23
        I/O ports at 1860 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: Lenovo ThinkPad T60/R60 series
        Flags: bus master, medium devsel, latency 0, IRQ 23
        Memory at ee404000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=15, subordinate=18, sec-latency=32
        I/O behind bridge: 0000a000-0000dfff
        Memory behind bridge: e4300000-e7ffffff
        Prefetchable memory behind bridge: 00000000e0000000-00000000e3ffffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
        Subsystem: Lenovo ThinkPad T60/R60 series
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: Lenovo Thinkpad R60e model 0657
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 1880 [size=16]

00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
        Subsystem: Lenovo Thinkpad R60e model 0657
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 16
        I/O ports at 18c8 [size=8]
        I/O ports at 18ac [size=4]
        I/O ports at 18c0 [size=8]
        I/O ports at 18a8 [size=4]
        I/O ports at 18b0 [size=16]
        Memory at ee404400 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
        Subsystem: Lenovo ThinkPad T60/R60 series
        Flags: medium devsel, IRQ 11
        I/O ports at 18e0 [size=32]

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400 (prog-if 00 [VGA])
        Subsystem: Lenovo Unknown device 2006
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at d8000000 (32-bit, prefetchable) [size=128M]
        I/O ports at 2000 [size=256]
        Memory at ee100000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at ee120000 [disabled] [size=128K]
        Capabilities: <access denied>

02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
        Subsystem: Lenovo ThinkPad T60
        Flags: fast devsel, IRQ 16
        Memory at ee000000 (32-bit, non-prefetchable) [size=128K]
        I/O ports at 3000 [size=32]
        Capabilities: <access denied>

03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
        Subsystem: Intel Corporation Thinkpad  X60s, R60e model 0657
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at edf00000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

15:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
        Subsystem: Lenovo ThinkPad T60/R60 series
        Flags: bus master, medium devsel, latency 168, IRQ 16
        Memory at e4300000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=15, secondary=16, subordinate=17, sec-latency=176
        Memory window 0: e0000000-e3fff000 (prefetchable)
        Memory window 1: 50000000-53fff000
        I/O window 0: 0000a000-0000a0ff
        I/O window 1: 0000a400-0000a4ff
        16-bit legacy interface ports at 0001


fglrxinfo
> 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.0.6473 (8.37.6)


Laptop Specs
> 
T5600(1.83GHz), 1GB RAM, 80GB 5400rpm HD, 14.1in 1400x1050 LCD, 128MB ATI Radeon X1400, CDRW/DVDRW, Intel 802.11abg wireless, Bluetooth/Modem, 1Gb Ethernet, UltraNav, Secure chip, Fingerprint reader, 9c Li-Ion batt,

---

### Post by thisismalhotra on 2008-04-07
> **BombeNissen said:**
> Its pretty easy to find out what model you have, simply go to this: [Lenovo Support]("http://www-307.ibm.com/pc/support/site.wss/homeLenovo.do?country=uk") and type in the Model number, like mine is a "2007-FUG", then it should say if its the Intel or ATI/nVidia gfx card.

Anyway, I have a similar problem, but this is a ati x1400 card that i got running perfectly, but when i enter the game X freezes. I can still hear the music, but my mouse isent working and i cant alt+ctrl+backspace to restart it..

lspci -v


fglrxinfo


Laptop Specs

Well to start with, ATI and linux/ubuntu does not have good history and you can see long threads on the same.

Coming back to your issues, did you try the registry change and config file fixes here: -

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

If you have please try to start wow with a separate X session. Also what version of WINE, ATI drivers etcetc are you using??

---

### Post by thisismalhotra on 2008-04-07
Here are some more performance tweaks from the link below(also contains info how to strat wow on a dedicated X session);

[http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine](http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine)

** Performance Tweaks**
**Kernel Boot Parameter**

Users of nvidia 8800 GTS and GTX cards have reported significant performance increases (around 10-30 fps improvements) by adding the vga=normal boot option on kernels 2.6.22 and 2.6.23.

**OpenGL Registry Edit**

A common performance tweak for wine and opengl games is a registry edit. While your results may vary, many users report up to a 100% increase in framerate with no loss of stability. To make this change, do the following:

   1. Open regedit (regedit)
   2. Navigate to HKEY_CURRENT_USER\Software\Wine\
   3. Right click on the wine folder and select [NEW] then [KEY].
   4. Replace the text New Key #1 with OpenGL (case sensitive).
   5. Right click in the right panel and select [NEW] then [String Value].
   6. Replace the text New Value #1 with DisabledExtensions (case sensitive).
   7. Now right click on DisabledExtensions and select Modify
   8. A dialog box should appear. In the value field type GL_ARB_vertex_buffer_object 
[B]
Startup Script[/B]

The idea for this tweak is to create a script which will allow you to launch WoW on a dedicated X server, and will give you a little FPS boost (up to 10-15fps).

    * Start by creating the script: nano -w ~/launch-wow.sh
    * Paste the following in the script: 

Code: ~/launch-wow.sh

 #!/bin/sh

 export WOW_PATH=~/".wine/drive_c/Program Files/World of Warcraft" # Installation path

 X :3 -ac -terminate &   # Launch on a new X session on display 3
 cd "${WOW_PATH}"        # Goto WoW dir 
 sleep 2
 DISPLAY=:3 `which wine` WoW.exe -opengl # Launches WoW

    * Press Ctrl+O then Ctrl+W to save and quit nano.
    * Make your script executable: chmod +x ~/launch-wow.sh 

**Enabling hardware rendering**

You should verify that you are actually rendering the game with OpenGL, not just software. If you are getting 1 FPS or the game is virtually unplayable, you're probably using software rendering. To switch to hardware/OpenGL rendering, run the following command as root:

**For nVidia Cards: eselect opengl set nvidia**

[B]For ATi Cards: eselect opengl set ati
[/B]
Exit X, Log out and back in, then start X again. Startup WoW, and you should be fine. See [http://forums.gentoo.org/viewtopic-t-448436-start-375.html](http://forums.gentoo.org/viewtopic-t-448436-start-375.html).
[B]
Config.wtf Tweaks[/B]
Warning: You need to run WoW at least once and log into a character so a Config.wtf file can be created.

The Config.wtf file is located in the WTF folder in your WoW installation. By default, this location is /home/<username>/.wine/drive_c/Program\ Files/World\ of\ Warcraft/.
[B]
OpenGL[/B]

Instead of launching WoW with the -opengl switch, you can make the change permanent by adding the following line:

```
SET gxApi "opengl"
```

---

### Post by kc5hwb on 2008-04-08
My model is a 2529-R5U
[http://www-307.ibm.com/pc/support/site.wss/quickPath.do?quickPathEntry=2529r5u&sitestyle=lenovo](http://www-307.ibm.com/pc/support/site.wss/quickPath.do?quickPathEntry=2529r5u&sitestyle=lenovo)


I already ran the OpenGL Registry Edit on this laptop.
I need to try the switch to hardware/OpenGL rendering.  I have XP on there now and it works great with WoW, but it is XP, so I am crying.  

On a good note, I did install WoW on my desktop running Ubuntu and after a few minor tweaks, it runs perfectly.  I played for 4 hours last night with no problems.

---

### Post by kc5hwb on 2008-04-09
Can anyone tell me what drivers I need for this vid card?  Because the default install must not have been the correct one for playing WoW, even though everything else seemed to work fine.

---

### Post by thisismalhotra on 2008-04-10
> **kc5hwb said:**
> Can anyone tell me what drivers I need for this vid card?  Because the default install must not have been the correct one for playing WoW, even though everything else seemed to work fine.

There is a module call xor--something--intel, which you might need but try to search in forums for intel gfx and wow and wine and ubuntu and see what you get ..

---

