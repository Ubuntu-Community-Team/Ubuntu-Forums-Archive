---
title: "n00b chroot and wine questions"
date: 2006-04-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by rj45 on 2006-04-17
Hi all,

not a n00b to Linux or compiling, etc, just new to chroot and wine

I'm trying to get wine to run on Breezy AMD64.
Following someone's sage advice, I installed a chroot32
and it seems to be working.

Trying to start wine, ie: "wine winemine"

Gives:

Application tries to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.

Question?  Do I need to have an X Server running in my chroot32
environment?

If not, how can I make wine happy?

](*,) 
regards,
rj

---

### Post by jswan on 2006-04-18
Im having the exact same problem!'

---

### Post by Xell on 2006-04-19
I also get this message. I followed the Wiki for installing chroot, installed wine, but when trying to do winecfg I get this. 

I find it frustrating when I follow step-by-step guides and then someting critical is missing. I think that is one of the main reasons why alot of people give up in Linux.

---

### Post by rj45 on 2006-04-19
Yeah, after all the threads about chroot32 and wine,
I figured some guy would know:
"That error means xxx, try running wine --debug,
and post the output."

Not much I can do if someone doesn't help out a bit.
I might try asking the wine folks.

-rj

---

