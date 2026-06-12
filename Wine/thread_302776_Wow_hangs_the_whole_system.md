---
title: "Wow hangs the whole system"
date: 2006-11-19
forum: Wine
---

### Post by klund on 2006-11-19
Ok i took a copy from a friend and start with "wine WoW.exe -opengl", the game loads fine and i can enter "the world" but about 10-20 secs into the game the whole system hangs and i have to push the power button to restart. Have tried i bit of googling but cant find any solution.

Have anyone else had the same issues?

I run ati(fglrx) and wine 0.9.24.

---

### Post by B0rsuk on 2006-11-19
Oh. Ati. What a suprise, hr hr hr.

---

### Post by klund on 2006-11-19
very useful reply thank you very much

---

### Post by unimatrix on 2007-12-12
This has nothing to do with ATI.
I have an nVidia 8600 with exactly the same problem.
Happens in the latest Cedega and Wine with the --opengl or without.
The funny thing is this used to work in wine, but now it suddenly stopped.

---

### Post by tripopOZ on 2007-12-12
WOW is a super fun game seriusly.  I got so addicted to it but now i have a little boy so he takes up a lot of my free time.

---

### Post by unimatrix on 2007-12-12
Great... but how does that help me solve the problem?

---

### Post by hikaricore on 2007-12-12
Have you checked the terminal output at the time of the crash for anything odd?

---

### Post by unimatrix on 2007-12-14
Nope, i've fixed the problem by editing WoW's config.wtf file
I changed the
SET hwDetect "0"
to
SET hwDetect "1"

Then it worked, I just had to change the resolution (same config file) next time.

---

