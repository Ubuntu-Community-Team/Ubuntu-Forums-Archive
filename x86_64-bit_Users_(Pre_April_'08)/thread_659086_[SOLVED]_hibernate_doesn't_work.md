---
title: "[SOLVED] hibernate doesn't work"
date: 2008-01-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by ghettosamson on 2008-01-05
Good Day.
I recently dual booted xp and ubuntu gutsy gibbons on my dell inspiron 1501 laptop. I had xp 1st and then installed ubuntu. Both of them are working fine, except for some features/functions. I would really like to be able to Hibernate my machine. So what happens is I click the Hibernate button and it goes to a black screen with a blinking cursor and there is nothing I can do to get it back up. I try the power button, the space bar, etc.. nothing seems to work. This also happens with my sleep button. What can I do to fix this? If some one could please shed some light on this matter.

---

### Post by pointyblue on 2008-01-06
I have the exact same problem - it worked fine in Ubuntu 7.04 but in 7.10 it doesn't.

---

### Post by nmehta6 on 2008-01-06
I have Inspiron 1501 with same problem. When I do standby/hibernate screen goes blank and i have to hold power button to force shut down and reboot. Please let me know if anybody has a fix for this.

---

### Post by fjgaude on 2008-01-06
It worked fine for 7.04 32-bit, but not for 7.10 64-bit on my Dell E1505n.

---

### Post by AdamTheNewbie on 2008-01-08
I upgraded from Feisty to Gutsy on my Dell 530 (Dell Feisty installed). Hibernate worked on Feisty and now doesn't work on Gutsy. Black screen, blinking cursor, power button is the only option.

Adam.

---

### Post by pointyblue on 2008-01-09
This is the weirdest thing ever! 

When I compare my Ubuntu 7.04 installation to my 7.10 installation the only thing I remember doing differently is using the restricted graphics driver for my ATI graphics card in Ubuntu 7.10 So I disabled the restricted driver in 7.10, rebooted the pc and hibernate works again!

Too bad to have to choose between using the (better) restricted graphics driver or the hibernate function, though.

Anyway, try it on your machine, it might work for you too...

(-And if anyone has an explanation for this strange behavior, please share.  ;) )

---

### Post by ghettosamson on 2008-01-09
@pointyblue

Dude, I don't know who you are or where you are, but that is freikin sweet. You just made my life a little sweeter. Screw the ATI graphics driver. Its for my laptop and I could really use it. So yes, that fixed my problem, and I will definetely relay that info. Awsome. You don't know how many times I have posted this issue. Whew! Thanks Buddy.

---

### Post by AdamTheNewbie on 2008-01-09
I just upgraded my Dell 530 (E2160 Dual Core) factory installed 1gb with more RAM and now hibernate is working for me.

Honestly, I think that is the only change I made. Strange.

Adam.

---

### Post by crjackson on 2008-01-09
> **ghettosamson said:**
> @pointyblue

Dude, I don't know who you are or where you are, but that is freikin sweet. You just made my life a little sweeter. Screw the ATI graphics driver. Its for my laptop and I could really use it. So yes, that fixed my problem, and I will definetely relay that info. Awsome. You don't know how many times I have posted this issue. Whew! Thanks Buddy.

It's a known issue for a long time.  I can't understand why no one tipped you off before now.  Sorry about that.  This IS an ATI driver issued.  The newest drivers probably would fix the problem for you, but they're rough around the edges and may bring with them problems of their own.

Good news though...  ATI is working hard to solve all the linux related ATI Graphics issues, and you will be able to have it all very soon....

---

### Post by juaka on 2008-01-13
I have nvidia driver and hibernate and suspend resumes on a blakc screen.

This issue is not only for ati.

---

