---
title: "Problem with mono (f-spot)..."
date: 2006-03-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by Lucas[PL] on 2006-03-20
Hello

First, Sorry for my English.

OS: Ubuntu Breezy AMD64

I have problem with aplications witch use mono.
When i started f-spot, cdcollect "nothing happened", I see in `top` that mono working and use 100% my cpu, but nothing started.

top
PID USER PR NI VIRT RES SHR S %CPU %MEM TIME+ COMMAND
14287 smok 25 0 21736 2060 1604 R 92.2 0.2 0:21.25 mono

ps ax | grep f-spot
14286 pts/1 S 0:00 /bin/sh /usr/bin/f-spot
14287 pts/1 R 2:14 mono /usr/lib/f-spot/f-spot.exe
14324 pts/1 S+ 0:00 grep f-spot


Maybe sombody met this problem, maybe some tips, sugestions...

Thanks for help
Lucas

---

### Post by Lucas[PL] on 2006-03-20
I solved! Problem was in one old config file...

---

