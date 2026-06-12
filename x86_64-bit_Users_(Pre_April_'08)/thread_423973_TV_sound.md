---
title: "TV sound"
date: 2007-04-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by Colin.mcewan on 2007-04-26
Just installed fiesty.

TV utilities work but I can't get any sound. The card is a Philips based 7130 (which is recognised). It is all the more annoying since a previous Suse distro set it all up automatically.

Anyone help please?

---

### Post by modorf on 2007-04-26
is module saa7133-alsa loaded?
dmesg information for loaded modules.

---

### Post by Colin.mcewan on 2007-04-27
Hi thanks for coming back.

Plenty of mentions of saa7130/4 (see below if you understand these things.) There is no mention of saa7133-alsa.

What it does say is :


saa7130/34: v4l2 driver version 0.2.14 loaded


49.873581] saa7134 ALSA driver for DMA sound loaded
[   49.873612] saa7130[0]/alsa: saa7130[0] at 0xf7e00000 irq 16 registered as card -2

Does this help or hinder ?

Colin




The full listing for the tuner is as follows:

 49.680236] saa7130[0]: found at 0000:00:0b.0, rev: 1, irq: 16, latency: 64, mmio: 0xf7e00000
[   49.680242] saa7130[0]: subsystem: 4e42:0138, board: LifeView/Typhoon FlyVIDEO2000 [card=3,autodetected]
[   49.680251] saa7130[0]: board init: gpio is 39000
[   49.680253] saa7130[0]: there are different flyvideo cards with different tuners
[   49.680255] saa7130[0]: out there, you might have to use the tuner=<nr> insmod
[   49.680256] saa7130[0]: option to override the default value.
[   49.680359] input: saa7134 IR (LifeView/Typhoon Fl as /class/input/input5
[   49.826658] saa7130[0]: i2c eeprom 00: 42 4e 38 01 10 28 ff ff ff ff ff ff ff ff ff ff
[   49.826666] saa7130[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   49.826672] saa7130[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   49.826678] saa7130[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   49.826683] saa7130[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   49.826689] saa7130[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   49.826694] saa7130[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   49.826700] saa7130[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   49.854618] tuner 1-0061: chip found @ 0xc2 (saa7130[0])
[   49.854665] tuner 1-0061: type set to 37 (LG PAL (newer TAPC series))
[   49.854668] tuner 1-0061: type set to 37 (LG PAL (newer TAPC series))
[   49.857074] saa7130[0]: registered device video0 [v4l2]
[   49.857099] saa7130[0]: registered device vbi0
[   49.857121] saa7130[0]: registered device radio0
[   49.857252] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 22
[   49.857390] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   49.873581] saa7134 ALSA driver for DMA sound loaded
[   49.873612] saa7130[0]/alsa: saa7130[0] at 0xf7e00000 irq 16 registered as card -2
[   50.372263] codec_read: codec 0 is not valid [0xfe0000]

---

### Post by modorf on 2007-04-27
[ 49.873581] saa7134 ALSA driver for DMA sound loaded
[ 49.873612] saa7130[0]/alsa: saa7130[0] at 0xf7e00000 irq 16 registered as card -2

the alsa driver is getting loaded, but getting assigned sound card -2, which doesn't help.
You probably want it as sound card 1, to do this you need to pass an option to the saa7133 driver.

/etc/modprobe.d/options
options saa7134 alsa=1

---

### Post by Colin.mcewan on 2007-04-27
Thanks Modorf, I tried it

I added 

options saa7134 alsa=1

and

options saa7130 alsa=1 (just for luck)

to /etc/modprobe.d/options

but it doesn't seem to have achieved anything.

I guess I'll need to keep digging . . .

Cheers

Colin

---

