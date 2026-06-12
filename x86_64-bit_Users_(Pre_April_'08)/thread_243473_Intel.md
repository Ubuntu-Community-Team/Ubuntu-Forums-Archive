---
title: "Intel"
date: 2006-08-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by morequarky on 2006-08-25
Intel processor 64bit.

I have a small xp 64bit professional partition.

the rest is used by linux

what version of the linux kernal should i use?  I have only heard of 385, 686 and the amd 64bit.

what is the difference between 386 and 686?

thanks.

---

### Post by quad3d@work on 2006-08-25
I used AMD64 kernel for a few days on my Pentium D 930 and works great. I stepped back down to 32-bit Ubuntu running 686-smp kernel due to software compatibility issues. Linux 64-bit just.... 'isn't there yet'. Not even WinXP is. But both hardware and software vendors are getting better at supporting it. If you want to be hardcore, go for 64-bit. My recommendation is staying with 32-bit. At least till Vista comes out... once Vista comes out it should help move Linux 64-bit greatly.

I don't feel like spending that extra time getting stuff to work in 64-bit environment. I would end up spending more time fixing stuff than getting any work done. 8)

Using 686 kernel allows more advanced features on your CPU (such as SSE?) to get used, instead of using 386 kernel.

[There is already a similar thread started on this]("http://ubuntuforums.org/showthread.php?t=243303")...

---

### Post by morequarky on 2006-08-25
Can some one tell me more about this 686 kernel?

What is SSE?

---

### Post by Kilz on 2006-08-25
> **quad3d@work said:**
> I used AMD64 kernel for a few days on my Pentium D 930 and works great. I stepped back down to 32-bit Ubuntu running 686-smp kernel due to software compatibility issues. Linux 64-bit just.... 'isn't there yet'. Not even WinXP is. But both hardware and software vendors are getting better at supporting it. If you want to be hardcore, go for 64-bit. My recommendation is staying with 32-bit. At least till Vista comes out... once Vista comes out it should help move Linux 64-bit greatly.

I don't feel like spending that extra time getting stuff to work in 64-bit environment. I would end up spending more time fixing stuff than getting any work done. 8)

Using 686 kernel allows more advanced features on your CPU (such as SSE?) to get used, instead of using 386 kernel.

[There is already a similar thread started on this]("http://ubuntuforums.org/showthread.php?t=243303")...

The software issue depends on what you are doing. Are you programing and need a lot of 32bit development tools? If so the setup could be a lot. Are you surfing, writing email, playing games, and burning/listening CD's? If so the extra setup is probably under a half hour to an hour.
Every user has diffrent needs. Advising someone to to go to 32bit on a 64bit system without knowing what the person is going to use the computer for is not a good idea.

---

### Post by Kilz on 2006-08-25
> **morequarky said:**
> Intel processor 64bit.

I have a small xp 64bit professional partition.

the rest is used by linux

what version of the linux kernal should i use?  I have only heard of 385, 686 and the amd 64bit.

what is the difference between 386 and 686?

thanks.

i386 = 386 processor up to a pentium
686 = Pentium pro or pentium2 up
Both are for 32bit processors. If you have a 64bit system you will only be using half of the processors ability to move data around. If you have the 64bit version installed you cant use these kernels.

---

