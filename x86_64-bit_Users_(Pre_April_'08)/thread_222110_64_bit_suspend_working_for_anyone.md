---
title: "64 bit suspend working for anyone?"
date: 2006-07-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by hizaguchi on 2006-07-24
I read a while back that the 64 bit kernel doesn't support suspend to ram.  Is there any truth to that?  I've been surfing around the forum a little and I can't find any success stories.  Certainly doesn't work with my laptop, and I don't know if I should spend a while tinkering or just wait till the support is implemented.

---

### Post by sproket81 on 2006-07-27
Works pretty well for me. I have an Acer Aspire 5000, with 1GB Ram and an up-to-date 2.6.15-26 amd64 Dapper kernel. 

I've had one hiccup coming back from suspend to a message telling me it had failed to go into suspend (which wasn't true), that's as bad as it's failed so far.

---

### Post by hizaguchi on 2006-07-28
Which suspend mode are you using?  Standby or mem?  Because I get that message with standby, but I can't wake up from mem at all.  And neither works with the k8 smp kernel, just the generic one.

---

### Post by dasyar613 on 2006-07-28
I also have an Acer 5002 64 bit, I use hibernate, and that also comes up with an error message that it did not go into hibernate, which it did, because the message only displays after I come out of hibernate.

I am curious about the selection of suspend, on my system I do not get a choice between standby and mem. Maybe that is available on the desktops and not the laptops.

---

### Post by MS7 on 2006-07-29
I've just tried mine, it appears to hibernate but won't come out of hibernation.

---

### Post by dasyar613 on 2006-07-29
That is interesting, can you supply some detail. When you press the power button, nothing happens? It takes about a minute, my guess, for it to come out of hibernation, remember this is not suspend.

---

### Post by MS7 on 2006-07-30
I've just tried it a couple more times and it worked fine. I had to hold the power button in for 4 seconds and press it again the first time I tried it but it started straight up today with all the apps running as it should.

Asus AN8 / 4400+ / 1Gb RAM

---

### Post by hizaguchi on 2006-08-01
It turns out my problem has more to do with SMP than 64-bit.  The SMP i686 and k7 kernels can't suspend either, but the stock kernel works perfectly.  Hmmm.

---

### Post by komputes on 2006-09-18
@sproket81: What installer did you use for the Aspire 5002. I've tried the desktop-amd64 version of Ubuntu 6.06.1 and it froze every time I got to the partition manager.

](*,) Komputes

---

### Post by Didjit on 2006-10-03
> **hizaguchi said:**
> It turns out my problem has more to do with SMP than 64-bit.  The SMP i686 and k7 kernels can't suspend either, but the stock kernel works perfectly.  Hmmm.

Sorry for the late response. What kernel are you using that suppends properly? I would love to get this working.

Didjit

---

