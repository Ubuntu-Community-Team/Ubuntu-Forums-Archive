---
title: "system shutdown fail"
date: 2008-11-03
forum: x86 64-bit Users
---

### Post by litnsio2 on 2008-11-03
Hello, I just installed amd64 version of Intrepid.
Everything looks fine, but when I shutdown my laptop, system hangs. (See the attachment : text on the screen in the attachment is 'acpid: exiting' )

I used beta, rc, the release version of Intrepid but, I'm going through same things.

How can I fix this?

Thanks in adv.


Intaek.

---

### Post by C. Wizard on 2008-11-03
I have the same problem using Kubuntu 8.10 amd_64.
Shutdown or reboot, it doesn't matter, the screen goes black and that is it. Nothing more happens.  Finally, I either turn the unit off or hit the reset button.
BTW, Kubuntu 7.04, 7.10, 8.04, and Slackware 12
never did shutdown the system properly.  However, Slackware 11 did shut it down, as does XP.
I'm wondering if this has something to do with the 2.6xx kernel?

---

### Post by paolol61 on 2008-11-06
hi, i nstalle 8.1 from the cd and all was working ok, last night I uodate the kernel to the new one and bang I got the problem on shutdown :(

---

### Post by El Ploppo on 2008-11-08
Same problem here. On my laptop (Intel Core2 Duo) as well as on a desktop machine (AMD Athlon XP (32 bit)) it takes forever and a day to shutdown.
It DOES shutdown however, albeit that it looks like the system hangs. The hdd-activity led burns all the time during shutdown, then, after (never timed it but I think) about two minutes shutdown finally happens.
I never had this problem with any previous version of Ubuntu, now I have it on two totally different systems.
It would be nice if this would be fixed.

---

### Post by slowhand73 on 2008-11-09
I have the same issue with my AMD64 desktop pc.
Shutdown fails with linux-image-2.6.27-3-rt kernel but it works with the previous kernel for Hardy (8.04) : linux-image-2.6.24-21-rt

My 2 cents,
Eric

---

### Post by CX15 on 2008-11-16
Same problem here...

Fresh install on Core2Duo 8500 & Intrepid.

Restart or Shutdown goes to black screen with flashing pointer and then freeze.

Anyone with a solution yet?:confused:

---

### Post by El Ploppo on 2008-11-16
What seems to help (partly) here is to add

*apm power_off=1*

to /etc/modules.

I found this a few days ago on some other forum, don't remember where.

Now my system often shuts down normally, but sometimes it still takes 2,5 minutes (yes, I timed it), to power-off.

To be honest, I have no idea what the line is supposed to do, so if anyone could shine some light there it would be welcomed.

---

