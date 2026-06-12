---
title: "CPU fan is always on"
date: 2005-12-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by todorov on 2005-12-02
Hi all,

I would be very grateful, if someone can point me to a solution to the following problem:I have a Fujitsu-Siemens Notebook (1665G), Turion MT-32 ; ACPI works, powernowd works; but my CPU fan is always turned on (even if there are no CPU intensive activities at all !). I have tried switching off ACPI , but this still didn't work. Thank you very much in advance. 

Regards,
Angel

---

### Post by tomski on 2005-12-02
there is only one reason for and that is the cpu is as it say's it is ie:
Central Processing Unit
and even if your cpu monitor is reporting 0-1% use believe me it's still doing a hell of a lot, like making sure the millions of transistors and switches inside the cpu are working & the trillions of other small components located on each seperate bit of hardware are working, thats why if there is a problem you get the beep code when you power up.
when you move the mouse the cpu is working, when you hit a key the cpu is working, all traffic in your pc goes through the cpu, it is the brain of the box.

Even when you press the eject button on your cd drive the cpu is aware of that and try's to pre empt what you might do and get ready.
most modern hardware has a small onboard mini-cpu to take some of the work off the main cpu (hence gpu for graphics cards) but even so it will allways be doing something and if you had the right access you could probably fry an egg on a idle cpu so the fan is your friend if that stops i would panic

---

### Post by todorov on 2005-12-02
you seem to be joking, dont you ? Why doesn't the FAN go on for most of the time,  under Windows XP then ?:) It's just a problem of setting the temperature boundaries, but i hoped someone could have had an idea where and how to. Thanks.

P.S: As i said, the fan is ON even when the laptop is completely idle, I mean, come on, you can easily see that using "top". On the other hand, i don't think that 1% cpu usage would raise the remperature sooo much , that it would have to switch on the fan. Think about it.

---

### Post by AndersAA on 2005-12-02
powernowd (powernow daemon) should be able to scale down your cpu.

Be 100% idle and try cat /proc/cpuinfo, see if the cpu's speed has been scaled down or not.

---

