---
title: "powernowd not stepping up"
date: 2006-04-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by TimP on 2006-04-29
I installed powernowd today to use with my Athlon 64 3000+ Venice. When I run it, it will scale the processor from 1.8 GHz to 1.0 GHz, but when I run a process that maxes the CPU load it will not scale back up to 1.8 GHz. I left the process running for 20 minutes and it never scaled back up. I ran with -u 100, but it didn't seem to make a difference. Anyone know what could be causing this?

Thanks,
Tim

---

### Post by moephan on 2006-04-29
Could your frequency scaling be set to "powersave"? If so, the cpu will stay at the lower setting no matter what. If this is the problem, the setting you want is "userspace" which will set the CPU cycles based on demand.

Perhaps this thread is related:
[http://ubuntuforums.org/showthread.php?t=125830&highlight=powersave+userspace](http://ubuntuforums.org/showthread.php?t=125830&highlight=powersave+userspace)

Cheers, Rick

---

### Post by TimP on 2006-04-29
The scaling_governor is userspace.

---

### Post by TimP on 2006-04-30
I figured out what the issue was. Despite seeing 99.9% processor usage in top, powernowd's verbose mode said it was using next to no processor. I don't know which is more accurate, but it was never getting anywhere near to the -u percentage. I wrote a tight addition loop in C and ran that and powernowd said it was using 100% of the processor and I saw it step up to the full speed. Since powernowd's indications seem to be low, I just set -u to 10 and -l to 3 and everything is great now.

---

