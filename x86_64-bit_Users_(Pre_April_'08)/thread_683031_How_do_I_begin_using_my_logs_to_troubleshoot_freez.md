---
title: "How do I begin using my logs to troubleshoot freezes?"
date: 2008-01-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by ewanchic on 2008-01-30
I'd like to start figuring out "what" exactly is causing this or that to freeze. I have my presumptions, but I need some suggestions on tools I could use to begin diagnosing.

For example, I think I might have issues with firefox. I think it might be overloading the RAM, maybe. Could be my RAM in general, I might have a bad RAM stick. But that's where I start?

So my system locks, I do a nice cold reset, but the then how can I back track? tail /var/log/syslog? Could I start diving up logs so that Firefox logs go somewhere else?

Open to suggestions. Thanks.

---

### Post by wjp.reg on 2008-01-30
Admin Menu | System Log serves up all the log files for you quite nicely.

You may need to add a kernel option like "noapic" to your startup grub command if you have BIOS issues.  Worked for me.

good luck

---

### Post by Yellow Pasque on 2008-01-30
If you suspect a bad RAM stick, boot into and run memtest (takes a length of time, so do it before going out or going to bed, etc.). You may have to hit 'Esc' to see the boot menu, but memtest86 should be on there.

---

### Post by Jouke74 on 2008-01-31
Exactly, the memtest.... freezes are most often caused by bad memory or bad memory settings. If you dual boot it will show up on grub as the third option. If you have only Ubuntu installed then hit Esc when 3 seconds are counting down. See post above ^

---

### Post by ewanchic on 2008-02-05
Thanks for the help. I think I need to try that memtest. I was executing some filters in Gimp on some large RAW images, and every so many pictures, I'd get a black line through it. Hmmm. I'd undo and redo the filter and the black line would be gone.

I'm going to do that memtest and see what comes back, and I'll report it here. Thanks for the help so far.

---

### Post by zubrug on 2008-02-05
I have been fighting grumlins here too, I have tried all the above with out much luck, I am currently using sidux 64bit (the least troublesome so far).

Yesterday I changed some settings in my bios that seems to have worked for me, no lock-ups so far after running all night through to 3:00pm so far, laugh if you want but I was having an issue every hour or two.
I did notice that my memory usage was gradually climbing through-out a session (sometimes fast = Ktorrent), this sent me to the bios after a mem check showed nothing. 

A-770M-A Mobo
AMD Phenom 9500 Quad
2 G 6400 ddr
Pata HD
Nvidia-8500 512mb

---

### Post by ewanchic on 2008-02-12
Thanks for the help. I ran a memtest and 18 passes all showed good. 

I haven't done anything with the acpi yet, but it hasn't been locking up either. However, I now have a new problem with nautlius.

[http://ubuntuforums.org/showthread.php?t=695287](http://ubuntuforums.org/showthread.php?t=695287)

---

