---
title: "Fiesty does not hibernate on my AMD64"
date: 2007-05-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by cemptor on 2007-05-06
First off, I don't see the explicit "hibernate" option in power management, as I used to in Edgy or previous. It only has an option to "Sleep". Is that by design? If so, is it Suspend (to RAM) or Hibernate (to disk)?

Second after it goes to "Sleep", I have to start it up like a fresh boot, and my open application data is not recovered.

I have an AMD Opteron single core, ASUS A8R-MVP mobo with ATI crossfire, 1 GB RAM, 2 GB swap partition, Seagate SATA II drive, ATI Radeon Xpress graphics card.

Dual boot with XP and Fiesty. Hibernate works fine with Windows.

How do I get hibernate to work correctly in Fiesty?

Thanks

---

### Post by reuscel on 2007-05-07
I'm having the same issue with my Sony Vaio PCG-K25 laptop (with a Pentium 4 2.8gHz).  I could never get suspend to work correctly on edgy, but was able to use hibernate.  Now, hibernate won't work either.  When it goes to restore my session, I get a blank screen and then nothing and have to shut down the computer and restart.

---

### Post by rivera151 on 2007-05-08
> **reuscel said:**
> I'm having the same issue with my Sony Vaio PCG-K25 laptop (with a Pentium 4 2.8gHz).  I could never get suspend to work correctly on edgy, but was able to use hibernate.  Now, hibernate won't work either.  When it goes to restore my session, I get a blank screen and then nothing and have to shut down the computer and restart.

I know cemptor is using an ATI card, I bet you are too.  And I bet both of you have the proprietary drivers.  If this is the case, you can get your missing buttons back, but the ATI driver breaks the hibernate and suspend/sleep functions; they don't work (at least without a hack, which I haven't found).  You can get the functions back if you use the open source ati driver, but since you have an XPRESS card, that means saying goodbye to your HW acceleration.  Still, you prbably want your shutdown button back; I'll check out how I got those back and post here when I have more time...

---

### Post by cemptor on 2007-05-08
Thanks Rivera! You're right. I installed the proprietary drivers. I will remove them and go back to the open source ones and post back as to what happens by the weekend.

How much difference would h/w acceleration make in everyday, non-gaming use without the fancy graphics effects?

---

### Post by rivera151 on 2007-05-09
> **cemptor said:**
> Thanks Rivera! You're right. I installed the proprietary drivers. I will remove them and go back to the open source ones and post back as to what happens by the weekend.

How much difference would h/w acceleration make in everyday, non-gaming use without the fancy graphics effects?

The most likely drawback that you might suffer from is that you might not benefit from a hardware accelerated desktop (e.g. compiz, beryl), which is a pretty cool feature, but from a practical standpoint, useless.  If you were thinking about running 3d games then this might also be a drawback, but seriously, if you want to play games, get a console.  In the time you rig a game to be playable you could probably kill a lot of baddies :) .

---

