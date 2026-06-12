---
title: "lm_sensors"
date: 2006-09-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by sonni_kuba on 2006-09-28
Dear all,

I was curious if anyone of you had managed to get lm-sensors working in a 64-bit distro. I have followed a number of the guides, but I keep getting an error that k8temp module is not found, when I run sensors-detect.

Any ideas...

ASUS M2N-E, FX-62, 2 GB RAM, 2x320 GB SATA Linux RAID

---

### Post by Bachstelze on 2006-09-28
Tried *sudo modprobe k8temp* ?

---

### Post by jamesford on 2006-09-28
works for me, by following the usual guides, so its not a 64 bit thing

---

### Post by sonni_kuba on 2006-09-28
-> Tried sudo modprobe k8temp ?

$ sudo modprobe k8temp
FATAL: Module k8temp not found.

---

### Post by sonni_kuba on 2006-09-29
> works for me, by following the usual guides, so its not a 64 bit thing

jamesford, can you please tell me which guide you followed, perhaps I did not follow the right one

thanks,
kuba

---

### Post by jamesford on 2006-09-29
this one i think [http://ubuntuguide.org/wiki/Dapper#How_to_detect_CPU_temperature.2C_fan_speeds_and_voltages_.28lm-sensors.29]("http://ubuntuguide.org/wiki/Dapper#How_to_detect_CPU_temperature.2C_fan_speeds_and_voltages_.28lm-sensors.29")

---

### Post by sonni_kuba on 2006-09-30
Finally, found the problem, FYI for others 
[http://www.lm-sensors.org/ticket/2092]("http://www.lm-sensors.org/ticket/2092")

> Tried sudo modprobe k8temp ?

Not supported by the kernel! ](*,) 

> works for me, by following the usual guides, so its not a 64 bit thing

You are right, it is an AM2 thing. :(

---

### Post by kuja on 2006-10-01
[http://www.ubuntuforums.org/showthread.php?t=2780&highlight=how-to+lm-sensors](http://www.ubuntuforums.org/showthread.php?t=2780&highlight=how-to+lm-sensors)

Here is a different guide that doesn't seem to have been mentioned... It's from the days of Ubuntu Warty, but it still works beautifully in my experience (though it does mix up my cpu and motherboard temperatures, of course, that's fixable later.)

Anyhow, this may be worth a try for you.

---

### Post by sonni_kuba on 2006-10-03
> 
Anyhow, this may be worth a try for you.

Thank you kuja for the suggestion... but the problem is not with lm_sensors, but with a lack of support for the temp-sensing module (k8temp) in tke current linux kernel

The good news is that it will be suported in kernels 2.6.19+ =D>

---

### Post by kuja on 2006-10-03
If I remember right edgy was using 2.6.17, unless they pushed in a newer one while I wasn't looking o_O

If this is the case it looks like you've got a long wait (6 months) Unless you feel like going through the  hassle of compiling your own kernel just to get lmsensors working.

---

