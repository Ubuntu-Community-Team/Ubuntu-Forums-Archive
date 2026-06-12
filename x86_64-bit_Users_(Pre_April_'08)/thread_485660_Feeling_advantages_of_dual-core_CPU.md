---
title: "Feeling advantages of dual-core CPU"
date: 2007-06-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by Ubivetz on 2007-06-27
Hi All!

I'm using Ubuntu (KDE Desktop) 7.04 AMD64 on iMac Intel (Core 2 Duo T7200, 1Gb RAM).
When I open large PDF document with KPdf, system works veeeery slow. But when I do the same task  on Windows XP on Athlon64 X2 4200+, only one core is busy, the system remains responsible for user input.

```

$ uname -a
Linux slavik 2.6.20-16-generic #2 SMP Thu Jun 7 19:00:28 UTC 2007 x86_64 GNU/Linux

```

How to make my computer works faster?

---

### Post by diesel1 on 2007-06-27
> **Ubivetz said:**
> Hi All!

I'm using Ubuntu (KDE Desktop) 7.04 AMD64 on iMac Intel (Core 2 Duo T7200, 1Gb RAM).
When I open large PDF document with KPdf, system works veeeery slow. But when I do the same task  on Windows XP on Athlon64 X2 4200+, only one core is busy, the system remains responsible for user input.

```

$ uname -a
Linux slavik 2.6.20-16-generic #2 SMP Thu Jun 7 19:00:28 UTC 2007 x86_64 GNU/Linux

```

How to make my computer works faster?


Try this in a console..

$ sudo su
$ echo performance > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
$ echo performance > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
$ watch -n 1 cat /sys/devices/system/cpu/*/cpufreq/scaling_cur_freq

Diesel1.

---

### Post by kansei on 2007-06-30
> **diesel1 said:**
> Try this in a console..

$ sudo su
$ echo performance > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
$ echo performance > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
$ watch -n 1 cat /sys/devices/system/cpu/*/cpufreq/scaling_cur_freq

Diesel1.

Even with sudo, I get permission denied when I try to echo performance (or ondemand for that matter) to those files.

---

### Post by Ubivetz on 2007-07-02
> **kansei said:**
> Even with sudo, I get permission denied when I try to echo performance (or ondemand for that matter) to those files.
He just joked ;)

---

### Post by CyberAngel on 2007-07-05
Also try:

```
sudo /etc/init.d/powernowd stop
```

This will stop the scaling of MHz in you CPU.
You can of course start it again using:

```
sudo /etc/init.d/powernowd start
```

---

### Post by incubus on 2007-07-05
I also use KDE and I absolutely see what you mean.  KPDF is partly guilty.  Here's what I do.  In KPDF Settings, go to Performance, and check "Aggressive".  That should give you some improvement.

But even with that, I still think KPDF could be improved.  If you open a big/complex PDF, the system starts to crawl.  Maybe I should consider other PDF readers.  Aren't they working on another one for KDE 4?

incubus

---

