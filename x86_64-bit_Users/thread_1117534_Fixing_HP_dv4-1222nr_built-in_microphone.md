---
title: "Fixing HP dv4-1222nr built-in microphone"
date: 2009-04-06
forum: x86 64-bit Users
---

### Post by GroovyTrucker on 2009-04-06
Hi all! If you've purchased one of these laptops and have found out how to get the speakers working with the ALSA sound system you may have been wanting to get the microphone(s) working as well.  You can download the new snapshot of the ALSA drivers and get the speakers working if you change the model number in the /etc/modprobe.d/alsa-base file:
```
alias snd-card-0 snd-hda-intel
alias snd-slot-0 snd-hda-intel
options snd-hda-intel model=hp-dv5
```

Here's what you need to do to get the microphone working. It works whether or not you are using the built-in ones at the top of the screen or you've plugged one in - there's a jack sense that disables the built-in ones.

First, you have to download the hda-verb sources at [ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/misc/hda-verb/hda-verb-0.3.tar.bz2]("ftp://ftp.kernel.org/pub/linux/people/tiwai/hda-verb/hda-verb-0.3.tar.bz2"). Unzip the file and compile the hda-verb tool.  Now you'll have to be root to use the tool - just```
sudo ./hda-verb /dev/snd/hwC0D0 0x1c 0x701 2
sudo ./hda-verb /dev/snd/hwC0D0 0x18 0x707 0x20
```
and you'll be set to use the microphone. If the sound isn't loud enough for you, you can use the regular mixer to increase its capture volume. If that isn't enough you'll have to adjust the mic boost. This isn't currently being picked up by the mixer so you'll have to use hda-verb to adjust this also. The mic boost can take values of 0-3 and there are two channels on the chip to control the boost. The code for this is:```
sudo ./hda-verb /dev/snd/hwC0D0 0x18 0x3a0 3
sudo ./hda-verb /dev/snd/hwC0D0 0x18 0x390 3
``` where the 3 is the level you want (0-3) and the 0x3a0 is for the left and 0x390 for the right channel.

If the on-board sound chip is all you have then the /dev/snd/hwC0D0 should work fine for you. If you have another sound device plugged in (like a USB or ExpressCard sound device) you may have to change that to get the mic to work, just change the hwC0D0 to where the built-in chip is sitting on the PCI bus.

Now the only bad news is that these changes will not last after you reboot, suspend, or hibernate the computer.  You'll have to do them at each resume or startup. I'm working on getting this into the current ALSA drivers. Be patient...

Have fun!

---

### Post by possessedskier on 2009-04-24
Thanks for this.  I thought for a minute you were going to be a life saver but...

I have a dv4-1220us and got the internal mic working with the sound recorder the first time I tried this.  With Skype all I could hear were metallic like noises whenever I talked.  So I changed some settings in the alsa mixer and the sound preferences app and the Mic stopped working.  No matter what I do now I can't get it to work with the sound recorder.  I've rebooted several times and reentered your hda-verb settings in the exact order I did it the first time with no luck.

What is your Sound Capture setting in your sound preferences?  What recording mixer channel is your sound recorder using?

I actually had an external mic working very well with Skype from the time they got sound working in mid Feb until a couple weeks ago when I installed a new nightly build of ALSA. I had installed several nightly builds before that and it worked after each one. Since then I got the metallic sound until it stopped altogether after another nightly build install last week.

---

### Post by GroovyTrucker on 2009-05-03
Sorry I've taken so long to reply but work has had me out of town (hence my username). I've been making changes to the source code of the ALSA driver and all I'm waiting for is the maintainer to sign off on them.  But until then...

I'd tell you my settings but by then you would be getting a new snapshot from ftp.kernel.org and it changes things somewhat - it even caught me off guard. If you are using PulseAudio you can try these (potential) fixes:

For the gnome-volume-control I was using the Digital Mic 1 setting - to get this you need to enable the Digital Input Source in the Preferences dialog. Make sure that you have the Capture unmuted on the Recording tab of the volume control.
For Sound Recorder I was using the Capture setting.

Now if you aren't using PulseAudio you'll need to also unmute the Digital Line on the Recording tab on gnome-volume-control. Which leads me to a question --

What was the nature of the metallic sound you were hearing? Did it sound like you had too much gain?  If so then, under PulseAudio, open gnome-volume-control and lower the Capture level on the Recording tab. Otherwise, you will have to adjust the Digital slider on the same tab (has no effect under PulseAudio) as well (it controls a software mic boost).

Now I'm going to ask you to do me a favor and do a
```
sudo lspci -nv
``` and post the results here. I want to check your PCI board against the changes I've made to ALSA and maybe I can get more than just my laptop working with the autodetect routines.

If it seems that this has been some kind of rigamaroll to go through you are right, but Linux gives so much flexibility that sometime ease of use gets thrown out. 

Thank you.

---

### Post by NazarXG on 2009-05-04
I have HP dv4-1225dx. Both sound and microphone work with Ubuntu 9.04.
The only changes i have done are additions to the alsa-base.conf

```
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=hp-dv5
options snd-hda-intel enable_msi=1
```

In the Sound Preferences (System > Preferences > Sound), everything is set to autodetect, except sound capture, which is set to ALSA. Device is set to HDA ATI SB (Alsa mixer).

In the volume control (at the panel), Master, headphone, front and PCM are unmuted. From the recording tracks, both capture and digital. These are mute, but mic works.

**Getting the sound working on Skype.**

Skype options > sound devices, select HDA ATI SB(hw: SB,0) on all, meaning Sound in, Sound out and Ringing. Make a test call.

---

### Post by GroovyTrucker on 2009-05-04
NazarXG, I don't know why, but the enable_msi has no effect on my system - dmesg reports it as not being activated. I don't know what HP has been changing on each of these systems, but it seems rather hit or miss. Do you know which of the IDT chips you are running? Mine is a 92HD71B7. I don't think you can get this info in the /sys/class/sound/hwCxDx directory unless you start up ALSA with no model selection. At least that's how I found out which chipset I had. Like possessedskier, if you could post a ```
sudo lspci -nv
``` here you'd be a lot of help.

Everyone else:
My code changes were accepted into the driver tree today and you can download a new version of the driver at [COLOR=blue][COLOR=Blue][ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot]("http://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot")[/COLOR][/COLOR]. Try it with no model selection to see if it autodetects your sound chip. Otherwise, try adding ```
model=hp-dv4-1222nr
``` to your modprobe. I know it's rather model-specific, but I wrote the code for myself and I do not know if it will work with other models. That's why I'm asking for the PCI reports to see if I can get it to work with other ones.

Thanks.

---

### Post by possessedskier on 2009-05-06
The metallic sounds I hear in the Skype test call are a result of me speaking loudly into the mic.  Speaking softly produced no sound.  It didn't change when I changed the Digital Input setting.  The mic would only work with the sound recorder the first time I used your hda-verb settings after I installed a new nightly build.  After a reboot I couldn't get it to work again until the first boot after the next time I installed a build.  I haven't tried it with recent builds.

Here's the results of sudo lspci -nv:

```
00:00.0 0600: 1022:9600
	Subsystem: 103c:30fb
	Flags: bus master, 66MHz, medium devsel, latency 0
	Capabilities: [c4] HyperTransport: Slave or Primary Interface
	Capabilities: [54] HyperTransport: UnitID Clumping
	Capabilities: [40] HyperTransport: Retry Mode
	Capabilities: [9c] HyperTransport: #1a
	Capabilities: [f8] HyperTransport: #1c

