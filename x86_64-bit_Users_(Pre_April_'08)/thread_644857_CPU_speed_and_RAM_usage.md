---
title: "CPU speed and RAM usage"
date: 2007-12-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by magikx21 on 2007-12-19
Using s a variety of system monitors for Superkaramba I have noticed a couple odd things. I am running Kubuntu 7.10 x64 and the processor is an AMD Semphon 1.8Ghz. Typically when I open the monitors it shows CPU speed as 1800Mhz, alright no problem there. After walking away from the PC for awhile and coming back it shows CPU speed as 1000Mhz. After reloading the theme it goes back to 1800Mhz for awhile. Anyone else had this problem or know why this is happening.

Also using these monitors I've noticed that after booting my RAM fills until there is about 20-10MB left and sits in that area for the rest of the time. Everything seems to run fine though and swap usage stays quite low (always under 100mb). Is this normal? I have 1 GB Ram in the system now.

---

### Post by mellowd on 2007-12-19
The cpu speed is dynamic because of cool and quiet. It only goes up to 1800 when its needed. If you really must keep it at 1800MHz at all times regardless of what its doing you can turn it off in the bios

---

### Post by mellowd on 2007-12-19
And yes, your ram usage is quite normal.

---

### Post by fjgaude on 2007-12-19
If you install into the Gnome panel CPU Freq Scaling Monitor, and then do this:

```
sudo chmod +s /usr/bin/cpufreq-selector
```

When you left click on the icon in the panel you have the able to set the speed and features where you wsih them to be.

---

### Post by magikx21 on 2007-12-19
I will leave cool and quiet on. It just rhough me off that my speed seemed to change. I figured something of the sort was happening but I wans't positive.

---

