---
title: "AMD 64 Ubuntu8.10 IOMMU error"
date: 2008-11-07
forum: x86 64-bit Users
---

### Post by Mark69 on 2008-11-07
Hi all....I keep trying to install 8.10 but still keep getting the same error message everytime i try to install it....

  [0.004000]Aperture beyond 4GB. Ignoring
  [0.004000]Your BIOS doesn't leave a aperture memory hole.
  [0.004000]Please enable the IOMMU option in the BIOS setup.
  [0.004000]This costs you 64MB of RAM

Does anyone have an incline to if its a bios enable problem or is it that its the periphals on the system?
I have downloaded different iso files and yet it will not install on my main systen but will on my laptop intel based processor but the main system is a AMD64 with 4gb ram & pci express Nvidia graphics card..
My main system has been installed with 8.04 64 bit and runs well but wont install 8.10..

Any ideas ?

---

### Post by Yashiro on 2008-11-07
I saw this last week in the official bug database.
Look in your bios but there may not be a fix.

Anyway try removing some ram. It should install OK.
Then get all updates. Shutdown, and plug your ram back in.
Pray its been fixed.

---

### Post by Yellow Pasque on 2008-11-07
I got that error message every time I booted before I updated my BIOS. It's not a "show-stopping" error, just a minor annoyance.
I'm guessing that it won't install on your AMD machine because of the Nvidia card. Maybe try the alternate install CD or search for other workarounds.

---

### Post by Mark69 on 2008-11-07
ok thank you for looking.....I have updated my Gigabyte bios to the latest one before
Ive also had another go and removed 2gb ram to leave me with only 2gb...and got this error message: 

[0.004000]Aperture beyond 4GB. Ignoring

The only other thing i can try is to enable the onboard ATI graphics and retry that but its a funny one :lolflag:

---

### Post by Yashiro on 2008-11-07
[http://www.google.co.uk/search?q=Aperture+beyond+4GB.+Ignoring&ie=utf-8](http://www.google.co.uk/search?q=Aperture+beyond+4GB.+Ignoring&ie=utf-8)
Hehe :s

---

### Post by Yashiro on 2008-11-07
double post

---

### Post by arilds on 2008-11-07
> **Temüjin said:**
> I got that error message every time I booted before I updated my BIOS. It's not a "show-stopping" error, just a minor annoyance.
I'm guessing that it won't install on your AMD machine because of the Nvidia card. Maybe try the alternate install CD or search for other workarounds.
I got the exact same issue after upgrading, but I have not found any fix to the error message either.

It's annoying, but it does not stop me from using my computer.

---

### Post by Mark69 on 2008-11-08
Well good news is ive got Ubuntu 8.10 64 bit installed and it running so all's good so far but still have the same errors listed on bootup...but can live with it till an update comes through :D


:popcorn:-all round


Thanks for looking

---

### Post by Artemis3 on 2008-11-08
I think i'm also getting that error at boot but i simply ignore it. 64m from 4g? Not the end of the world :)

---

### Post by Mark69 on 2008-11-09
ok with an bit of experimenting ive found a reason my system was locking up on install.
I disabled "HPET Support" withing the power options in the bios...
Dont know if this means anything maybe someone might put a some light on the subject
Many thanks

---

### Post by Yashiro on 2008-11-09
> The HPET, short for High Precision Event Timer, is a new system timer developed by Intel and Microsoft to replace the four system timers currently in use.

Because of its higher precision and performance, it is naturally desirable to use the HPET instead of the older system timers. However, older operating systems do not support HPET. This is where the HPET Support BIOS option comes in.

    Setting it to Enabled allows the operating system and applications to use the High Precision Event Timer (HPET) for higher precision and better performance.

    Setting it to Disabled disables the High Precision Event Timer (HPET). The operating system and applications will use the older system timers instead.

If you are using a newer operating system like Windows Vista or Windows 2008, you should enable this BIOS option. Other operating systems that support HPET include Linux 2.6, FreeBSD and x86 versions of Mac OS X.

If you are using an older operating system like Windows XP or Windows Server 2003, you should disable this BIOS option.

Some chipsets, Nvidia, and older setups bug out with HPET set, apparently.

---

### Post by hvralpha on 2008-11-09
With the 8.10 64 bit installations add the following statement to your boot line and you can install:

pci=nomsi

Press F6 during options before boot. and add at end of boot line.

---

