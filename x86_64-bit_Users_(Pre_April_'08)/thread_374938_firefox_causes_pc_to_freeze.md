---
title: "firefox causes pc to freeze"
date: 2007-03-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by oboontoo on 2007-03-03
Can someone tell me how to fix this or if it's some sort of kernel bug that I'm stuck with.

Using a fresh install of Ubuntu Edgy with only the nvidia drivers added, firefox will cause the pc to freeze up when browsing certain pages (opening an email in web outlook always causes the freeze). I can still move the mouse, but the computer is not responding to any input and I have to turn off the box from the off button.

I could see the following message in an open console window.
```
Message from syslog@ubuntu
ubuntu kernel: [1309.795074] Disabling IRQ #169.
```

Also I see this in the /var/log/syslog```

Mar  3 17:42:29 ubuntu kernel: [ 5081.248995] APIC error on CPU0: 40(40)
Mar  3 17:42:30 ubuntu kernel: [ 5082.146909] irq 169: nobody cared (try booting with the "irqpoll" option)
Mar  3 17:42:30 ubuntu kernel: [ 5082.146915] 
Mar  3 17:42:30 ubuntu kernel: [ 5082.146916] Call Trace: <IRQ> <ffffffff802b6875>{__report_bad_irq+53}
Mar  3 17:42:30 ubuntu kernel: [ 5082.146942]        <ffffffff802b6af0>{note_interrupt+544} <ffffffff802b6160>{__do_IRQ+224}
Mar  3 17:42:30 ubuntu kernel: [ 5082.146959]        <ffffffff802737a2>{do_IRQ+66} <ffffffff80265cd0>{ret_from_intr+0} <EOI>
Mar  3 17:42:30 ubuntu kernel: [ 5082.146972]        <ffffffff802657d6>{system_call+126}
Mar  3 17:42:30 ubuntu kernel: [ 5082.146985] handlers:
Mar  3 17:42:30 ubuntu kernel: [ 5082.146988] [_end+133660703/213045
```

There's a suggestion to boot with irqpoll option, but I don't know if that will help me. I'm over the trial and error method by now. Booting with ```
acpi=off
``` fixes the freezeups, but now I have a speedy clock.

So it seems to be one or the other, too fast a'clock or no browsing.

Help!

---

### Post by John Jason Jordan on 2007-03-03
> **oboontoo said:**
> 
So it seems to be one or the other, too fast a'clock or no browsing.
I know little of these things -- been using Linux for only a year. But I have read that pci=assign-busses helps sometimes with IRQ problems. Note that there are two esses.

---

### Post by hoyaabc on 2007-03-03
I gave up using fire-fox.
freeze king. throw away.

---

### Post by oboontoo on 2007-03-03
> **hoyaabc said:**
> I gave up using fire-fox.
freeze king. throw away.

What are you using when browsing?

I've tried the irqpoll option and it looked okay for awhile, but then the whole pc frooze up. Couldn't even move the mouse this time. Clock was working okay though and I could open up emails in web-outlook.

---

### Post by oboontoo on 2007-03-03
It seems to be the nvidia driver that's causing problems.

If I'm using the "nv" driver I can't get the freeze to happen.

---

### Post by geakMonkey on 2007-03-04
I'm a n00bie to Ubuntu (been using mandrake since last century) and I have had more than a dozen crashes since the first install in the last 2-3 weeks on a brand new build AMD64 on ECS  Mobo with built-in ATI X200 core graphics (am using this as a server only and it will not need graphics often). 

The crash occurs when browsing the world wide web then wham! (sic) and the machine freezes and I have to hard boot. There is a blank screen or color patterns on screen. Either case, I have to reboot. Is this a 64 bit Firefox w/Flash issue too?

---

### Post by hoyaabc on 2007-03-05
epiphary I using now
I believe same mozila based on.
and no freeze to me after all.

---

### Post by geakMonkey on 2007-03-06
I have not had another firefox freeze since I installed the Radeon X200 ATI Driver. We will see how long this lasts.

---

### Post by geakMonkey on 2007-03-07
Ok, my server crashed yesterday. The only thing I can think of was that I left firefox on a flash website. Does anyone know what flash behaviors trigger firefox?

---

### Post by chrism66 on 2007-03-08
I am having the same symptoms. Firefox lock ups or multi color screen. Mainly happens when i am listening to my radio station in the morning which require Firefox to use flash.

---

### Post by oboontoo on 2007-03-11
I'm not sure what to think now. I upgraded my bios and I don't get any freeezes with firefox where everything locks up except the mouse. Now I get hard lock ups, which I believe is related to an nvidia driver bug. This bug was identified as an incompatability between ATI RS480/482 chipset and an nvidia card. It took nvidia 7 months to fix the bug and they only did it for the 6 series, cause the guy who raised the problem had a 6200 card. Since I have a 7300 card I'm out of luck. Hopefully I don't have to wait until october before it's fixed.

It never rains, but it pours.:confused:

---

