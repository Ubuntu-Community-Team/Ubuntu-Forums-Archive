---
title: "Fan control in Gusty amd64"
date: 2007-12-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by sings64 on 2007-12-05
I have the following machine... HP pavilion desktop a6235x with AMD Athlon 64 X2 6000+ (3GHz) with 4Gb ram.  I have removed vista and installed gusty amd64 edition.  

Problem: my cpu (and case) fan speeds never change, even when both cores are taxed for an hour.  The core temps max out at ~68 C, which seems unnecessary since the fan is still running so slow.  I get the temps from lm_sensors.

I've noticed that the temp given by acpi (/proc/acpi/thermal_zone/THRM/temperature) is always 40 C and fan is always simply listed as 'on'.

Is there any way to 1) check the cpu fan speed and 2) control the fan speed in Gusty and64?

I've seen references to i8k and dellfand but I haven't for the life of me been able to find an answer for a standard amd64 PC.

Help please! This is potentially a show stopper because this machine is meant to be a number cruncher.

---

### Post by Yellow Pasque on 2007-12-05
Do you have fan control Enabled in the BIOS? Try disabling it and running: 
```
sudo pwmconfig
```
to control the fans in software. This script will allow you to choose the sensor you want to correspond with the fan speed.
Note: IF you have quiet fans, you'll probably need to open your case so you can watch your fan and set it up accurately.

Good luck and keep us informed.

---

### Post by sings64 on 2007-12-05
pwmconfig gives the following result:

/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed

As such, none of the available monitoring applets pick up fan info -- just hdd and cpu tmps.

Question: is acpi controlling the fan speed?  If so, does the fact that acpi reports the same 40 C value indicate that my fan speed problem lies in acpi somewhere??

---

### Post by sings64 on 2007-12-05
Fan control in BIOS -- there isn't any mention of fan control in my bios settings.  My BIOS is a Phoenix AwardBios v. 6.0

---

### Post by Yellow Pasque on 2007-12-05
> **sings64 said:**
> pwmconfig gives the following result:
/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed

Have you run *sudo sensors-detect* yet?

> Question: is acpi controlling the fan speed? If so, does the fact that acpi reports the same 40 C value indicate that my fan speed problem lies in acpi somewhere??
It could be. Any option for disabling ACPI in the BIOS to see if that helps? (even if you don't leave it off permanently)

---

### Post by vgrisham on 2007-12-07
> **Temüjin said:**
> Have you run *sudo sensors-detect* yet?



That command wouldn't do anything. Would you please clarify what you mean?

---

### Post by saru411 on 2007-12-08
i8k is not available in 64bit. ive dug around these forums looking for it earlier this fall and everywhere i turned i got the same answer. no i8k for us. its the one thing i really need to make 64bit ubuntu THE o/s to run on my laptop........and dont worry about hurting your cpu, i've found that its common knowledge that laptop cpus can run at much higher temps compared to desktops. 70*c is when your fan will kick in to high gear. thats what happens on my laptop anyway.

give us our i8k please!

---

### Post by sings64 on 2007-12-11
Thanks saru411.

And yes, that is essentially where this problem has led me -- so I guess it is simply not possible to control the fan manually in amd65 Gusty.

Although I agree that the temps are probably OK, it just seems odd that the fan always runs at the same speed.  As I've said this machine will be used to run very long jobs (days to a week) which use 100% of the cpu.  I am considering wiring the cpu fan directly to the power supply -- at least that way I can test how much cooler it will run under full load.

---

### Post by Yellow Pasque on 2007-12-11
> **vgrisham said:**
> That command wouldn't do anything. Would you please clarify what you mean?
You'll need the lmsensors package (possibly libsensors too). Install them in Synaptic and then try sensors-detect again.

---

