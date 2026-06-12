---
title: "lm-senors"
date: 2009-04-16
forum: x86 64-bit Users
---

### Post by wfp on 2009-04-16
Installed lm-sensors this is the out put does not look right to me any suggestions>  acpitz-virtual-0
Adapter: Virtual device
temp1:       +14.0°C  (crit = +75.0°C)                  

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +11.0°C                                    
Core0 Temp:   +9.0°C                                    
Core1 Temp:  +11.0°C                                    
Core1 Temp:   +7.0°C

Seems a bit cool to me.

---

### Post by mister_p_1998 on 2009-04-16
Sometimes it reads the sensors a bit off, boot into your bios & check the temps, write them down, then boot Ubuntu, go into sensor preferences, click on Properties, Sensor Value Offset, and increase/decrease the offsets to match your BIOS temps. Have to be quick though, cos they'll get hotter while you wait!

Steve

---

### Post by wfp on 2009-04-16
Thanks

---

### Post by WatchingThePain on 2009-04-16
What's the problem?. Do you want it hotter.

---

### Post by cariboo on 2009-04-16
Try:

```
sensors -u
```

for the raw output, to see if that looks more normal.

I would also suggest trying:

```
sudo sensors -s
```

then run sensors again. for more info have a look at man sensors.

Jim

---

### Post by djtnz on 2009-04-16
I had the same issues, this is apparently a known bug in the K8 architecture, and can't be fixed.

[http://www.lm-sensors.org/ticket/2152]("http://www.lm-sensors.org/ticket/2152")

---

