---
title: "[SOLVED] Question for 64-bit machine/32-bit ubuntu user"
date: 2008-07-18
forum: x86 64-bit Users
---

### Post by drs305 on 2008-07-18
SOLVED: Answered by 3rdalbum on original thread:
There is no output when you are running a 32-bit Ubuntu on a 64-bit machine.

Over on the Beginner's Thread we were [discussing]("http://ubuntuforums.org/showthread.php?t=862691") how to tell which software version was in use. Several of us offered the "uname -m" command but Sef pointed out that command returns the type of *machine* in use.

ilrudie came up with the answer, which I refined a bit to:
```
cat /boot/config-`uname -r` | grep CONFIG_X86_64=
```

So far, we've established:
32-bit machine, 32-bit system: 
```
CONFIG_X86_64 is not set
```

64-bit machine with 64-bit ubuntu:
```
CONFIG_X86_64=y
```

Could someone who is running 32-bit ubuntu on a 64-bit machine post their results? We believe it will result in the "not set" output but would like confirmation.

Thanks.

Link to original thread: [http://ubuntuforums.org/showthread.php?t=862691]("http://ubuntuforums.org/showthread.php?t=862691")

---

