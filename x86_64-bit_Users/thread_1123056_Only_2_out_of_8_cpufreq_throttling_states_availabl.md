---
title: "Only 2 out of 8 cpufreq throttling states available"
date: 2009-04-11
forum: x86 64-bit Users
---

### Post by scolbeck on 2009-04-11
With cpufreq on 8.10, only 2 out of 8 CPU frequencies are available.  Other than that, cpufreq seems to be working.  I have an Intel Core 2 Duo 3Ghz (E8400).  Any idea what may be wrong here?

```
# cat /sys/devices/system/cpu/cpu1/cpufreq/scaling_available_frequencies
3000000 2000000
```

```
# dmesg | grep throttling
[    1.230546] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.230843] ACPI: Processor [CPU1] (supports 8 throttling states)

```

---

### Post by stmiller on 2009-04-12
Could be a bug. Can you submit a bug report? 

[https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/)

---

### Post by scolbeck on 2009-04-13
> **stmiller said:**
> Could be a bug. Can you submit a bug report? 

[https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/)

Thanks.  I opened bug [#360336]("https://bugs.launchpad.net/ubuntu/+source/cpufreqd/+bug/360336")

---

### Post by _khAttAm_ on 2009-04-13
edit

---

### Post by _khAttAm_ on 2009-04-13
```
# cat /sys/devices/system/cpu/cpu1/cpufreq/scaling_available_frequencies
2333000 2000000
# dmesg | grep throttling
[    1.588508] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.628551] ACPI: Processor [CPU1] (supports 8 throttling states)

```

same here... I don't think its a bug.. the bios provides only two..

---

### Post by Yellow Pasque on 2009-04-15
As I wrote on your Launchpad..
> This is not a bug. Basically, you're confusing throttling states ("t-states") with performance states ("p-states"). Don't feel bad; the names are a little confusing (because changing t-states doesn't change the clock speed).
See this for more detail: [http://acpi.sourceforge.net/documentation/processor.html](http://acpi.sourceforge.net/documentation/processor.html)

---

