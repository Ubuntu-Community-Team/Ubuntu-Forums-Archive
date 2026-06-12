---
title: "Memory problems in Feisty Fawn"
date: 2008-03-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by bhagdave on 2008-03-12
HI,

I have been running Feisty for a while and it has correctly identified my 4GB of memory.  Did an upgrade of some software and the Kernel and now Feisty only recognises 512mb....  I thought perhaps my memory modules were playing up but a memtest identifies 4GB and and reports no errors.

Anyone any idea what is going on? And possibly point me in the right direction for a fix.

Thanks

---

### Post by Twitch6000 on 2008-03-12
Well yeah are you still using feisty when you can upgrade to gusty?Gusty does have some fixes as far as I know relating to memory,internet,and a few other things.

---

### Post by bhagdave on 2008-03-12
Good point but this is a production box running a webserver.  It was working fine and now just does not... And I would like to understand why it does not work rather than go through an upgrade.

Dave

---

### Post by Twitch6000 on 2008-03-12
Well I have not used feisty as I am a semi new user so my only guess would be.The ram not all the way in?

---

### Post by dcstar on 2008-03-13
> **bhagdave said:**
> HI,

I have been running Feisty for a while and it has correctly identified my 4GB of memory.  Did an upgrade of some software and the Kernel and now Feisty only recognises 512mb....  I thought perhaps my memory modules were playing up but a memtest identifies 4GB and and reports no errors.

Anyone any idea what is going on? And possibly point me in the right direction for a fix.

Thanks

Install a previous kernel version and see what happens when you boot off that - and check you Grub boot string for any "mem=" string.

---

### Post by bhagdave on 2008-03-18
Sorry for the delay in replying but thank you...

It was the mem= in the grub config that caused the problem.  Have used linux for years and just did not think to look there...

Thanks

Dave

---

