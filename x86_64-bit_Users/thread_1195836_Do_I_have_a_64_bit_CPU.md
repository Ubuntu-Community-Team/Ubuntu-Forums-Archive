---
title: "Do I have a 64 bit CPU?"
date: 2009-06-24
forum: x86 64-bit Users
---

### Post by calcio1 on 2009-06-24
I'm embarrassed to ask this question.

Was just looking in my system settings and it says the processor is

AMD Athlon(tm) 64 Processor 3500+

I got my computer a few years ago so didn't think it was 64 bit but should I have the 64 bit version of ubuntu installed and not 32?

thank you

---

### Post by regala on 2009-06-24
> **calcio1 said:**
> I'm embarrassed to ask this question.

Was just looking in my system settings and it says the processor is

AMD Athlon(tm) 64 Processor 3500+

I got my computer a few years ago so didn't think it was 64 bit but should I have the 64 bit version of ubuntu installed and not 32?

thank you

you **can** but you don't have to. Performance would be higher and, if you intend to host at least 3 or 4 Gb ram, you should use a 64 bit kernel and userland, support would be definitly better.
There may be some drawbacks, though, flash some would say, or other proprietary plugins for firefox, but that would have been right a quite substantially long time ago. So go for it. Be sure to have backups of your data and important setups, or be careful not to squash your home partition (if separated from /)

---

### Post by Kikoolol on 2009-06-24
> **calcio1 said:**
> I'm embarrassed to ask this question.

Was just looking in my system settings and it says the processor is

AMD Athlon(tm) 64 Processor 3500+

I got my computer a few years ago so didn't think it was 64 bit but should I have the 64 bit version of ubuntu installed and not 32?

thank you

I've a been a long running Kubuntu 64 bits user (started with Hoary 5.04), and as Regala said, it has been a real pain in the *** at the beginning, but I can tell that everything's just fine now (since Hardy I would say).

So rock on (K)Ubuntu amd64 ! :D

And by the way, don't feel embarrassed ... you are on ubuntu forums ...  some never do I can assure you ! :P

Kkl

---

### Post by Yellow Pasque on 2009-06-24
If you already have Ubuntu installed and configured to your liking, reinstalling is probably not worth the hassle unless you're doing something that gets a significant performance boost for 64-bit (virtualization, video encoding, editing large images in GIMP, etc.)

---

### Post by regala on 2009-06-25
> **Temüjin said:**
> If you already have Ubuntu installed and configured to your liking, reinstalling is probably not worth the hassle unless you're doing something that gets a significant performance boost for 64-bit (virtualization, video encoding, editing large images in GIMP, etc.)

it is worth it. keeping one's configuration is one thing one should learn or at least try and learn to do. You're telling the OP, it would be hard to reconfigure, to back up or whatever one system should be able to ease for the user: configuration backup. He's got a good processor he uses in a poor man's way of running, a compatibility mode the processor was not meant for, with a loss of 30% performance; if Ubuntu was that bad as not easing backing up or configuring to your liking, that he should not try and run his real architecture, like in the good ol'days of Windows XP 32 bits on every 64 bits processors that AMD shipped, then Ubuntu would be crap.
It isn't. So he should run 64 bits at the full extense of power of his processor.

---

### Post by sabre2th on 2009-06-25
If a system is already configured and doesn't do a lot of operations that would benefit from 64 bit Ubuntu, then I'd say it's not worth the effort.

For any reconfiguration or new install, 64 is definitely the way to go.  It hasn't been significantly different from 32 bit in operation for quite some time, and it does have a number of advantages.

I actually have the same processor in a 64 bit Mythbuntu box and it runs quite nicely.  Completely subjectively, I'd say it runs smoother than when I used to run 32 bit on it.

---

### Post by calcio1 on 2009-06-26
Thanks for all the replies.

Do I have to do a fresh install to go 64-bit?

cheers

---

### Post by Elfy on 2009-06-26
Yes you do. 

When you install use the manual option and you can install over the top of the existing install.

If you have a seperate /home then you can keep that - give it a mountpoint of /home but don't format it.

---

