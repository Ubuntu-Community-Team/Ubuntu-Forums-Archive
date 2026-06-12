---
title: "Black screen problem"
date: 2008-04-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by phyerboss on 2008-04-11
Greetings,

Im trying to run the new Kubuntu7.10 LiveCD. I am pretty much not having any luck to at least test it out or install anything. What happens is, regardless of whatever option or boot method I try, It'll bring up the typical loading graphic and when it tries to go into the login prompt. I get "Black screened".

I tried searching for this issue before posting. But all the ones that came up were for situations AFTER the OS was installed. Is there anyone that might know what is causing this and how I can bypass/resolve it?

My specs:
ECS Geforce6100SM-M V1.0/1.0A with nforce sound & LAN
AMD 4200+ 64 X2AM2
2x 1gb DDR2 533mhz

Thanks

---

### Post by frcr on 2008-04-11
Remove the word "splash" in boot options. You will see black screen while cd will be loading, and have to wait about 1-5 minutes. Then u should see ubuntu desktop.

<snip>

---

### Post by phyerboss on 2008-04-11
Last I recall tech support forums are not chan boards.

I appreciate the advice but if you read what I stated before you posted what you did just now. You would see that I had no luck finding that info. Plus, theres those of us that dont have the time to sit here idling and picking apart posts.

---

### Post by wieman01 on 2008-04-11
There is also an alternate CD which you should give a try. There might an issues with your graphics card or lack of support of the latter.

---

### Post by felker2 on 2008-04-11
I would try the second boot option from the live CD: "Safe Graphics".

---

### Post by phyerboss on 2008-04-11
Heres something odd... 

Kubuntu7.04 was able to run in Live mode just fine. Full sound, vid & LAN. So, that does help solidify that the board is'nt foobared. But when I went to install it and that seemed to have went well. It booted up giving me this error which I seemed to been only getting from Mepis:

"Kernel panic - not syncing: No init found. Try passing init= option to kernel"

Anyone have a clue what that means & why I cant seem to get AROUND it?

---

### Post by phyerboss on 2008-04-12
> **felker2 said:**
> I would try the second boot option from the live CD: "Safe Graphics".

Thanks!

I tried it and no such luck. The video stays on, but I just keep getting that blasted black screen! =\

Im just gonna try the alternate install cd.

---

### Post by phyerboss on 2008-04-12
Ok, I just burned & verified the data of the Alternate install CD. Still no luck. All, Im getting is a blinking cursor.

---

### Post by phyerboss on 2008-04-12
GAAAAHHH!

Tried the 64bit alternate installer. It at least got past having a blinking courser BUT, not it just generates a never ending wall of error code:

*Inconsistency detected by Id.so: ../sysdeps/86_64/dI-machine.h: 416: elf_machine_rela_relative: Assertion '((reloc->r_info) & 0xffffffff) = =8' failed!*

I really cant understand why I seem to be the only guy with 3 boards & cpu's in a row is unable to peacefully get dualcore going^^;

---

