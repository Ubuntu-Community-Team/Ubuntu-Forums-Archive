---
title: "Did i blow my sound card with my guitar amp?"
date: 2008-03-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by darkenemy on 2008-03-06
im running hardy alpha 5 on this setup

AMD X2 64-bit 6400+ Processor
Asus M2N-SLI Motherboard

I run 5.1 speakers through the on board sound

Recently, the audio seemed to work fine, until i decided to attach my guitar amp to the mic input on the front of my box.  The line i took from the guitar amp was designed for headphones to be plugged in, and i figured that if no harm would come to headphones, then my computer should be able to take the input with no issues

well, it worked for a bit-but was VERY scratchy and over distorted.  after about a minuet it seemed to get quieter, and i could hear my guitar less and less.  now, here it gets tricky because the cable i connected my guitar to the amp with was actually not so great, and so i thought that this was the reason for the mess of sound.

i unplugged the mic input after a minuet or so and gave it up.  later i noticed that my computer wasn't outputting any sound, so i checked to make sure all the volumes were up (via the speaker icon on the top bar) and found no issue.  

i plugged the speakers into another computer and they worked just fine -- which means there is no problems with the speakers themselves.

I put in a DVD and tried to listen to it, adn found that if i turn up my speakers and all the inputs on my computer, i _can_ faintly hear the sound from the DVD.  but it too is pretty scratchy and very low in volume, compared to usual.

I checked my sound stuff (under System>Preferences>Sound to find that when i push test, i can hear the test beep, a little louder than the dvd, but still not what it should be when my speakers are up all the way.

here are some outputs of some commands -- hopefully they can help nail down the issue

```
alpha@alpha-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 0: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [PnP Audio Device        ], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

```
lspci -v
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a4)
	Subsystem: ASUSTeK Computer Inc. A8N-E Mainboard
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev f1)
	Subsystem: ASUSTeK Computer Inc. K8N4-E or A8N-E Mainboard
	Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
	Subsystem: ASUSTeK Computer Inc. K8N4-E or A8N-E Mainboard
	Flags: 66MHz, fast devsel, IRQ 11
	I/O ports at fc00 [size=32]
	I/O ports at 4c00 [size=64]
	I/O ports at 4c40 [size=64]
	Capabilities: <access denied>

00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2) (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. K8N4-E or A8N-E Mainboard
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a4) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. K8N4-E or A8N-E Mainboard
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at fe02e000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f3) (prog-if 8a [Master SecP PriP])
	Subsystem: ASUSTeK Computer Inc. K8N4-E or A8N-E Mainboard
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at e800 [size=16]
	Capabilities: <access denied>

00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3) (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. A8N-E Mainboard
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	I/O ports at 09f0 [size=8]
	I/O ports at 0bf0 [size=4]
	I/O ports at 0970 [size=8]
	I/O ports at 0b70 [size=4]
	I/O ports at d400 [size=16]
	Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3) (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. K8N4-E or A8N-E Mainboard
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	I/O ports at 09e0 [size=8]
	I/O ports at 0be0 [size=4]
	I/O ports at 0960 [size=8]
	I/O ports at 0b60 [size=4]
	I/O ports at c000 [size=16]
	Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev f2) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=128
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: fdf00000-fdffffff

00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev f3)
	Subsystem: ASUSTeK Computer Inc. Unknown device 812a
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at fe02a000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at bc00 [size=8]
	Capabilities: <access denied>

00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Capabilities: <access denied>

00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Capabilities: <access denied>

00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Capabilities: <access denied>

00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: fde00000-fdefffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>

01:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0) (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 81fe
	Flags: bus master, medium devsel, latency 32, IRQ 17
	Memory at fdfff000 (32-bit, non-prefetchable) [size=2K]
	I/O ports at ac00 [size=128]
	Capabilities: <access denied>

05:00.0 VGA compatible controller: ATI Technologies Inc RV630 [Radeon HD 2600XT] (prog-if 00 [VGA controller])
	Subsystem: Hightech Information System Ltd. Unknown device 2003
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fdee0000 (64-bit, non-prefetchable) [size=64K]
	I/O ports at 9c00 [size=256]
	Expansion ROM at fdec0000 [disabled] [size=128K]
	Capabilities: <access denied>

05:00.1 Audio device: ATI Technologies Inc RV630/M76 audio device [Radeon HD 2600 Series]
	Subsystem: Hightech Information System Ltd. Unknown device aa08
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at fdefc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>


```

when i do a test under preferences>sound the only one that works is the pulse audio one.  The OSS appears to work, but doesnt actually make any sounds, and neither ATI HDMI, USB audio, or ALSA work at all -> they give this message 

> audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.




the output of 

```
alsamixer
```

looks like this

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=61788&stc=1&d=1204821860[/IMG]



could it be that i blew my sound card?
 
any help whatsoever would be very appreciated

---

### Post by Whiffle on 2008-03-06
Sounds like its toasted to me.  From your descriptioon of the initial sound quality, it had way too much amplitude, causing the input to clip.  Given enough time, that could definitly burn something up.  I'd try a different sound card and one of those inputs made for guitars :D

---

### Post by RD1 on 2008-03-06
OUCH! I'm afraid you blew it.
A headphone output is stronger than a line out. And the mic input is boosted. This is the reason for the distorted sound you heard.
You should NEVER connect a headphone out to a mic in.
If you have a line level output it should be connected to a line in. If you only have a phone out, you can connect it to a line in if you are careful. First, open the input mixer controls and lower the line in level completely. Then, with the output of the phone out turned down, make the connection. Slowly increase line in and phone out while observing recording levels. It won't take much to max out the recording level into the red.

Sorry but, I believe you are gonna need a new sound card. :(

---

### Post by darkenemy on 2008-03-06
alright :( thanx very much.... they're not that expensive i guess....

---

### Post by crjackson on 2008-03-07
> **RD1 said:**
> OUCH! I'm afraid you blew it.
A headphone output is stronger than a line out. And the mic input is boosted. This is the reason for the distorted sound you heard.
You should NEVER connect a headphone out to a mic in.
If you have a line level output it should be connected to a line in. If you only have a phone out, you can connect it to a line in if you are careful. First, open the input mixer controls and lower the line in level completely. Then, with the output of the phone out turned down, make the connection. Slowly increase line in and phone out while observing recording levels. It won't take much to max out the recording level into the red.

Sorry but, I believe you are gonna need a new sound card. :(

+1

You fubar'd it dude...  No doubt about it at all...

---

