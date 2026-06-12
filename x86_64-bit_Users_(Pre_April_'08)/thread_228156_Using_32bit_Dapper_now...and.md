---
title: "Using 32bit Dapper now...and"
date: 2006-08-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by LinuxConvertJune2006 on 2006-08-02
I just bought a 64bit AMD Athlon 3500+ w new mobo, will be re-using memory, vid card, and SATA drive.

I and I searched the 64bit forums for this, not sure I used correct search pattern, but I couldn't find an answer:

Question:
Can I just plug my hard drive into this new mobo (along with everytihng else) then switch from linux-image-k7 (currently Athlon XP 2300) to linux-image (whatever was AMD 64 requires) then run apt-get upgrade distro to switch all apps I have over to 64bit versions? Meaning, is it that easy? Aside from the programs in the sticky at the top of the forums, for which it seems I'd force a 32bit 386 version down and follow work arounds, could it be done this way?

Or should I install cleanly the 64bit iso desktop cd ? And totally start from scratch (I really don't want to do that) ?

Or, how should I do it?

---

### Post by Kilz on 2006-08-02
> **LinuxConvertJune2006 said:**
> I just bought a 64bit AMD Athlon 3500+ w new mobo, will be re-using memory, vid card, and SATA drive.

I and I searched the 64bit forums for this, not sure I used correct search pattern, but I couldn't find an answer:

Question:
Can I just plug my hard drive into this new mobo (along with everytihng else) then switch from linux-image-k7 (currently Athlon XP 2300) to linux-image (whatever was AMD 64 requires) then run apt-get upgrade distro to switch all apps I have over to 64bit versions? Meaning, is it that easy? Aside from the programs in the sticky at the top of the forums, for which it seems I'd force a 32bit 386 version down and follow work arounds, could it be done this way?

Or should I install cleanly the 64bit iso desktop cd ? And totally start from scratch (I really don't want to do that) ?

Or, how should I do it?
I would recommend the from scratch method. You might be able to reuse a /home partition if its separate. But I wouldn't try to upgrade an existing 32 bit install to 64bit. 
But keep the 32bit partition and install a 64bit one if you have the room. That way if you have any problems wit the install you should be able to boot into 32bit to search for answers. You could also mount the 32bit partition and transfer files. Then when 64bit is all setup and files transferred delete 32bit.
You could try what you suggest, but its bound to give you nothing but problems.

---

### Post by LinuxConvertJune2006 on 2006-08-02
Thank you for the reply! Yes I was afraid you might say that ;) Oh well, I didn't create a seperate home slice (my bad) I took the default install options when I started using Ubuntu about 1.5 months ago. I do have a second computer running Ubuntu as well, I might just transfer all my files (pictures/movies/email) over to the second computer AND install 64bit on a seperate slice as you suggest (I have the room). That way I have multiple options to get my data back if I decide to keep 64bit Dapper.

I started to download the 64bit ISO while I waited for the reply, so I am ready, I'll probably start this switch tomorrow (too hot even with AC on! in the computer room)

Thanks again for you help, it is much appreciated ! :grin:

---

### Post by RAOF on 2006-08-02
Sadly, **apt** doesn't know that x86-64 processors can run IA32 code.  As far as the package manager is concerned, upgrading from i386 to AMD64 would be like "upgrading" from i386 to PPC - it doesn't make sense.  You need to install everything afresh.

---