00:01.0 0604: 103c:9602
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00007000-00007fff
	Memory behind bridge: d2300000-d24fffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
	Capabilities: [44] HyperTransport: MSI Mapping Enable+ Fixed+
	Capabilities: [b0] Subsystem: 103c:30fb
	Kernel modules: shpchp

00:04.0 0604: 1022:9604
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=07, sec-latency=0
	I/O behind bridge: 00003000-00006fff
	Memory behind bridge: d1300000-d22fffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000d0ffffff
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Root Port (Slot+), MSI 00
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [b0] Subsystem: 103c:30fb
	Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
	Capabilities: [100] Vendor Specific Information <?>
	Capabilities: [110] Virtual Channel <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:05.0 0604: 1022:9605
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
	Memory behind bridge: d1200000-d12fffff
	Prefetchable memory behind bridge: 00000000b0000000-00000000b00fffff
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Root Port (Slot+), MSI 00
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [b0] Subsystem: 103c:30fb
	Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
	Capabilities: [100] Vendor Specific Information <?>
	Capabilities: [110] Virtual Channel <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:06.0 0604: 1022:9606
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
	Memory behind bridge: d1100000-d11fffff
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Root Port (Slot+), MSI 00
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [b0] Subsystem: 103c:30fb
	Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
	Capabilities: [100] Vendor Specific Information <?>
	Capabilities: [110] Virtual Channel <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:07.0 0604: 1022:9607
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: b0100000-b01fffff
	Prefetchable memory behind bridge: 00000000d1000000-00000000d10fffff
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Root Port (Slot+), MSI 00
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [b0] Subsystem: 103c:30fb
	Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
	Capabilities: [100] Vendor Specific Information <?>
	Capabilities: [110] Virtual Channel <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:11.0 0106: 1002:4391 (prog-if 01)
	Subsystem: 103c:30fb
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
	I/O ports at 8038 [size=8]
	I/O ports at 804c [size=4]
	I/O ports at 8030 [size=8]
	I/O ports at 8048 [size=4]
	I/O ports at 8010 [size=16]
	Memory at d2508000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [60] Power Management version 2
	Capabilities: [70] SATA HBA <?>
	Kernel driver in use: ahci

