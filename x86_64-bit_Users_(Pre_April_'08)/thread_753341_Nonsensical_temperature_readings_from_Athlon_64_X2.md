---
title: "Nonsensical temperature readings from Athlon 64 X2"
date: 2008-04-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by jeeves on 2008-04-12
I recently installed **lm-sensors** to monitor the temperature on my  **AMD Athlon 64 X2 Dual Core Processor 5400**. Although I get temperature readings for the CPU, they make no sense at all -- since all the core temperature readings are showing the CPU to be close to freezing!

Here is what I get when I run the** sensors **command in terminal:
```
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:
              +1°C
Core0 Temp:
              -4°C
Core1 Temp:
              +3°C
Core1 Temp:
             -12°C

it8716-isa-0290
Adapter: ISA adapter
VCore:     +1.01 V  (min =  +0.00 V, max =  +4.08 V)   
VDDR:      +3.14 V  (min =  +0.00 V, max =  +4.08 V)   
+3.3V:     +0.00 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
+5V:       +4.76 V  (min =  +0.00 V, max =  +6.85 V)   
+12V:     +11.65 V  (min =  +0.00 V, max = +16.32 V)   
in5:       +0.00 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
in6:       +0.00 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
5VSB:      +4.62 V  (min =  +0.00 V, max =  +6.85 V)   
VBat:      +2.90 V
fan1:     2436 RPM  (min = 3245 RPM)                   ALARM
fan2:     1744 RPM  (min = 3245 RPM)                   ALARM
fan3:        0 RPM  (min =    0 RPM)                   
temp1:       +20°C  (low  =    -1°C, high =  +127°C)   sensor = diode   
temp2:       +30°C  (low  =    -1°C, high =  +127°C)   sensor = thermistor   
temp3:       +25°C  (low  =    -1°C, high =  +127°C)   sensor = thermistor   
vid:      +0.925 V

```

I'm assuming "core0, core1, etc. are the reading for the CPU. Any ideas on how to find out what the true temperature of my CPU is?

---

### Post by mkarnicki on 2008-04-12
Haha, funny. And I've got scaling problems (using 2.6.24-15 and always 2GHz) I've got:

```

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +62.0°C
Core0 Temp:  +57.0°C
Core1 Temp:  +60.0°C
Core1 Temp:  +54.0°C

```
I hope it's not too bad.. is it?

---

### Post by Yellow Pasque on 2008-04-12
The temperature from the CPU itself behaves exactly the same way for me (X2 4800 Brisbane here). One of the temp sensors from the mobo sensor chip is probably set to monitor the CPU. Do something that stresses the CPU for a bit and see if one of those goes up.

---

### Post by xelapond on 2008-04-12
What kind of cooling do you have in that thing?:lolflag:

---

### Post by dcstar on 2008-04-12
> **jeeves said:**
> I recently installed **lm-sensors** to monitor the temperature on my  **AMD Athlon 64 X2 Dual Core Processor 5400**. Although I get temperature readings for the CPU, they make no sense at all -- since all the core temperature readings are showing the CPU to be close to freezing!
........
I'm assuming "core0, core1, etc. are the reading for the CPU. Any ideas on how to find out what the true temperature of my CPU is?

It is a know problem in the "Brisbane" core X2s, add 20C to the readings and they are closer to reality.

---

### Post by jamesford on 2008-04-13
i have temps well below 30 idle too on my x2 6000+
im using a thermalright ultra-120 extreme and yes the temps correspond with the temps listed in bios

---

### Post by mlapaglia on 2008-05-21
I've got a 4400+ brisbane, my stock temperatures are like everyone else, negative values, 9 degrees, etc.

I have 4 cpu sensor values.. 2 from the chip and 2 from the board I guess. after adding 20 degrees to all of them i am getting 36, 34, 41, and 41.. under 100% load for the past hour.

Any way to get the correct temperatures, or is this processor line just crap with sensors?

---

### Post by slick_nick on 2008-05-29
Just checking; I know I made this mistake when I first installed lm-sensors! Did you run "sudo sensors detect" after you installed it?
Also, as others have suggested, you may have to put in an adjustment factor.  IMO run a heavy load on your processor, see what reading it is giving you in ubuntu; restart, go into your BIOS and check the cpu temp reading there.
I'm on a buddy's laptop right now, not on my desktop, but from what I can recall, there are 2 sensors readings that are pretty close. I determined which one was my cpu by putting a load on it and seeing which reading climbed first.
Hope this helps!

---

