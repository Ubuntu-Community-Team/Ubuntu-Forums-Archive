---
title: "Boot trouble on HP laptop || Freeze during install!"
date: 2007-08-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by shermynator on 2007-08-26
Hey!

I've downloaded Ubuntu 7.04 and burned the image file with InfraRecorder to a DVD. When i boot the dvd, i choose the "start/install ubuntu" option. Then, lots of text are written on the screen and it says "ok" to the right at every line. When this is finished, the system hangs up/freezes with a blank screen. _Nothing_ will work from here... I've tried a lot, and i'm starting to get fed up. 

Will someone please help me with this!?

My computer is a 6 months old HP with amd 64 x2, 2gb ram, and geforce 7400

---

### Post by John.Michael.Kane on 2007-08-26
> **shermynator said:**
> Hey!

I've downloaded Ubuntu 7.04 and burned the image file with InfraRecorder to a DVD. When i boot the dvd, i choose the "start/install ubuntu" option. Then, lots of text are written on the screen and it says "ok" to the right at every line. When this is finished, the system hangs up/freezes with a blank screen. _Nothing_ will work from here... I've tried a lot, and i'm starting to get fed up. 

Will someone please help me with this!?

My computer is a 6 months old HP with amd 64 x2, 2gb ram, and geforce 7400

Try rebooting the machine with the ubuntu cd/dvd in the drive. At the boot/install prompt (make sure to hit F6 first), and add the command below to the boot parameter.
```
nosplash noapic nolapic
```  
note: do not remove any of the commands already shown in the boot line. just add the above commands to it.

---