00:12.0 0c03: 1002:4397 (prog-if 10)
	Subsystem: 103c:30fb
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at d2507000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:12.1 0c03: 1002:4398 (prog-if 10)
	Subsystem: 103c:30fb
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at d2506000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:12.2 0c03: 1002:4396 (prog-if 20)
	Subsystem: 103c:30fb
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at d2508500 (32-bit, non-prefetchable) [size=256]
	Capabilities: [c0] Power Management version 2
	Capabilities: [e4] Debug port: BAR=1 offset=00e0
	Kernel driver in use: ehci_hcd

00:13.0 0c03: 1002:4397 (prog-if 10)
	Subsystem: 103c:30fb
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at d2505000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.1 0c03: 1002:4398 (prog-if 10)
	Subsystem: 103c:30fb
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at d2504000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.2 0c03: 1002:4396 (prog-if 20)
	Subsystem: 103c:30fb
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at d2508400 (32-bit, non-prefetchable) [size=256]
	Capabilities: [c0] Power Management version 2
	Capabilities: [e4] Debug port: BAR=1 offset=00e0
	Kernel driver in use: ehci_hcd

00:14.0 0c05: 1002:4385 (rev 3a)
	Subsystem: 103c:30fb
	Flags: 66MHz, medium devsel
	Capabilities: [b0] HyperTransport: MSI Mapping Enable- Fixed+
	Kernel driver in use: piix4_smbus
	Kernel modules: i2c-piix4

00:14.1 0101: 1002:439c (prog-if 8a [Master SecP PriP])
	Subsystem: 103c:30fb
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 8000 [size=16]
	Capabilities: [70] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Kernel driver in use: pata_atiixp

00:14.2 0403: 1002:4383
	Subsystem: 103c:30fb
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at d2500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:14.3 0601: 1002:439d
	Subsystem: 103c:30fb
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 0604: 1002:4384 (prog-if 01)
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=80, subordinate=8f, sec-latency=64
	I/O behind bridge: 00001000-00001fff

00:18.0 0600: 1022:1300 (rev 40)
	Flags: fast devsel
	Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 0600: 1022:1301
	Flags: fast devsel

00:18.2 0600: 1022:1302
	Flags: fast devsel

00:18.3 0600: 1022:1303
	Flags: fast devsel
	Capabilities: [f0] Secure device <?>

00:18.4 0600: 1022:1304
	Flags: fast devsel

01:05.0 0300: 1002:9612
	Subsystem: 103c:30fb
	Flags: bus master, fast devsel, latency 0, IRQ 2297
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at 7000 [size=256]
	Memory at d2400000 (32-bit, non-prefetchable) [size=64K]
	Memory at d2300000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: [50] Power Management version 3
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx

01:05.1 0403: 1002:960f
	Subsystem: 1002:960f
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at d2410000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 3
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

08:00.0 0880: 197b:2382
	Subsystem: 103c:30fb
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at d1200300 (32-bit, non-prefetchable) [size=256]
	Expansion ROM at b0000000 [disabled] [size=64K]
	Capabilities: [a4] Power Management version 3
	Capabilities: [80] Express Endpoint, MSI 00
	Capabilities: [94] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

08:00.2 0805: 197b:2381 (prog-if 01)
	Subsystem: 103c:30fb
	Flags: fast devsel, IRQ 17
	Memory at d1200200 (32-bit, non-prefetchable) [size=256]
	Capabilities: [a4] Power Management version 3
	Capabilities: [80] Express Endpoint, MSI 00
	Capabilities: [94] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Kernel modules: sdhci-pci

08:00.3 0880: 197b:2383
	Subsystem: 103c:30fb
	Flags: bus master, fast devsel, latency 0, IRQ 5
	Memory at d1200100 (32-bit, non-prefetchable) [size=256]
	Capabilities: [a4] Power Management version 3
	Capabilities: [80] Express Endpoint, MSI 00
	Capabilities: [94] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-

08:00.4 0880: 197b:2384
	Subsystem: 103c:30fb
	Flags: bus master, fast devsel, latency 0, IRQ 5
	Memory at d1200000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [a4] Power Management version 3
	Capabilities: [80] Express Endpoint, MSI 00
	Capabilities: [94] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-

