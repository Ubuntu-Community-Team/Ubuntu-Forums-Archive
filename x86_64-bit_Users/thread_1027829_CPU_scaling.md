---
title: "CPU scaling"
date: 2009-01-01
forum: x86 64-bit Users
---

### Post by HVJoel on 2009-01-01
Hi all,

I have a problem with scaling my CPU via cpufreq-utils.

```

$ sudo cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies 
2501000 2500000 2000000 1600000 1200000 800000 

$ sudo cpufreq-selector -f 800000

$ sudo cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_cur_freq 
1200000

```

For some reason it doesn't want to go below 1.2GHz, which is a waste of battery. Anyone knows how to fix this problem?

Second question: Is it possible to turn off the second core? 

Thanks.

---

### Post by sonofusion82 on 2009-01-01
what governor are you current using?
I believe you have to set it to manual or user to enable manual frequency selection, else set it to ondemand and set the scaling_min_freq to 800000?

---

### Post by MighMoS on 2009-01-03
> **HVJoel said:**
> Hi all,
Second question: Is it possible to turn off the second core? 


I hate to be the bearer of bad news, but as far as I know there is no way to dynamicaly disable cores.

---