09:00.0 0280: 14e4:432b (rev 01)
	Subsystem: 103c:137f
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at d1100000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [40] Power Management version 3
	Capabilities: [58] Vendor Specific Information <?>
	Capabilities: [e8] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [d0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [13c] Virtual Channel <?>
	Capabilities: [160] Device Serial Number 21-00-5f-ff-ff-00-a0-25
	Capabilities: [16c] Power Budgeting <?>
	Kernel driver in use: wl
	Kernel modules: wl

0a:00.0 0200: 10ec:8136 (rev 02)
	Subsystem: 103c:30fb
	Flags: bus master, fast devsel, latency 0, IRQ 2298
	I/O ports at 2000 [size=256]
	Memory at d1010000 (64-bit, prefetchable) [size=4K]
	Memory at d1000000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at d1020000 [disabled] [size=128K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [70] Express Endpoint, MSI 01
	Capabilities: [ac] MSI-X: Enable- Mask- TabSize=2
	Capabilities: [cc] Vital Product Data <?>
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Virtual Channel <?>
	Capabilities: [160] Device Serial Number 00-00-ff-ff-00-00-01-43
	Kernel driver in use: r8169
	Kernel modules: r8169

```

---

### Post by GroovyTrucker on 2009-05-06
Okay, possessedskier - Thank you for that report! It seems that we have the same PCI boards. Make sure you have your current snapshot backed up if this goes wrong. Download the new snapshot, compile and let me know what you get then. It could be as simple as that. When you boot up with it make sure that you don't have anything but:
```
alias snd-card-0 snd-hda-intel
alias snd-slot-0 snd-hda-intel
```
in your /etc/modprobe.d/alsa-base file. You'll find that (at least if things haven't changed since yesterday) that you'll only have a Master choice in the Sound Recorder (at least if you're using PulseAudio).

---

### Post by possessedskier on 2009-05-07
I installed the latest snapshot on top of the new alsa version 1.0.20 that was released on 5/6 and put only the following in alsa-base.conf (it's .conf now in Ubuntu 9.04):

```
alias snd-card-0 snd-hda-intel
alias snd-slot-0 snd-hda-intel

```


There's no change with the mic.

---

### Post by GroovyTrucker on 2009-05-09
possessedskier:
Hmmm...is Skype the only thing not working? Or is nothing working? I installed Skype (though I don't plan on using it) and I had to use these settings:
Sound In - HDA ATI SB (hw:SB,0)
Sound Out - pulse
Ringing - pulse

Try adding this to your alsa-base after the snd-slot settings:
```
options snd-hda-intel model=hp-dv4-1222nr
```

maybe adding enable_msi=1 as well will fix it though I don't know. I don't have your specific model.

I am still running 8.10 and don't plan on upgrading for at least a couple of months, so if this doesn't work, I'm kinda at a loss. Good luck and keep me posted if you find a workaround or real fix. I'm hoping that eventually I'll get enough feedback on this from other hp-dv4 users that I can get everyone working properly.

Thanks for your patience and efforts.

---

### Post by jadez03 on 2009-05-10
Sorry for barging in on your topic, but I seem to be having the same/similar issue on similar hardware. I've subscribed to this topic and will do my best to try provide helpful information. I'm running a two day old install of jaunty x86 64, and have an hp pavillion dv7 1133cl.

Here is the output of my sudo lspci -nv:

```

00:00.0 0600: 1022:9600
    Subsystem: 103c:30fc
    Flags: bus master, 66MHz, medium devsel, latency 0
    Capabilities: [c4] HyperTransport: Slave or Primary Interface
    Capabilities: [54] HyperTransport: UnitID Clumping
    Capabilities: [40] HyperTransport: Retry Mode
    Capabilities: [9c] HyperTransport: #1a
    Capabilities: [f8] HyperTransport: #1c

00:01.0 0604: 103c:9602
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00007000-00007fff
    Memory behind bridge: d2300000-d24fffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
    Capabilities: [44] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [b0] Subsystem: 103c:30fc
    Kernel modules: shpchp

00:04.0 0604: 1022:9604
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=07, sec-latency=0
    I/O behind bridge: 00003000-00006fff
    Memory behind bridge: d1300000-d22fffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000d0ffffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [b0] Subsystem: 103c:30fc
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information <?>
    Capabilities: [110] Virtual Channel <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:05.0 0604: 1022:9605
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
    Memory behind bridge: d1200000-d12fffff
    Prefetchable memory behind bridge: 00000000b0000000-00000000b00fffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [b0] Subsystem: 103c:30fc
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information <?>
    Capabilities: [110] Virtual Channel <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:06.0 0604: 1022:9606
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
    Memory behind bridge: d1100000-d11fffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [b0] Subsystem: 103c:30fc
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information <?>
    Capabilities: [110] Virtual Channel <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:07.0 0604: 1022:9607
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: b0100000-b01fffff
    Prefetchable memory behind bridge: 00000000d1000000-00000000d10fffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [b0] Subsystem: 103c:30fc
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information <?>
    Capabilities: [110] Virtual Channel <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:11.0 0106: 1002:4391 (prog-if 01)
    Subsystem: 103c:30fc
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
    I/O ports at 8038 [size=8]
    I/O ports at 804c [size=4]
    I/O ports at 8030 [size=8]
    I/O ports at 8048 [size=4]
    I/O ports at 8010 [size=16]
    Memory at d2508000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [60] Power Management version 2
    Capabilities: [70] SATA HBA <?>
    Kernel driver in use: ahci

00:12.0 0c03: 1002:4397 (prog-if 10)
    Subsystem: 103c:30fc
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    Memory at d2507000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.1 0c03: 1002:4398 (prog-if 10)
    Subsystem: 103c:30fc
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    Memory at d2506000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.2 0c03: 1002:4396 (prog-if 20)
    Subsystem: 103c:30fc
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at d2508500 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci_hcd

00:13.0 0c03: 1002:4397 (prog-if 10)
    Subsystem: 103c:30fc
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at d2505000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.1 0c03: 1002:4398 (prog-if 10)
    Subsystem: 103c:30fc
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at d2504000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.2 0c03: 1002:4396 (prog-if 20)
    Subsystem: 103c:30fc
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    Memory at d2508400 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci_hcd

00:14.0 0c05: 1002:4385 (rev 3a)
    Subsystem: 103c:30fc
    Flags: 66MHz, medium devsel
    Capabilities: [b0] HyperTransport: MSI Mapping Enable- Fixed+
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c-piix4

00:14.1 0101: 1002:439c (prog-if 8a [Master SecP PriP])
    Subsystem: 103c:30fc
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 8000 [size=16]
    Capabilities: [70] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
    Kernel driver in use: pata_atiixp

00:14.2 0403: 1002:4383
    Subsystem: 103c:30fc
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at d2500000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:14.3 0601: 1002:439d
    Subsystem: 103c:30fc
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 0604: 1002:4384 (prog-if 01)
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=80, subordinate=8f, sec-latency=64
    I/O behind bridge: 00001000-00001fff

00:18.0 0600: 1022:1300 (rev 40)
    Flags: fast devsel
    Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 0600: 1022:1301
    Flags: fast devsel

00:18.2 0600: 1022:1302
    Flags: fast devsel

00:18.3 0600: 1022:1303
    Flags: fast devsel
    Capabilities: [f0] Secure device <?>

00:18.4 0600: 1022:1304
    Flags: fast devsel

01:05.0 0300: 1002:9612
    Subsystem: 103c:30fc
    Flags: bus master, fast devsel, latency 0, IRQ 2297
    Memory at c0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at 7000 [size=256]
    Memory at d2400000 (32-bit, non-prefetchable) [size=64K]
    Memory at d2300000 (32-bit, non-prefetchable) [size=1M]
    Capabilities: [50] Power Management version 3
    Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx

01:05.1 0403: 1002:960f
    Subsystem: 1002:960f
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at d2410000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 3
    Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

08:00.0 0880: 197b:2382
    Subsystem: 103c:30fc
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at d1200300 (32-bit, non-prefetchable) [size=256]
    Expansion ROM at b0000000 [disabled] [size=64K]
    Capabilities: [a4] Power Management version 3
    Capabilities: [80] Express Endpoint, MSI 00
    Capabilities: [94] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

08:00.2 0805: 197b:2381 (prog-if 01)
    Subsystem: 103c:30fc
    Flags: fast devsel, IRQ 17
    Memory at d1200200 (32-bit, non-prefetchable) [size=256]
    Capabilities: [a4] Power Management version 3
    Capabilities: [80] Express Endpoint, MSI 00
    Capabilities: [94] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
    Kernel modules: sdhci-pci

08:00.3 0880: 197b:2383
    Subsystem: 103c:30fc
    Flags: bus master, fast devsel, latency 0, IRQ 5
    Memory at d1200100 (32-bit, non-prefetchable) [size=256]
    Capabilities: [a4] Power Management version 3
    Capabilities: [80] Express Endpoint, MSI 00
    Capabilities: [94] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-

08:00.4 0880: 197b:2384
    Subsystem: 103c:30fc
    Flags: bus master, fast devsel, latency 0, IRQ 5
    Memory at d1200000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [a4] Power Management version 3
    Capabilities: [80] Express Endpoint, MSI 00
    Capabilities: [94] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-

09:00.0 0280: 168c:002a (rev 01)
    Subsystem: 103c:1381
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at d1100000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [40] Power Management version 2
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
    Capabilities: [60] Express Legacy Endpoint, MSI 00
    Capabilities: [90] MSI-X: Enable- Mask- TabSize=1
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [140] Virtual Channel <?>
    Capabilities: [160] Device Serial Number 00-00-00-00-00-00-00-00
    Kernel driver in use: ath9k
    Kernel modules: ath9k

0a:00.0 0200: 10ec:8136 (rev 02)
    Subsystem: 103c:30fc
    Flags: bus master, fast devsel, latency 0, IRQ 2298
    I/O ports at 2000 [size=256]
    Memory at d1010000 (64-bit, prefetchable) [size=4K]
    Memory at d1000000 (64-bit, prefetchable) [size=64K]
    Expansion ROM at d1020000 [disabled] [size=128K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
    Capabilities: [70] Express Endpoint, MSI 01
    Capabilities: [ac] MSI-X: Enable- Mask- TabSize=2
    Capabilities: [cc] Vital Product Data <?>
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [140] Virtual Channel <?>
    Capabilities: [160] Device Serial Number 00-00-ff-ff-00-00-00-50
    Kernel driver in use: r8169
    Kernel modules: r8169

```

Please let me know if there's anything else I could provide to maybe help find a solution to this problem :)

Thanks!

---

### Post by GroovyTrucker on 2009-05-10
Hi jadez03, I'll probably not be able to help you directly, but you can try using the hda_analyzer python program from the ALSA project. It's URL is [http://www.alsa-project.org/main/index.php/HDA_Analyzer]("http://www.alsa-project.org/main/index.php/HDA_Analyzer"). You might have problems with it as it doesn't always read all the hda nodes properly. Make sure you run it with sudo otherwise it will say you don't have the proper permissions.

The reason I can't directly help you is that 1) I don't have your model and 2) your PCI board is different from mine, meaning that your settings will probably be different from mine.

In your lspci you'll notice lines like:
```
subsystem: 103c:30fc
```
The 103c is HP's vendor ID, while the 30fc is the PCI board ID.
Looking at possessedskier's you'll notice that his/hers is 103c:30fb. Mine is the same as possessedskier's, therefore my mods to the ALSA project's code is keyed to that board. You can add the
```
options model=hp-dv4-1222nr
``` and hope for the best, but YMMV.

Play with hda_analyzer and you'll probably find the right settings. These can then be used to create hda_verb commands to run in a script. Go to IDT's website and they have the specs downloadable in PDF form for their different chipsets. Intel has the generic HDA specification. Put them together and you can eventually find what you need. That's what I did and after reading the source for ALSA it isn't that difficult to figure it out. Of course, I'm assuming you are familiar with C programming :).

Good luck and Godspeed. We all need people to create mods to the ALSA drivers. Sooner or later we'll get to all of HP's umpteen different models.

---

### Post by jadez03 on 2009-05-10
Thanks for the quick reply Groovy :o

Right after I posted that, in my excitement getting back into development (i stopped tinkering a few years ago), i went out and picked up O'Rielly's Linux Device Drivers 3rd edition at the book store. There's a lot about ALSA and the way it's processed, so I'm beginning to understand a bit more.

And thanks for the info on HDA, i'll definitely give a try, OOP doesn't scare me ;).

You've been a tremendous help, and quite quick about it too! 

I'll report back after I mess around some more. Thanks again!

---

### Post by NazarXG on 2009-05-12
I have STAC92HD71B. I guess I was happy too soon, because the internal speaker working is sporadic, but what I have listed works with the mic 100% on dv4-1225dx.

You are right, enable_msi=1 has no effect whatsoever.

```
00:00.0 0600: 1022:9600
	Subsystem: 103c:30fb
	Flags: bus master, 66MHz, medium devsel, latency 0
	Capabilities: [c4] HyperTransport: Slave or Primary Interface
	Capabilities: [54] HyperTransport: UnitID Clumping
	Capabilities: [40] HyperTransport: Retry Mode
	Capabilities: [9c] HyperTransport: #1a
	Capabilities: [f8] HyperTransport: #1c

00:01.0 0604: 103c:9602
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00007000-00007fff
	Memory behind bridge: d2300000-d24fffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
	Capabilities: [44] HyperTransport: MSI Mapping Enable+ Fixed+
	Capabilities: [b0] Subsystem: 103c:30fb
	Kernel modules: shpchp

00:04.0 0604: 1022:9604
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=07, sec-latency=0
	I/O behind bridge: 00003000-00006fff
	Memory behind bridge: d1300000-d22fffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000d0ffffff
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Root Port (Slot+), MSI 00
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [b0] Subsystem: 103c:30fb
	Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
	Capabilities: [100] Vendor Specific Information <?>
	Capabilities: [110] Virtual Channel <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:05.0 0604: 1022:9605
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
	Memory behind bridge: d1200000-d12fffff
	Prefetchable memory behind bridge: 00000000b0000000-00000000b00fffff
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Root Port (Slot+), MSI 00
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [b0] Subsystem: 103c:30fb
	Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
	Capabilities: [100] Vendor Specific Information <?>
	Capabilities: [110] Virtual Channel <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:06.0 0604: 1022:9606
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
	Memory behind bridge: d1100000-d11fffff
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Root Port (Slot+), MSI 00
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [b0] Subsystem: 103c:30fb
	Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
	Capabilities: [100] Vendor Specific Information <?>
	Capabilities: [110] Virtual Channel <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:07.0 0604: 1022:9607
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: b0100000-b01fffff
	Prefetchable memory behind bridge: 00000000d1000000-00000000d10fffff
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Root Port (Slot+), MSI 00
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [b0] Subsystem: 103c:30fb
	Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
	Capabilities: [100] Vendor Specific Information <?>
	Capabilities: [110] Virtual Channel <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:11.0 0106: 1002:4391 (prog-if 01)
	Subsystem: 103c:30fb
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
	I/O ports at 8038 [size=8]
	I/O ports at 804c [size=4]
	I/O ports at 8030 [size=8]
	I/O ports at 8048 [size=4]
	I/O ports at 8010 [size=16]
	Memory at d2508000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [60] Power Management version 2
	Capabilities: [70] SATA HBA <?>
	Kernel driver in use: ahci

00:12.0 0c03: 1002:4397 (prog-if 10)
	Subsystem: 103c:30fb
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at d2507000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:12.1 0c03: 1002:4398 (prog-if 10)
	Subsystem: 103c:30fb
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at d2506000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:12.2 0c03: 1002:4396 (prog-if 20)
	Subsystem: 103c:30fb
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at d2508500 (32-bit, non-prefetchable) [size=256]
	Capabilities: [c0] Power Management version 2
	Capabilities: [e4] Debug port: BAR=1 offset=00e0
	Kernel driver in use: ehci_hcd

00:13.0 0c03: 1002:4397 (prog-if 10)
	Subsystem: 103c:30fb
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at d2505000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.1 0c03: 1002:4398 (prog-if 10)
	Subsystem: 103c:30fb
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at d2504000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.2 0c03: 1002:4396 (prog-if 20)
	Subsystem: 103c:30fb
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at d2508400 (32-bit, non-prefetchable) [size=256]
	Capabilities: [c0] Power Management version 2
	Capabilities: [e4] Debug port: BAR=1 offset=00e0
	Kernel driver in use: ehci_hcd

00:14.0 0c05: 1002:4385 (rev 3a)
	Subsystem: 103c:30fb
	Flags: 66MHz, medium devsel
	Capabilities: [b0] HyperTransport: MSI Mapping Enable- Fixed+
	Kernel driver in use: piix4_smbus
	Kernel modules: i2c-piix4

00:14.1 0101: 1002:439c (prog-if 8a [Master SecP PriP])
	Subsystem: 103c:30fb
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 8000 [size=16]
	Capabilities: [70] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Kernel driver in use: pata_atiixp

00:14.2 0403: 1002:4383
	Subsystem: 103c:30fb
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at d2500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:14.3 0601: 1002:439d
	Subsystem: 103c:30fb
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 0604: 1002:4384 (prog-if 01)
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=80, subordinate=8f, sec-latency=64
	I/O behind bridge: 00001000-00001fff

00:18.0 0600: 1022:1300 (rev 40)
	Flags: fast devsel
	Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 0600: 1022:1301
	Flags: fast devsel

00:18.2 0600: 1022:1302
	Flags: fast devsel

00:18.3 0600: 1022:1303
	Flags: fast devsel
	Capabilities: [f0] Secure device <?>

00:18.4 0600: 1022:1304
	Flags: fast devsel

01:05.0 0300: 1002:9612
	Subsystem: 103c:30fb
	Flags: bus master, fast devsel, latency 0, IRQ 2297
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at 7000 [size=256]
	Memory at d2400000 (32-bit, non-prefetchable) [size=64K]
	Memory at d2300000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: [50] Power Management version 3
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx

01:05.1 0403: 1002:960f
	Subsystem: 1002:960f
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at d2410000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 3
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

08:00.0 0880: 197b:2382
	Subsystem: 103c:30fb
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at d1200300 (32-bit, non-prefetchable) [size=256]
	Expansion ROM at b0000000 [disabled] [size=64K]
	Capabilities: [a4] Power Management version 3
	Capabilities: [80] Express Endpoint, MSI 00
	Capabilities: [94] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

08:00.2 0805: 197b:2381 (prog-if 01)
	Subsystem: 103c:30fb
	Flags: fast devsel, IRQ 17
	Memory at d1200200 (32-bit, non-prefetchable) [size=256]
	Capabilities: [a4] Power Management version 3
	Capabilities: [80] Express Endpoint, MSI 00
	Capabilities: [94] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Kernel modules: sdhci-pci

08:00.3 0880: 197b:2383
	Subsystem: 103c:30fb
	Flags: bus master, fast devsel, latency 0, IRQ 5
	Memory at d1200100 (32-bit, non-prefetchable) [size=256]
	Capabilities: [a4] Power Management version 3
	Capabilities: [80] Express Endpoint, MSI 00
	Capabilities: [94] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-

08:00.4 0880: 197b:2384
	Subsystem: 103c:30fb
	Flags: bus master, fast devsel, latency 0, IRQ 5
	Memory at d1200000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [a4] Power Management version 3
	Capabilities: [80] Express Endpoint, MSI 00
	Capabilities: [94] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-

09:00.0 0280: 14e4:4315 (rev 01)
	Subsystem: 103c:137c
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at d1100000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [40] Power Management version 3
	Capabilities: [58] Vendor Specific Information <?>
	Capabilities: [e8] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [d0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [13c] Virtual Channel <?>
	Capabilities: [160] Device Serial Number 21-00-a5-ff-ff-00-6d-f8
	Capabilities: [16c] Power Budgeting <?>
	Kernel driver in use: wl
	Kernel modules: wl

0a:00.0 0200: 10ec:8136 (rev 02)
	Subsystem: 103c:30fb
	Flags: bus master, fast devsel, latency 0, IRQ 2298
	I/O ports at 2000 [size=256]
	Memory at d1010000 (64-bit, prefetchable) [size=4K]
	Memory at d1000000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at d1020000 [disabled] [size=128K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [70] Express Endpoint, MSI 01
	Capabilities: [ac] MSI-X: Enable- Mask- TabSize=2
	Capabilities: [cc] Vital Product Data <?>
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Virtual Channel <?>
	Capabilities: [160] Device Serial Number 00-00-ff-ff-00-00-00-c9
	Kernel driver in use: r8169
	Kernel modules: r8169

```

I hope this helps :)

Now I'm experiencing a rather different problem after upgrading to ubuntu 9.04, display redraws leave black spaces on the screen. ...

---

### Post by Iowan on 2009-05-13
Well,  another problem (for me) to solve... My dv4-1222nr microphone won't work with Sound Recorder.  I did manage to get internal speaker working, but it was touchy - putting things back didn't always undo the effect.  Currently working, so dunno if I wanna risk the one step forward for the possible two steps back. (But got the thread marked - just in case).

---

### Post by NazarXG on 2009-05-14
I noticed that as well, speaker/headphone/mic work randomly. Sometimes all work, sometimes only headphones, etc. I can't figure it out...

---

### Post by GroovyTrucker on 2009-05-16
Hi Iowan, welcome to our little hell :)
I noticed that you're using the same computer as I am. I don't know if you are using the AMD64 version of Ubuntu like me, but I'll let you know that the 64-bit works better with 8.10 than what you are reporting that you use. Another thing is that if you've at least upgraded to 8.10 things *will* work, although I've not upgraded to 9.04 yet and I don't know if Ubuntu has changes that affect things. If you download the latest stable snapshot (I don't know about the unstable snapshot) from the ALSA project it will autodetect the dv4-1222nr. I know - I created the patch set for it. After downloading and unzipping, cd to the toplevel of the ALSA source and
```
./configure
make
sudo make install
```
then change your /etc/modprobe.d/alsa-base to *only*
```
alias snd-card-0 snd-hda-intel
alias snd-slot-0 snd-hda-intel
```
and reboot.
Your gnome-volume-control will then be usable after you set the Preferences to include the Capture1 and Digital Input Source sliders. Then go to Options, select the Digital Mic1 setting for the built-in microphone, or select Analog Inputs for a plugged-in one. Set Capture1 slider to desired level and you should be set.
I will admit that I don't know if this works with any other board/model/Ubuntu flavor/Ubuntu version. I need dv4-1222nr testers to let me know if the HDMI settings work, because I don't have a means to know if they work.

---

### Post by GroovyTrucker on 2009-05-17
Hey NaxarXG, I was looking back at one of your previous posts. If you are using PulseAudio, try changing all of your System->Preferences->Sound to pulseaudio, except Default Mixer Tracks which you can't set to that anyway. This is what I've done. See if that works.

---

### Post by Iowan on 2009-05-20
> **GroovyTrucker said:**
> Hi Iowan, welcome to our little hell :)
I noticed that you're using the same computer as I am. I don't know if you are using the AMD64 version of Ubuntu like me, but I'll let you know that the 64-bit works better with 8.10 than what you are reporting that you use.  Yup, I dual-boot Jaunty-64 with Vista on the laptop (my desktop runs Gutsy). After the horror stories about Network Manager in Hardy and Intrepid, I'm either lucky (unlikely) or they've ironed out many of the problems.  

I don't have anything to try the HDMI, either.

Gotta make a backup, take a deep breath, and try the snapshot...
(Don't s'pose it fixes the mute icon?)

---

### Post by GroovyTrucker on 2009-05-22
Iowan asks:
(Don't s'pose it fixes the mute icon?)

Why, yes it does :D

---

### Post by GroovyTrucker on 2009-05-29
Iowan (and others):
There has been a recent modification to the ALSA snapshot that will affect any attempts to use the driver i.e. it just won't work. If possible, use alsa-driver-20090527 or earlier. I've sent a message to the maintainers letting them know...

Oh and BTW I know my mods work with Jaunty: I setup a temporary WUBI installation to test it.

---

### Post by Iowan on 2009-05-30
Jaunty must have fixed "most" of the problems.  The microphone works - audio level is just down (I turned up my headphones, and can hear recordings - VU meter shows microphone working.  So far, the only thing that doesn't seem to work is that "mute" button.  Well, it works (mutes sound), but doesn't turn orange (red?) like it does when disabled under Windows.  Thanks for warning - if/when I get brave enough to try the snapshot, I'll look for alsa-driver-20090527.

---

### Post by GroovyTrucker on 2009-06-03
Problems worked out...snapshot works now.

---

